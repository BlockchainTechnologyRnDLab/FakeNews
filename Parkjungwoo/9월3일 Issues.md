## Issues 9/3 

* zake7749 실행해보기
  - https://github.com/zake7749/WSDM-Cup-2019/tree/master/zake7749/data/bert   
  => 재대로된 데이터셋을 찾지 못하여 소스코드만 확인 및 분석 진행.

* 실제 데이터 셋이 가지고 있는 필드 정보

|데이터셋 종류|소유하는 필드명|
|------------|--------------|
|Kaggle|title, text, subject, date 등등  다양한 컬럼 선택하여 구성 가능|
|BuzzeFeed|id,title,text,url,top_img,authors,source,publish_date,movies,images,canonical_link,meta_data|
|EMRGENT|emergent_url_phase1,category_phase1,fact_tag_phase1,claim_phase1,claim_description_phase1,article_tags_phase1<br/>article_date_phase1,article_tracking_body_phase1,original_url_phase1,error_phase2,original_article_text_phase2<br/>article_title_phase2,publish_date_phase2,author_phase2|
|PolitiFact|politifact_url_phase1,fact_tag_phase1(8가지),article_title_phase1,article_claim_phase1,article_claim_citation_phase1<br/>article_published_date_phase1,article_researched_by_phase1,article_edited_by_phase1,article_categories_phase1<br/>original_url_phase1,page_is_first_citation_phase1,error_phase2,original_article_text_phase2,<br/>article_title_phase2,publish_date_phase2,author_phase2|
|Liar|jsonNum , fat_tag(6가지), 뉴스종류, 뉴스 인물, 뉴스 인물 직업, 지역, 성격(민주주의/공화주의),발췌 종류 등|
|SNOPE|fact_rating_phase1,snopes_url_phase1,article_title_phase1,article_category_phase1,article_date_phase1,article_claim_phase1<br/>article_origin_url_phase1,index_paragraph_phase1,page_is_first_citation_phase1,error_phase2,original_article_text_phase2<br/>article_title_phase2,publish_date_phase2,author_phase2


* SNU FACTCHECK 데이터를 활용하는 논문에서 어떤 데이터를 활용하였나? 

* CBOW model, Fast Text Model가 BERT와의 차이점
https://dalpo0814.tistory.com/4
https://medium.com/@omicro03/%EC%9E%90%EC%97%B0%EC%96%B4%EC%B2%98%EB%A6%AC-nlp-15%EC%9D%BC%EC%B0%A8-fasttext-2b1aca6b3b56
