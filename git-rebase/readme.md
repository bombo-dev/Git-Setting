# Rebase

```bash
git switch(checkout) [rebase할 브랜치명]
git rebase [rebase목적지 브랜치명]
```
## Example(아래 순서)
```bash
git switch feature-C
git rebase master
```

### Fast Forward Merge를 하고 싶지만 아래 상황처럼 Fast Forward Merge를 못하는 상황이 있다. 그럴때 사용할 수 있는 것이 rebase이다.
```css
                              master              
                                ⇣  
A <- B <- C <- D <- E <- F ↖︎ <- I  
                            ↖︎ 
                              G <- H 
                                   ⇡ 
                                feature-C 
```
---

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
A <- B <- C <- D <- E <- F <- I  
                                ↖︎(Rebase) 
                                  G' <- H' 
                                        ⇡ 
                                     feature-C 
```
3.
```css                
A <- B <- C <- D <- E <- F <- I       master
                                ↖︎       ⇣
                                  G' <- H' 
                                        ⇡ 
                                   /*feature-C*/ 
```

### 위와 같이 Fast-Forward-Merge가 가능하도록 할 수 있다.
> ### 장점 : Fast-Forward-Merge가 가능해져서 log를 깔끔하게 할 수 있다.
> ### 단점 : Commit은 불변의 원칙이 있다. 따라서 Rebase는 포인터의 위치를 옮기는 것이 아닌 포인터를 새로 생성해서 갱신하는 것이다.
> ### 때문에 해당 branch가 서버(Remote)에 올라와 있고 같이 작업하는 다른 개발자가 있다면 나중에 푸시할 때 Conflict가 발생할 수 있다.
> ### 따라서 혼자 작업하는 브랜치이고 아직 서버에 올리지 않았을 때 Rebase하는 것을 추천한다.
---
## Rebase --onto

- ### 브랜치 위의 브랜치를 특정 브랜치에 rebase하는 것을 말한다.
```bash
git switch [rebase 할 브랜치명]
git rebase --onto [rebase 목적지 브랜치명] [거쳐가는 브랜치 명] [rebase 할 브랜치명]
```

1.
```css
                              master              
                                ⇣  
A <- B <- C <- D <- E <- F ↖︎ <- I    service
                            ↖︎           ⇣
                              G <- H <- J 
                                   ⬆️  
                                   K <- L
                                        ⬆️
                                        UI
```

2.
```css
                                      UI
                                      ⇣ 
                                K' <- L'
                                ⇣           
A <- B <- C <- D <- E <- F ↖︎ <- I    
                            ↖︎   ⬆️     
                             ↖︎ master   service
                              ↖︎           ⇣
                                G <- H <- J 
                                     
```

> ### 장점 : branch 전체를 rebase를 안하고 merge를 할 수 있다는 장점이 있고, 작업이 오래 걸릴 것 같은거는 두고 미리 끝난 것을 merge할 수 있다.
> ### 단점 : Rebase의 단점과 동일하다.
