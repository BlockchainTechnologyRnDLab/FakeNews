 # FAKEDETECTOR: Effective Fake News Detection with Deep Diffusive Neural Network, 2019
 
* 논문 저자 정보 (이름, 소속)   
Jiawei Zhang, IFM Lab, Florida State University, USA
Bown Dong, Philip S.Yu, BDSC Lab, University of Iilinois, USA
2019 / 08

* 논문에서 가짜뉴스를 검출하려는 뉴스 종류
  * 소셜미디어에서의 가짜뉴스

* 논문에서 정의하고 있는 가짜뉴스
  * 고의적인 잘못된 정보(Misinformation),사기(Hoaxes)
  * 상업적, 정치적 목적을 위한 가짜뉴스

* 가짜뉴스 탐지방법 
  * 가짜뉴스 제작자와 주제를 식별하여 탐지
  * 가짜뉴스 제작자의 프로필 정보
  * 뉴스제작자의 신뢰성
  
  텍스트 컨텐츠/ 프로필/ 저자 및 기사주제와의 관계 
      
* 논문에서 학습에 사용되는 데이터
  - 데이터의 양 및 취득 방법(또는 경로)
    - PolitiFact 
    - 데이터의 양 : Twitter 계정의 PolitiFact의 모든 게시물(14,055개)과 PolitiFact 웹사이트(634개)에서 진술된 기사
    Table명 : PROPERTIES OF THE HETEROGENEOUS NETWORKS
property PolitiFact Network
# node
articles 14,055
creators 3,634
subjects 152
# link
creator-article 14,055
article-subject 48,756
    
  - 데이터 전처리 방법 : 
    - 뉴스주제에 따라 분류
    - 뉴스작성자의 프로필정보 및 뉴스 작성자의 신뢰성에 따른 분류
    - PolitiFact 데이터세트를 기사, 제작자 및 주제를 노드로 포함
      - Test 데이터셋 주소 : https://twitter.com/PolitiFact , http://www.politifact.com
      1. 텍스트 내용을 사용한 기사 신뢰성 분석 : 6가지의 라벨로 분류(True, Mostly True, Half True, Mostly False, False, Pants on Fire)  
      2. 제작자 신뢰도 분석 : 공화당 vs 민주당 등으로 나누어 신뢰도 비율 분류 
      3. 제작자와 기사 출판 기록에 대한 분석 : 기사를 게시한 작성자의 비율에 대해 뉴스 기사의 수를 분석
      4. 주제 신뢰성 분석 : 주제에 따라 참/거짓 분류 
      
    
    
* 논문에서 사용하는 알고리즘  
  - 사용한 머신러닝 알고리즘 종류 
    - deep diffusive network model,hybrid feature learning unit (HFLU)
  - 학습 방식 : 
  - 신경망을 사용할 경우 네트워크 내용
   

  - **(검토자 의견) 알고리즘이 논문에서 정의하는 가짜 뉴스를 검출하기에 적합한지 검토 의견** 

* **오픈소스 공개 여부** 
  
* 논문의 평가
  - 논문에서 주장하는 내용 
   
    
   - 논문 결과 (정량적 또는 정성적 결과)
    
     
  - **(검토자 의견) 논문 결과에 대한 객관성에 대한 검토의견** 



