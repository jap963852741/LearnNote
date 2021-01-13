## 題目
>	You are given two non-empty arrays A and B consisting of N integers. Arrays A and B represent N voracious fish in a river, ordered downstream along the flow of the river.
>	
>	The fish are numbered from 0 to N − 1. If P and Q are two fish and P < Q, then fish P is initially upstream of fish Q. Initially, each fish has a unique position.
>	
>	Fish number P is represented by A[P] and B[P]. Array A contains the sizes of the fish. All its elements are unique. Array B contains the directions of the fish. It contains only 0s and/or 1s, where:
>	
>	0 represents a fish flowing upstream,
>	1 represents a fish flowing downstream.
>	
>	If two fish move in opposite directions and there are no other (living) fish between them, they will eventually meet each other. Then only one fish can stay alive − the larger fish eats the smaller one. More precisely, we say that two fish P and Q meet each other when P < Q, B[P] = 1 and B[Q] = 0, and there are no living fish between them. After they meet:
>	
>	If A[P] > A[Q] then P eats Q, and P will still be flowing downstream,
>	If A[Q] > A[P] then Q eats P, and Q will still be flowing upstream.
>	
>	We assume that all the fish are flowing at the same speed. That is, fish moving in the same direction never meet. The goal is to calculate the number of fish that will stay alive.
>	
>	For example, consider arrays A and B such that:
>	
>	A[0] = 4 B[0] = 0 A[1] = 3 B[1] = 1 A[2] = 2 B[2] = 0 A[3] = 1 B[3] = 0 A[4] = 5 B[4] = 0
>	
>	Initially all the fish are alive and all except fish number 1 are moving upstream. Fish number 1 meets fish number 2 and eats it, then it meets fish number 3 and eats it too. Finally, it meets fish number 4 and is eaten by it. The remaining two fish, number 0 and 4, never meet and therefore stay alive.
>	
>	Write a function:
>	
>	class Solution { public int solution(int[] A, int[] B); }
>	
>	that, given two non-empty arrays A and B consisting of N integers, returns the number of fish that will stay alive.
>	
>	For example, given the arrays shown above, the function should return 2, as explained above.
>	
>	Write an efficient algorithm for the following assumptions:
>	
>	N is an integer within the range [1..100,000];
>	each element of array A is an integer within the range [0..1,000,000,000];
>	each element of array B is an integer that can have one of the following values: 0, 1;
>	the elements of A are all distinct.

## 解題思路
>用 stack 去解 \
>如果 stack 是空的 就直接放魚\
>如果 不是空的\
>再把 stack 的第一個拿出來比方向及大小

## 程式碼
### Detected time complexity : O(N)
```java
// you can also use imports, for example:
import java.util.*;

// you can write to stdout for debugging purposes, e.g.
// System.out.println("this is a debug message");

class Solution {
    public int solution(int[] A, int[] B) {
        // write your code in Java SE 8
        Stack st = new Stack();
        int count = 0;

        while(count < A.length){
            if(st.empty()){
                st.push(count);
            }else{ //裡面有魚
                boolean ok = false; 
                int now_fish_big = A[count];
                int now_fish_zero_one = B[count];
                //如果裡面有魚的話可能會一值往下把魚取出來  >> 所以default false
                //等確定魚的位置時將 ok 設為true 結束這隻魚
                while(!ok){
                    if(st.empty()){  //有可能會一值取出 結果 st空了
                        st.push(count);
                        ok = true;
                        break;
                    }
                    int first_in_box_fish_big = A[(Integer) st.peek()];
                    int first_in_box_fish_zero_one = B[(Integer) st.peek()];
                    /**
                    *邏輯
                    *
                    *裡面最上面的魚 0 >> 可以放魚
                    *裡面最上面的魚 1 >> 
                    *放 1 OK
                    *放 0  
                    *>> 比裡面的大  把裡面取出
                    *>> 比裡面的小  下一隻魚
                    */
                    if(first_in_box_fish_zero_one == 0){
                        st.push(count);
                        ok = true;
                    }else{
                        if(now_fish_zero_one == 1){
                            st.push(count);
                            ok = true;
                        }else{
                            if(now_fish_big > first_in_box_fish_big){
                                st.pop();
                            }else{
                                ok = true;
                            }
                        }
                    }
                }
            }    
            count++;
        }
        return st.size();
    }
}


```






