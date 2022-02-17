# create a new repository on the command line
```bash
echo "# js_grammer" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin 본인의 깃 주소
git push -u origin main
```

# push an existing repository from the command line
```bash
git remote add origin 본인의 깃 주소
git branch -M main
git push -u origin main
```

# git master -> main
```bash
git branch -m master main
git fetch origin
git branch -u origin/main main
```

# Delete master Remote Branch 
```bash
git push origin --delete master
```

# Cancel Commit
```
- commit을 취소하고 해당 파일들은 staged 상태로 워킹 디렉터리에 보존
$ git reset --soft HEAD^
- commit을 취소하고 해당 파일들은 unstaged 상태로 워킹 디렉터리에 보존
$ git reset --mixed HEAD^ // 기본 옵션
$ git reset HEAD^ // 위와 동일
$ git reset HEAD~n // 마지막 n개의 commit을 취소
- commit을 취소하고 해당 파일들은 unstaged 상태로 워킹 디렉터리에서 삭제
$ git reset --hard HEAD^
```
