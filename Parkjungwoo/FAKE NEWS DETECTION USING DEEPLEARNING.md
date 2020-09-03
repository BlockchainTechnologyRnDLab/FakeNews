## FAKE NEWS DETECTION USING DEEPLEARNING

 * 논문 저자 정보 (이름, 소속)
   - Álvaro Ibrain Rodríguez, Department of Computer Science University of Cantabria, Spain, 2019.12.29

 * 논문에서 가짜뉴스를 검출하려는 뉴스 종류
   - Kaggle, 뉴욕타임즈,워싱턴포스트 웹사이트의 가짜뉴스

 * 논문에서 정의하고 있는 가짜뉴스: 무엇을 가짜뉴스라 규정하고 있는지 정리
   - 편견, 클릭베이트,가짜, 정치적 또는 사실과 무관한 여러범주로 분류된 수백만개의 기사 
  
 * 논문에서 학습에 사용되는 데이터
   - TI-CNN 데이터셋  
     - https://github.com/several27/FakeNewsCorpus
   - Kaggle, 뉴욕타임즈, 워싱턴포스트 웹크롤링, 20015개의 데이터(가짜 : 11941 + 진짜 : 8074)
     - https://drive.google.com/file/d/0B3e3qZpPtccsMFo5bk9Ib3VCc2c/view
   
 * 데이터의 양 및 취득 방법(또는 경로)
   - 웹크롤링 및 GitHub, GoogleDrive
  
 * 데이터 전처리 방법
   - BERT
     1)입력 시퀀스입력
     2)attention mechanisms에 따라 관련성이 높은 부분 결정
     3)텍스트요약 : 인코더(아이디어 표현을 만듦) - 디코더(표현을 취하고 다른 시퀀스 생성) 작업 
      ![En/decoder](https://github.com/MDPJW/FakeNews/blob/master/image/Incoder-Decoder.PNG)

 * 논문에서 사용하는 알고리즘
   - RNN, CNN, BERT

 * 사용한 머신러닝 알고리즘 종류
  학습 방식 : 지도학습
 * 신경망을 사용할 경우 네트워크 내용    
   - LSTM Based(RNN 신경망)    
   - Convolucional Based(CNN 신경망)    
   - BERT 
     - 12개의 블록과 , 24개의 블록으로 학습 모델 제안
     - 추가레이어 구성 및 활성화 함수로 시그모이드와 소프트맥스 함수 사용
     - 마지막 계층의 뉴런 수는 분류문제이고 이진 분류 문제(참/거짓 인경우) 출력 뉴런수는 2
     - 입력데이터 형식은 텍스트만으로 함. 문자열, 토큰화 및 분리 프로세스 모델의 기능에 포함
     - 토큰화는 WordPiece 전략을 따름 (Ex, do + ing 결합하여 수행)
     - 사용가능한 어휘를 증가하여 잠재적인 out of vocabulary를 최소화 함.
     - BERT는 하나의 입력 벡터만 허용, 제목과 기사 본문이 연결되어 있음.

 * 논문에서 주장하는 내용
   - 해마다 증가하는 가짜뉴스로 강력한 속임수를 구별하기 위한 강력한 시스템이 필요함.
   - LSTM, Convolucional Based, BERT를 다음과 같이 제안하고 신경망을 훈련시켜 가짜뉴스 탐지가 현실에 적용 될 수 있기를 바람.
   
 * 논문 결과 (정량적 또는 정성적 결과)
     
 |Model|Acurracy(%)|
 |-----|-----------|
 |LSTM|0.91|
 |Convolution|0.937|
 |BERT|0.98|
