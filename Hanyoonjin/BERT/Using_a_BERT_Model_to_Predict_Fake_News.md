## BERT 기반 가짜뉴스 예측

1. 데이터 업로드
2. 모듈 import
3. transformers 설치
4. BertForSequenceClassification 패키지와 BertTokenizer import
5. 데이터 전처리
    - 미리 학습된 BertTokenizer를 사용한 토큰화
    ```python
    tokenizer = BertTokenizer.from_pretrained('bert-base-multilingual-cased', do_lower_case=False)
    ```
    - [CLS]와 [SEP] 사이에 기사 토큰화된 기사 내용 삽입
    ```python
    sentences = news_data['text']
    sentences = ["[CLS] " + str(sentence) + " [SEP]" for sentence in sentences]
    tokenized_df = [tokenizer.tokenize(sent)[:510] for sent in sentences]
    ```
    - 토큰들의 index 값으로 변경
    ```python
    indexed_tokens = list(map(tokenizer.convert_tokens_to_ids, tokenized_df))
    ```
    - 라벨링 내용으로 변수 초기화
    ```python
    target_variable = news_data['label'].values
    ```
    - 인덱스와 토큰 쌍으로 맵을 생성하여 저장
    ```python
    word_to_ix = dict(zip(all_words, all_indices))
    ```
    - 마스킹된 데이터 생성
    ```python
    mask_variable = [[float(i>0) for i in ii] for ii in index_padded]
    ```
6. 학습 단계 실행과 테스트 단계 실행 함수 생성
```python
def format_tensors(text_data, mask, labels, batch_size):
．．．
```
7. 학습 데이터와 테스트 데이터 분리
```python
X_train, X_test, y_train, y_test = train_test_split(index_padded, target_variable, test_size=0.1, random_state=42)
```
8. BERT 모델 생성
    - 사전학습된 BertForSequenceClassification 사용
    ```python
    model = BertForSequenceClassification.from_pretrained('bert-base-multilingual-cased')
    ```
    - 12개의 레이어
    - Encoder와 Pooler, Dropout, 그리고 Classifier 단계로 이루어짐
9. 정확도 예측 함수 생성
```python
def compute_accuracy(model, dataloader, device):
．．．
```
10. 모델 학습
    - Epochs : 3번
    - Optimizer : Adam
    - BATCH_SIZE : 14
    - DataSet : [Kaggle](https://www.kaggle.com/c/fake-news/data?select=train.csv)의 Fake News 데이터셋 train.csv 사용(약 20,000개의 기사)
    - Training Accuracy : 99.64%
11. 모델 테스트
    - Test Accuracy : 99.13%
12. 잘못 예측된 데이터를 수집하여 오류 분석 수행

#

###### [CVPcorp - Using a BERT Model to Predict Fake News](https://colab.research.google.com/drive/1FwbW5lhgTUl4VfSGIb2oMPeAATYrTJj1?usp=sharing)
###### ※ 기존의 오픈소스에서 BertTokenizer 모델과 데이터셋을 수정하였음
