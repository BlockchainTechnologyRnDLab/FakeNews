## dEFEND: Explainable Fake News Detection

| Platform | PolitiFact | GossipCop |
|---|---|---|
| Users | 68,523 | 156,467 |
| Comments | 89,999 | 231,269 |
| Candidate news | 415 | 5,816 |
| True news | 145 | 3,586 |
| Fake news | 270  | 2,230 |

### Twitter 크롤링이 필요한 PolitiFact / Gossipcop 데이터셋 사용
- 학습 : 75% / 테스트 : 25%
- 기사 콘텐츠와 이와 관련된 소셜 미디어의 답변들을 활용하여 가짜뉴스를 탐지함
- 가짜뉴스 탐지 결과를 설명가능하도록 학습시키기 위해 기사에 대한 사용자 의견들을 활용함
- 기사의 라벨링에 따라 달라지는 사용자들의 답변으로 학습시킴

### nltk(자연어 처리 패키지)의 Tokenizer를 사용하여 단어 토큰화
-

### Glove를 사용한 토큰 가중치 부여
-

### 양방향 GRU를 사용한 학습
-

#
###### [오픈소스](https://www.dropbox.com/sh/rzczwopo618jyv2/AAA1mI2yvbt6TAfqpcxfjL8va?dl=0)
###### [논문](https://www.researchgate.net/publication/332864316_dEFEND_Explainable_Fake_News_Detection)
