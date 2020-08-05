## Multimodal Explanations: Justifying Decisions and Pointing to the Evidence


* 논문 저자 정보 (이름, 소속)   
Dong Huk Park1, Lisa Anne Hendricks1, Zeynep Akata2,3, Anna Rohrbach1,3,Bernt Schiele3, Trevor Darrell1, and Marcus Rohrbach4   
1EECS, UC Berkeley,2University of Amsterdam,3MPI for Informatics,4Facebook AI Research

![그림](https://storage.googleapis.com/groundai-web-prod/media%2Fusers%2Fuser_14%2Fproject_200103%2Fimages%2Fx1.png)

* 요약
  - 두 가지 데이터셋을 기반으로 학습시켜 이미지 속 움직임을 설명할 수 있고 질문에 답변할 수 있는 PJ-X 모델을 제안함

* 논문에서 학습에 사용되는 데이터
  - 데이터의 양 및 취득 방법(또는 경로)
    - 두 개의 데이터셋 사용
    1. Activity recognition tasks (ACT-X)
        - 이미지에서 사람이나 사물의 움직임을 텍스트로 설명한 데이터
        - 이미지 18,030개
        - 움직임 종류 397개 
        - 이미지당 3개의 설명
        - 설명당 최소 10개의 단어 사용
        - 이미지 설명을 위해 MPII Human Pose (MHP) 데이터셋에서 주석 수집   
          a-1. MPII Human Pose (MHP)   
                  - 움직임 설명을 위한 주석   
                  - 사람의 포즈, 사람과 사물의 상호작용 등을 기반으로 움직임 분류   

     2. Visual question answering tasks (VQA-X)
        - 이미지에 대한 질문과 그에 맞는 응답으로 이루어진 데이터
        - 응답하는 부분을 시각적으로 표시하여 보여줌
        - 이미지 200,000개
        - 이미지당 3개의 질문 구성
        - 질문당 10개의 답변

* 논문에서 사용하는 알고리즘  
  - Pointing and Justification Explanation (PJ-X)
    - 텍스트로 결과를 설명하고 그에 맞는 시각적 증거를 표시해주는 모델
  - 사용한 머신러닝 알고리즘 종류
    - CNN, LSTM
  - 학습 방식 : 지도학습
  - 신경망을 사용할 경우 네트워크 내용
  ![그림](https://storage.googleapis.com/groundai-web-prod/media%2Fusers%2Fuser_14%2Fproject_200103%2Fimages%2Fx6.png)
  1. Answering model을 사용하여 입력된 이미지와 질문에 대한 답변을 예측함
      - CNN : 이미지 특징 추출
      - LSTM : 질문 분석
      - 특징과 분석한 질문 결합
      - 이미지의 특징 중 질문과 관련있는 특징에 가중치 적용
      - 다시 질문과 결합하여 답변 예측
  2. Multimodal explanation model을 사용하여 시각적 설명과 텍스트 설명을 생성함
      - 이미지, 질문, 답변을 입력으로 받아 답변을 설명할 수 있는 Visual Pointing 생성
      - 이미지, 질문, 답변을 기반으로 LSTM 디코더를 사용하여 답변에 대한 설명을 생성
