# Activity
Android 的核心元件，App 與使用者互動的基礎介面

# [Service](https://github.com/jap963852741/LearnNote/blob/main/android/Service%20vs%20IntentService.md)
短時間的 background 活動

# Broadcast
* Android 裡預設的溝通模式
* 用 intent 發訊號，訂義相應的 Action 頻道讓 Receiver 接收
* 生命只有 10 秒，超過會發生 ANR
* Ex : 打電話、聯絡人…

# ContentProvider
* 資料接口元件，將自己可供人讀取的資料包住，讓別的 App 能存取
* Ex : 通訊錄要給不同 App 讀取時就會包在此類
