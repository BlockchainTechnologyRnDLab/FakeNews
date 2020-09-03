 ## Fake News Detection as Natural Language Inference
 
  * 논문 저자 정보 (이름, 소속)
    - Kai-Chou Yang, National ChengKungUniversity Taiwan 2019.7
  
  * 논문에서 가짜뉴스를 검출하려는 뉴스 종류 : X 
  * 논문에서 정의하고 있는 가짜뉴스: 무엇을 가짜뉴스라 규정하고 있는지 정리 : X
  
 * 논문에서 학습에 사용되는 데이터   
   - 중국의 Tencent 사의 웹포털사이트의 데이터 
   - 중국의 Character World
  
 * 데이터의 양 및 취득 방법(또는 경로)
   - 웹포털 사이트 크롤링(예상)
 * 데이터 전처리 방법   
   1. 임베딩
      - 중국의 다양한 말뭉치 및 단어들을 Skip-gram Model,CBOW Model, FastText Model에 사전훈련시킴
   2. Firtst Level NLI Models
      - RNN, CNN, ESIM, Gated CNN, Decomposable Attention 사용하여 단어들의 특징점과 다른 레벨을 비교분석하며 반복작업을 하고 훈련
   3. First Level Ensemble
         - 첫번째 훈련시킨 모델들을 통합하기위해 LightGBM4 사용
         - 조밀하게 연결된 10개의모델, 3개의 클래스 라벨을 연결하여, 30차원 입력벡터를 가짐
         - 86.741% 정확도를 달성
   4. BERT
        - Bert기반 중국모델 5를 훈련 시킴 *****
        - 에포크동안 학습률은 5E-5, 최대 문장길이 128이고 배치크기는 32
        - 86.689% 정확도를 달성
   5. Blending
       - First Level Ensemble 과 BERT를 혼합하여 훈련진행
       - 86.963% 정확도를 달성
   6. Second Level : Fine Tune NLI Models
      - Blending 한 결과와 처음 1단계에서 사전 훈련된 NLI 모델 미세조정
   7. Second Level Ensemble
      - LigthGBM4와 Second Level의 결과를 조합하여 훈련 진행
      - 87.990% 정확도를 달성
   8. BERT Pseudo-Label Training
      - 4단계에서 훈련된 모델에 동일하개 3번 훈련을 진행
      - 87.484% 정확도를 달성
   9. Final Blending
      - Bert와 NLI 모델을 혼합하여 훈련을 진행
      - 88.019%  

![팩트체크과정](https://github.com/MDPJW/FakeNews/blob/master/image/Figure%201.PNG)

* 신경망을 사용할 경우 네트워크 내용    
  - DNN, CNN

* 논문에서 주장하는 내용
  - Fine-tunig BERT와 NLI(Natural Language Inference)모델을 조합하고 가중치값을 적절히 조합하면 가장 좋은 성능을 나타냄

* 논문 결과 (정량적 또는 정성적 결과)

|Model|Accuracy|
|-----|--------|
|Ensemble(1)|0.86741%|
|BERT(1)|0.86689%|
|Blended(1)|0.86963%|
|Ensemble(2)|0.87990%|
|BERT(2)|0.87484%|
|Blended(2)|0.88019%|
|Blended(2) + Trnsitivity|0.88063%|

 * (검토자 의견) 논문 결과에 대한 객관성에 대한 검토의견
   - BERT에 대한 상세설명이 부족하며, 데이터셋에 대한 설명 부족과 가짜뉴스에 대한 정의, 종류 나타나지않음. 
 
