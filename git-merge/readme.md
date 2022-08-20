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
