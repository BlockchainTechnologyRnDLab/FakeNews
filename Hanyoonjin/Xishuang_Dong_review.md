## Deep Two-path Semi-supervised Learning for Fake News Detection

* 논문 저자 정보 (이름, 소속)   
Xishuang Dong, Uboho Victor, Shanta Chowdhury, Lijun Qian   
Department of Electrical and Computer Engineering,   
Prairie View A&M University, Texas A&M University System, Prairie View, Texas   
2019/06   

* 논문에서 가짜뉴스를 검출하려는 뉴스 종류
  * 소셜 미디어 게시물

* 논문에서 정의하고 있는 가짜뉴스
  * 개인 또는 조직의 이익을 목적으로 독자를 속이기 위해  고의적으로 작성된 정보
  * 스팸 메시지와 유사하게 제한된 단어들을 사용하며, 문법적인 실수 등 문맥상 공통적인 특징들을 가짐

* 논문에서 학습에 사용되는 데이터
  - 데이터의 양 및 취득 방법(또는 경로)
    - PHEME dataset (Zubiaga et al., 2016b) : 특정 사건별로 트윗 정리
    
      | Event | Tweets | Fake | True |
      |---|---|---|---|
      |GC|4,651|2,637|2,014|
      |CH|40,178|7,697|32,481|
      |SS|25,221|9,046|16,175|
      |FE|25,054|6,686|18,368|
      |OS|12,656|6,624|6,032|
      |**Total**|**107,760**|**32,690**|**75,070**|
      
      ###### Event : 사건 내용
      
      LOEO(Leave-one-event-out) 교차 검증(Kochkina et al.,2018)을 사용하여 학습 데이터와 테스트 데이터의 개수가 다를 수 있음

  - 데이터 전처리 방법 : X
 
* 논문에서 사용하는 알고리즘  
  - 사용한 머신러닝 알고리즘 종류 : CNN
  - 학습 방식 : 지도학습 / 비지도학습
  - 신경망을 사용할 경우 네트워크 내용
    1. 공유 CNN
        - 컨볼루션 레이어 3개 : 각각 128개(3×3) 필터 포함
        - 최대 풀링(2×2) 레이어
        - 컨볼루션 레이어 3개 : 각각 256개(3×3) 필터 포함
        - 최대 풀링(2×2) 레이어
    2. 지도학습 CNN
        - 512개(3×3) 필터, 256개(3×3) 필터, 128개(3×3) 필터
        - Softmax
        - Cross entropy(교차 엔트로피 손실)
    3. 비지도학습 CNN
        - 512개(3×3) 필터, 256개(3×3) 필터, 128개(3×3) 필터
        - Mean squared error(평균 제곱 오차)
    4. 지도학습 CNN과 비지도학습 CNN의 결과를 동시에 최적화하기 위한 가중치 적용
    5. 최적화
    
    [사진 출처](https://www.researchgate.net/figure/Framework-of-deep-two-path-semi-supervised-learning-DTSL-Samples-x-i-are-inputs_fig1_333773193)
    
    ![img](https://www.researchgate.net/profile/Uboho_Victor2/publication/333773193/figure/fig1/AS:769538295603204@1560483635675/Framework-of-deep-two-path-semi-supervised-learning-DTSL-Samples-x-i-are-inputs.png "구조")
    
    

  - **(검토자 의견) 알고리즘이 논문에서 정의하는 가짜 뉴스를 검출하기에 적합한지 검토 의견** 

* **오픈소스 공개 여부** 

* 논문의 평가
  - 논문에서 주장하는 내용 
    - 지도 학습과 비지도 학습을 모두 사용하여 가짜뉴스 검출에 성능을 높임
    - 라벨링되어 있지 않은 데이터로 학습하여도 제안된 모델(DTSL; Deep Two-path Semi-supervised Learning)이 가짜뉴스를 효과적으로 검출할 수 있음
    - 지도 학습 방식을 사용하는 모델들은 소셜미디어에서 빠른 속도로 퍼지는 가짜뉴스들을 효과적으로 검출할 수 없음
  - 논문 결과 (정량적 또는 정성적 결과)
  
      | Event | F-score |
      |---|---|
      |Naive Bayes|41.24%|
      |Decision Tree|33.03%|
      |AdaBoost|20.43%|
      |SVM|12.56%|
      |BRNN|35.85%|
      |**DTSL (5%)**|**53.90%**|
      |**DTSL (10%)**|**61.53%**|
      |**DTSL (30%)**|**57.98%**|
      
      - 라벨링된 데이터의 비율을 증가시키면 성능도 향상됨
      - 30%로 비율을 높였을 때 성능이 감소하는데, 이는 교육 데이터와 테스트 데이터 간의 데이터 분포 차이임

  - **(검토자 의견) 논문 결과에 대한 객관성에 대한 검토의견** 


