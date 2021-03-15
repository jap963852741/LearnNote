### 用途
避免 Main Thread 堵塞  
  
### 原理
1. Handler 資料塞進  >>  MessageQueue  
2. Looper 把 Queue 的值不斷的取出做處理  
  
### 補充
Handler 有 synchronized 以防多執行緒存取  
Looper 裡面是一個無窮迴圈來取 queue 的值
