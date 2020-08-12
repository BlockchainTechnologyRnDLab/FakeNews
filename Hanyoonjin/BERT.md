## BERT
- 딥러닝 자연어처리에서 단어를 벡터로 표현하는 단어임베딩은 필수적임
- 심볼인 단어를 실수 벡터로 표현해야 뉴럴네트워크 적용 가능
- BERT에서는 입력 문장의 단어에 대해서 뉴럴넷을 적용한 결과를 단어의 문맥 반영 벡터로 활용
- Transformer의 Self-Attention 모델에서 인코더만을 사용함

### Pre-training(사전 학습)
1. 공백 단어 예측(MLM; Masked Language Model)
- 입력 문장 중, 15%의 단어를 Masking 후 해당 단어를 맞히는 과정
- 양방향 정보를 이용하여 단어 예측
2. 문장 선후관계 예측(NSP; Next Sentence Prediction)
- 임의의 두 문장에 대해, 두 문장이 선/후 관계가 맞는지 맞히는 과정
※ 두 과정 모두 별도의 정답 없이 대용량 말뭉치 데이터로부터 자동으로 생성 가능

### Fine-tuning(응용 단계)
- 언어처리, 문장분류, 기계독해 등에 적용
- 언어처리 : 개체명 인식, 구문 분석 등 언어처리 문제에 적용
- 문장분류 : 단일 문장 주제 분류 또는 두 문장 사이의 유사성 분석 문제에 적용
- 기계독해 : 질문과 단락을 입력 받은 후, 단락에서 정답 경계 인식 문제에 적용

![BERT 기능](https://user-images.githubusercontent.com/60456487/89921360-8ff99800-dc38-11ea-9651-642da03bad88.png)
   ###### 그림 출처 : [NLU Tech Talk with KorBERT](https://www.slideshare.net/LGCNSairesearch/nlu-tech-talk-with-korbert)

### BERT를 사용한 모델링
- 일반 모델링 과정 : 분류를 원하는 데이터 → LSTM, CNN 등의 신경망 → 분류
- BERT를 사용한 모델링 과정 : 대량의 말뭉치 → BERT 사전 학습 → 분류를 원하는 데이터 → LSTM, CNN 등의 신경망 → 분류
- BERT 출력에 모델(신경망)을 추가시켜 원하는 결과를 수행
- 간단한 DNN을 추가해도 다른 신경망과 성능 차이가 거의 없음

### BERT의 내부 동작 과정
1. Input
- Token Embedding : 단어 단위로 토큰화
- Segment Embedding : 토큰화 시킨 단어들을 하나의 문장으로 표현
- Position Embedding : 토큰 순서 표현
※ 두 문장을 구분시켜 각각 하나의 Segment로 지정하여 입력
2. Pre-Training
- MLM과 NSP 두 가지 방식을 사용하여 언어의 특성 학습
- 둘 다 함께 사용하지만 BERT 논문에서는 MLM 방식이 학습에 더 좋은 성능을 보여주고 있다고 밝힘
3. Transfer Learning
- 실제 자연어처리를 수행하는 과정
- 분류를 위한 모델을 추가하는 부분
- 사전학습 모델 BERT를 Fine-tuning하여 사용할 분야에 맞게 재조정
- Classificatoin 부분만 목적에 맞게 수정하여 새로 학습시킴


## KorBERT
- 한국어 BERT 언어 모델
- 모델1 : 한국어의 특성을 반영한 형태소분석 기반의 언어 모델
- 모델2 : 형태소분석을 수행하지 않은 어절 기반의 언어 모델

### 기존 BERT와 KorBERT의 차이점
- KorBERT는 토큰 입력시 형태소 분석을 하여 형태소 태그가 붙은 상태로 전달됨
- 형태소 태그를 붙이면 문맥에 따라 해석이 달라짐 

### Korean_BERT_Morphology	
- 명사/동사에 조사/접미사가 결합된 어절을 의미의 최소 단위인 형태소로 구분하여 분석한 언어 모델
- 어절 기반 언어 모델 보다 우수한 성능을 보임
- 사용하기 위해서는 형태소 분석 API를 사용하여 형태소 분석 후 입력하여야 함

### 형태소 분석 API
- ETRI의 형태소 분석 API : 일 5,000건 횟수 제한
- Saltlux의 ADAM과 카카오의 Khaii의 경우 ETRI의 태그와 동일하기에 사용 가능
- 카카오의 Khaii 형태소 분석기가 분석 정확도가 높은 것으로 알려져있음

![형분석기](https://user-images.githubusercontent.com/60456487/89919229-f6c98200-dc35-11ea-8f9a-be8019fec0f7.png)
   ###### 그림 출처 : [자연어 언어모델 'BERT'_04 한국어 BERT](https://blog.naver.com/jeanmy1102/221747257049)

