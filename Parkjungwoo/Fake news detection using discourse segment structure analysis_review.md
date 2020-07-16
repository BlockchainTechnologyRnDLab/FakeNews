# Fake news detection using discourse segment structure analysis
* 논문 저자 정보 (이름, 소속)
  - Anmol Uppal, Vipul Sachdeva, Seema Sharma, INDIA, Amity University Noida University

* 논문에서 가짜뉴스를 검출하려는 뉴스 종류 : 소셜 Context, 뉴스 Content Model, 가짜뉴스 탐지

* 논문에서 정의하고 있는 가짜뉴스
  - 단순히 거짓 뉴스, 대중을 오해 하기위해 기존 또는 온라인 뉴스매체를 통해 고의적인 오보
  
||진위|의도|뉴스|
|------|---|---|---|
|악의적으로 거짓 뉴스|FALSE|BAD|YES|
|가짜 뉴스|FALSE|Unknown|YES|
|풍자 뉴스|Unknown|Not Bad|YES|
|잘못된 정보| FALSE|BAD| Unknown|
|사라진 정보|FALSE|Unknown|Unknown|
|소문|Unknown|Unknown|Unknown|

* 가짜뉴스 탐지방법
   1. 지식기반탐지 : 뉴스기사에 제시된 유익한 내용
   2. 스타일기반탐지 : 작문스타일과 언어 내용의 패턴
   3. 소셜 콘텍스트 모델 : 뉴스의 전파 패턴, 새로운 뉴스 생성자와 전파 기반 기술의 관계 신뢰도

* 가짜뉴스 탐지를 위한 다양한 방법론(2016년 이후)

|AUTHOR|OUTCOME|CONCLUSION/TECHNIQUE USED|
|------|---|---|
|Monu Waskale, Prof.Pritesh Jain, 2019|GRU-2 can identify bits of gossip with exactness 83.9% for twitter within 12-hours.|Rational investigation of large portion of existing techniques identified from the earlier bits of gossip using GRU-2 and Tanh-RNN classifier for comparison.|
|Cody Buntain, Jennifer Golbeck, 2018|66.93% and 70.28% in PHEME and CREDBANK|Automated system for distinguishing fake newsin famous Twitter threads.|
|Kursuncu et al. , 2018|Analysis resulting in 73% F score. Supervised learning F score of 88.2 and ROC of 94.3.|Discussed Sentiment predictive analysis by time series in different domains.|
|Jiawei Zhang, Bowen Dong, Philip S. Yu, 2019|Comparing with existing systems, Bi-Class Inference Results in 14.5% higher and 40% higher in multi- Class Inference.|A deep diffusive network model to learn the depictions of news articles, subjects and creators.|
|Ruchansky et al. , 2017|Positive correlation of 0.867 for Weibo, 0.631 for Twitter.|Propose the CSI model which consists of three modules.|
|Monther Aldwairi, Ali Alwahedi|99.4% accuracy|Clickbait Detection using Logistic Classifier|
|Traylor et al. ,2019|Classifier Accuracy: 0.69 Overall Classifier Error:0.31.|ML-classification for large fake newsdocuments with one extraction feature.|
|Oshikawa et al. ,2018|Maximum accuracy in 94.4% using GCN model|Comparison of existing fake news detection models|
|Gurav et al. ,2019|Series of methods accomplished by Machine Leaning|Pure NLP perspective towards false news detection|
|Agarwalla et al. ,2019|Accuracy in Naïve Bayes classifier with lid stone smoothing is 83% and in Naïve Bayes (without lidstone smoothing) is 74%.|An algorithm have been explored that can distinguish the difference between the fake and true news|
|Zellers et al. ,2019|Grover-Large yields 78% accuracy, 92% when dataset is increased.|Investigated the threats posed by adversaries seeking to spread disinformation and the possibilities of machine generated fake news.|
|Sivasangar i V et al. ,2018|Precision: 0.86 F1-score: 0.86|Rumor Detection by lever maturing the setting going before a tweet with a consecutive classifier|
|O'Brien et al. ,2018|Accuracy: 93.5% ± 0.2.|Deep neural networks to capture steady differences in the language of fake and real news: signatures of exaggeration and other forms of rhetoric| 
|Shu et al. ,2017|Studying existing literature in two segments: detection and characterization.|Datasets, evaluation metrics, and promising future ways in fake news detection discussed.|
|Silva et al. ,2019|ANN achieving 75% accuracy|An amalgamation of classic techniques with neural network|
|Dong et al. ,2019|Detect fake news from PHEME datasets using labeled data and unlabeled data.|Deep semi-supervised learning model by constructing two-path CNN|
|Yang et al. ,2019|88.063% accuracy|Soft labels are used to fine-tune NLI models, BERT, and the Decomposable Attention model. NLI models are trained independently and ensemble with a BERT model to define the soft labels.|
|Monti et al.,2019|More than 93% accuracy achieved by automatic fake news detection model built on geometric deeplearning.|The underlying core algorithms allow for a fusion of dissimilar data such as content, profile, activity of a user, social graph and propagation pattern of news, which is achieved by generalizing CNN to graphs.|
|Ajao et al.,2018|82% accuracy via both text and images by automatic identification of features within Twitter posts|A hybrid deep learning model of LSTM and CNN models is used.|
|Thota et al. ,2018|94.21% accuracy. The Dense Neural Network beats existing model architectures by 2.5%.|A finely tuned TF-IDF Dense neural network architecture to predict the stance between a given pair of headline and article body.|
|Helmstetter, Heiko Paulheim ,2018|F1 score of 0.9 achieved|Trustworthy or untrustworthy source are used to automaticallylabel the data during collection, and train a classifier on this dataset.|
|Atodiresei et al. ,2018|Tweet score can be 1000, -500 or in [-50,100] User score can be in [0,12]|Credibility score fromhashtag sentiments, emoji sentiments, text sentiments and namedentity recognition. Higher the credibility score, higher the trust|
|Hamid Karimi, Jiliang Tang ,2019|82% accuracy|Hierarchical Discourse level structural data analysis for fake newsdetection. A structure is trained on the dataset, quantifiable properties of which are used for classification process in the model.|
|Shuo Yang et al., 2019|Graphical model is built taking into account reliability of the news and credibility score of the user. 75.9% max. Accuracy accomplished on LIAR dataset.|Unsupervised method is investigated. Opinion is extracted from hierarchy social engagement information acquired from social media users..Reality and credibility is considered by an efficient Gibbs-sampling method.|
|Zhou et al.,2018|Models so far possess a greater possibility to misclassify fake news that tampers with facts as well as under-written real news articles|Simply looking into Linguistic aspects is not enough for fake news detection.|
|Álvaro and Lara,2019|93% accuracy with superior metrics compared to other deep learning models|BERT, LSTM and Convolutional Neural Network models are trained based merely on textual features.|

* 논문에서 학습에 사용되는 데이터
  - 데이터의 양 및 취득 방법(또는 경로)
   취득 경로 : Kaggle.com, Buzzfeed, PolitiFact
   데이터의 양 : 교육용 6398개의 문서
  
  - 데이터 전처리 방법
   1. 담론의존성 파싱 접근법, 유사한 의존성 트리구조로 문서를 나뉨
   2. 수집된 데이터 세트 영어 이외의 모든 문자와 중지단어를 제거
   3. 모든 문자를 소문자로 변환 
      
  -  **(검토자 의견) 데이터 객관성 여부에 대한 검토 의견**  
* 논문에서 사용하는 알고리즘  
  - 사용한 머신러닝 알고리즘 종류
    Google : WORD2VEC
    ELU(비선형활성화 함수)
  - 학습 방식 : 비지도학습 
  - 신경망을 사용할 경우 네트워크 내용
  
* **오픈소스 공개 여부** 
   X
* 논문의 평가
  - 논문에서 주장하는 내용
    가짜뉴스 탐지의 기존 방법론을 검토하고, 담론의존성 파싱 접근법으로 뉴스 맥락분석과 관련된 중요 설명,
    담론의존성 접근법과는 달리 또다른 문법적 구조 트리가 있을 수 있다고 주장.
    
  - 논문 결과 (정량적 또는 정성적 결과)
    데이터를 WORD2VEC과 ELU를 사용하여 학습한 결과 제안된 모델 탐지율 : 74.62% 
   


