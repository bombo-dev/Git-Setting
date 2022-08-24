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

---
## git rebase interactive
- 이전 시점부터 현재 시점의 커밋 내용을 수정하고 싶을 때 사용하는 명령어이다.
- rebase이기 때문에 이전 시점 이후의 커밋들도 새로이 업데이트 되는 것이기 때문에 **새로운 커밋 포인트를 생성**하는 것이다.
- 서버에 push가 돼있을 경우 conflict가 발생하기 때문에 사용을 주의해야 한다.
- a <- b <- c <- d 에서 **c를 수정하고 싶을 경우 d로 이동을 해서 수정**을 해주어야 한다.
```bash
git rebase -i [commit 해시코드]
```
> rebase를 위한 설정한 편집 에디터가 나타나고, 아래의 명령어를 입력하여 수정하면 된다.  
>> ex) 
>>```ini
>>pick [commit 해시코드] [commit 메세지]
>>pick [commit 해시코드] [commit 메세지]
>>pick [commit 해시코드] [commit 메세지]
>>pick [commit 해시코드] [commit 메세지]
>>```
>>```ini
>>r(reword) [commit 해시코드] [commit 메세지]
>>pick [commit 해시코드] [commit 메세지]
>>pick [commit 해시코드] [commit 메세지]
>>pick [commit 해시코드] [commit 메세지]
>>```
> 새로운 창이 다시 열리고 reword
### rebase -i edit 명령어
1. p, pick : 해당 커밋을 그대로 사용한다.
2. r, reword : 해당 커밋을 사용하되, 커밋 메시지를 변경한다.
3. e, edit : 해당 커밋을 사용하되, 해당 커밋의 변경 사항을 바꿀때 사용
4. s, squash : 해당 커밋을 사용하되, 이전 커밋들과 합친다.
5. f, fixup : squash와 동일하지만, 커밋의 내용을 버린다.
6. x, exec : 이 시점부터 shell 명령어를 사용한다는데, 잘 안쓴다고 한다.
7. b, break : 이 시점에서 rebase를 잠시 멈춘다. git rebase --continue를 통해 계속 진행 가능
8. d, drop : 해당 커밋을 버린다.
