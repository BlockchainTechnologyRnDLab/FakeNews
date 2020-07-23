### EMET: EMBEDDINGS FROM MULTILINGUAL-ENCODER TRANSFORMER FOR FAKE NEWS DETECTION

* 논문 저자 정보 (이름, 소속)   
Stephane Schwarz1, Antônio Theóphilo2, Anderson Rocha1      
1. Institute of Computing – University of Campinas, Campinas/SP, Brazil      
2. CTI Renato Archer, Campinas/SP, Brazil   

* 논문에서 가짜뉴스를 검출하려는 뉴스 종류
  * 소셜 미디어 네트워크의 텍스트 게시물

* 논문에서 정의하고 있는 가짜뉴스
  * 소셜 미디어 네트워크를 통해 유포되는 게시물 중 다른 뉴스의 일반적인 주장들과 상반되는 정보

* 논문에서 학습에 사용되는 데이터
   - 데이터의 양 및 취득 방법(또는 경로)
      1. Google이 Twitter에서 수집한 데이터 **(데이터 사이트/얻는 방법 재검토)**
      2. 트위터 게시물 답변 웹 스크랩 프로그램을 사용하여 답변 수집
      3. 관련 뉴스를 찾기 위해 BBC 및 웹 사이트에서 주제 키워드를 사용하여 뉴스 검색

    - 데이터 전처리 방법
      1. 트위터 게시물의 URL 및 사용자 태그, 해시 태그 제거
      2. 트위터와 답변, 관련 뉴스를 연관시킴
      3. 연관 시킨 데이터는 확장됨

![img](https://ieeexplore.ieee.org/mediastore_new/IEEE/content/media/9040208/9052899/9054673/schwa.t2-p5-schwa-large.gif "1")


* 논문에서 사용하는 알고리즘  
  - 사용한 머신러닝 알고리즘 종류 : CNN
  - 학습 방식 : 지도학습
  - 신경망을 사용할 경우 네트워크 내용
    - CNN
      1. 입력 데이터는 소셜 미디어 게시물, 답변 게시물, 게시물에서 언급한 주제와 관련된 뉴스로 구성됨
      2. 각각의 입력 데이터 인코더 통과
      3. 1차원 Convolutions Filter : 5개씩
      4. 세 가지 입력 조합 평면화
      4. Conv3와 FC2 사이에 Dropout 0.5
      5. FC4 뒤에 활성화 함수 ReLU

![img](https://ieeexplore.ieee.org/mediastore_new/IEEE/content/media/9040208/9052899/9054673/schwa1-p5-schwa-large.gif "1")

![img](https://ieeexplore.ieee.org/mediastore_new/IEEE/content/media/9040208/9052899/9054673/schwa.t1-p5-schwa-large.gif "1")

###### 그림 출처 : [EMET: EMBEDDINGS FROM MULTILINGUAL-ENCODER TRANSFORMER FOR FAKE NEWS DETECTION 논문](https://ieeexplore.ieee.org/document/9054673)

  - **(검토자 의견) 알고리즘이 논문에서 정의하는 가짜 뉴스를 검출하기에 적합한지 검토 의견** 

* **오픈소스 공개 여부 : X** 

* 논문의 평가
  - 논문에서 주장하는 내용 
    - 인코더를 사용하여 소셜 미디어 게시물에서 의심스러운 콘텐츠를 식별하는 방법

  - 논문 결과 (정량적 또는 정성적 결과)
![img](https://ieeexplore.ieee.org/mediastore_new/IEEE/content/media/9040208/9052899/9054673/schwa.t3-p5-schwa-large.gif "1")

  - **(검토자 의견) 논문 결과에 대한 객관성에 대한 검토의견** 
