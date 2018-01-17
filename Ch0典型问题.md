## 第零章 典型问题
### 0.1 函数声明还是变量定义
在下面的代码中，`read`既可以理解为无实参传入的函数`read`的声明，又可以理解成`string`类型变量的定义(默认初始化)。
容易引起二义性，编译器会根据自身策略选择`warning`或者选择一种策略(根据上下文？)。
```cpp
string read();
```
> warning: empty parentheses interpreted as a function declaration. replace parentheses with an initializer to declare a variable.

### 0.2 零初始化、值初始化、默认初始化
参考：
[零初始化、值初始化、默认初始化](https://stackoverflow.com/questions/1613341/what-do-the-following-phrases-mean-in-c-zero-default-and-value-initializat)
