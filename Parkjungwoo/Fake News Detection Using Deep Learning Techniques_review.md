# Fake News Detection Using Deep Learning Techniques
* 논문 저자 정보 (이름, 소속)
  - Chaitra K Hiramath, Prof.G.C.Deshpande, INDIA, KLS Gogte Institute of Technology University

* 논문에서 가짜뉴스를 검출하려는 뉴스 종류 
  - 웹기반 생활채널, 온라인 신문, 뉴스사이트
  
* 논문에서 정의하고 있는 가짜뉴스
  - Misdirection(잘못된 방향성), Gossip(잡담), 사기, 속임수등과 관련
  
* 논문에서 학습에 사용되는 데이터
  - 데이터의 양 및 취득 방법(또는 경로)
    온라인 신문, 웹기반 생활채널, 웹기반 뉴스사이트 
  - 데이터 전처리 방법
   1. 구두점,URL,이미지,형태소 분석 및 중지단어의 추출
   2. NLP(자연어처리)를 수행하여 분류기를 통해 정보를 분류
   3. Stemming 기술 : 단어에서 접미사 또는 접두사를 분리하는 기술
   4. Stops Word 제거 : and, or, but, of, in ,from ,to ,a ,an 
   5. 특징점 추출 
   
  -  **(검토자 의견) 데이터 객관성 여부에 대한 검토 의견**  
* 논문에서 사용하는 알고리즘  
  - 사용한 머신러닝 알고리즘 종류
    1. Logistic regression(LR)
    2. Naive bays(NB)
    3. Support Vector Machine(SVM)
    4. Random Forest(RF)
    5. Deep Neural Network(DNN)
    
  - 학습 방식 : 지도 학습
  - 신경망을 사용할 경우 네트워크 내용 : 
    * 역전파 방법, Sigmoid Layer 사용
     1. 입력레코드로 데이터 전달
     2. 오류값 계산
     3. 숨겨진 레이어와 출력레이어 계산(갯수)
     4. 출력 레이어 가중치 조절
     5. 숨겨진 레이어 가중치 조절
     6. 1단계 반복
     7. 종료
    * 사용 셋팅 
     1. TOOL : JAVA SYSTEM (NETBEANS8.1 + MYSQL) + 분류알고리즘
     2. DB : 웹에서 다운로드
     
  - **(검토자 의견) 알고리즘이 논문에서 정의하는 가짜 뉴스를 검출하기에 적합한지 검토 의견** 
* **오픈소스 공개 여부** 
* 논문의 평가
  - 논문에서 주장하는 내용 
    지도학습에 관련된 LR, RF,SVM, NB, DNN 과 같은 분류 기술중에 메모리는 비록 많이 소모하지만, 정확성과 소모시간이
    DNN이 가장 뛰어남
  - 논문 결과 (정량적 또는 정성적 결과)
 
 * 메모리 소모율 

|SR NO.|Algorithm|Memory in Bytes|
|1|LR|920000000|
|2|RF|950000000|
|3|SVM|110000000|
|4|NB|110000000|
|5|DNN|112000000|

 * 알고리즘 소요시간

|SR NO.|Algorithm|Time in ms|
|1|LR|3750|
|2|RF|1800|
|3|SVM|2800|
|4|NB|1900|
|5|DNN|400|
 
 * 가짜뉴스 판별 정확도

|SR NO.|Algorithm|Accuracy in %|
|1|LR|75|
|2|RF|77|
|3|SVM|79|
|4|NB|89|
|5|DNN|91|

  - **(검토자 의견) 논문 결과에 대한 객관성에 대한 검토의견** 
   어떠한 데이터셋을 사용하여 논문을 작성하였는지, 데이터셋에 대해서 적절한 설명 부족, 참고문헌을 조사하여 데이터셋을 확보하면
   DNN을 이용하여 영어로 된 영어뉴스의 가짜뉴스 탐지를 실험해 볼 수 있을 것 같음.
   
* 관련연구: 논문에서 기술하는 관련 연구 부분 중 검토필요가 있는 것은 일반 논문의 검토와 같은 수준의 논문 리뷰를 하는 것으로 
확장하기 위한 것으로 규정

