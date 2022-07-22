# <time.h> #

---

```c
clock_t
```
* 儲存處理器時間單位(tick)的變數型態

---

```c
CLOCKS_PER_SEC
```
* 常數，定義一秒鐘等於多少個時間單位

---

```c
time_t
```
* 儲存 "calendar time" 的變數型態(其實也就是秒)
* 初始值為 `1970/01/01 00:00:00` 起至現在經過的秒數

---

```c
struct tm 
{
   int tm_sec;         /* seconds,  range 0 to 59          */
   int tm_min;         /* minutes, range 0 to 59           */
   int tm_hour;        /* hours, range 0 to 23             */
   int tm_mday;        /* day of the month, range 1 to 31  */
   int tm_mon;         /* month, range 0 to 11             */
   int tm_year;        /* The number of years since 1900   */
   int tm_wday;        /* day of the week, range 0 to 6    */
   int tm_yday;        /* day in the year, range 0 to 365  */
   int tm_isdst;       /* daylight saving time             */	
}; 
```
* 儲存 "calendar time" 的結構體 (有時分秒等)

---

```c
clock_t clock(void);
```
* 回傳從程式開始到現在所經過的tick數
* 時間不可用或發生錯誤回傳 `-1`

---

```c
time_t time(time_t* tp);
```
* 回傳目前的calendar time
* 如果 `tp` 非 `NULL`，回傳值也會指定給 `*tp`
* 時間不可用或發生錯誤回傳 `-1`

---

```c
struct tm* gmtime(const time_t* tp);
```
* 把calendar time從 `time_t` 型態轉為 `tm` 型態
* 發生錯誤時回傳 `NULL`
