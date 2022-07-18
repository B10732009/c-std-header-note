# <string.h> #

---

```c
size_t strlen(const char *str);
```
* 計算 `str` 的長度(不包含結尾的 `'\0'` )

---

```c
int strcmp(const char *str1, const char *str2);
int strncmp(const char *str1, const char *str2, size_t n);
```
* 比較 `str1` 和 `str2`
    * 若 `回傳值<0`，表示 `str1<str2`
    * 若 `回傳值==0`，表示 `str1==str2`
    * 若 `回傳值>0`，表示 `str1>str2`

---

```c
char *strcat(char *dest, const char *src);
char *strncat(char *dest, const char *src, size_t n);
```
* 追加 `src` 到 `dest` 的尾端

---

```c
char *strcpy(char *dest, const char *src);
char *strncpy(char *dest, const char *src, size_t n);
```
* 複製 `src` 到 `dest`

---

```c
char *strstr(const char *str, const char *substr);
```
* 檢查 `substr` 是不是 `str` 的子字串
* 如果是，回傳指向該位置的指標; 若不是，回傳 `NULL`
* 可用 `strlen(str)-strlen(p)` 的方式得到index

---

```c
char *strtok(char *str, const char *delim);
```
* 字串分割
* 用法
    ```c
    char str[] = "Hello world, nice to meet you";
    char delim[] = " ,";

    //第一次呼叫正常帶入str和delim
    char *token = strtok(str, delim);
    while (token)
    {
        printf("%s...\n", token);

        //第二次開始str的位置要使用NULL
        token = strtok(NULL, str);
    }
    ```
* 注意原字串會被修改

---

```c
void *memset(void *str, int c, size_t n);
```
* 將 `str` 指向的記憶體區塊全部設定成 `c`
* 一般用來初始化用

```c
int memcmp(const void *str1, const void *str2, size_t n)
```
* 比較str1和str2
    * 若 `回傳值<0`，表示 `str1<str2`
    * 若`回傳值==0`，表示 `str1==str2`
    * 若 `回傳值>0`，表示 `str1>str2`

---

```c
void *memcpy(void *dest, const void *src, size_t n);
```
* 複製src記憶體區塊到dest記憶體區塊