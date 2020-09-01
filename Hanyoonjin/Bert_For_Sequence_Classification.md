## BertForSequenceClassification

<pre>
from transformers import BertForSequenceClassification

(bert): BertModel(
    (embeddings): BertEmbeddings(   <b>// BERT는 세 가지의 입력 벡터가 있어야 함</b>
      (word_embeddings): Embedding(119547, 768, padding_idx=0)   <b>// 단어 임베딩</b>
      (position_embeddings): Embedding(512, 768)   <b>// 단어의 위치 임베딩</b>
      (token_type_embeddings): Embedding(2, 768)   <b>// 어느 문장에 속하는 단어인지 타입 임베딩</b>
      (LayerNorm): LayerNorm((768,), eps=1e-12, elementwise_affine=True)   <b>// Normalization : 레이어마다 평균 출력을 정규화하여 입력 분포를 일정하게 함으로써 학습 효율이 높아짐</b>
      (dropout): Dropout(p=0.1, inplace=False)   <b>// 네트워크 생략</b>
    )
    (encoder): BertEncoder(   <b>// Encoder 부분</b>
      (layer): ModuleList(
        (0): BertLayer(   <b>// BERT의 Attention과 intermediate(Feed-forward Network)를 반복하게 됨</b>
          (attention): BertAttention(
            (self): BertSelfAttention(   <b>// 입력 벡터 Query/Key/Value를 이용한 단어들의 연관성 계산</b>
              (query): Linear(in_features=768, out_features=768, bias=True)
              (key): Linear(in_features=768, out_features=768, bias=True)
              (value): Linear(in_features=768, out_features=768, bias=True)
              (dropout): Dropout(p=0.1, inplace=False)
            )
            (output): BertSelfOutput(
              (dense): Linear(in_features=768, out_features=768, bias=True)
              (LayerNorm): LayerNorm((768,), eps=1e-12, elementwise_affine=True)
              (dropout): Dropout(p=0.1, inplace=False)
            )
          )
          (intermediate): BertIntermediate(   <b>// 특징을 더 큰 차원으로 늘렸다가 다시 줄임</b>
            (dense): Linear(in_features=768, out_features=3072, bias=True)
          )
          (output): BertOutput(   <b>//intermediate에선 Linear Layer 사이에 활성화함수로 GELU를 사용, GELU는 ReLU와 유사하지만 음수에 대해서도 미분이 가능</b>
            (dense): Linear(in_features=3072, out_features=768, bias=True)
            (LayerNorm): LayerNorm((768,), eps=1e-12, elementwise_affine=True)
            (dropout): Dropout(p=0.1, inplace=False)
          )
        )

   　·  ·  ·   BertLayer 반복　·  ·  ·   

    (pooler): BertPooler(   <b>// 입력신호를 (−1,1) 사이의 값으로 정규화</b>
      (dense): Linear(in_features=768, out_features=768, bias=True)
      (activation): Tanh()   <b>// 논문엔 GELU를 사용한다고 했는데 코드는 Tanh 해둠</b>
    )
  )
  (dropout): Dropout(p=0.1, inplace=False)
  (classifier): Linear(in_features=768, out_features=2, bias=True)   <b>// Softmax를 통한 분류</b>
)
</pre>


###### ※ BertForSequenceClassification 대신 BertModel 모듈을 가져와서 따로 분류 계층을 생성할 수 있음
