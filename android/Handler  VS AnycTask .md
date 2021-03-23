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
    - 解決方法  
        - （1）AsyncTask 改为静态内部类，也可以在内部类AsyncTask里面持有Activity的弱引用。
            * 補充 :根据Oracle官方的说法：Nested classes are divided into two categories: static and non-static. Nested classes that are declared static are called static nested                   classes. Non-static nested classes are called inner classes.  
            * 从字面上看，一个被称为静态嵌套类，一个被称为内部类。从字面的角度解释是这样的：什么是嵌套？
            * 嵌套就是我跟你没关系，自己可以完全独立存在，但是我就想借你的壳用一下，来隐藏一下我自己。
            * 什么是内部？内部就是我是你的一部分，我了解你，我知道你的全部，没有你就没有我。（所以内部类对象是以外部类对象存在为前提的）
        - （2）在Activity的onDestroy生命周期方法里调用AsyncTask的cancel销毁AsyncTask
2.  AnycTask如結束則會找不到 UI 產生 Exception
