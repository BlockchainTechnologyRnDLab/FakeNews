#Fake News Detection Using Machine Learning approaches: A systematic Review

* 논문 저자 정보 (이름, 소속)   
Syed Ishfaq Manzoor, Dr Jimmy Singla, Nikita 
Phagwara Punjab University. India
04/23/2019

* 논문에서 가짜뉴스를 검출하려는 뉴스 종류
 소셜 미디어 네트워킹 사이트(Facebook, Twitter)의 게시물

* 논문에서 정의하는 소셜미디어 게시물 데이터 유형
 - TEXT 형식의 많은 포스트
 - Multimedia : 여러 형태의 미디어가 통합 (단일게시물, 오디오,비디오,이미지,그래픽 포함)
 - Hyperlinks : 다른출처를 참조하는 게시물
 
* 논문에서 정의하고 있는 가짜뉴스: 무엇을 가짜뉴스라 규정하고 있는지 정리
 1. Visual-based    : 변형된 이미지, Doctor Video(?), 두개의 조합을 포함하는 그래픽으로 생성
 2. User-based      : 가짜 계정에 의해 생성되고, 특정 연령,성별,문화 정치적 소속을 나타내는 특정 대상이 생성
 3. Knowledge-based : 해결되지 않은 문제에 과학적인 설명을 제공하여 독자가 사실이라고 믿게만들도록 생성
 4. Style-based     : 공인된 인물이나 언론인의 형태를 가장하고 유사하게 행동하여 생성
 5. Stance-based    : 의미와 목적을 변화시키는 진실된 제안으로 생성
 
* 가짜뉴스 탐지 방법
 1. Linguistics basis(언어학 기초)
 2. Clustering(군집)
 3. Predictive modelling(예측 모델)
 4. Content cue based methods (콘텐츠 기반)
 5. Non text cue based methods (비언어 기반)

<가짜뉴스 탐지 방법-표>
|Fake News|Fake news detection Method|| 
|  Type   |Linguistic Modeling|Deceptive|Clustering|Predictive Modeling|Content Cues|Non-Text Cues|| 
|---------|-------------------|---------|----------|-------------------|------------|-------------||
|Visual-based|NO|NO|NO|NO|NO|YES||
|User Based|NO|NO|NO|YES|YES|YES||
|User Post Based|YES|YES|YES|YES|NO|YES||
|Social Network Based|NO|NO|NO|NO|YES|NO||
|Knowledge Based|NO|NO|YES|NO|NO|NO||
|Style Based|YES|NO|NO|YES|YES|NO||
|Stance Based|NO|NO|NO|NO|NO|NO||
  정확도 : 63~70% 

* 논문에서 학습에 사용되는 데이터
  - 데이터의 양 및 취득 방법(또는 경로)
   트위터 API : DMOZ
  - 데이터 전처리 방법
   텍스트 기반의 언어적 큐 접근 방식 : 머신러닝, 단어접근방법, 수사구조 및 담화 분석, 네트워크 분석 접근 및 SVM 분류기 사용
   이진 분류 방식 : 트윗과 게시물로 분류 
  -  **(검토자 의견) 데이터 객관성 여부에 대한 검토 의견** 
   
* 논문에서 사용하는 알고리즘  
  - 트위터 API : DMOZ 의 데이터셋으로 사용한 머신러닝 알고리즘 종류 
   1. Naive Bayes
   2. Descision trees
   3. SVM
   4. Nueral Networks
   5. Random Frest
   6. XG Boost 
   결과는 15% 가짜트윗, 45%는 실제트윗, 미정의 휴식 게시물로 결과 도출
  - 학습 방식 (지도학습, 비지도학습, 강화학습)
   지도학습
  - 신경망을 사용할 경우 네트워크 내용
    
 * 논문에서 제안한 내용들  
  - 뉴스컨텐츠 + 소셜 컨텐츠 접근 방식을 이용한 ML(머신러닝)탐지 제안
  - 가짜 게시물과 뉴스탐지 효율성이 향상된 "LIAR" 를 이용한 탐지 제안
  - Click Baiting을 이용한 어휘 및 의미 수준의 분석 탐지 제안
  - 의견, 소문, 정치적 발언을 NLP연구(자연어처리)하여 탐지 제안
  - 컨텐츠기반 및 소셜미디어 Boolean Crowd Sourcing 알고리즘을 사용하여 탐지 제안  
  - Fake Detector로 가짜뉴스 추론 모델에 대한 제안
  
* **오픈소스 공개 여부** 
  X 

* 논문의 평가
  - 논문에서 주장하는 내용
  자신들이 제안하는 가짜뉴스 탐지방법을 제시하고 (5가지), FakeNews를 탐지하기 위한 여러 논문들을 열거 해 놓음. 
   
  - 논문 결과 (정량적 또는 정성적 결과)
  - **(검토자 의견) 논문 결과에 대한 객관성에 대한 검토의견** 

* 관련연구: 논문에서 기술하는 관련 연구 부분 중 검토필요가 있는 것은 일반 논문의 검토와 같은 수준의 논문 리뷰를 하는 것으로 
확장하기 위한 것으로 규정
