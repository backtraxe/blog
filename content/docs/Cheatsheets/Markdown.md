---
title: "Markdown"
author: "backtraxe"
date: "2023-11-04T01:58:17+08:00"
lastmod: "2023-11-04T01:58:17+08:00"
description: ""
tags: ["test"]
icon: "article"
weight: 999
draft: false
toc: true
katex: true
---

# 一级标题

## 二级标题

### 三级标题

#### 四级标题

##### 五级标题

###### 六级标题

## 代码

### 单行代码

`go run main.go`

### 代码块

```go
package main

import "fmt"

func main() {
    fmt.Println("Hello World!")
}
```

{{< prism lang="html" line="3,6" >}}
<html>
  <head>
    <title>A code block using the Prism Shortcode</title>
  </head>
  <p>
    This shortcode is nested inside a Tabs shortcode
  </p>
</html>
{{< /prism >}}

### 多语言代码块

{{< tabs tabTotal="5" >}}

<!-- C -->
{{< tab tabName="C" >}} {{< prism lang="c" >}}
#include <stdio.h>

int main() {
    printf("Hello World!\n");
    return 0;
}
{{< /prism >}} {{< /tab >}}

<!-- C++ -->
{{< tab tabName="C++" >}} {{< prism lang="cpp" >}}
#include <iostream>

using namespace std;

int main() {
    cout << "Hello World!" << endl;
    return 0;
}
{{< /prism >}} {{< /tab >}}

<!-- Java -->
{{< tab tabName="Java" >}} {{< prism lang="java" >}}
public class Main {
    public static void main(String[] args) {
        System.out.Println("Hello World!");
    }
}
{{< /prism >}} {{< /tab >}}

<!-- Python -->
{{< tab tabName="Python" >}} {{< prism lang="python" >}}
print("Hello World!")
{{< /prism >}} {{< /tab >}}

<!-- Go -->
{{< tab tabName="Go" >}} {{< prism lang="go" >}}
package main

import "fmt"

func main() {
    fmt.Println("Hello World!")
}
{{< /prism >}} {{< /tab >}}

{{< /tabs >}}

## 列表

### 有序列表

1. 列表项1
1. 列表项2
1. 列表项3

### 无序列表

- 列表项1
- 列表项2
- 列表项3

## 公式

### 行内公式

$\int \frac{1}{x} dx = \ln \left| x \right| + C$

### 单行公式

$$
\int \frac{1}{x} dx = \ln \left| x \right| + C
$$

### 多行公式

{{< katex >}}
$$
\begin{array} {lcl}
  L(p,w_i) &=& \dfrac{1}{N}\Sigma_{i=1}^N(\underbrace{f_r(x_2
  \rightarrow x_1
  \rightarrow x_0)G(x_1
  \longleftrightarrow x_2)f_r(x_3
  \rightarrow x_2
  \rightarrow x_1)}_{sample\, radiance\, evaluation\, in\, stage2}
  \\\\\\ &=&
  \prod_{i=3}^{k-1}(\underbrace{\dfrac{f_r(x_{i+1}
  \rightarrow x_i
  \rightarrow x_{i-1})G(x_i
  \longleftrightarrow x_{i-1})}{p_a(x_{i-1})}}_{stored\,in\,vertex\, during\,light\, path\, tracing\, in\, stage1})\dfrac{G(x_k
  \longleftrightarrow x_{k-1})L_e(x_k
  \rightarrow x_{k-1})}{p_a(x_{k-1})p_a(x_k)})
  \newline
  \newline
\end{array}
$$
{{< /katex >}}

## 链接

[Plausible Analytics Guide]({{% relref "/docs/Go/Go基本语法" %}})
