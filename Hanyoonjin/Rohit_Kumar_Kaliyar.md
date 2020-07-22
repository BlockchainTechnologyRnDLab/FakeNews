## Fake News Detection Using A Deep Neural Network

* 논문 저자 정보 (이름, 소속)   
Rohit Kumar Kaliyar   
Computer Science & Engineering, Bennett University   
Greater Noida, India   

* 논문에서 가짜뉴스를 검출하려는 뉴스 종류
  - 다양한 사이트에서 조작되어 소셜미디어를 통해 쉽게 퍼질 수 있는 텍스트 뉴스

* 논문에서 정의하고 있는 가짜뉴스
  - 의도적으로 퍼트리는 잘못된 정보(재검토)

* 논문에서 학습에 사용되는 데이터
  - 데이터의 양 및 취득 방법(또는 경로)
    - [kaggle](https://www.kaggle.com)에서 제공 받은 약 8000개의 데이터(가짜뉴스 진짜뉴스 혼합)
  - 데이터 전처리 방법
    - TF-IDF(Term Frequency-Inverted Document Frequency) : 문서 내에서 어떤 단어의 중요도에 따라 가중치를 결정
  -  **(검토자 의견) 데이터 객관성 여부에 대한 검토 의견**  
  
* 논문에서 사용하는 알고리즘  
  - 사용한 머신러닝 알고리즘 종류 
    1. Naïve Bayes Model(머신러닝)
        - 정보의 단어를 모두 토큰화시켜서 분류기의 입력으로 사용
        - BoW처럼 단어의 빈도수를 고려
        - 단어들의 특성으로 다른 정보와 분류
    2. Decision Tree(머신러닝)
        - 특정 속성에 따라 데이터를 구분
    3. Random Forest(머신러닝)
        - 랜덤으로 뽑은 특성을 기반으로 여러 개의 결정 트리를 생성하여 합치는 방식
    4. K nearest neighbor(머신러닝)
        - 데이터 입력시 가장 가까이 있는 것을 중심으로 데이터 종류를 정해줌
    5. CNN&LSTM(딥러닝)
        - CNN : 텍스트 분류
        - LSTM : 단어 사이의 관계 정보를 기억
        - 둘의 조합으로 구현하였으나 정확한 구조는 설명이 없음

  - 학습 방식 : 지도학습
  - 신경망을 사용할 경우 네트워크 내용
    - CNN : ReLU / Pooling / Padding
  - **(검토자 의견) 알고리즘이 논문에서 정의하는 가짜 뉴스를 검출하기에 적합한지 검토 의견** 

* **오픈소스 공개 여부 : X**

* 논문의 평가
  - 논문에서 주장하는 내용 
    - 자연어 처리, 머신러닝 및 딥러닝의 다양한 모델을 사용하여 비교하고, 가짜뉴스와 실제뉴스가 포함된 데이터셋을 소개함

  - 논문 결과 (정량적 또는 정성적 결과)
    - 정확도
      1. CNN&LSTM : 97.3%
      2. Naïve Bayes Model : 89%
      3. Decision Tree : 73%
      4. Random Forest : 71%
      5. K nearest neighbor : 53%

  - **(검토자 의견) 논문 결과에 대한 객관성에 대한 검토의견** 
    - 다른 머신러닝 알고리즘을 이용한 정밀도 및 재현도 결과는 나와있었으나 CNN&LSTM의 결과만 나와있지 않았기에 정리하지 않음. 네트워크 구조도 알 수 없어 모델의 성능을 평가하기 힘듦

* 분류 모델을 평가하는 기준 
1. 모델이 얼마나 정밀한가
2. 얼마나 실용적인 분류를 했는가
3. 얼마나 정확한 분류를 했는가

※ Confusion Matrix는 모든 기준을 평가할 수 있음

* Confusion Matrix에서 3가지의 척도 평가
1. 정확도(Accuracy) : 정확하게 분류되었는지 평가
2. 정밀도(Precision) : 모델이 True라고 분류한 것 중에서 실제 True인 것의 비율
3. 재현도(Recall) : 실제 True인 것 중에서 모델이 True라고 예측한 것의 비율

* F1 Score
  - Precision과 Recall의 조화평균
