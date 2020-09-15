# [Fake News Detection Using GATs ](https://colab.research.google.com/drive/1O0u_ACECauuv76QYFdhdO0hFimOF07Cc?usp=sharing)

###### 구독자-기사 관계와 BERT를 통한 기사의 벡터를 이용하여 GAT를 통한 예측을 하는 모델

![fake-news-GATs](https://user-images.githubusercontent.com/60456487/92510610-1957b680-f247-11ea-979b-b3586f6993e2.png)
###### 그림 출처 : [SWM-Final-Project-Report-Group-10.pdf](https://github.com/iamjagdeesh/Fake-News-Detection/blob/master/SWM-Final-Project-Report-Group-10.pdf)

### 오픈소스 실행
- BERT + GAT(Graph Attention Networks : 그래프 형태의 데이터 학습 모델)
- Test accuracy: 0.72
- DataSet : BuzzFeed

#

### 단계
1. Data Pre-processing
    - Buzzfeed or PolitiFact 데이터 사용
    - 소셜 미디어 네트워크 게시물
    - 이미지 URL, 내용, 작성자, 키워드, 제목, URL, 날짜, 출처 등의 필드
    - 라벨링 : 진짜/가짜
2. Derive Relationships
    - 모든 기사를 확인함
    - 각 기사에 대한 구독자를 식별함
    - 구독자와 관련된 다른 기사를 확인함(작성, 공유, 리트윗 등)
    - 기사들 사이의 관련성을 확인함
    - 결과를 행렬의 형태로 저장함
3. Feature Extraction(BERT)
    - BERT를 사용하여 특징 벡터를 추출함
4. Classification Model(GATs)
    - 2단계의 행렬과, 3단계의 특징 벡터 및 라벨을 입력함
    - GATs를 사용하여 분류

#

### Graph Neural Network
- Node-Edge로 구성된 그래프 데이터의 구조를 학습하는 딥러닝 모델
- Node : 데이터의 매트릭스로 이루어짐
- Edge : 데이터와 관련된 데이터
- 그래프 데이터 : 소셜 네트워크 데이터 / 분자 형태 데이터 / 3D Mesh 데이터 등 표현하기 힘든 데이터
- 사용 예
  - Node Level : Node 분류
  - Edge Level : Edge들 간의 관계를 분류
  - Graph Level : 노드 각각이 단어 하나씩이면 전체 노드들의 관계를 보고 라벨링

#

### Graph Attention Networks
- Node-Edge로 구성된 그래프 데이터의 **중요 Node에 가중치를 부여하는 어텐션 메커니즘을 사용하여** 구조를 학습하는 딥러닝 모델
- Node와 Edge의 Attention(Query/Key/Value) 계산을 통해 중요한 Node를 중심으로 학습

#

![GAT](https://user-images.githubusercontent.com/52561006/93244611-f8521100-f7c4-11ea-82f2-799f388eb90f.png)


#
###### 참고 : [Graph Attention Networks](https://www.youtube.com/watch?v=NSjpECvEf0Y)

###### 오픈소스 : [iamjagdeesh/Fake-News-Detection](https://github.com/iamjagdeesh/Fake-News-Detection)
