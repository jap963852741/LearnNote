# 說明
Service 不能做長時間的事情，需要在另一個 Thread 去操作。  

## IntentService繼承自Service類的
而 IntentService 則可以省去 Thread 的動作，並且可以重覆呼叫 IntentService ( 單例 )，  
他會排進一個 queue 裡，用 onHandleIntent 去處理，最後會自動 onDestroy。  
這些如果使用 Service 都要手動。
