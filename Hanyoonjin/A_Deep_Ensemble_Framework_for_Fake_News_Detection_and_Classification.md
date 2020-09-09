# A Deep Ensemble Framework for Fake News Detection and Classification

* 논문 저자 정보 (이름, 소속)   
Arjun Roy, Kingshuk Basak, Asif Ekbal, Pushpak Bhattacharyya   
Department of Computer Science and Engineering   
Indian Institute of Technology Patna, India   
2018/11   

* 논문에서 가짜뉴스를 검출하려는 뉴스 종류
  * 텍스트 기사

* 논문에서 정의하고 있는 가짜뉴스
  * 주제와 맞지 않는 내용이 작성되어 있고, 주장에 근거가 없는 뉴스(앞뒤 문장의 연결이 자연스럽지 않은 내용)

* 논문에서 학습에 사용되는 데이터
  - 데이터의 양 및 취득 방법(또는 경로) : 6개의 클래스로 분류된 LIAR(학습: 10,269개 / 검증: 1,284개 / 테스트: 1,266개)
  - 데이터 전처리 방법 : X

* 논문에서 사용하는 알고리즘  
  - 사용한 머신러닝 알고리즘 종류 : CNN, Bi-LSTM, Multi-layer Perceptron
  - 학습 방식 : 지도학습
  - 신경망을 사용할 경우 네트워크 내용
    - Bi-LSTM : 정보의 문맥 탐색
    - CNN :  정보의 특징, 정보와 관련된 정보 탐색
    - Multi-layer Perceptron : 멀티 클래스 분류

* **오픈소스 공개 여부 : X**

* 논문의 평가
  - 논문에서 주장하는 내용 
    - 본 논문에선 딥러닝 기반 가짜뉴스 탐지 모델을 이용하여 결과를 true, mostly-true, half-true, barely-true, false and pants-fire로 분류하였음
  - 논문 결과 (정량적 또는 정성적 결과)
    - 클래스마다 Precision, Recall, F1-score 등의 확률로 표를 정리하였음
    - 가짜뉴스 탐지 정확도는 44.87%로 좋지 않음
    - 다른 모델과 비교하지 않았음

