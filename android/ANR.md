# ANR
Android中表示应用程序无响应

# 常見原因
* 主线程进行了大量耗时的操作
* 多线程操作引起的死锁，主线程被锁住了
* 系统资源耗尽（管道、CPU、io）

# 類型
* KeyDispatchTimeout（常见）: input事件在5S内没有处理完成发生了ANR
* BroadcastTimeout : 
1. 前台Broadcast：onReceiver在10S内没有处理完成发生ANR
2. 后台Broadcast：onReceiver在60s内没有处理完成发生ANR
* ServiceTimeout : 
1. 前台Service：onCreate，onStart，onBind 等生命周期在20s内没有处理完成发生ANR
2. 后台Service：onCreate，onStart，onBind 等生命周期在200s内没有处理完成发生ANR
* ContentProviderTimeout : ContentProvider 在10S内没有处理完成发生ANR

