## BERT Pooler

### 다양한 BERT 사용 비교
![conll](https://user-images.githubusercontent.com/60456487/96452051-6ae65e80-1253-11eb-86c2-fe9deb259eb6.png)
###### 표1. BERT 분류 [(1)](https://arxiv.org/pdf/1810.04805.pdf)

#

- 사전 훈련된 모델에 단순 분류 레이어를 추가시켜 미세조정하는 접근방식을 사용하면 높은 정확도의 결과를 출력할 수 있음
- 그러나 모델에서 사용되는 pooler의 출력은 입력 토큰의 의미를 유지하고 있지 않음
- 입력에 대해 Hidden state 값을 평균내거나 합하여 사용하는 것이 의미를 유지시킬 수 있음
  - ###### This output is usually not a good summary of the semantic content of the input, you’re often better with averaging or pooling the sequence of hidden-states for the whole input sequence.[(2)](https://huggingface.co/transformers/model_doc/bert.html#tfbertmodel)
- Hidden layers의 마지막 출력을 사용하거나, 합하거나, concat하는 등의 방식을 사용하면 토큰 의미를 유지할 수 있음
- Hidden layers의 마지막 레이어 4개를 concat한 벡터를 학습시킨 분류 모델은 기존의 BERT 모델인 BERT-base/BERT-large 성능에 가까운 결과를 보임

#

### 문장 벡터 생성 방법 
<img src="https://jalammar.github.io/images/bert-feature-extraction-contextualized-embeddings.png" width="650" height="400">

###### 그림1. 표1의 접근법을 설명 [(3)](https://jalammar.github.io/illustrated-bert/)
