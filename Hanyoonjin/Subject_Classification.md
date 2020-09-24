## Subject Classification

| Model | Subject | Datasets | Accuracy |
|---|---|---|---|
| [BERT](https://github.com/BlockchainTechnologyRnDLab/FakeNews/blob/master/Hanyoonjin/BERT/Using_a_BERT_Model_to_Predict_Fake_News.md) | News / politics | [Kaggle Fake and real news dataset](https://www.kaggle.com/clmentbisaillon/fake-and-real-news-dataset#Fake.csv) | 97.36% |
| [BERT](https://github.com/BlockchainTechnologyRnDLab/FakeNews/blob/master/Hanyoonjin/BERT/Using_a_BERT_Model_to_Predict_Fake_News.md) | News / politics / left-news / Government News / US_News / Middle-east | [Kaggle Fake and real news dataset](https://www.kaggle.com/clmentbisaillon/fake-and-real-news-dataset#Fake.csv) | 66.79% |
| [LSTM+CNN](https://github.com/BlockchainTechnologyRnDLab/FakeNews/blob/master/Hanyoonjin/FakeNews-Classifier_Open_Source.md) | News / politics / left-news / Government News / US_News / Middle-east | [Kaggle Fake and real news dataset](https://www.kaggle.com/clmentbisaillon/fake-and-real-news-dataset#Fake.csv) | 70.91% |

1. BERT 모델로 2가지 Subject 데이터만 추출하여 분류할 수 있는지 테스트함
2. BERT 모델로 6가지 Subject를 가진 전체 데이터를 분류할 수 있는지 테스트함
3. LSTM+CNN 모델로 6가지 Subject를 가진 전체 데이터를 분류할 수 있는지 테스트함

#

###### ※ Kaggle Fake and real news dataset 이외에 Subject가 있는 데이터셋을 찾지 못하여 같은 데이터로 테스트함
###### ※ Subject의 분류 기준이 명확하지 않음(ex. 트럼프 내용이 News Subject에 있음)
###### ※ Subject를 가진 데이터를 찾으면, 각각의 데이터마다 Subject 분류하는 기준을 학습할 수 있도록 할 것임
