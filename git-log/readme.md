## log의 여러가지 기능

---

### 몇 줄만 보기
```bash
git log --oneline -3
```

### 작성자별 보기
```bash
git log --author="ellie"
```

### 시간대 이전 보기
```bash
git log --before ="yyyy-mm-dd"
```

### 커밋 메세지 별 검색하여 보기
```bash
git log --grep="text"
```

### 커밋 된 수정 파일에 포함된 내용 검색하여 보기
```bash
git log -S "modify text"
```

```bash
git log -S "modify text" -p
```
### 파일 이름 별 검색하여 보기
```bash
git log file.txt
```

### 헤드를 기준으로 로그 보기
```bash
git log HEAD == git log
git log HEAD~1
git log HEAD~2
```
