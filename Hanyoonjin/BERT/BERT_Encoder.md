## BERT Encoder
1. BERT는 Transformer의 Encoder만 사용함
2. Transformer의 Encoder와 차이점은 단어 토큰뿐만 아니라 토큰의 순서 정보, 토큰이 소속된 문장 정보를 포함한다는 점

#

### Scaled Dot Product Attention : Self-Attention이 일어나는 단계
``` python
class ScaledDotProductAttention(nn.Module):
    def __init__(self, config):
        super().__init__()
        self.config = config
        self.dropout = nn.Dropout(config.dropout)
        self.scale = 1 / (self.config.d_head ** 0.5)
    
    def forward(self, Q, K, V, attn_mask):
        scores = torch.matmul(Q, K.transpose(-1, -2))     // ㅡ*ㅣ : Query와 Key의 단어 유사도 측정(내적한 결과 반환)
        scores = scores.mul_(self.scale)     // 가중치 편차 줄이기
        scores.masked_fill_(attn_mask, -1e9)     // word가 아닌 부분(padding된 부분)인지 확인하고 필요 없는 부분이면 가중치 확 줄임

        attn_prob = nn.Softmax(dim=-1)(scores)     // 가중치를 확률로 변환, mask한 부분은 모두 0으로 변환
        attn_prob = self.dropout(attn_prob)

        context = torch.matmul(attn_prob, V)     // 가중치*Value 벡터 생성

        return context, attn_prob
```

#

### Multi-Head Attention
``` python
class MultiHeadAttention(nn.Module):
    def __init__(self, config):
        super().__init__()
        self.config = config

        self.W_Q = nn.Linear(self.config.d_hidn, self.config.n_head * self.config.d_head)     // 768 → 12*64(=768)
        self.W_K = nn.Linear(self.config.d_hidn, self.config.n_head * self.config.d_head)
        self.W_V = nn.Linear(self.config.d_hidn, self.config.n_head * self.config.d_head)
        self.scaled_dot_attn = ScaledDotProductAttention(self.config)     // Self-Attention
        self.linear = nn.Linear(self.config.n_head * self.config.d_head, self.config.d_hidn)
        self.dropout = nn.Dropout(config.dropout)
    
    def forward(self, Q, K, V, attn_mask):
        batch_size = Q.size(0)
        q_s = self.W_Q(Q).view(batch_size, -1, self.config.n_head, self.config.d_head).transpose(1,2)     // view : tensor의 모양 변경
        k_s = self.W_K(K).view(batch_size, -1, self.config.n_head, self.config.d_head).transpose(1,2)     // Q/K/V를 head 수로 나눔
        v_s = self.W_V(V).view(batch_size, -1, self.config.n_head, self.config.d_head).transpose(1,2)     // n_head : Head 수 / d_head : 차원 수

        attn_mask = attn_mask.unsqueeze(1).repeat(1, self.config.n_head, 1, 1)

        context, attn_prob = self.scaled_dot_attn(q_s, k_s, v_s, attn_mask)     // ScaledDotProductAttention 클래스 사용으로 각 head별 Attention 계산
        context = context.transpose(1, 2).contiguous().view(batch_size, -1, self.config.n_head * self.config.d_head)     // 여러 개의 head를 하나로 합침, 순서 유지 가능

        output = self.linear(context)     // 최종 Multi-Head Attention 값 생성
        output = self.dropout(output)
        return output, attn_prob
```

#

### Feed-Forward Network : 각 head가 만들어낸 Self-Attention을 치우치지 않게 균등하게 섞는 역할
``` python
class PoswiseFeedForwardNet(nn.Module):
    def __init__(self, config):
        super().__init__()
        self.config = config

        self.conv1 = nn.Conv1d(in_channels=self.config.d_hidn, out_channels=self.config.d_ff, kernel_size=1)
        self.conv2 = nn.Conv1d(in_channels=self.config.d_ff, out_channels=self.config.d_hidn, kernel_size=1)
        self.active = F.gelu
        self.dropout = nn.Dropout(config.dropout)

    def forward(self, inputs):
        output = self.conv1(inputs.transpose(1, 2))     // 특징 벡터 크기를 크게 키움
        output = self.active(output)     // Activation 함수 실행
        output = self.conv2(output).transpose(1, 2)     // 다시 줄임
        output = self.dropout(output)
        return output
```

#

### Encoder Layer
``` python
class EncoderLayer(nn.Module):
    def __init__(self, config):    // 준비
        super().__init__()
        self.config = config

        self.self_attn = MultiHeadAttention(self.config)    // MultiHeadAttention : Head가 여러 개인 Self-Attention
        self.layer_norm1 = nn.LayerNorm(self.config.d_hidn, eps=self.config.layer_norm_epsilon)     // 레이어 정규화
        self.pos_ffn = PoswiseFeedForwardNet(self.config)     // FeedForward
        self.layer_norm2 = nn.LayerNorm(self.config.d_hidn, eps=self.config.layer_norm_epsilon)
    
    def forward(self, inputs, attn_mask):     // Encoder 실행
        att_outputs, attn_prob = self.self_attn(inputs, inputs, inputs, attn_mask)     // Attention한 결과(단어 관계 계산 결과)
        att_outputs = self.layer_norm1(inputs + att_outputs)
        ffn_outputs = self.pos_ffn(att_outputs)     // Attention 결과를 정규화한 값을 입력으로 Feed-Forword 실행
        ffn_outputs = self.layer_norm2(ffn_outputs + att_outputs)     // 정규화 값과 Feed-Forword 값을 더한 후 다시 정규화 실행
        return ffn_outputs, attn_prob
        // ffn_outputs : Attention Value / attn_prob : 단어의 가중치 확률분포
```

#

### Encoder
``` python
class Encoder(nn.Module):
    def __init__(self, config):
        super().__init__()
        self.config = config     // BERT 모델 세부 사항이 작성된 config 파일 호출

        self.enc_emb = nn.Embedding(self.config.n_enc_vocab, self.config.d_hidn)
        self.pos_emb = nn.Embedding(self.config.n_enc_seq + 1, self.config.d_hidn)     // Position Embedding : 단어 위치 임베딩
        self.seg_emb = nn.Embedding(self.config.n_seg_type, self.config.d_hidn)     // Segment Embedding : 두 개의 문장이 입력될 경우 문장 구분을 위한 임베딩

        self.layers = nn.ModuleList([EncoderLayer(self.config) for _ in range(self.config.n_layer)])     // EncoderLayer 실행 생성
    
    def forward(self, inputs, segments):
        positions = torch.arange(inputs.size(1), device=inputs.device, dtype=inputs.dtype).expand(inputs.size(0), inputs.size(1)).contiguous() + 1
        pos_mask = inputs.eq(self.config.i_pad)
        positions.masked_fill_(pos_mask, 0)     // 입력 데이터 크기에 맞게 패딩 채우기

        outputs = self.enc_emb(inputs) + self.pos_emb(positions)  + self.seg_emb(segments)     // 입력 데이터 생성

        attn_mask = get_attn_pad_mask(inputs, inputs, self.config.i_pad)     // 토큰 마스킹 데이터 생성

        attn_probs = []
        for layer in self.layers:     // 각 Layer 실행, Layer의 입력은 이전 Layer의 출력 값
            outputs, attn_prob = layer(outputs, attn_mask)     // 입력 데이터 / 마스킹 데이터 입력
            attn_probs.append(attn_prob)
        return outputs, attn_probs
```

#

### BERT
``` python
class BERT(nn.Module):
    def __init__(self, config):
        super().__init__()
        self.config = config

        self.encoder = Encoder(self.config)     // Transformer Encoder 클래스

        self.linear = nn.Linear(config.d_hidn, config.d_hidn)
        self.activation = torch.tanh
    
    def forward(self, inputs, segments):
        outputs, self_attn_probs = self.encoder(inputs, segments)
        outputs_cls = outputs[:, 0].contiguous()     // 결과의 첫 번째 토큰([CLS]) 저장(분류할 문장)
        outputs_cls = self.linear(outputs_cls)
        outputs_cls = self.activation(outputs_cls)     // Linear와 Activation 함수를 통한 분류
        return outputs, outputs_cls, self_attn_probs
```
