# Service
Service 不能做長時間的事情，需要在另一個 Thread 去操作。  

## IntentService繼承自Service類的
而 IntentService 則可以省去 Thread 的動作，並且可以重覆呼叫 IntentService ( 單例 )，  
他會排進一個 queue 裡，用 onHandleIntent 去處理，最後會自動 onDestroy。  
這些如果使用 Service 都要手動。  
    
- 本质上是封装了HandlerThread和Handler的异步框架。
- 当任务会执行完成后，它会自动停止，因为它是一个服务，所以它的优先级比线程高很多，不容易被杀死，所以适合执行一些高优先级的耗时的后台任务。
