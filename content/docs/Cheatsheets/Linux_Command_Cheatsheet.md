---
weight: 999
title: "Linux Command Cheatsheet"
description: ""
icon: "article"
date: "2023-11-15T00:26:15+08:00"
lastmod: "2023-11-15T00:26:15+08:00"
draft: false
toc: true
---

## 分类

- 目录
    - [cd](#cd)
    - [ls](#ls)
- 进程
    - [ps](#ps)
    - [kill](#kill)
- 查看文件内容
    - [cat](#cat)
    - [head](#head)
    - [tail](#tail)
- 查找文件内容
    - [grep](#grep)
    - [sed](#sed)
    - [awk](#awk)

## 命令

### awk

### cat

打印文件所有内容、拼接文件。

- 常用参数

```bash
cat [-belnstuv] [file ...]
-n # 同时打印行号，从 1 开始。
-b # 同时打印行号，从 1 开始，跳过空白行。
-s # 多个空行只保留一个。
-v # 打印控制字符，如制表符 '\t'。
-e # 换行符打印为 '$'。
-t # 制表符打印为 '^I'。
```

- 使用示例

```bash
# 顺序合并文件
cat file1.txt file2.txt > total.txt

# 清空文件内容
cat /dev/null > test.txt
```

### cd

### cp

### crontab

设置定时任务。

文件绝对路径：`/var/spool/cron/<用户名>`

```bash
# 查看当前用户的所有定时任务
crontab -l

# 查看指定用户的定时任务
crontab -u

# 删除当前用户的所有定时任务
crontab -r

# 编辑当前用户的所有定时任务
crontab -e
```

```bash
# 时间设置
* * * * *
1 2 3 4 5
# 1 minute 代表一小时内的第几分，范围 0-59。
# 2 hour   代表一天中的第几小时，范围 0-23。
# 3 mday   代表一个月中的第几天，范围 1-31。
# 4 month  代表一年中第几个月，范围 1-12。
# 5 wday   代表星期几，范围 0-7 (0及7都是星期天)。


```

```bash
# 每隔 1 分钟执行一次
* * * * * (<shell1>;<shell2>)

# 每个小时的 3 分整执行一次
3 * * * * (<shell1>;<shell2>)

# 每天凌晨 4 点整执行一次
0 4 * * * (<shell1>;<shell2>)
```

### grep

### head

打印文件开头内容，默认打印 10 行。

- 常用参数

```bash
head [-n count | -c bytes] [file ...]
-n count # 指定开头行数，默认 -n 10。
-c bytes # 指定开头字符数。
```

- 使用示例

```bash
# 打印第一行
head -n 1 test.txt

# 打印前 5 个字符
head -c 5 test.txt

# 打印第 X 行
head -n X test.txt | tail -n 1
```

### kill

进程通信。

```bash
# 杀死进程
kill -9 <PID>
```

### ln

### ls

### mv

### ps

查看进程信息。

```bash
# 显示所有进程的详细信息（包括内存情况和进程状态，无父进程情况）
ps -aux
# -a 显示所有用户创建的进程
# -u 显示进程详细信息
# -x 显示无终端的进程

# 用户 进程id CPU占用率 内存占用率 最大内存占用 实际内存占用 终端 状态 启动时间 已使用CPU时间 命令
# USER PID    %CPU      %MEM       VSZ       RSS     TTY STAT START     TIME   COMMAND
# root   2     0.0       0.0         0         0     ?   S    Aug04     0:01   [kthreadd]

# 进程状态：
#    R  运行、待运行         <  高优先级
#    S  可中断睡眠           N  低优先级
#    D  不可中断睡眠         s  包含子进程
#    T  停止                +  位于前台
#    Z  僵死                l  多线程
```

```bash
# 显示所有进程的详细信息（包括父进程id，无内存情况和进程状态）
ps -ef
# -e
# -f

# 用户id 进程id 父进程id CPU占用率 启动时间  终端 已使用CPU时间  命令
#  UID    PID   PPID      C     STIME   TTY       TIME    CMD
#  root     2      0      0     Aug04   ?     00:00:01    [kthreadd]
```

```bash
# 查找包含 xxx 的进程
ps -aux | grep xxx

# 查找不含 xxx 的进程
ps -aux | grep -v xxx
```

### sed

### tail

打印文件末尾内容，默认 10 行。

- 常用参数

```bash
tail [-f] [-qv] [-c number | -n number] [file ...]
-n number # 指定末尾行数，默认 -n 10。
-c number # 指定末尾字符数。
-f # 实时打印文件末尾新增内容。
-q # 多文件时，不打印文件名。
-v # 多文件时，打印每个文件名，默认。
```

- 使用示例

```bash
# 实时打印
tail -f test.txt

# 打印最后 1 行
tail -n 1 test.txt

# 从第 10 行开始打印
tail -n +10 test.txt
```


### top

### touch
