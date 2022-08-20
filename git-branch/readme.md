# branch

---

### 브랜치별 최종 커밋 내용과 해시코드
```bash
git branch -v
```

### 해당 브랜치에 머지된 브랜치 확인
```bash
git branch --merged
```

### 해당 브랜치에 머지되지않은 브랜치 확인
```bash
git branch --no-merged
```

### 원격 레포지토리에 있는 브랜치 삭제
```bash
git push origin --delete [브랜치명]
```

### 브랜치명 변경
```bash
git branch --move [원래 브랜치명] [변경할 브랜치명]
```
