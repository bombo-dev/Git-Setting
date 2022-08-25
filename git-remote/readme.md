# remote
- ### 원격 레포지토리(서버)와 관련된 명령어
---
#### git clone [서버주소]
- 서버에 있는 레포지토리를 local에 가져오는 것

#### git remote -v
- 현재 연결된 remote 경로를 확인할 수 있다.

#### git remote add [서버이름] [서버주소]
- 새로운 서버를 연결할 수 있다.

#### git remote show
- 연결돼있는 서버 명을 확인 할 수 있다.

#### git fetch
- Server의 history를 local의 history에 가져온다.
- **HEAD의 포인터는 옮겨지지 않는다.**

#### git pull
- Server에 있는 history를 가지고 오면서 local의 history도 그대로 반영한다.
- **HEAD에 있는 포인터도 server에 history와 동일해지기 때문에 conflict가 발생할 수 있고 merge가 이루어진다.**

#### git pull -rebase
- Server에 있는 history를 가지고 오면서 local의 history도 그대로 반영한다.
- **단, Fast-Forward merge를 하기 위해 rebase를 하여 기록을 보존한다.**
