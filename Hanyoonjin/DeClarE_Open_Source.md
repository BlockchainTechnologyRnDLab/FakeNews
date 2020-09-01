## [DeClarE](https://github.com/atulkumarin/DeClare)
- 설명해주지 않음
- Glove를 사용하여 각 단어에 가중치를 준다는 그림이였음
- 사람들이 신뢰할 수 있도록 설명한다 하였지만 설명을 생성하는 단계가 없음(잘못 해석)
- 문맥을 파악하고 기사를 비교하고 기사의 출처에 따라 신뢰도가 달라지는 모델

### 단계

1. 필요한 모듈 import
2. 데이터셋 다운로드
    - Snopes
    - PolitiFact
    - 내용에 맞는 기사들 연결하여 데이터 정리
3. Glove를 이용한 데이터 전처리
4. 모델 생성
    - num_epochs = 20
    - batch_size = 64   // 한 번에 처리하는 데이터 개수
    - nb_lstm_units = 64   // LSTM layers
    - 기사, 관련기사, 관련기사의 출처 등 데이터 사용
<pre>DeClareModel(
  (word_embeddings): Embedding(56755, 100)
  (claim_source_embeddings): Embedding(4342, 4)
  (article_source_embeddings): Embedding(12237, 8)
  (attention_dense): Linear(in_features=200, out_features=1, bias=True)
  (attention_dropout): Dropout(p=0.5)
  (dense_1): Linear(in_features=140, out_features=64, bias=True)
  (dense_1_dropout): Dropout(p=0.5)
  (dense_2): Linear(in_features=64, out_features=64, bias=True)
  (dense_2_dropout): Dropout(p=0.5)
  (output_layer): Linear(in_features=64, out_features=1, bias=True)
  (biLSTM): LSTM(100, 64, batch_first=True, bidirectional=True)
)</pre>
5. 최적화
    - Adam 사용
6. 모델 학습 및 테스트
