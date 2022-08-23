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
