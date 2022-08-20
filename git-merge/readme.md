# Merge
---

## Fast-forward Merges
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
