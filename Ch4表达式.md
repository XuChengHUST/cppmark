## 第四章 表达式
### 4.5 递增和递减运算符
```cpp
int i = 0, j;
j = ++i;    // j = 1, i = 1：前置版本得到递增后的值
j = i++;    // j = 1, i = 2：后置版本得到递增前的值
```
> **除非必须，否则不用后置版本**  
前置版本的递增运算符避免了不必要的工作，它把值加一后直接返回改变了的运算对象。与之相比，后置版本需要将原始值储存下来以便于返回这个未修改的内容。  
对于整数或者指针类型来说，编译器可能会进行一定的优化；但是对相对复杂的迭代器类型，这种额外的工作就消耗巨大了。

```cpp
// 前置版本
template <typename T>
T& operator++(T& v) {
  v += 1;
 }
// 后置版本1
template <typename T>
T operator++(T& v) {
  T temp = v;
  v += 1;
  return temp;
}
// 后置版本2
template <typename T>
T operator++(T& v, int i) {
  T temp = v;
  v += i;
  return temp;
}
```
