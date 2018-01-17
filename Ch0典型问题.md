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

### 0.3 默认构造函数与自定义默认构造函数
根据 **cppreference** 上的说明，用户自定义的“空初始化列表+空函数体”默认构造函数和隐式合成的默认构造函数式完全相同的——都是调用基类以及非静态成员的默认构造函数。
> **Implicitly-defined default constructor**  
If the implicitly-declared default constructor is not defined as deleted, it is defined (that is, a function body is generated and compiled) by the compiler if odr-used, and **it has exactly the same effect as a user-defined constructor with empty body and empty initializer list**. That is, it calls the default constructors of the bases and of the non-static members of this class.  
参考: [Default constructors](http://en.cppreference.com/w/cpp/language/default_constructor)

下面的三种类定义，都是通过默认初始化完成了内置类型`int`变量`i`的初始化，都是未定义行为。
```cpp
class Foo {
private:
  int i;
};
class Foo {
public:
  Foo() = default;
private:
  int i;
};
class Foo {
public:
  Foo() {}
private:
  int i;
};
```
使用类内初始值，会首先用类内初始值初始化`int i`，此时`i`就不是未定义的了。
```cpp
class Foo {
private:
  int i = 0;    // C++11 required
};
```
使用初始化列表，也会首先用初始化列表初始化`int i`，此时`i`同样也不是未定义的了。
```cpp
class Foo {
  Foo() :
    i() {}  // 值初始化
private:
  int i;    // C++11 required
};
```
