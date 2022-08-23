# Stash

- Commit은 하지 않았는데 현재 내 파일들의 상태를 임시 저장해두고 브랜치를 옮길때 사용할 수 있다.
```bash
git stash (push)
```
---


### 현재 나의 Working Directory에 있는 작업 파일 stash
```bash
git stash push -m "first"
```

### Staging Area의 상태는 유지하면서 stash
- 아마도 현재까지의 기록을 commit하기 싫고 저장은 해두고 싶을 때 사용할 것 같다. 예를 들어 어떤 bug fix 돌입하기 전같은 경우
```bash
git stash push -m "keep staging" --keep-index
```

### Untrackted된 파일을 stash
- 기본적으로 stash는 Untrackted 파일을 stash 하지 않는다.
```bash
git stash -u
```

### stash된 목록 보기
```bash
git stash list
```

### 해당 stash 가져오면서 stash list 유지
```bash
git stash apply [stash번호]
```

### 해당 stash 가져오고 stash list 삭제
- 스택으로 공간이 유지되기 때문에 최상단부터 빠져나온다.
```bash
git stash pop
```
### 해당 stashlist에서 stash 삭제
- stash번호를 입력하지 않으면 최상단의 stash가 삭제된다.
```bash
git stash drop [stash번호]
```

### stashlist의 내용을 반영하면서 새로운 브랜치 만들기
- stashlist에 있는 내용이 반영되면서 새로운 브랜치가 만들어진다.
```bash
git stash branch [브랜치명]
```
