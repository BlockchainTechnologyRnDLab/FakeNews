## FNDNet – A deep convolutional neural network for fake news detection

* 논문 저자 정보 (이름, 소속)   
Rohit Kumar Kaliyar1, Anurag Goswami1, Pratik Narang2, Soumendu Sinha3
1. Department of Computer Science Engineering, Bennett University, Greater Noida, India
2. Department of CSIS, BITS Pilani, Rajasthan, India
3. Smart Sensors Area, CSIR - Central Electronics Engineering Research Institute, Pilani, Rajasthan, India
2020/01

* 논문에서 가짜뉴스를 검출하려는 뉴스 종류
  * 소셜 미디어의 텍스트 뉴스

* 논문에서 정의하고 있는 가짜뉴스
  * 문장에서 주제와 맞지 않고, 근거가 없는 선동적인 주장을 보이는 뉴스

* 논문에서 학습에 사용되는 데이터
  - 데이터의 양 및 취득 방법(또는 경로)
    - Kaggle 가짜뉴스 데이터셋
  - 데이터 전처리 방법
    - GloVe(Global Vectors for Word Representation)을 사용한 단어 임베딩
      - Word2Vec : 중심 단어로 주변 단어를, 주변 단어로 중심 단어를 예측하는 과정에서 단어를 벡터로 임베딩
      - GloVe : 벡터로 임베딩하는 것은 같지만 병렬 구현으로 Word2Vec보다 대규모 데이터셋 학습에 유리
      - 단어마다 가중치를 주게 되는데, the 및 an 같은 의미없는 중지 단어에는 가중치를 낮춰 학습에 방해되지 않게 함

  -  **(검토자 의견) 데이터 객관성 여부에 대한 검토 의견**  


* 논문에서 사용하는 알고리즘  
  - 사용한 머신러닝 알고리즘 종류 : CNN
  - 학습 방식 : 지도학습
  - 신경망을 사용할 경우 네트워크 내용
    1. 입력 데이터 단어 임베딩
    2. 3개의 컨볼루션 레이어+최대 풀링 레이어에 모두 같은 임베딩 벡터 통과
        - 중요한 단어의 수를 정확하게 정의하기 위하여
    3. 출력을 통합한 후 효율적인 결과를 위하여 2개의 컨볼루션 레이어 통과(활성화 함수 : ReLU)
    4. Flatten layer : 완전 연결 레이어로 전달하기 위해 컨볼루션을 거친 2차원 데이터를 1차원으로 변환
    5. Dense layer or fully connected layer) : softmax 분류(Dropout : 0.2)

      |Hyperparameter|Description or value| 
      |---|---|
      |No. of convolution layers|5|
      |No. of max pooling layers|5|
      |No. of dense layers|4|
      |Dropout rate|0.2|
      |Activation function|ReLU|

  - **(검토자 의견) 알고리즘이 논문에서 정의하는 가짜 뉴스를 검출하기에 적합한지 검토 의견** 


* **오픈소스 공개 여부** 


* 논문의 평가
  - 논문에서 주장하는 내용
    - 이전 실험에서 머신러닝 기반 모델은 데이터가 많아질 수록 성능이 저하되는 것이 보였음 
    - 딥러닝에 사전 훈련된 임베딩 모델을 추가하여 구현해야 한다고 생각함
    - 결과로 본 논문은 CNN을 기반으로 하는 FNDNet을 제안했음
    - 제안된 모델과 다른 여러 개의 모델을 비교하였음
    - 기존의 머신러닝 및 딥러닝 기반 구현보다 우수한 성능(높은 정확도)을 보였음
    - 향후 **BERT**를 사용하여 딥러닝 기반 가짜뉴스 탐지 모델을 구현할 것임
  - 논문 결과 (정량적 또는 정성적 결과)

      |Word Embedding Model|Classification Model|Precision|Recall|F1-Score|Accuracy|
      |---|---|---|---|---|---|
      |Tf-Idf|Neural Network|95.31|92.78|94.03|94.31|
      |BoW|Neural Network|91.45|87.67|89.57|89.23|
      |Word2Vec|Neural Network|80.23|72.34|76.08|75.67|
      |GloVe|Mutinomial Naive Bayes|88.99|92.48|90.70|89.97|
      |GloVe|Decision Tree|68.56|86.97|73.68|73.65|
      |GloVe|Random Forest|68.95|77.41|72.94|71.34|
      |GloVe|KNN|52.31|80.69|63.37|53.75|
      |GloVe|CNN|90.74|92.07|91.40|91.50|
      |GloVe|LSTM|99.20|95.49|97.31|97.25|
      |**GloVe**|**Our Proposed model (FNDNet)**|**99.40**|**96.88**|**98.12**|**98.36**|


  - **(검토자 의견) 논문 결과에 대한 객관성에 대한 검토의견** 
