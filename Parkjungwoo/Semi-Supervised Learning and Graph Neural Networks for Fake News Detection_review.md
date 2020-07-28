  # Semi-Supervised Learning and Graph NeuralNetworks for Fake News Detection

* 논문 저자 정보 (이름, 소속)   
Adrien Benamira,Benjamin Devillers, Etienne Lesot, Ayush K.Ray, Manal Saadi, Fragkiskos D.Malliaros, CentraleSupelec   
University of Paris-Saclay, France
2019/08   

* 논문에서 가짜뉴스를 검출하려는 뉴스 종류
  * 소셜미디어에서의 가짜뉴스

* 논문에서 정의하고 있는 가짜뉴스
  * 잘못된 정보(MissInformation)의 확산
  * 가짜뉴스는 EchoChamber 현상 이용 
    * EchoChamber : 인터넷 공간에서 자신과 유사한 생각을 가진 사람들과만 소통하면서 점차 편향된 사고를 갖는 현상
 
  
  * 개인 또는 조직의 이익을 목적으로 독자를 속이기 위해  고의적으로 작성된 정보
  * 스팸 메시지와 유사하게 제한된 단어들을 사용하며, 문법적인 실수 등 문맥상 공통적인 특징들을 가짐
  * 가짜뉴스 탐지방법 
    - 유클리드 공간(평면과 공간을 일반화 거리와 길이와 각도를 좌표계를 도입하여, 임의 차원의 공간으로 확장)
    - Content Based Detection(단어잠재성 확인), Graph Based Detection(문맥간의 유사성)
  
* 논문에서 학습에 사용되는 데이터
  - 데이터의 양 및 취득 방법(또는 경로)
    - 실제가짜뉴스 (ICWSM Workshops)
    - 데이터의 양 : 150개의 가짜뉴스
    
  - 데이터 전처리 방법 : 
    - Glove Word Embedding : 기사내 단어의 평균 벡터를 계산
    - Graph 구성 : 각 기사간의 노드 거리를 K-nearrest Neighbours Based) 하여 임베디드 공간 거리
    - 분류 : 기사간의 유사성 분류를 위해 두개의 Graph Neural Network 사용
    - 네트워크 방법 : GCN(Graph Convolution Network), AGNN(Attention Graph Neural Network)
 
* 논문에서 사용하는 알고리즘  
  - 사용한 머신러닝 알고리즘 종류 
    - Semi-Supervised Learning 
  - 학습 방식 : Semi-Supervised Learning, 지도학습
  - 신경망을 사용할 경우 네트워크 내용
    - Graph Neural Networks
     - 두개의 4,4 개의 레이어 사용
     - 16개의 숨겨진 레이어 사용
     - 0.01% 학습률 
     - 1000번의 Epochs

  - **(검토자 의견) 알고리즘이 논문에서 정의하는 가짜 뉴스를 검출하기에 적합한지 검토 의견** 

* **오픈소스 공개 여부** 
   - 잘못된 정보 Detection Embedding Code : : https://github.com/bdvllrs/misinformation-detection-tensor-embeddings 
   - 가짜뉴스 탐지알고리즘 개발 커뮤니티 : https://dl.acm.org/doi/10.1145/3341161.3342958
  
* 논문의 평가
  - 논문에서 주장하는 내용 
    - 유클리드공간과 Content 기반 탐지방법론과, Graph Based의 표현체계로 문맥 유사성을 찾은 뒤 , Graph Neural Networks를 사용 하였을 경우 기존의 Content 기반 탐지방법론보다 우수한 결과를 나타냄.
    - AGNN+GCN 제안모델이 가짜뉴스를 효과적으로 검출할 수 있음
    
   - 논문 결과 (정량적 또는 정성적 결과)
    
      | Methods | Accuracy (in %)|||||
      |---------|--|---|---|---|-----|
      ||2% labeled data|5% labeled data|10% labeled data|15% labeled data|20% labeled data|
      |Guacho|56.65 ± 9.67|63.60 ± 7.52|70.95 ± 5.28|74.05 ± 3.80|79.8 ± 3.10|
      |SVM|63.55 ± 5.73|66.55 ± 7.14|75.05 ± 5.20|76.05 ± 4.80|78.90 ± 5.16|
      |RANDOM Forest|60.25 ± 10.02|69.05 ± 3.33|76.65 ± 3.48|83.55 ± 5.06|84.70 ± 2.48|
      |AGNN|70.45± 5.39|72.00 ± 8.05|78.70 ±3.54|83.35 ± 1.74|84.25 ± 3.51|
      |GCN|72.04 ± 6.00|77.35 ± 3.72|79.85 ± 3.41|82.35 ± 2.44|84.94 ± 2.30|
      
     * 레이블이있는 데이터의 10 %만으로 최대 3 %의 성능 향상을 달성하면서도보다 안정적이고 결과의 표준 편차를 줄임
     
  - **(검토자 의견) 논문 결과에 대한 객관성에 대한 검토의견** 



