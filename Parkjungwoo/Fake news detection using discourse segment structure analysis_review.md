# Fake news detection using discourse segment structure analysis
* 논문 저자 정보 (이름, 소속)
  - Anmol Uppal, Vipul Sachdeva, Seema Sharma, INDIA, Amity University Noida University

* 논문에서 가짜뉴스를 검출하려는 뉴스 종류 : 소셜 Context, 뉴스 Content Model, 가짜뉴스 탐지

* 논문에서 정의하고 있는 가짜뉴스
  - 단순히 거짓 뉴스, 대중을 오해 하기위해 기존 또는 온라인 뉴스매체를 통해 고의적인 오보

* 가짜뉴스 탐지방법
   1. 지식기반탐지 : 뉴스기사에 제시된 유익한 내용
   2. 스타일기반탐지 : 작문스타일과 언어 내용의 패턴
   3. 소셜 콘텍스트 모델 : 뉴스의 전파 패턴, 새로운 뉴스 생성자와 전파 기반 기술의 관계 신뢰도

||진위|의도|뉴스|
|------|---|---|---|
|악의적으로 거짓 뉴스|FALSE|BAD|YES|
|가짜 뉴스|FALSE|Unknown|YES|
|풍자 뉴스|Unknown|Not Bad|YES|
|잘못된 정보| FALSE|BAD| Unknown|
|사라진 정보|FALSE|Unknown|Unknown|
|소문|Unknown|Unknown|Unknown|

* 가짜뉴스 탐지를 위한 다양한 방법론(2016년 이후)
|AUTHOR|OUTCOME|CONCLUSION/TECHNIQUE USED|
|------|---|---|
|Monu Waskale, Prof.Pritesh Jain, 2019|GRU-2 can identify bits of gossip with exactness 83.9% for twitter within 12-hours.|Rational investigation of large portion of existing techniques identified from the earlier bits of gossip using GRU-2 and Tanh-RNN classifier for comparison.|
|Cody Buntain, Jennifer Golbeck, 2018|66.93% and 70.28% in PHEME and CREDBANK|Automated system for distinguishing fake news
in famous Twitter threads.|
|Kursuncu et al. , 2018|Analysis resulting in 73% F score. Supervised learning F score of 88.2 and ROC of 94.3.|Discussed Sentiment predictive analysis by time series in different domains.|
|Jiawei Zhang, Bowen Dong, Philip S. Yu, 2019|Comparing with existing systems, Bi-Class Inference Results in 14.5% higher and 40% higher in multi- Class Inference.|A deep diffusive network model to learn the depictions of news articles, subjects and creators.|
|Ruchansky et al. , 2017|Positive correlation of 0.867 for Weibo, 0.631 for Twitter.|Propose the CSI model which consists of three modules.|
|Monther Aldwairi, Ali Alwahedi|99.4% accuracy|Clickbait Detection using Logistic Classifier|
|테스트1|테스트2|테스트3|
|테스트1|테스트2|테스트3|
|테스트1|테스트2|테스트3|
|테스트1|테스트2|테스트3|
|테스트1|테스트2|테스트3|
|테스트1|테스트2|테스트3|
|테스트1|테스트2|테스트3|
|테스트1|테스트2|테스트3|
|테스트1|테스트2|테스트3|
|테스트1|테스트2|테스트3|
|테스트1|테스트2|테스트3|

* 논문에서 학습에 사용되는 데이터
  - 데이터의 양 및 취득 방법(또는 경로)
  - 데이터 전처리 방법
  -  **(검토자 의견) 데이터 객관성 여부에 대한 검토 의견**  
* 논문에서 사용하는 알고리즘  
  - 사용한 머신러닝 알고리즘 종류 
  - 학습 방식 (지도학습, 비지도학습, 강화학습)
  - 신경망을 사용할 경우 네트워크 내용
  - **(검토자 의견) 알고리즘이 논문에서 정의하는 가짜 뉴스를 검출하기에 적합한지 검토 의견** 
* **오픈소스 공개 여부** 
* 논문의 평가
  - 논문에서 주장하는 내용
    가짜뉴스 탐지의 기존 방법론을 검토하고, 자동으로 탐지방법을 제안하고 구현
    
  - 논문 결과 (정량적 또는 정성적 결과)
  - **(검토자 의견) 논문 결과에 대한 객관성에 대한 검토의견** 

* 관련연구: 논문에서 기술하는 관련 연구 부분 중 검토필요가 있는 것은 일반 논문의 검토와 같은 수준의 논문 리뷰를 하는 것으로 
확장하기 위한 것으로 규정


표 1 : 가짜 뉴스 카테고리
                       진위 / 의도 / 뉴스?
악의적으로 거짓 뉴스    FALSE   BAD     YES
가짜 뉴스              FALSE  Unknown  YES
풍자 뉴스             Unknown Not Bad  YES
잘못된 정보            FALSE  BAD      Unknown  
사라진 정보            FALSE  Unknown  Unknown
소문                  Unknown Unknown Unknown


 
 
 
 
 
 
 
 
 
 
 
