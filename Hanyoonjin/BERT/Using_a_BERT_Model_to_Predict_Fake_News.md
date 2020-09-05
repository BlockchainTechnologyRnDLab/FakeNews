## BERT 기반 가짜뉴스 예측

1. 데이터 업로드
2. 모듈 import
3. transformers 설치
4. BertForSequenceClassification 패키지와 BertTokenizer import
5. 데이터 전처리
    - 미리 학습된 BertTokenizer를 사용한 토큰화
    - [CLS]와 [SEP] 사이에 기사 토큰화된 기사 내용 삽입
    - 토큰들의 index 값으로 변경
    - 라벨링 내용으로 변수 초기화
    - 인덱스와 토큰 쌍으로 맵을 생성하여 저장
    - 마스킹된 데이터 생성
6. 학습 단계 실행과 테스트 단계 실행 함수 생성
7. 학습 데이터와 테스트 데이터 분리
8. BERT 모델 생성
    - 사전학습된 BertForSequenceClassification 사용
    - 12개의 레이어
    - Encoder와 Pooler, Dropout, 그리고 Classifier 단계로 이루어짐
9. 정확도 예측 함수 생성
10. 모델 학습
    - Epochs : 3번
    - Optimizer : Adam
    - BATCH_SIZE : 14
    - Training Accuracy : 98.79%
11. 모델 테스트
    - Test Accuracy : 96.36%
12. 잘못 예측된 데이터를 수집하여 오류 분석 수행

#

###### [CVPcorp - Using a BERT Model to Predict Fake News](https://colab.research.google.com/drive/1FwbW5lhgTUl4VfSGIb2oMPeAATYrTJj1?usp=sharing)
