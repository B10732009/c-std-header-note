# <math.h> #

---

```c
double log(double x); 
```
* 回傳ln(x)。

---

```c
double log10(double x); 
```
* 回傳log~10~(x)

---

```c
double pow(double x, double y); 
```
* 回傳x^y^
* 若想要的值為整數的次方，要特別注意浮點數誤差的問題。
---

```c
double sqrt(double x); 
```
* 回傳根號x

---

```c
double fabs(double x); 
```
* 回傳x的絕對值 (浮點數版本)。
* 處理整數絕對值要使用 `int abs(int x);` (在`stdlib.h`)。

---

```c
double sin(double x); 
double cos(double x); 
double tan(double x); 
double asin(double x); 
double acos(double x); 
double atan(double x); 
double sinh(double x); 
double cosh(double x); 
double tanh(double x); 
```
* 回傳三角函數的值
