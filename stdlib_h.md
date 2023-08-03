# <stdlib.h> #

---

```c
EXIT_SUCCESS
EXIT_FAILURE
```
* 給 `exit()` 用的常數，表示成功和失敗。

---

```c
RAND_MAX
```
* `rand()` 回傳值的範圍。

---

```c
int atoi(const char* s); 
long atol(const char* s); 
```
* **a**scii **to** **i**nt/**l**ong。
* 把字串 `s` 轉換成 `int` / `long` 型態。
* 若發生錯誤回傳 `0`。

---

```c
void* malloc(size_t size);
```
* **m**emory **alloc**ation (記憶體配置)。
* 配置 `size` byte的記憶體空間，回傳新空間第一個位元組的記憶體位址。
* 通常會使用以下的方式配置陣列空間 :
    ```c
    <type>* ptr = (<type> *) malloc(sizeof(<type>) * <array-size>);
    ```
* 配置的空間**沒有初始化**。
* 配置失敗時回傳 `NULL`。

---

```c
void* calloc(size_t nobj, size_t size);
```
* **c**ontiguous **alloc**ation (連續配置)。
* 配置 `nobj` 個大小為 `size` 的陣列的記憶體空間，回傳新空間第一個位元組的記憶體位址。
* 配置的空間會被初始化為 `0` 或 `NULL`。
* 配置失敗時回傳 `NULL`。

---

```c
void* realloc(void* p, size_t size); 
```
* 擴充或是縮減已經配置好的記憶體空間。
* 將原本配置的空間 `p` 的大小更新成 `size`。
* 原空間中所儲存的資料會被保留。
* 新增的空間**沒有初始化**。
* 配置失敗時回傳 `NULL`。

> 擴充記憶體空間通常是很耗時的動作，因為如果已配置的記憶體空間在擴充時，其後方沒有足夠的剩餘記憶體空間，系統就會在另外一個地方再找一塊足夠大小的記憶體空間，然後把整塊記憶體的資料都搬過去，所以比較好的記憶體配置方式是一次給足，減少記憶體資料搬家的發生頻率。

---

```c
void free(void* p); 
```
* 若 `p` 不為 `NULL`，釋放 `p` 所指向的空間。

---

```c
void exit(int status);
```
* 結束程式。
* 狀態 `status` 有以下選項 :
    | 狀態 | 描述 |
    | ---- | ----------- |
    | EXIT_SUCCESS | 成功結束 |
    | EXIT_FAILURE | 失敗結束 |

---

```c
int system(const char* s); 
```
* 呼叫主控台執行命令 `s`。
* 若 `s` 為 `NULL` 或是命令執行發生錯誤，回傳非零值。

---

```c
void qsort(void* base, size_t n, size_t size, int (*cmp)(const void* a, const void* b));
```
* 對一共有 `n` 個元素，且每個元素大小為 `size` byte的陣列 `base` 進行排序。
* 比較函數 `cmp` :
    * 必定要為 `int cmp(const void *a, const void *b)` 的形式，運算需使用casting，如下 :
        ```c
        int cmp(const void *a, const void *b) {
            return (*(int *)a) - (*(int *)b);
        }
        ```
        * 如果 `a在前b在後`，回傳負值。
        * 如果 `a在後b在前`，回傳正值。
        * 如果 `大小相等`，回傳 `0`。

---

```c
int rand(void); 
```
* 回傳一範圍在 `1` ~ `RAND_MAX` 之間的假亂數。

---

```c
void srand(unsigned int seed); 
```
* 設定亂數種子 `seed`。
