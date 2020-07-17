# A Deep Learning Approach for Automatic Detection of Fake News

* 논문 저자 정보 (이름, 소속)   
Tanik Saikh, Arkadipta De   
Department of Computer Science and Engineering, Indian Institute of Technology Patna   
Department of Computer Science and Engineering, Government College of Engineering and Textile Technology, Berhampore   
05/11/2020    

* 논문에서 가짜뉴스를 검출하려는 뉴스 종류   
  * 텍스트 기사
  * 소셜 미디어 정보
     
* 논문에서 정의하고 있는 가짜뉴스   
  * 잘못된 정보
  
* 논문에서 학습에 사용되는 데이터
  - 데이터의 양 및 취득 방법(또는 경로) : [P ́erez-Rosas 연구](https://www.aclweb.org/anthology/C18-1287/)
  - 데이터 전처리 : FastText/ELMo
      
* 논문에서 사용하는 알고리즘
  - 사용한 머신러닝 알고리즘 종류 : GRU, LSTM, Multi-Layer Perceptron
  - 학습 방식 : 지도학습
  - 신경망 내용
    * Model 1
    1. Embedding Layer
        - Word2Vec의 확장 버전인 FastText를 사용하여 단어 임베딩을 함
        - 잘 쓰이지 않는 단어나 외래어들에 대한 임베딩도 가능함
        - 여러 도메인에서 얻은 데이터를 사용하므로 다양한 어휘에 대한 임베딩이 가능해야함
    2. Encoding Layer
        - 각 단어의 표현은 Bi-directional Gated Recurrent Unit(BiGRU) 모델 사용
        - GRU은 LSTM에 비해 매개변수와 자원을 적게 소모하여 학습에 효율적임
    3. Word Level Attention
        - 단어와 중요하게 연계된 다른 단어를 정리하는 것
        - 문장을 이해하기 위해 관련이 높은 단어 표현들을 취합하여야 함
    4. Multi-Layer Perceptron
        - ReLU 사용
        - 5개의 각 레이어에서 512, 256, 128, 50, 10개의 뉴런 사용
        - 2개의 Softmax 레이어를 사용하여 분류   
        
    * Model 2
    1. Embedding Layer
        - 딥러닝을 사용하여 미리 학습된 ELMo 사용
    2. Multi-Layer Perceptron
        - ReLU 사용
        - 5개의 각 레이어에서 512, 256, 128, 50, 10개의 뉴런 사용
        - 2개의 Softmax 레이어를 사용하여 분류

* 실험
  1. Fake News AMT / Celebrity news 데이터셋을 개별적으로 실험 (표1)
      - 학습 데이터셋 전체를 이용하여 모델 학습
      - 각 데이터셋의 테스트셋을 이용하여 테스트
      - Model 2의 정확도가 가장 높음
      
  2. 실험1의 결과로 가장 성능이 좋았던 Model 2를 서로 다른 데이터셋으로 학습/테스트 (표2)
      - Fake News AMT로 학습시키고 Celebrity news로 테스트
      - Celebrity news로 학습시키고 Fake News AMT로 테스트
      - 실험1에 비해 성능이 크게 떨어짐
      - 어떤 도메인의 데이터냐에 따라 결과가 크게 다름
      
      
  3. 여러 도메인의 데이터로 학습 vs 하나의 도메인의 데이터로 학습 (표3)
      - 어떤 영역이든 하나의 도메인의 데이터로 학습했을 때의 정확도가 더 낮음

| Dataset | System | Model | Test Accuracy(%) |
|---|---|---|---|
|FakeNews AMT|Proposed|Model 1|77.08|
|FakeNews AMT|Proposed|Model 2|83.30|
|FakeNews AMT|P ́erez-Rosas|Linear SVM|74|
|Celebrity|Proposed|Model 1|76.53|
|Celebrity|Proposed|Model 2|79|
|Celebrity|P ́erez-Rosas|Linear SVM|76|
###### 표1. 각각의 데이터셋을 이용한 테스트 결과   

| Training | Testing | Accuracy(%) |
|---|---|---|
|FakeNews AMT|Celebrity|54.3|
|Celebrity|FakeNews AMT|68.5|
###### 표2. Model 2를 이용한 서로 다른 데이터셋으로 학습/테스트 

| Domain | Exp. a || Exp. b ||
|---|---|---|---|---|
|| **Model 1** | **Model 2** | **Model 1** | **Model 2** |
|Business|74.75|78.75|63.56|68.56|
|Education|77.25|91.25|65.65|70.65|
|Technology|76.22|88.75|64.36|5.35|
|Politics|73.75|88.75|64.27|69.22|
|Entertainment|68.25|76.25|65.89|71.2|
|Sports|70.75|73.75|67.86|71.45|
###### 표3. 여러 도메인의 데이터로 학습 vs 하나의 도메인의 데이터로 학습


  
* **오픈소스 공개 여부**     
   #### X
   
* 논문의 평가
  - 논문에서 주장하는 내용   
    - 두 가지의 딥러닝 기반 가짜뉴스 탐지 기법 제안함
    - 정치 영역으로만 제한되었던 가짜뉴스 탐지를 여러 영역으로 확장시켜 여러 도메인에서 추출한 데이터를 사용함
    - 가짜뉴스 탐지에서 도메인의 역할이 중요하다는 점을 보임 
  - 논문 결과 (정량적 또는 정성적 결과)
    - 위의 표
  
  - **(검토자 의견) 논문 결과에 대한 객관성에 대한 검토의견**    

* 가짜뉴스 탐지 이전 연구
  - Snopes, PolitiFact등의 데이터셋에 의존함
  - 대부분의 데이터셋은 정치 관련 데이터를 가지고 있음
  - 데이터는 여러 도메인에서 가져온 뉴스가 아니라 소수의 도메인에서 가져오기 때문에 편향된 데이터일 수 있음
  - ※ 정치가 아닌 다른 영역에서 가짜뉴스 탐지를 하기 위해선 여러 도메인의 여러 영역이 포함된 데이터를 활용하여야 함
  
* 연구 요약
  1. [P ́erez-Rosas 외 연구진](https://www.aclweb.org/anthology/C18-1287/)의 연구가 제공한 Fake News AMT(AmazonMechanical Turk 수집) / Celebrity news 데이터셋을 제공받음
  2. AMT 데이터셋은 사업, 교육, 기술, 엔터테인먼트, 스포츠 등 정치 포함 다른 영역을 다룸
      - 여러 도메인의 진짜뉴스를 기반으로 가짜뉴스를 수동으로 생성하여 실험
      - ABCNews, CNN, USAToday, New York, Times, FoxNews, Bloomberg, and CNET 등 미국의 주류 웹사이트에서 수집
  3. Celebrity news 데이터셋은 연예계 뉴스를 다룸
  4. 언어적 특징을 기준으로 SVM(Support Vector Machine)을 이용하여 분류함
  5. Fake News AMT / Celebrity news 데이터셋에서 74%, 76% 정확도를 보임
  6. 딥러닝 기반 가짜뉴스 탐지   
      - Bi-directional Gated Recurrent Unit(BiGRU)   
      - Embedding from Lan-guage Model (ELMo)
