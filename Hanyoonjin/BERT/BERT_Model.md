## BERT 분석

1. BERT에서 제공하는 기본 config, CheckPoint, Vocab 다운로드
2. 사전학습된 BERT 인코더 다운로드
3. 데이터셋 다운로드
4. Tokenizer 설정
    - 다운로드한 Vocab 적용
    - 소문자로 바꿀 것인지 설정(한국어 해당 안 됨)
    - ##은 앞 토큰과 이어진다는 표시
5. BERT의 입력 형식에 맞는 데이터로 문장 인코딩
    - [CLS] [SEP]
    - 기본 데이터와 마스킹 데이터 준비
    - 토큰의 자리를 알 수 있게 0과 1로 이루어진 타입 데이터 준비
    
   ![bertmodel](https://user-images.githubusercontent.com/60456487/91255676-4fedf580-e7a0-11ea-8f0d-ee38e5abc4b1.png)

6. 모델 구축
    - BERT_config 파일 준비
      -  입력 데이터 길이, Dropout, 양방향 설정, Activation Function, Hidden Size, Vocab Size 등 모델 구조 변경 가능
    - config 내용을 기반으로 Bert_classifier, Bert_Encoder 생성
    - Bert_Encoder : Transformer 기반
    - CheckPoint(학습된 모델의 변수) 내용을 기반으로 Bert_Encoder 가중치 초기화
7. 최적화 설정
    - epoch : 학습 횟수
    - batch : 모델의 가중치를 업데이트시킬 때 사용되는 데이터 묶음 개수
    - optimizer : 최적화 도구 생성
8. 모델 학습
    - loss : 훈련 과정에서 사용할 손실 함수(loss function)를 설정
    - metric : 모델의 성능을 평가할 때 어떤 평가지표로 평가할지 결정, 학습 과정을 모니터링하는데 사용
    - compile : 손실 함수와 최적화 도구, 메트릭을 선택하고 기계가 모델을 이해할 수 있도록 컴파일
    - fit : 손실 함수를 최소로 만들어주는 가중치를 찾기 위해 변수를 업데이트 시키는 과정
      - 학습 데이터
      - 라벨 데이터
      - 총 학습 횟수
      - 배치 크기 등 설정
9. 미세조정된 모델에 테스트 데이터를 사용하여 작동 확인
10. 모델 저장 및 사용
