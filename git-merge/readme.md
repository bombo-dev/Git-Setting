# Merge
---

## Fast-forward Merges
```bash
git merge [브랜치명]
```
1.
```css
             master              
               ⇣  
A <- B <- C <- D <- E <- F  
                         ⇡  
                     feature-A  
```                     

2.
```css
                      master              
                         ⇣  
A <- B <- C <- D <- E <- F  
                         ⇡  
                   /*feature-A*/
```

3.

```css
                      master              
                         ⇣  
A <- B <- C <- D <- E <- F  
                          
                   
```
> 장점 : 간단하게 merge를 할 수 있고 깔끔함.  
> 단점 : merge 기록이 남지 않음.

---

## no Fast-forward Merges
```bash
git merge --no-ff [브랜치명]
```

1.
```css
             master              
               ⇣  
A <- B <- C <- D <- E <- F ↖︎  
                            ⇡  
                           feature-C  
```                     

2.
```css
                                    master              
                                      ⇣  
A <- B <- C <- D <- E <- F ↖︎ <- <- <-↙️G
                            ⇡       ⇣
                           feature-C   
```               

3.
```css
                                    master              
                                      ⇣  
A <- B <- C <- D <- E <- F ↖︎ <- <- <-↙️G
                            ⇡       ⇣
                          /*feature-C*/   
```     
> 장점 : Merge 기록을 남길 수 있음  
> 단점 : 누군가는 지저분하다고 생각 할 수 있음. 

---
## Three-way-merge

1.
```css
                              master              
                                ⇣  
A <- B <- C <- D <- E <- F ↖︎ <- I  
                            ↖︎ 
                              G <- H 
                                   ⇡ 
                                feature-C  
```                     

2.
```css
                                        master              
                                          ⇣  
A <- B <- C <- D <- E <- F ↖︎ <- I <- <- ↙️ J 
                            ↖︎        ↙️
                              G <- H 
                                   ⇡ 
                                feature-C  
```

3.
```css
                                        master              
                                          ⇣  
A <- B <- C <- D <- E <- F ↖︎ <- I <- <- ↙️ J 
                            ↖︎        ↙️
                              G <- H 
                                   ⇡ 
                              /*feature-C*/  
```

> 위와 같이 merge가 Fast-Forward가 불가능한 상황이면 자동으로 --no-ff 가 된다.

---
# Conflict
- 서로 다른 branch에서 동일한 파일을 수정후에 merge를 하면 conflict가 발생한다.
```java
<<<<<<<<<<<<<< HEAD
내용
/* 여기까지가 HEAD 포인터의 머지 내용이다. */
=============== 
내용
>>>>>>>>>>>>>> [브랜치명] 
/* 여기까지가 Merge한 브랜치의 내용이다. */
```

---

### Merge 취소
```bash
git merge --abort
```

### Merge 계속
```bash
git merge [브랜치명]

<Conflict 발생>

Auto-merging main.txt
CONFLICT (content): Merge conflict in main.txt
Automatic merge failed; fix conflicts and then commit the result.

<Conflict 해결>

git add [conflict 파일]
git merge --continue
```
---
# Cherry-pick
- 다른 브랜치에 있는 하나의 커밋만 따로 뽑아서 가져올 수 있는 기능이다.

```css
                              master              
                                ⇣  
A <- B <- C <- D <- E <- F ↖︎ <- I  
                            ↖︎ 
                              G <- H 
                                   ⇡ 
                                feature-C  
```
### 위와 같은 상황일때 G 커밋만 가지고 오고 싶다면

```bash
git log -> G의 해시코드 가져오기
git switch master
git cherry-pick [G해시코드]
```
