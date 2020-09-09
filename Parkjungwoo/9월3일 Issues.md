## Issues 9/3 

* Deep Learning PC 동영상 견적

|종류|상세규격|가격|
|:---:|:--------:|:---:|
|CPU|Ryzen 9 3900X 24쓰레드|771,860원|
|GPU|RTX 2080 Ti D6 11GB|2,287,000원|
|MOBO|AUROS Master|300,560원|
|Ram|Vengeance RGB Pro 64gb|498,000원|
|M.2|970 EVO NVMe M.2 1TB|292,400원|
|PowerSU|Corsair AX 850W|439,770원|
|Case|Phanteks Eclipse P600s|119,300원|
|Cooler|NOCTUA NH-D15|157,230원|
|합산결과|            |4,866,120원|


* zake7749 실행해보기
  - https://github.com/zake7749/WSDM-Cup-2019/tree/master/zake7749/data/bert   
  => 재대로된 데이터셋을 찾지 못하여 소스코드만 확인 및 분석 진행.   
  **=> 윤진학생에게 물어서 진행 해 볼 것**
  

* 실제 데이터 셋이 가지고 있는 필드 정보

|데이터셋 종류|소유하는 필드명|
|------------|--------------|
|Kaggle|title, text, subject, date 등등  다양한 컬럼 선택하여 구성 가능,(2가지)|
|BuzzeFeed|id,title,text,url,top_img,authors,source,publish_date,movies,images,canonical_link,meta_data,(2가지)|
|EMRGENT|emergent_url_phase1,category_phase1,fact_tag_phase1,claim_phase1,claim_description_phase1,article_tags_phase1<br/>article_date_phase1,article_tracking_body_phase1,original_url_phase1,error_phase2,original_article_text_phase2<br/>article_title_phase2,publish_date_phase2,author_phase2,(2가지)|
|PolitiFact|politifact_url_phase1,fact_tag_phase1(8가지),article_title_phase1,article_claim_phase1,article_claim_citation_phase1<br/>article_published_date_phase1,article_researched_by_phase1,article_edited_by_phase1,article_categories_phase1<br/>original_url_phase1,page_is_first_citation_phase1,error_phase2,original_article_text_phase2,<br/>article_title_phase2,publish_date_phase2,author_phase2|
|Liar|jsonNum , fat_tag(6가지), 뉴스종류, 뉴스 인물, 뉴스 인물 직업, 지역, 성격(민주주의/공화주의),발췌 종류 등|
|SNOPE|fact_rating_phase1,snopes_url_phase1,article_title_phase1,article_category_phase1,article_date_phase1,article_claim_phase1<br/>article_origin_url_phase1,index_paragraph_phase1,page_is_first_citation_phase1,error_phase2,original_article_text_phase2<br/>article_title_phase2,publish_date_phase2,author_phase2,(10가지)


* SNU FACTCHECK 데이터를 활용하는 논문에서 어떤 데이터를 활용하였나? 
  - 작업하지 못하였습니다... 
  
* CBOW Model, Fast Text Model가 BERT와의 차이점
 1. CBOW Model(Continuous Bag of Words Model)
    - 정리
      - 주변단어를 통해서 주어진 단어가 무엇인지 찾는것.
      - 정확히는 앞뒤로 C/2개의 단어를(총 C개) 통해<평균값> 주어진 단어를 예측
      - 목적 : 주변단어들이 주어졌을때 중심단어의 조건부 확률을 최대화 하는 것.
    - 네트워크 진행과정 
      - 학습시킬 문장의 모든단어를 one-hot encoding 방식으로 벡터화 함. 0과 1의 벡터로 구성
      - 하나의 중심단어에 대해 2m개의 단어 벡터를 INPUT값으로 갖음 
      - 파라미터는 Input Layer => Hidden Layer로 가는 파라미터매트릭스(A)   
                 Hidden Layer => Output Layer로 가는 파라미터매트릭스(B)를 갖음.
      - one-hot Encoding 방식의 단어벡터들과 파라미터(A)와 곱해져서 embedded word vector가 됨
      - 이후 2m개의 embedded vector 평균을 구하고, 이때의 벡터가 Hidden Layer 값이 됨.  v`= Vc-m + Vc-m+1+ - - - + Vc+m/2m
      - hidden layer에서 OutputLayer로 전달할 Score 값 계산. 
      - hidden Layer와 파라미터(B)가 곱혀저 Score를 만듦. z(Score)= U v` (U = hidden Layer, v`= embedded vector)
      - Score값들을 확률(Softmax)을 사용하여 계산. y` = softmax(z) 
    - 학습 
      - Objective 함수(loss function)를 정의
      - 함수의 값을 최소화하는 방향으로 학습진행. H(y`,y) = -yilog(y`i)
      - i는 예측하는 단어, H 결과값이 0일수록 예측이 잘됨
      - SGD(확률적경사하강법)방법 가중치 적용 : 미분값(기울기)이 최소가 되는 점을 찾아 알맞은 weight(가중치매개변수)를 찾아냄
    - 요약
      - C개의 단어를 Hidden Layer로 보내는 C*N (파라미터매트릭스[A]사용)
      - Hidden Layer에서 Output Layer로 가는 N*V (파라미터매트릭스[B]사용)
      - 전체 계산량은 C*N + N*V   
      
 2. FastText Model 
    - 정리 
      - World2Vec 이후 나옴, WordVec의 확장
      - 모르는단어에 대한 대응
      - 글자들을 n-gram으로 나타냄
      - n의 갯수에 따라 단어를 분리하고 이를 임베딩 <,>을 도입. <ap, app, ppl, ple, le> 
      - 추가적으로 특별한 토큰값 하나를 더 임베딩 
      - 기본 n-gram의 n 값 : 3과 6으로 설정되어 있음
      - 모든단어가 각 n-gram에 대해 워드 임베딩, 데이터셋 충분히 많으면 내부단어를 통해 모르는 단어와의 유사도를 이용해 추론
      - 입력단어가 vocabulary에 있을경우, word2Vec과 마찬가지로 해당 단어의 word vector를 return 함
      - 모르는단어 일경우, 입력 단어의 n-gram Vector들의 합산을 return 함
      - 이전학습에서 birth와 place 단어를 학습한적이 있으면, birthplace의 임베딩 벡터를 만들어 낼수 있음.
 3. CBOW Model VS Fast Text Model       
    - 정리(성능 : CBOW < Fast Text) 
      - CBOW의 경우 단어 집합에서 등장 빈도수가 높으면 비교적 정확하게 임베딩, 등장빈도수가 적은단어에 대해서는 임베딩 정확도가 낮음.
      - FastText의 경우 등장 빈도 수가 적은 단어라 하더라도, n-gram으로 임베딩을 하는 특성상 이전학습된 참고할수있는 경우의 수가 많아지므로 정확도가 Word2Vec과 비교하여 정확도가 높은 경향이 있음.
      - FastText의 경우 노이즈가 많은 코퍼스에서 강점을 가지는 것 또한 이와 같은이유. 모든 훈련 코퍼스에 오타나 맞춤법이 틀린 단어가 없으면 이상적, 실제 많은 비정형 데이터에는 오타가 있음.
      - 오타가 섞인단어는 당연히 등장 빈도수가 매우적으므로 일종의 희귀 단어가 된다. Word2Vec에서는 오타가 섞인 단어는 임베딩이 제대로 되지않지만 FastText는 이에 대해서도 일정 수준의 성능을 보임.
      - CBOW 모델이나 FastText와 같은 word embedding 방식은 동형어, 다의어 등에 대해선 embedding 성능이 좋지 못하다는 단점.
      - 주변 단어를 통해 학습이 이루어지기 때문에, '문맥'을 고려할 수 없음.
 4. BERT 
    - 정리
      - BERT는 문맥에 의존하는 특징적인 표현의 전학습(deep-양방향 문맥고려)을 실시하는 대응을 바탕으로 구축
      - deep-양방향 문맥고려 : DNN 최하층에서 이용해 특징을 표현 Ex) A와 B의 두개의 글을 받았을때, B가 A의 뒤에오는 실제문장인지, 코퍼스 안의 랜덤한 글인지 판정
    - 임베딩 방법 
      - Token Embedding : Word Piece 임베딩 방식 사용, 가장 긴 길이의 Sub-word를 하나의 단위로 만듦, 자주등장하는 sub-word는 그자체의 단위, 자주등장하지않는 단어는 sub-word로 쪼개짐
      - Sentence Embedding : [CLS] : 분류할 문장 쌍의 시작 토큰, [SEP] : 문장 쌍을 각 문장으로 분리하는 토큰.
                두개의 문장을 문장구분 토큰과 합쳐서 넣음, 입력길이 두문장을 합쳐 512 subword로 제한, 대개 문장 입력길이를 128로 제한하고 학습, 128보다 긴입력들을 따로 모아 추가학습
      - Position Embedding : Transformer 모델에서 Self-Attention 모델 사용. Self-Attention 모델 입력위치에 대해 고려하지 못하므로 입력 토큰 위치정보 제공 해야 함.   
      => 3가지의 입력 임베딩을 취합하여 하나의 임베딩값으로 만듦.
    - 학습 방법
      - BERT 두가지버전 : BERT-base(L=12, H=768, A=12), BERT-large(L=24, H=1024, A=16) 은 Transformer 블록의 숫자이고 H는 hidden size, A는 Transformer의 Attention block 숫자
      - MLM과 NSP 사용
        - MLM : Token을 마스킹하고 그 Token을 맞추는 방식   
        문장의 빈칸채우기 문제 연상. 한단어를 통째로 마스킹하는 whole word masking 방법도 있음.
        - NSP : 두문장이 주어졌을때, 순서 예측하는 방식. NLI와 QA의 fine-tunning을 위해 연관이 있는 맞추도록 학습.   
        => 학습된 언어모델을 전이학습시켜 실제 NLP Task 수행

  5. 비교
 
 |모델|문맥의 의존성|임베딩 방법|
 |---|-------------|---------|
 |CBOW|문맥에 의존 X|One-hot Encoding방식 0/1로 구성, 앞뒤로 C/2개의 단어를 통해<평균값> 주어진 단어 예측|
 |FaxtText|문맥에 의존 X|n-gram방식 n의 갯수로 단어분리, 특별 토큰추가 하여 임베딩|
 |BERT|문맥에 의존 O|Token+Sentence+Position 임베딩|

