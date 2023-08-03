# <assert.h> #

---

```c
void assert(int expression);
```
* 用來偵測錯誤的巨集。
* 如果 `expression` == 0 (== false)，就在 `stderr` 輸出訊息，並呼叫 `abort()` 結束程式。