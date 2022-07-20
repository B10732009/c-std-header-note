# <stdio.h> #

---

```c
EOF
```
* 表⽰資料流結束或資料流讀取錯誤的值

---

```c
stdin 
stdout 
stderr 
```
* 指向 `標準輸入字元流` `標準輸出字元流` `標準錯誤輸出字元流` 的檔案指標
* 程式開始執⾏時會被⾃動開啟

---

```c
struct FILE
```
* 含有控制字元流所需資訊的物件類型

---

```c
struct FILE* fopen(const char* filename, const char* mode); 
```
* 開啟檔名為 `filename` 的檔案並傳回字元流，失敗時回傳 `NULL`
* `mode` 如下

    | Mode | Description |
    | ---- | ----------- |
    | r | 以純文字檔案⽅式讀取 |
    | w | 以純文字檔案⽅式寫入 |
    | a | 以純文字檔案⽅式添加在尾端 |
    | r+ | 以純文字檔案⽅式更新（讀取、寫入） |
    | w+ | 以純文字檔案⽅式更新，**清除原始檔案內容**（如果有的話） |
    | a+ | 以純文字檔案⽅式添加在尾端，在尾端讀取和寫入 |

* 在以上字串插入 `b` （要在第⼀個字元以後），表⽰以⼆進位檔案的⽅式開啟

---

```c
int fclose(struct FILE* stream); 
```
* 關閉 `stream` 指向的字元流（如果是輸出⽤字元流，則先釋出緩衝區）。
* 錯誤時傳回 `EOF`，否則傳回 `0`

---

```c
size_t fread(void* ptr, size_t size, size_t nobj, struct FILE* stream);
size_t fwrite(const void* ptr, size_t size, size_t nobj, struct FILE* stream); 
```
* 從檔案流 `stream` 中讀取/寫入至多 `nobj` 個大小為 `size` 的物件
* 回傳成功讀取/寫入的物件數量

---

```c
int fprintf(struct FILE* stream, const char* format, ...); 
```
* 根據字串 `format` 轉換參數，並且輸出到字元流 `stream`
* 回傳輸出的字元數⽬，發⽣錯誤時傳回負數

* 格式參數
    | character | Description |
    | ---- | ----------- |
    | %i, %d  | int (十進位) |
    | %o | int (八進位) |
    | %x | int (十六進位) |
    | %u | unsigned int |
    | %c | 字元 |
    | %s | 字串 |
    | %f | 浮點數 |
    | %e | 浮點數 (科學記號) |
    | %% | 顯示% |
    | %p | 顯示指標位置 |

---

```c
int printf(const char* format, ...); 
```
* 根據字串 `format` 轉換參數，並且輸出到字元流 `stdout`
* 等價於 `fprintf(stdout, format, ...);`

---

```c
int sprintf(char* s, const char* format, ...);
```
* 根據字串 `format` 轉換參數，並且輸出到字串 `s`

---

```c
int fscanf(struct FILE* stream, const char* format, ...); 
```

* 根據字串 `format` 轉換參數，並且從字元流 `stream` 讀入到變數中
* 所有的格式參數必須為**指標**型態

---

```c
int scanf(const char* format, ...); 
```
* 根據字串 `format` 轉換參數，並且從字元流 `sdtin` 讀入到變數中
* 等價於 `fscanf(stdin, format, ...);`

---

```c
int sscanf(char* s, const char* format, ...);
```
* 根據字串 `format` 轉換參數，並且從字串 `s` 讀入到變數中

---

```c
int fgetc(struct FILE* stream); 
int fputc(int c, struct FILE* stream);
```
* 從檔案流 `stream` 中讀取下一個字元/寫入字元 `c`
* 發生錯誤或讀到檔案尾端時回傳 `EOF`

---

```c
char* fgets(char* s, int n, struct FILE* stream); 
char* fputs(const char* s, struct FILE* stream);
```
* 從檔案流 `stream` 中讀取至多n-1個字元/寫入字串 `s`
* 錯誤或讀到檔案結尾時傳回 `EOF`，否則傳回 `s`

---


```c
char* gets(char* s);
int puts(const char* s); 
```
* 在檔案流 `stdio` 中讀入/寫入一行
* 發生錯誤或讀到檔案尾端時回傳 `NULL` / `EOF` 

---

```c
int fseek(struct FILE* stream, long offset, int origin); 
```
* 變更檔案指標的位置到 `origin + offset` 的位置
* `origin` 有三種值可選
    | name | Description |
    | ---- | ----------- |
    | SEEK_SET | 檔案開頭 |
    | SEEK_CUR | 檔案指標目前位置 |
    | SEEK_END | 檔案尾端 |
* 執行成功返回 `0`，否則返回非零值

---

```c
int feof(struct FILE* stream);
```
* 如果 `stream` 遇到 `EOF` ，回傳非0值