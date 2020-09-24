## BERT Word Vector
- BERT Encoder 과정에서 출력되는 토큰의 벡터를 사용하여 유사성 비교
- 결과물을 시각화하여 보여줄 수 있도록 시도

### 1. BERT Classifier 과정이 없는 모델 사용
```python
tokenizer = BertTokenizer.from_pretrained('bert-base-uncased')     // BertTokenizer 사용

text = "After stealing money from the bank vault, the bank robber was seen " \     // 벡터 비교 테스트에 사용될 문장
       "fishing on the Mississippi river bank."

marked_text = "[CLS] " + text + " [SEP]"     // 입력 데이터 전처리

tokenized_text = tokenizer.tokenize(marked_text)     // 토큰화

indexed_tokens = tokenizer.convert_tokens_to_ids(tokenized_text)     // 토큰 인덱싱

segments_ids = [1] * len(tokenized_text)

model = BertModel.from_pretrained('bert-base-uncased',
                                  output_hidden_states = True,     // 출력으로 hidden_states 내용을 받으려면 True 설정
                                  )

``` 

### 2. 입력 후 Encoder를 거친 결과를 얻음
```python
outputs = model(tokens_tensor, segments_tensors)     // tensor 변환한 값을 입력하고 출력값을 얻음

token_output = outputs[0]     // 단어마다 개별적으로 벡터 표현
pooler_output = outputs[1]     // pooler 출력, 전체 시퀀스 벡터 표현
hidden_states = outputs[2]     // 레이어마다 단어 벡터 표현
```

### 3. 'bank' 단어끼리의 cosine 유사성 비교
```python
same_bank = 1 - cosine(token_output[0][10], token_output[0][6])     // 은행=은행
diff_bank = 1 - cosine(token_output[0][10], token_output[0][19])     // 은행!=강둑

print('같은 의미 단어 비교:  %.2f' % same_bank)
print('다른 의미 단어 비교:  %.2f' % diff_bank)
```
```
[Output]
같은 의미 단어 비교:  0.95
다른 의미 단어 비교:  0.70
```

### 4. Linear와 Activation을 임의로 설정
```python
m = torch.nn.Linear(768, 1)
n = torch.nn.ReLU()
```

### 5. 토큰 순서대로 함수 호출
```python
for i, token_str in enumerate(tokenized_text):     // 토큰 하나씩 반복
  if token_str == "[CLS]" or token_str == "[SEP]"  :     // 태그 과정은 넘어감
    continue 
    
  vis(i, token_str)     // 함수 호출
```

### 6. NN
```python
def vis(i, token_str):
  output = m(token_output[0][i])     // 선형 레이어를 사용하여 차원 축소
  output = n(output)     // ReLU
  output= np.max(output.detach().numpy())     // Tensor→Float
    
  call_html(i, output, token_str)     // HTML로 시각화하는 함수 호출
```

### 7. HTML로 시각화하는 함수
```python
def call_html(i, output, token_str):
  color = str(int(round(output*800)))     // 결과물을 표시하기 위한 값 생성
  H = "<script type='text/javascript'> var span = document.createElement('span');" \
      "var newContent = document.createTextNode('"+token_str+" '); span.appendChild(newContent);" \
      "span.style.color='rgb("+color+",0,0)'; document.body.appendChild(span); </script>"
  display(HTML(H))
```

### 8. 결과물
![bank](https://user-images.githubusercontent.com/60456487/94177652-dc412480-fed4-11ea-9aba-f33584f37869.png)
