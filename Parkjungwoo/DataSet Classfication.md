# DATA SET 분류 작업.

Dataset 라벨 좀더 상세히 분류하고 조사 할 것. DeepLearning 부분만 조사 인것인지, 전체적인 논문에 다 조사 
 
 * 영어 DATA SET 
 
|DATA SET 종류|DATA SET 획득경로|DATA SET 크기(단위:개)|DATA SET 라벨|정보제공자|
|------|---|---|---|---|
|LIAR|Short Claim(짧은 주장)|12,836|six-grade|Editor, Journalists|
|FEVER|Short Claim(짧은 주장)|185,445|three-grade|Trained Annotators|
|BuzzzFeedNews|FB post(FaceBook)|2282|four-grade|Journnalists|
|BuzzzFace|FB post(FaceBook)|2263|four-grade|Journnalists|
|some-like-it-hoax|Tweet|15,500|hoaxes or non-hoaxes(사기/비사기)|None|
|PHEME|Tweet|330|true or false|Jounarlists|
|CREDBANK|Tweet|60 milion|30-element vecotr|Workers|
|FAKENEWSNET|article|23,921|fake or real|Editors|
|BS Detector|article|-|10 different Types|None|
|PolitiFact|자세히조사必|||Enterprise|
|...|..|...|..|

  * 한국 DATA SET 

|DATA SET 종류|DATA SET 획득경로|DATA SET 크기(단위:개)|DATA SET 라벨|정보제공자|
|------|---|---|---|---|
|Kinds|News,article|200(더조사해보아야함)|tree-grade|한국언론진흥재단| 
|...|..|...|..|
 
 * dataset 참조 논문 
   - Fake News Detection on Social Media: A Data Mining Perspective 
   - 사이트 : https://arxiv.org/pdf/1708.01967.pdf 
                    
 * 주소 
   - 한국어
   1. SNU FactCheck : http://factcheck.snu.ac.kr/
   2. Kinds : https://www.bigkinds.or.kr/
   
   - 영어
   1. kaggle : https://kaggle.com , https://www.kaggle.com/mrisdal/fake-news
   2. Fever :  http://fever.ai , https://github.com/awslabs/fever , https://github.com/sheffieldnlp/fever-baselines
   3. Emergent : http://www.emergent.info/led-zeppelin-contract
   4. CREDBANK : http://compsocial.github.io/CREDBANK-data/
   5. Liar : https://www.cs.ucsb.edu/ , https://www.cs.ucsb.edu/~william/data/liar_dataset.zip
   6. BuzzFeed : https://github.com/BuzzFeedNews/2016-10-facebook-fact-check/tree/master/data
   7. George Mcintre : https://www.quora.com/What-are-some-datasets-about-fake-news
   8. FakeNewsNET : https://github.com/KaiDMML/FakeNewsNet
   9. FNC-1 : http://www.fakenewschallenge.org/
   10. Politifact : https://www.politifact.com/
   11. MediaEval Multimedia 2015 : http://www:multimediaeval:org/mediaeval2015/verifyingmultimediause
   12. MediaEval Multimedia 2016 : http://www:multimediaeval:org/mediaeval2016/verifyingmultimediause
   13. Twitter : www.twitter.com
   14. weibo : www.weibo.com
   15. Snopes : www.snopes.com
   16. PHEME : https://www.pheme.eu/
  
 * 논문에 따른 DataSet 정리

|논문명|DATA SET|
|-----|--------|
|A Benchmark Study on Machine Learning Methods for Fake News Detection|Liar, Fake or Real News, Combined Corpus|
|A Deep Ensemble Framework for Fake News Detection and Classification|Liar, PolitiFact.com|
|A Deep Learning Approach for Automatic Detection of Fake News|FakeNewsATM, Celebrity|
|EMET: EMBEDDINGS FROM MULTILINGUAL-ENCODER TRANSFORMER FOR FAKE NEWS DETECTION|Social Media : MediaEval Multimedia Benchmark(2015/16)|
|Exploiting Multi-domain Visual Information for Fake News Detection|Social Media : MediaEval Multimedia Benchmark(2016),Weibo ACM 2017|
|Fake News Detection Using A Deep Neural Network|Kaggle|
|Fake news detection using discourse segment structure analysis|Kaggle, Buzzfeed, Politifact|
|Fake News Detection Using Machine Learning approaches- A systematic Review|리뷰논문으로 데이터셋 X|
|Fake News Detection: A long way to go|kaggle,Liar,Fever,Emergent,CredBank, George Mcintire, FakeNewsNET, UNBLASED, FNC-1 CHallenge|
|A Benchmark Study on Machine Learning Methods for Fake NewsDetection|Liar, Fake or RealNews(GeorgeMcintire,Kaggle)|
|A Deep Learning Approach for Automatic Detection of Fake News|Fakenws AMT(AmazonMechanical Turk), Celebrity NEWS(web Crawled)|
|BRENDA: Browser Extension for Fake News Detection|Politifact, SGD-LSTM 학습모델데이터(https://github.com/apepa/claim-rank/tree/master/data)|
|CSI: A Hybrid Deep Model for Fake News Detection|Twitter, Webio|
|DeClarE: Debunking Fake News and False Claimsusing Evidence-Aware Deep Learning|Snopes, Politifact,SemEval, NewsTrust|
|Deep Diffusive Neural Network based Fake NewsDetection from Heterogeneous Social Networks|Politifact,Liar|
|Detecting Fake News using Machine Learning Algorithms|Doc 문서 열수없음.|
|Detecting Fake News using Machine Learning and Deep Learning Algorithms|Twitter(Chile Earthquake Dataset 2010)|
|Fake News Detection Using Deep Learning Techniques|Liar,PHEME|
|Fake News Detection: A Deep Learning Approach|FNC-1|
|FNDNet- A deep convolutional neural network for fake news detection|Kaggle|
|TI-CNN: Convolutional Neural Networks for FakeNews Detection|Kaggel, 실제뉴스(뉴욕타임즈,워시텅포스트)크롤링|
|exBAKE: Automatic Fake News Detection Model Based on Bidirectional Encoder Representations from Transformers|          |
|A Deep Ensemble Framework for Fake NewsDetection and Classification|Kaggle, Liar|
|Deep Two-path Semi-supervised Learning for Fake News Detection|Twitter, PHEME|
|Detecting Incongruity between News Headline and Body Textvia a Deep Hierarchical Encoder|FNC-1|
|Fake News Identification on Twitter with Hybrid CNN and RNN Models|PHEME|
|FAKEDETECTOR: Effective Fake News Detection with Deep Diffusive Neural Network|PolitiFact|
|Semi-Supervised Learning and Graph NeuralNetworks for Fake News Detection|Buzzfeed,자신들의 모델링 뉴스(https://github.com/rpitrust/fakenewsdata1), Burfoot and Baldwin 2009|
