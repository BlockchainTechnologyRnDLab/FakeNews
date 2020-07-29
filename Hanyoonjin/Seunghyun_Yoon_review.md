# Detecting Incongruity between News Headline and Body Text via a Deep Hierarchical Encoder

* 논문 저자 정보 (이름, 소속)   
Seunghyun Yoon1,2, Kunwoo Park3,4, Joongbo Shin1, Hongjun Lim4   
Seungpil Won1, **Meeyoung Cha**4,5, Kyomin Jung1,2   
1. Department of Electrical and Computer Engineering, Seoul National University, Seoul, Korea   
2. Automation and Systems Research Institute, Seoul National University, Seoul, Korea   
3. Qatar Computing Research Institute, Doha, Qatar   
4. School of Computing, KAIST, Daejeon, Korea   
5. Data Science Group, Institute for Basic Science (IBS), Daejeon, Korea   

* 논문에서 가짜뉴스를 검출하려는 뉴스 종류
  * 텍스트 뉴스, ClickBait, 광고

* 논문에서 정의하고 있는 가짜뉴스
  * 뉴스 제목이 본문의 내용을 올바르게 나타내지 않은 정보

* 논문에서 학습에 사용되는 데이터
  - 데이터의 양 및 취득 방법(또는 경로)
    - 4,000,000(4백만)개의 한국어 기사(2016.01~2017.10) 수집
       - 가짜뉴스 : 기존 기사 제목+다른 기사 본문을 합쳐 생성했음
       - 진짜뉴스로 분류한 실제 기사 중에서도 가짜뉴스가 있을 수 있으므로 추가 조치를 취해야함
          1. n-gram 사전으로 광고 문구가 있는지 점검함
          2. 데이터 셋에서 무작위로 1,000개의 기사를 추출하여 사람이 수작업으로 검사하여 제목과 본문의 내용이 일치하지 않는지 확인함
    - 1,700,000개의 데이터셋 사용

  - 데이터 전처리 방법
    1. 비중요 정보 제거(기자명, 사진, 동영상 등)
    2. 단어 토큰화(언어 장벽없이 데이터 집합을 활용할 수 있도록 하기 위해 정수로 변환)

* 논문에서 사용하는 알고리즘  
  - 사용한 머신러닝 알고리즘 종류
    * AHDE(Attentive Hierarchical Dual Encoder)
      * GRU(Gated Recurrent Unit : LSTM보다도 간단한 구조를 가진 순환 신경망) 2개
  - 학습 방식 : 지도학습
  - 신경망을 사용할 경우 네트워크 내용
  
<img src="https://github.com/david-yoon/detecting-incongruity/blob/master/assets/AHDE.png?raw=true" width="50%" height="50%" />

##### 그림 1 : [AHDE 구조](https://github.com/david-yoon/detecting-incongruity/blob/master/assets/AHDE.png)

<img src="https://images.deepai.org/converted-papers/1811.07066/rsc/fig_ip.png" width="50%" height="50%" />

##### 그림 2 : IP(Independent Paragraph) 함수를 사용하여 각 문단과 제목의 관계를 독립적으로 학습할 수 있는 확대 방식 사용 [사진 출처](https://deepai.org/publication/detecting-incongruity-between-news-headline-and-body-text-via-a-deep-hierarchical-encoder)


* **오픈소스 공개 여부 : [Detecting-incongruity](https://github.com/david-yoon/detecting-incongruity/)** 

* 논문의 평가
  - 논문에서 주장하는 내용 
    - 데이터셋 백만쌍을 사용해 학습하여, 오해를 부르는 제목의 뉴스를 탐지할 수 있었음
    - 제목과 본문 사이의 불일치를 측정하기 위해 두 개의 신경망을 사용함
    - 각 단락마다 제목과 독립적으로 비교하여 성능을 더 끌어올릴 수 있었음
  - 논문 결과 (정량적 또는 정성적 결과)
    - 문단이 많아지면 HRE가 AHDE보다 예측 성공률이 높았지만 AHDE가 평균적으로 정확도가 높음
    <img src="https://images.deepai.org/converted-papers/1811.07066/rsc/fig_analysis_length_whole.png" width="50%" height="50%" />
    <img src="https://images.deepai.org/converted-papers/1811.07066/rsc/fig_analysis_length_para.png" width="50%" height="50%" />
  
  ###### HRE(Hierarchical Recurrent Encoder) : 문단마다 속한 단어의 벡터를 평균화한 값을 문단의 벡터값으로 설정하여 계산
