# Maisie-Memo

## 의도

**트위터에서 썼던 글들을 편하게 모아 볼 수 있는 방법이 없을까?**

반론<br>
- 마음을 찍으면 되잖아 ㅇㅅ"ㅇ)99 >> 마음은 주로 남의 글(정보성 트윗이 아닌것 포함)을 담을 때 쓰게 됨
- 다른 좋은 메모 어플리케이션이 많다구 >> 나는 트위터 밖으로 나가기 귀찮아
- 이거 결국은 안 쓰게 되는거 아님? >> 내가 쓸 수 있게 편한 앱을 만드는게 목표임

## 목표
**트위터/데이터베이스/웹 어플리케이션을 이용한 트위터 내의 정보 트윗 Tracker**

### **HOW TO**
- Twitter

Python Library `TWEEPY` 이용 - `USER STREAM READ`, `USER STATUS UPDATE`, `RT/FAVORITED READ`<br>
Limit 조심 - DATABASE를 주기적으로 연동하여 Twitter API의 Limit을 주의<br>
`KoNLP` 사용 - 자연어 분해를 할 수 있도록 만들자

- Database

Twtter REST API에서 받아오는 Datatype은 JSON Parser을 이용<br>
**하면 된다고 되어있지만 사실 Tweepy를 이용하면 적절하게 알아서 잘 됨**<br>
사용 예정 Database - `SQLAlchemy`

- Web-Application

Minimal 했으면 좋겠다..<br>
타임라인과 Due의 확인 위주로 되었으면 좋겠다<br>
사실 나도 잘 모름

## 상세 구현 목표
1. **Twitter API <-> DB**
- Twitter API에서 필요한 정보는 `TWEET_ID`/`TWEET_TIME`/`TWEET_STRING`<br>
TWEET_ID와 TWEET_TIME은 그대로 저장하지만, TWEET_STRING은 Python KoNLP Library를 활용하여 Parsing.

- Parsing 목표<br>
Due (목표 시간이 있는지)<br>
WHAT (무엇을 할 것인지)<br>
WHO (누구와 할 것인지)

- 글 구분<br>
Reminder: 특정 Hash Tag Text<br>
Read Later: Favorite Twit을 임시 리스트로 구성, 유저가 리스트 내에서 선택
