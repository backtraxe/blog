---
weight: 999
title: "C++ STL 教程"
description: "标准模板库（Standard Template Library，STL）是一组 C++ 模板类，提供常见的数据结构和函数，如列表、堆栈、数组等。它是由容器类、算法和迭代器构成的一个通用库，它的组件是参数化的。"
icon: "article"
date: "2021-02-06T22:06:43+08:00"
lastmod: "2023-11-04T11:22:50+08:00"
draft: false
toc: true
---

STL 包含以下四个组件：

1. 算法（Algorithms）：头文件`<algorithm>`定义了一组函数，作用于容器，并为容器中的内容提供各种操作方法。
2. 容器（Containers）：存储数据。
3. 函数（Functions）：
4. 迭代器（Iterators）：遍历容器。

## vector

vector 是一个动态数组，顺序存放元素。

- 数组大小动态改变
- 可以进行逻辑操作（是否相等、比较大小）

### 初始化

```cpp
#include <vector>
using namespace std;

int main() {
    // 初始化为空
    vector<int> v1;                              // []

    // 列表初始化
    vector<int> v2 = {1, 2, 3};                  // [1, 2, 3]
    vector<int> v3({1, 2, 3});                   // [1, 2, 3]

    // 拷贝初始化
    vector<int> v4 = v3;                         // [1, 2, 3]
    vector<int> v5(v3);                          // [1, 2, 3]

    // 指定大小和初始值（默认 0）
    vector<int> v6(3);                           // [0, 0, 0]
    vector<int> v7(3, 2);                        // [2, 2, 2]
    vector<vector<int>> v8(2, vector<int>(3));   // [[0, 0, 0], [0, 0, 0]]

    // 数组初始化
    int arr[] = {1, 2, 3};
    vector<int> v9(arr, arr + 1);                // [1]

    // 迭代器初始化
    vector<int> v10(v4.begin(), v4.begin() + 2); // [1, 2]
}
```

### 添加元素

- `void push_back(const value_type& val)` 在末尾添加元素
- `void emplace_back(Args&&... args)` 在末尾构造并插入元素
- `iterator emplace(const_iterator position, Args&&... args)` 在指定位置构造并插入元素
- `iterator insert(const_iterator position, const value_type& val)` 在指定位置插入元素
- `iterator insert(const_iterator position, size_type n, const value_type& val)` 在指定位置插入 n 个 val
- `iterator insert(const_iterator position, InputIterator first, InputIterator last)` 在指定位置插入数组或迭代器 [first, last) 区间内的元素
- `iterator insert(const_iterator position, initializer_list<value_type> il)` 在指定位置插入指定列表中的元素

```cpp
#include <vector>
#include <string>
using namespace std;

int main() {
    vector<pair<string, int>> vec;                       // []

    // 添加到末尾
    vec.push_back(make_pair("one", 1));                  //
    vec.emplace_back("two", 2);                          //         隐式地构造了 pair

    // 添加到指定位置
    vec.emplace(vec.begin(), "three", 3);                //
    vec.insert(vec.begin(), make_pair("four", 4));       //
    vec.insert(vec.begin(), 2, make_pair("five", 5));    //
    vec.insert(vec.begin(), vec.begin(), vec.end());     //
    vec.insert(vec.begin(), {{"six", 6}, {"seven", 7}}); //
}
```

#### 删除元素

- `void pop_back()` 删除最后一个元素
- `iterator erase(const_iterator position)` 删除指定位置的元素
- `iterator erase(const_iterator first, const_iterator last)` 删除迭代器 [first, last) 区间内的元素
- `void clear() noexcept` 清空

#### 1.4 容量

- `bool empty() const` 判断容器是否为空
- `size_type size() const` 返回元素个数
- `size_type capacity() const noexcept` 返回已分配存储容量的大小
- `void resize(size_type n)` 改变大小，变小截断，变大补 0
- `void resize(size_type n, const value_type& val)` 改变大小，变小截断，变大补 val

#### 1.5 其他操作

- `void assign(size_type n, const value_type& val)` 赋值为 n 个 val
- `void assign(InputIterator first, InputIterator last)` 赋值为数组或迭代器 [first, last) 区间内的元素
- `void assign(initializer_list<value_type> il)` 赋值为指定列表中的元素
- `void swap(vector& x)` 交换两个 vector

#### 1.6 遍历

- `reference operator[](size_type n)` 返回位置为 n 的元素的引用，越界发生未知错误（不推荐）
- `reference at(size_type n)` 返回位置为 n 的元素的引用，越界抛出 out_of_range 异常（推荐）
- `reference front()` 返回第一个元素的引用
- `reference back()` 返回最后一个元素的引用

```cpp
for (auto it = v.begin(); it != v.end(); it++)   {*it;}  // 正向遍历，有迭代器
for (auto it = v.rbegin(); it != v.rend(); it++) {*it;}  // 反向遍历，有迭代器
for (int& e : v) {e;}                                    // 正向遍历，无索引
for (int e : v)  {e;}                                    // 正向遍历，无索引，不改变原数据
for (int i = 0; i < v.size(); i++)      {v.at(i);}       // 正向遍历，有索引
for (int i = v.size() - 1; i >= 0; i--) {v.at(i);}       // 反向遍历，有索引
```

