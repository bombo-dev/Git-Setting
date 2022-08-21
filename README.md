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

# Save Credential File

- Credential 정보 반영구로 저장하는 방식
```bash
git config --unset credential.helper [기존에 세팅된 credential.helper 데이터를 해제]
git config credential.helper store [저장 / 따로 설정해주지 않았다면, ~/.git-credentials에 저장
```

- Credential 정보를 특정시간동안 git cache에 임시로 저장하는 방식
```bash
git config --unset credential.helper
git config credential.helper cache
git config credential.helper 'cache --timeout 7200' [sec 단위, 필요에 따라 변경가능 Default는 900초]
```
* --global 옵션을 추가할 경우 모든 repository에 적용할 수 있다.

# Link Local Branch to Remote Branch

```bash
git push --set-upstream origin [브랜치명]
```

# vscode를 이용한 merge
```bash
git config --global -e
```

```ini
[merge]
	tool = vscode
[mergetool "vscode"]
	cmd = code --wait $MERGED
[mergetool]
	keepBackup = false
```

>> keepBackup은 mergetool을 이용하여 merge를 하게 됐을때 파일.orig 이라는 백업 파일이 생기게 되는데 이걸 막아주는 것이다.

