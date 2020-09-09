## [FakeNews-Classifier](https://colab.research.google.com/drive/1_mXtFYPXfSJtFpt1zscTRgU803tBhKUj?usp=sharing)

1. 모듈 import
2. 데이터셋 가져오기
    - [Kaggle](https://www.kaggle.com/c/fake-news/)의 Fake-news dataset(Train.csv) 
3. 토큰화
    - tensorflow.keras의 Tokenizer 사용
    - 토큰 인덱스 변환
4. 데이터 분할
    - 학습 데이터와 검증 데이터로 분할
5. Glove를 사용한 특징 벡터 추출
6. 모델 생성
      1. Embedding : Glove
      2. Dropout : 0.2
      3. Conv1D : 64
      4. Activation : ReLU
      5. MaxPooling1D : 4
      6. LSTM
      7. LSTM
      8. Dropout : 0.2
      9. Dense
      10. Dropout : 0.3
      11. Dense
      12. Dense
      13. Activation : Sigmoid
6. 모델 학습
    - LSTM layer : 20
    - Batch : 100
    - Epochs : 5
    - Optimizer : Adam
7. 모델 테스트
    - Accuracy : 0.9413

#
###### [How to build a recurrent neural network to detect fake news](https://towardsdatascience.com/how-to-build-a-recurrent-neural-network-to-detect-fake-news-35953c19cf0b)
