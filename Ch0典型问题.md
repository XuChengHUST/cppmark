## 第零章 典型问题
### 0.1 函数声明还是变量定义
在下面的代码中，`read`既可以理解为无实参传入的函数`read`的声明，又可以理解成`string`类型变量的定义(默认初始化)。
容易引起二义性，编译器会根据自身策略选择`warning`或者选择一种策略(根据上下文？)。
```cpp
string read();
```
> warning: empty parentheses interpreted as a function declaration. replace parentheses with an initializer to declare a variable.

### 0.2 零初始化、值初始化、默认初始化
如果定义变量时没有指定初值，则变量被 **默认初始化** (default initialized).
```cpp
// 这些都是默认初始化
int i;
string str;
Sales_data obj;
```
```cpp
string *ps1 = new string;   // 默认初始化为空string
string *ps = new string();  // 值初始化为空string
int *pi1 = new int;         // 默认初始化，*pi1未定义
int *pi2 = new int();       // 值初始化为0, *pi2为0
```
> Sometimes the memory returned by the new operator will be initialized, and sometimes it won't depending on whether the type you're newing up is a POD, or if it's a class that contains POD members and is using a compiler-generated default constructor.
* In C++1998 there are 2 types of initialization: zero and default
* In C++2003 a 3rd type of initialization, value initialization was added.

参考：
[零初始化、值初始化、默认初始化](https://stackoverflow.com/questions/1613341/what-do-the-following-phrases-mean-in-c-zero-default-and-value-initializat)
