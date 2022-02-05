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
