## Kaggle 데이터 필드 정리

- 필연적 : **title, text, url, author**
 1. title/ text를 사용하여 가짜뉴스탐지
 2. 1 + url, author (신뢰할만한 사이트인지 , 저자인지)를 추가적으로 사용하여 가짜뉴스 탐지
   
- 부가적 (뉴스들에 대한 상세 정보를 나타내는 모든 부분)   
  date, date, location, topic area, country, language, crawled, types, 

|NO|Kaggle 데이터셋 이름|사용하고 있는 필드명|
|-|-------------------|------------------|
|1|Fake and Real news Dataset|title / text/ subject /date / label(True/Fake)|
|2|Fake News detection|url / text(Body) / Headline(title)/ label(True/Fake)|
|3|Fake News|title/ text / label(True/Fake)|
|4|Recognizing Fake News|author / published date / title/ text / url / types / label(True/Fake)|
|5|Fake News Classifier|title / text / site_url / publication / label(True/Fake)|
|6|Getting Real about Fake News|id / author / published date/ title/ text/ language / crawled / site_url /country / label(True/Fake)|
|7|FA-KES-Dataset|id / title / content / source / data / location / label(True/Fake)|
|8|Covid_public_datset|title / date / author / url / content / topic area|
|9|News Data Set - Fake OR Real|title / text / label(True/Fake)|
|10|Fake news|id / title / author / text|
