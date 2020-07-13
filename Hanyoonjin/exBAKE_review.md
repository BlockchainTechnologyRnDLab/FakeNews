# exBAKE: Automatic Fake News Detection Model Based on Bidirectional Encoder Representations from Transformers (BERT)

* 논문 저자 정보 (이름, 소속)   
Heejung Jwa, Dongsuk Oh, Heuiseok Lim   
Korea University   
2019/09/24     

* 논문에서 가짜뉴스를 검출하려는 뉴스 종류   
  * 텍스트 가짜뉴스(뉴스, SNS, 연설, 문서 등)
     
* 논문에서 정의하고 있는 가짜뉴스   
  * 거짓인 내용을 독자가 한 눈에 알아보지 못하여 사기나 허위 사실이 확산되어 문제를 일으킬 수 있는 정보
  
* 가짜뉴스 특징
  * 제목과 본문의 내용이 일치하는가
  
* 팩트체크 네트워크/사이트
  - IFCN(International Fact-Checking Network) : 미국 미디어 교육 기관 Poynter가 팩트체크 동향을 관찰하고 팩트 체커 교육 프로그램 제공
  - [Politifact](https://www.politifact.com)/[Snopes](https://www.snopes.com) : 제시된 기준에 따라 단계별로 가짜뉴스 수준 수동 분류

* 관련연구
  1. [Fake news challenge stage 1 (FNC-1)](www.fakenewschallenge.org) : 어떤 주제가 있을 때 주제에 대한 각 기사들의 입장을 분류함. 주제에 대하여 동의/동의 안 함/논의/관련 없음 으로 나뉠 수 있음
  2. [Web Search and Data Mining (WSDM) 2019 fake news challenge](www.kaggle.com/c/fake-news-pair-classification-challenge) : 한 기사의 사실 판단을 할 때 웹 검색을 통해 다른 기사들의 제목과 비교하여 세 가지 단계로 수동 분류
  3. [clickbait-challenge](www.clickbait-challenge.org) : SNS의 clickbait(광고) 분류 탐지 챌린지
  4. [국내 인공지능 연구개발 과제](www.ai-challenge.kr) 중 하나 : 기사 본문에서 주제와 관련 없는 맥락의 내용 탐지, 독자가 의도하지 않은 정보에 노출되는 것 방지

* FNC-1
  1. SWEN - TalosComb (1등)
      - TalosCNN과 TalosTree 기반의 평균 가중치 모델
      - TalosTree : singular-value decomposition (SVD, 특이값 분해), term frequency-inverse document frequency (TF-IDF), word2vec를 사용한 Gradient boosted decision tree model
      - TalosCNN : word2vec로 임베딩하며, CNN 기반(3개의 히든 레이어와 1개의 소프트맥스 레이어) 분류
  2. Athene - Multi-layer perceptron (MLP) (2등)
      - 6개의 히든 레이어와 1개의 소프트맥스 레이어
      -
      -
  3. UCL Machine Reading (UCLMR) (3등)
      - 단일 히든 레이어를 사용하여 MLP
      - TF-IDF를 사용하여 학습 및 테스트 데이터 세트에서 자주 등장하는 5000개 어휘 추출

* 논문에서 학습에 사용되는 데이터
  * 데이터 전처리 방법
    * 기존 단어 임베딩
      - word2vec / fastText : 임베딩에 많이 사용되지만 고정 벡터 값을 사용하므로 성능이 좋지 않음
      
    * 문맥을 고려한 단어 임베딩
      - Embeddings from Language Models (ELMO)   
        -> 2018년에 제안되었으며, 문맥을 반영한 단어 임베딩을 함   
        -> Bi-LSTM(Bidirectional-LSTM, 양방향 LSTM)을 사용하여 wiki와 같은 대용량 unlabeled 데이터로 사전에 학습된 언어 모델을 이용함.
      - Generative Pre-Training (GPT)   
        -> 단방향 언어 모델을 이용하여 단어 예측
      - Bidirectional Encoder Representations from Transformers model (BERT)
      - ELMO는 양방향으로 앞뒤 단어를 예측하지만, 가까운 단어들까지만 예측할 수 있는 즉 얕은 양방향성을 보임
      - BERT는 더 깊은 양방향으로 구현되어 문장의 의미를 더 잘 분석할 수 있음
      - 문장에서 단어 사이의 관계를 명확하게 식별함
      - 입력 단어 전체의 15%를 랜덤으로 숨겨 해당 단어를 예측하는 방법으로 맥락을 이해함

     ![img](https://mino-park7.github.io/images/2018/12/%EA%B7%B8%EB%A6%BC1-bert-openai-gpt-elmo-%EC%B6%9C%EC%B2%98-bert%EB%85%BC%EB%AC%B8.png "비교")
     ###### 출처 : BERT WhitePaper

  - 데이터의 양 및 취득 방법(또는 경로)
    - BERT는 사전에 학습된 언어 모델로 단어를 예측할 수 있지만 추가 학습을 위해 [CNN](www.cnn.com)과 [데일리 메일](www.dailymail.co.uk)의 [데이터셋](https://github.com/abisee/cnn-dailymail)을 사용함
    - BERT는 엄청난 정보를 포함하고 있지만 다방면으로 자세한 정보를 가지진 않았기에 사전 훈련을 위해 뉴스 데이터 학습이 필요함
    - CNN 문서 약 9만개, 질문 약 38만개(?) / 2007.04~2015.04
    - 데일리 메일 문서 약 197만개, 질문 약 87만개 / 2010.06~2015.04
    - 더 높은 판별 성능을 위하여 [FNC-1 데이터셋](https://github.com/FakeNewsChallenge/fnc-1) 추가 사용
    - FNC-1 데이터 2587개의 제목-본문 쌍
  
  -  **(검토자 의견) 데이터 객관성 여부에 대한 검토 의견**
      - 흠..
      
* BAKE Model
  - 데이터셋을 Agrees (AGR; 동의), Disagrees (DSG; 동의 안 함), Discusses (DSC; 논의), and Unrelated (UNR; 관련 없음) 4개의 클래스로 분류함
  - BERT 모델 그대로이지만 가짜뉴스에 BERT를 처음 적용해봤기에 BAKE라고 정의

* exBAKE Model
  - BAKE 모델에 CNN/데일리 메일 뉴스 데이터를 추가하여 exBAKE 모델 구현
  - 소프트맥스 레이어에서 데이터를 4개의 클래스로 분류
  - Cross Entropy : 실제값과 예측값이 맞는 경우에는 0으로 수렴하고, 값이 틀릴경우에는 값이 커지기 때문에, 실제 값과 예측 값의 차이를 줄이기 위한 엔트로피
  - 손실 함수로 Weighted cross entropy (WCE)를 사용하여 데이터셋의 클래스 분포에 따라 가충치를 다르게 하는 것이 특징
  - FNC-1 데이터 집합은 ARG 7.4%, DSG 2.0%, DSC 17.7%, UNR 72.8%로 불균형함
  - FNC-1 대회에서는 높은 성능을 보일 수 있는 데이터지만, 다른 방면으론 좋지 않음
     ![img](https://www.mdpi.com/applsci/applsci-09-04062/article_deploy/html/images/applsci-09-04062-g001.png "비교")
     ###### 출처 : mdpi exBAKE: Automatic Fake News Detection Model Based on Bidirectional Encoder Representations from Transformers (BERT)

* 논문에서 사용하는 알고리즘
  - 사용한 머신러닝 알고리즘 종류 : CNN
  - 학습 방식 : 지도학습
  - 신경망을 사용할 경우 네트워크 내용
  - **(검토자 의견) 알고리즘이 논문에서 정의하는 가짜 뉴스를 검출하기에 적합한지 검토 의견** 
  
* **오픈소스 공개 여부**     
   #### X
   
* 논문의 평가
  - 논문에서 주장하는 내용   
    - 사전 학습을 거치는 BERT를 개선하여 exBAKE 모델을 제안했음 
    - 기사의 제목과 본문의 관계를 잘 분석하여 가짜뉴스를 탐지함
    - 다른 가짜뉴스 탐지를 하기 위해선 추가 데이터 학습이 필요할 것임
  - 논문 결과 (정량적 또는 정성적 결과)
    - FNC-1 데이터를 테스트 하였을 때 다른 모델들로 예측한 것 보다 좋은 결과를 보임
    - 표 출처 : 해당 논문 결과
  
| Models | F1 | AGR | DSG | DSC | UNR |
|---|---|---|---|---|---|
|Majority vote|0.210|0.0|0.0|0.0|0.839|
|TalosComb|0.582|0.539|0.035|0.760|0.994|
|TalosTree|0.570|0.520|0.003|0.762|0.994|
|TalosCNN|0.308|0.258|0.092|0.0|0.882|
|Athene|0.604|0.487|0.151|0.780|0.996
|UCLMR|0.583|0.479|0.114|0.747|0.989|
|featMLP|0.607|0.530|0.151|0.766|0.982|
|stackLSTM|0.609|0.501|0.180|0.757|0.995|
|BERT|0.656|0.651|0.145|0.839|0.989|
|BAKE|0.734|0.667|0.463|0.822|0.986|
|exBAKE|0.746|0.684|0.501|0.813|0.988|
|Upper bound|0.754|0.588|0.667|0.765|0.997|

  - **(검토자 의견) 논문 결과에 대한 객관성에 대한 검토의견**    
