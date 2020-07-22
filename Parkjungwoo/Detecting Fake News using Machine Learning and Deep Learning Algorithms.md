 # Detecting Fake News using Machine Learning and Deep Learning Algorithms
 
* 논문 저자 정보 (이름, 소속)
  - Abdullah-All-Tanvir, Ehesas Mia Mahir, Saima Akhter, Mohmmad Rezwanul Huq
   East West University, Bangladesh, 2019 
   
* 논문에서 가짜뉴스를 검출하려는 뉴스 종류
  - 트위터에서의 뉴스(소셜미디어)
   정부문제, 세계 유행주제, 정신적 학대, 도시의 전설, 재난사건 등의 여러종류의 트윗
 
* 논문에서 정의하고 있는 가짜뉴스
  - 뉴스정의가 아닌 트윗을 분류 (가짜, 실수, 사실이 아닌)
 
* 논문에서 학습에 사용되는 데이터
  - 데이터의 양 및 취득 방법(또는 경로)
    - 메릴랜드 대학교의 교수로 부터 데이터 ,Chile Earthquake 2010 Dataset, 데이터양 : 20,360개의 데이터
  - 데이터 전처리 방법
    - 데이터셋 처리
      - 데이터 집합을 H : 가짜, 나쁜의도를 가진 트윗 , N : 실수, 나쁜의도를 가지지않은 트윗으로분류
      - 트윗의 단어길이를 분석 : 인증되지 않은 뉴스 컨텐츠가 많은 제목, 단어 및 허구의 진술, 링크, 날짜 또는 표시가 없는 부분
    - Count Vectors
    - TF_IDF
      - World Level
      - N-gram Level
      - Character Level
    - Word Embedding : 단어와 문서를 벡터로 표현
   
  - 개발 관련 구현언어 : Python 3.65.
  
* 논문에서 사용하는 알고리즘  
  - 사용한 머신러닝 알고리즘 종류
   1. SVM
   2. NaiveBayes
   3. LR (Logistic Regression)
   4. Recurrent Neural Network(RNN)
   5. Long short-term memory
  - 학습 방식 : 지도(분류기) + 강화(RNN)
  - 신경망을 사용할 경우 네트워크 내용
     - LSTM 이용 : 임베디드레이어, 숨겨진레이어, 입/출력 레이어, Sigmoid 활성화 함수와 glorot_nomal사용 
    
* **오픈소스 공개 여부** : X
* 논문의 평가 : 5가지의 알고리즘과, 신경망을 활용한 결과를 한눈에 수치를 알아 볼 수 있는 논문
* 논문 결과 (정량적 또는 정성적 결과)  
  - SVM과 Naive Bayes가 다른알고리즘보다 우수
  - 제안하는 4가지의 벡터 (Count Vector, World Level Vectors, N-gram Vectors, Character Level Vectors) 비교 
  - LSTM과 알고리즘을 사용하여 가짜트윗 결과를 도출


* LSTM을 이용한 모델과 알고리즘을 활용한 가짜트윗 결과

      - 교차검증 후 정확도
  
|classifires|count Vector|TF-IDF|
|--|----------|---|
|LR|62.47%|69.47%|
|NB|84.56%|89.06%|
|SVM|89.34%|89.34%|

      - 딥러닝 알고리즘 적용 후 정확도
  
|classifires|Defalut|with Kernel Initialization|
|--|----------|---|
|Long Shot-Term Memory|73%|76%|
|Recurrent Neural Network|74%|73%|
  
      - NB,LR,SVM의 Precision,Recall,F1-Score 점수 ***(앞발표에 지적하신 참고사항 토대로 , 정리다시한번할 것)

||Precision|Recall|F1-Score|
|--|--|----------|---|
|NB|0.89|0.99|0.94|
|LR|0.89|0.75|0.81|
|SVM|0.89|1.0|0.94|
