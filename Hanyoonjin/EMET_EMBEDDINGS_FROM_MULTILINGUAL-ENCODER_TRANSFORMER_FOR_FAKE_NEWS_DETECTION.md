### EMET: EMBEDDINGS FROM MULTILINGUAL-ENCODER TRANSFORMER FOR FAKE NEWS DETECTION

* 논문 저자 정보 (이름, 소속)   
Stephane Schwarz1, Antônio Theóphilo2, Anderson Rocha1      
1. Institute of Computing – University of Campinas, Campinas/SP, Brazil      
2. CTI Renato Archer, Campinas/SP, Brazil   

* 논문에서 가짜뉴스를 검출하려는 뉴스 종류
  * 소셜 미디어 텍스트 게시물

* 논문에서 정의하고 있는 가짜뉴스
  * 소셜 미디어 네트워크를 통해 유포되는 게시물 중 다른 뉴스의 일반적인 주장들과 상반되는 정보

* 논문에서 학습에 사용되는 데이터
   - 데이터의 양 및 취득 방법(또는 경로)
      1. [소셜 미디어 게시글 조작을 탐지하기 위해 수집되었던 Twitter 게시물(2015/2016)](http://www.multimediaeval.org/mediaeval2015/verifyingmultimediause/)
         - 6개의 언어
         - 35개 이상의 주제
         - 600개의 데이터를 무작위로 추출하여 데이터셋 생성
      2. 트위터 게시물 답변 웹 스크랩 프로그램을 사용하여 답변 수집
      3. 관련 뉴스를 찾기 위해 BBC 및 웹 사이트에서 주제 키워드를 사용하여 뉴스 검색

    - 데이터 전처리 방법
      1. 트위터 게시물의 URL 및 사용자 태그, 해시 태그 제거
      2. 트위터와 답변, 관련 뉴스를 연관시킴
      3. 연관 시킨 데이터는 확장됨
      4. 다국어 인코더를 사용하여 특징 벡터 추출

![img](https://ieeexplore.ieee.org/mediastore_new/IEEE/content/media/9040208/9052899/9054673/schwa.t2-p5-schwa-large.gif "1")


* 논문에서 사용하는 알고리즘  
  - 사용한 머신러닝 알고리즘 종류 : CNN
  - 학습 방식 : 지도학습
  - 신경망을 사용할 경우 네트워크 내용
    - CNN
      1. 입력 데이터는 소셜 미디어 게시물, 답변 게시물, 게시물에서 언급한 주제와 관련된 뉴스로 구성됨
      2. 각 입력 데이터 Transformer 인코더 통과
      3. 각 입력 데이터의 특징 벡터 생성
      4. 1차원 Convolutions Filter : 5개씩
      5. 세 가지 입력 조합 평면화
      6. Conv3와 FC2 사이에 Dropout 0.5
      7. FC4 뒤에 활성화 함수 ReLU

![img](https://ieeexplore.ieee.org/mediastore_new/IEEE/content/media/9040208/9052899/9054673/schwa1-p5-schwa-large.gif "1")

![img](https://ieeexplore.ieee.org/mediastore_new/IEEE/content/media/9040208/9052899/9054673/schwa.t1-p5-schwa-large.gif "1")

###### 그림 출처 : [EMET: EMBEDDINGS FROM MULTILINGUAL-ENCODER TRANSFORMER FOR FAKE NEWS DETECTION 논문](https://ieeexplore.ieee.org/document/9054673)

* **오픈소스 공개 여부 : X** 

* 논문의 평가
  - 논문에서 주장하는 내용 
    - 인코더를 사용하여 소셜 미디어 게시물에서 의심스러운 콘텐츠를 식별하는 방법

  - 논문 결과 (정량적 또는 정성적 결과)
![img](https://ieeexplore.ieee.org/mediastore_new/IEEE/content/media/9040208/9052899/9054673/schwa.t3-p5-schwa-large.gif "1")
    1. UCN(Unchecked news) : 게시글과 증거 뉴스가 다른 주제로 묶여있는 데이터 사용
    2. CN(Checked news) : 게시글과 증거 뉴스가 같은 주제로 묶여있는 데이터 사용
    3. CNC(Checked news and comments) : 게시글, 뉴스, 게시글에 대한 답변까지 모두 관련되어 있는 데이터 사용
    4. CNCE(Checked news, comments, and ensemble) : 각 데이터의 특징 벡터를 얻는 단계와 벡터를 합산하여 분류하는 단계로 구성된 앙상블 방법 사용

