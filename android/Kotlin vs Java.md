# Null Safety

Safe Calls（?） 與 Not-null Assertion（ !! ）  
在 !! 時如果 null 會出現 Exception  
因此在寫 Kotlin 時，還是盡可能用 Safe calls 才能享受到 Kotlin 的精髓

# Extensions 

Extension function 可以為任何一個 Class 加上 function，卻不必更改該 Class 的原始碼  
減少在java 中寫 Util的習慣  

# Coroutines  vs Thread
|  協同式 (Coroutines)  | 搶佔式 (Thread)  |
|  ----  | ----  |
| 程式會定時放棄已佔有的執行資源讓其它程式可以執行| 程式有各自的優先權，作業系統會根據程式的優先權安排當下哪個程式能擁有執行資源去執行 |
| 由程式自己讓出執行資源，作業系統不會干涉  | 作業系統有權中斷任何正在執行中的程式，變更執行資源的擁有者 |
  
 ### Coroutine 是輕量化的 Thread  
 建立一個 Coroutine 不會綁定到作業系統的 Thread，Coroutine 之間的切換由當前執行的 Coroutine 主動讓出執行權給其它 Coroutine，藉此達到並行運作，    
 因為 Coroutine 的切換是在上層，不需要由底層的作業系統來處理，所以 Coroutine 交替時所產生的上下文切換負擔比 Thread 小。   
 Coroutine 執行時還是會被指派到一個 Thread 上， 
 ### Coroutine 框架下 Thread 為 容器
 因為只有 Thread 才能真正從作業系統獲取到實際 CPU 執行時間。  
![image](https://user-images.githubusercontent.com/32256068/111961525-232e7080-8b2c-11eb-9235-e61366094710.png)

# 寫法簡潔
