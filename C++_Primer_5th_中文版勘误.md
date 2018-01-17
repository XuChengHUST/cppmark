## 第十三章
### 13.5 动态内存管理类
Page 466
##### 使用construct
```cpp
void StrVec::push_back(const string& s) {
  chk_n_alloc();
  alloc.construct(first_free++, s);
}
```
原文
> 它使用前置递增(参见4.5节，第131页)，因此这个调用会在`first_free`当前值指定的地址构造一个对象，并递增`first_free`指向下一个未构造的元素。

勘误：使用的是后置递增。
