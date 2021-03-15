# Handler  
### 用途
避免 Main Thread 堵塞  
  
### 原理
1. Handler 資料塞進  >>  MessageQueue  
2. Looper 把 Queue 的值不斷的取出做處理  
  
### 補充
Handler 有 synchronized 以防多執行緒存取  
Looper 裡面是一個無窮迴圈來取 queue 的值
  
# AnycTask   
### 用途
簡單的執行 background 作業  

### 原理
Handler + Thread 回傳 msg 

### 補充
會抓著 Activity 所以不適合做長時間的作業
Activity 若消毀 --> 
1.  AnycTask還在跑就會造成 memory leak 
2.  AnycTask如結束則會找不到 UI 產生 Exception
