# DeClarE: Debunking Fake News and False Claims using Evidence-Aware Deep Learning

* 논문 저자 정보 (이름, 소속)   
Kashyap Popat   
Max Planck Institute for Informatics, Saarbrucken, Germany   
09/17/2018   

* 논문에서 가짜뉴스를 검출하려는 뉴스 종류   
  * 텍스트 기사의 신뢰도 평가   
  * 트위터, 웨이보 같은 소셜 미디어 플랫폼의 텍스트에 대한 신뢰도 평가
* 논문에서 정의하고 있는 가짜뉴스   
  * 다른 기사와 상반되는 주장을 사람들이 오해할 수 있는 선동적인 어휘로 작성된 뉴스

* 논문에서 학습에 사용되는 데이터
  - 데이터의 양 및 취득 방법(또는 경로)
    * 네 가지 데이터셋을 사용한 실험
      1. Snopes(진짜:1164/가짜:3177)
          * 일반적인 내용의 사실 판단 데이터셋
          * 진짜/가짜 분류
      2. PolitiFact(진짜:1867/가짜:1701)
          * 정치 내용의 사실 판단 데이터셋
          * 진짜/가짜 분류
      3. NewsTrust(총:5344)
          * 뉴스 기사의 신뢰성 판단 데이터셋
          * 각 뉴스에 대해 회원들의 리뷰 및 평가로 구성되어 있음
          * 평가에 따라 신뢰도 점수(1-5점) 할당
          * 입력 기사의 신뢰도 점수 예측
      4. SEMEVAL-2017 TASK 8(진짜:127/가짜:50)
          * 소셜 미디어 콘텐츠(트위터 등)의 신뢰성 판단 데이터셋
          * 진짜/가짜 분류
  - 데이터의 90%는 학습 데이터로, 10%는 검증 데이터로 사용
  - [데이터셋 다운로드](https://www.mpi-inf.mpg.de/departments/databases-and-information-systems/research/impact/deep-learning-based-credibility-analysis)
  - 데이터 전처리 방법
      - GloVe를 사용한 단어 임베딩

* 논문에서 사용하는 알고리즘  
  * DeClarE
    * 입력 기사가 주어지면 입력과 관련된 웹 기사를 검색함
    * 양방향 LSTM(Bi-LSTM)을 통해 웹 기사들의 맥락을 파악함
    * 입력 기사의 주장에 반대되는 웹 기사의 단어를 찾아내면 입력 기사의 신뢰도가 하락
    * 사람들이 이해할 수 있는 설명을 생성하여 신뢰도를 높임
  - 사용한 머신러닝 알고리즘 종류 : 양방향 LSTM - 앞 뒤 단어와 모두 연관시켜 객관적인 언어를 포함하였는지 판단
  - 학습 방식 : 지도학습
  - 신경망을 사용할 경우 네트워크 내용
    - 구현 : Tensorflow Keras
    - 손실 함수 : Cross Entropy
    - 최적화 : Adam Optimizer   
    
  | 매개변수 | Snopes | PolitiFact | NewsTrust | SEMEVAL |
  |---|---|---|---|---|
  | 문장 길이 | 100 | 100 | 300 | 100 |
  | LSTM Layer | 64 | 64 | 64 | 16 |
  | FC Layer | 32 | 32 | 64 | 8 |
  | 드롭아웃 | 0.5 | 0.5 | 0.3 | 0.3 |   
        
     ![img](https://images.deepai.org/converted-papers/1809.06416/x1.png "신경망 모델")

* **오픈소스 공개 여부**     
   #### [오픈소스](https://github.com/atulkumarin/DeClare)

* 논문의 평가
  - 논문에서 주장하는 내용
  어휘나 단어만을 보고 자동으로 사실 판단을 하는 것은 외부 뉴스들의 내용을 증거로 삼지 않기 때문에 정확성이 떨어짐. 본 논문에서는 기사의 어휘, 출처와 외부 증거에 의해서 사실 판단을 하고, 해당 뉴스의 신뢰도 점수를 매길 수 있는 신경망 모델을 제안함
  - 논문 결과 (정량적 또는 정성적 결과)      
    - 다른 모델들과의 비교
    1. Rashkin(2017)의 LSTM 모델
    2. Wang(2017)의 CNN 모델
    3. Popat(2017)의 Distant Supervision 모델
    4. DeClare(Plain) : Bi-LSTM 모델
    5. DeClare(Plain+Attn) : Bi-LSTM+Attention(가중치 적용) 모델
    6. DeClare(Full) : Bi-LSTM+Attention+외부 증거 모델
    - 모델들과의 비교에서 데이터셋 4가지 모두 DeClare(Full)의 정확성이 높은 것으로 나옴
    - DeClare가 학습하는 동안 가중치가 높게 적용된 단어에 강조표시 됨
    - 웹에서 크롤링된 기사와 비교하여 가짜뉴스를 판별하고, 강조표시된 부분을 증거로 제시함
  - **(검토자 의견) 논문 결과에 대한 객관성에 대한 검토의견**    
  2018년도 논문이라 웹 검색을 통해 증거를 찾는 모델이 흔하지 않았던 것으로 보임 그러나 현재는 비슷한 방법으로 사실 판단을 하는 모델이 존재할 것이라 생각하여 다른 논문의 신경망 구조와 비교가 필요하다고 봄

