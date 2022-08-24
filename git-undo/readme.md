# Undo
- #### 깃은 파일을 되돌리거나, 커밋을 수정하는 등 실수를 했을 때 만회할 수 있는 여러가지 방법들이 있다.
---

### restore

1. Unstaged Working Directory에 변경된 사항 전체 되돌리기
```bash
git restore .
git restore [파일이름]
```

2. Staging Area에 변경된 사항 Unstaged Working Directory로 되돌리기
```bash
git restore --staged .
git restore --staged [파일이름]
```

3. 특정 commit 시점에 있는 파일 내용으로 되돌리기
```bash
git restore --source=[해시코드] [파일이름]
git restore --source=[HEAD~n] [파일이름]
```

---

### reset
- #### 특정 커밋 시점으로 되돌아간다. 과거로 되돌아가 해당 사건 이후의 커밋들이 모두 지워진다.
- #### reset은 과거의 이력이 커밋에 안남고 깔끔하게 과거로 돌아간다.

1. staging area에 있는 파일들을 보존하면서, 이전 상태로 되돌리기
- commit의 시점만 변경되고 staging area와 working directory의 상태는 reset --soft하기 이전과 동일하다.
```bash
git reset --soft [해시코드]
git reset --soft [HEAD~n]
```

2. staging area에 있는 파일들을 unstaged 상태로 되돌리기
- 옵션 작성을 하지 않으면 기본 값이다.
- commit과 staging area의 시점이 변경된다. 단, working directory의 상태는 reset --mixed하기 이전과 동일하다.
```bash
git reset --mixed [해시코드]
git reset --mixed [HEAD~n]
```

3. 해당 커밋 시점으로 아예 초기화 하기
- commit을 한 그 시점과 아예 동일하게 commit, staging area, working directory가 초기화 된다.
```bash
git reset --hard [해시코드]
git reset --hard [HEAD~n]
```
---

### amend
- #### 커밋의 내용을 변경한다.

1. 커밋 메세지 변경하기

```bash
git commit --amend -m "[text]"
git commit --amend (설정한 에디터가 열린다.)
```
