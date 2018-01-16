## 第三章 函数
#### 3.2.1 定义和初始化对象
如果使用等号(=)初始化一个变量，实际上执行的是 **拷贝初始化** (copy initialization)，编译器把等号右边的初始值拷贝到新创建的变量中去。与之相反，如果不使用等号，则执行的是 **直接初始化** (direct initialization)。
```C
string s1;            //默认初始化
string s2 = s1;       //拷贝初始化
string s3 = "hiya";   //拷贝初始化
string s4("hiya");    //直接初始化
string s5(10, 'c');   //直接初始化
```
