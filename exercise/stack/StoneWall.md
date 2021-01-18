## 題目
>	You are going to build a stone wall. The wall should be straight and N meters long, and its thickness should be constant; however, it should have different heights in different places. The height of the wall is specified by an array H of N positive integers. H[I] is the height of the wall from I to I+1 meters to the right of its left end. In particular, H[0] is the height of the wall's left end and H[N−1] is the height of the wall's right end.	\
>		\
>	The wall should be built of cuboid stone blocks (that is, all sides of such blocks are rectangular). Your task is to compute the minimum number of blocks needed to build the wall.	\
>		\
>	Write a function:	\
>		\
>	class Solution { public int solution(int[] H); }	\
>		\
>	that, given an array H of N positive integers specifying the height of the wall, returns the minimum number of blocks needed to build it.	\
>		\
>	For example, given array H containing N = 9 integers:	\
>		\
>	H[0] = 8    H[1] = 8    H[2] = 5	\
>	H[3] = 7    H[4] = 9    H[5] = 8	\
>	H[6] = 7    H[7] = 4    H[8] = 8	\
>	the function should return 7. The figure shows one possible arrangement of seven blocks.	\
>		\
>		\
>		\
>	Write an efficient algorithm for the following assumptions:	\
>		\
>	N is an integer within the range [1..100,000];	\
>	each element of array H is an integer within the range [1..1,000,000,000].	

## 解題思路
>用 stack 去紀錄目前較低的石牆如果有相等就可以少放一塊

## 程式碼
### Detected time complexity : O(N)
```java
// you can also use imports, for example:
import java.util.*;

// you can write to stdout for debugging purposes, e.g.
// System.out.println("this is a debug message");

class Solution {
    public int solution(int[] H) {
        // write your code in Java SE 8
        int ans = H.length;
        Stack min_arraylist = new Stack();
        int cnt = 0;
        while(cnt < H.length){
            if(min_arraylist.empty()){
                min_arraylist.push(H[cnt]);
            }else{ //放石堆
                int the_stone_high = H[cnt];//要放入的石頭高度
                boolean ok = false;
                int inside_stone_high = (Integer) min_arraylist.peek();
                while(!ok){
                    if(min_arraylist.empty()){
                        ok = true;
                        min_arraylist.push(H[cnt]);
                        break;
                    }else{
                        inside_stone_high = (Integer) min_arraylist.peek();
                    }
                    
                    if(inside_stone_high == the_stone_high){
                        ans--;
                        ok = true;
                    }else if(inside_stone_high > the_stone_high){
                        min_arraylist.pop();
                    }else if(inside_stone_high < the_stone_high){
                        min_arraylist.push(the_stone_high);
                        ok = true;
                    }

                }
                
            }
            cnt++;
        }
        return ans;
    }
}

```






