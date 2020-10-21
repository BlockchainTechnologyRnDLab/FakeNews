## SNU FeckCheck
- 온라인 기사, 뉴스 발언, 청와대 게시글, 블로그, 카페, SNS 등등 다양한 출처의 데이터 팩트체크
- 출처 url이 제공되지 않는 팩트체크 결과가 많음
- 팩트체크하려는 내용을 요약해둔 데이터를 크롤링함
- 가짜:105개(label:1) / 진짜:105개(label:0) 수집

![데이터](https://user-images.githubusercontent.com/60456487/96664183-2c54bf00-138d-11eb-8374-3480ed26668c.png)

### 가짜
- '전혀 사실 아님'으로 분류된 데이터 크롤링

### 진짜
- '전혀 사실 아님' 데이터에 비해 '사실' 데이터가 부족함
- '사실', '대체로 사실'로 분류된 데이터 크롤링

### 실험
- 학습데이터 90%, 테스트데이터 10%로 나누어 실험함
- 데이터셋의 크기가 작아 Epoch의 수를 30으로 설정하여 학습시킴
- Training Accuracy: 98.41%
- Test Accuracy: 80.95%

###### ※ 데이터 수집 중

[수집한 데이터를 사용하여 학습시킨 모델 결과](https://github.com/BlockchainTechnologyRnDLab/FakeNews/blob/master/Hanyoonjin/BERT/BERT_SNU_fakeNews_Data_Detection.ipynb)
