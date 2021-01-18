## 問題

val fragments = fragmentutil.manager.fragments \
會發生錯誤，頁面顯示不出來\
\
val fragments = getParentFragmentManager().fragments\
這個卻ok

## 解析
錯誤部分來自的 manager 來自 FragmentActivity.java\
ok的來自 Fragment.java\
因為在 Fragment的 頁面呼叫 \
