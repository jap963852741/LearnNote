# JobScheduler
在android开发中经常会有这样的需求，开发者需要在稍后的某个时间点或者满足某个特定的条件时去执行某个任务，  
Ex : 当设备开始充电，或者网络状态连接到wifi状态时执行某些推送通知的任务，jobscheduler就是用来处理这类场景的任务。

# JobService
JobService 會透過 JobScheduler 去發送分配任務

# JobIntentService
JobService vs JobIntentService 就像 Service vs IntentService  
JobIntentService 會處理掉 JobScheduler 的部份，讓我們專心覆寫 onHandleWork 即可
