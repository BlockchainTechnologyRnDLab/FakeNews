## [Detecting Fake News With Deep Learning](https://colab.research.google.com/drive/1Hs03msKgDYCLLeP22R5xv_C2OjkG2Elj?usp=sharing)

1. 모듈 import
2. 데이터셋 가져오기
   - [Kaggle](https://www.kaggle.com/clmentbisaillon/fake-and-real-news-dataset#Fake.csv)의 Fake and real news dataset(True.csv/Fake.csv) 
3. 데이터 전처리
    - 내용 중 URL이 있거나 비어있는 데이터 제거
    - True 데이터의 [fake] 속성엔 0, Fake 데이터의 [fake] 속성엔 1으로 라벨링
    - True, Fake 데이터 결합
    - 학습 데이터와 테스트 데이터로 분할
4. 토큰화
    - tensorflow.keras의 Tokenizer 사용
    - 한 글자씩 다 토큰화
5. 모델 생성
    1. Embedding
    2. LSTM
    3. Dense
    4. Activation : ReLU
    5. Dropout : 0.5
    6. Dense
    7. Activation : Sigmoid
6. 모델 학습
    - LSTM layer : 64
    - Batch : 32
    - Epochs : 5
    - Optimizer : Adam
7. 모델 테스트
    - Accuracy : 0.9868

#
###### [Detecting Fake News With Deep Learning - A Simple LSTM Implementation With Keras](https://towardsdatascience.com/detecting-fake-news-with-deep-learning-7505874d6ac5)
