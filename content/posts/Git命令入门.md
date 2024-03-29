---
title: "Git命令入门"
date: 2019-11-12T20:40:01+08:00
draft: false
---

# 命令基础

## 命令是计算机编程学习者所具备的基本功之一，下面我们就来简单的讨论一下命令以及所需要的知识点

### 命令所需要的英语词汇:

#### 为了加深对命令内容的理解，我们简单的介绍一些涉及命令的基本词汇。

1.  file --> 文件
2.  remove --> 删除
3.  recursive --> 递归的
4.  make --> 制作
5.  copy --> 拷贝
6.  link --> 链接
7.  move --> 移动
8.  list --> 列表
9.  echo --> 回声
10. touch --> 触摸
11. change --> 改变
12. directory --> 目录
13. force --> 强制

命令的缩写:

1.  file -- 无
2.  remove -- rm
3.  recursive -- 无
4.  make -- mk
5.  copy -- cp
6.  link --ls
7.  move -- mv
8.  list -- ls
9.  echo -- echo
10. touch -- touch
11. change -- cd 中的 c
12. directory -- cd 中的 d
13. force -- f

## 用命令对文件进行增删改查的操作:

1. 查看文件与目录:

   1. 文件的查看:

      1. 查看当前目录的绝对路径:

      ```
      $ pwd
      ```


      2. 查看当前目录的内容:

      ```
      $ ls
      ```

      3. 查看指定目录的内容:

      ```
      $ ls (路径名)
      ```

      4. 查看文件的内容:

      ```
      & cat 路径
      & head 路径
      & tail 路径
      & less 路径
      ```

      **几种查找的区别**:

      - cat 显示文件内的全部内容
      - head 只会查看文件的前 10 行
      - tail 只查看文件的后 10 行
      - less 显示的内容是可以滚动的

2. 文件的增:

   1. 文件的创建:

      1. 单文件的创建:

      ```
      $ touch 文件名(要写扩展名)
      ```

      1. 多文件的创建:

      ```
      $ touch (文件名1) (文件名2)······(文件名n)
      ```

   2. 目录的创建:

      1. 创建单个目录:
         ```
         $ mkdir a
         ```
      2. 创建多个目录:

         ```
         $ mkdir -p a/b/c/d  (不加p会认为这是一个文件而报错)
         ```

      3. 文件的复制:

         ```
         $ cp (文件1) (文件2)
         ```

      4. 目录的复制:

         ```
         $ cp -r (路径1) (路径2)
         ```

3. 文件的删除:

   1. 文件的删除:

   ```
   $ rm (文件名)
   ```

   2. 目录的删除:

   ```
   $ rm -r (路径名)
   ```

4. 文件的修改:

   1. 打开文件:

      1. 在 Windows 上:

         ```
         start (文件名)
         ```

      2. 在 Mac 上:

         ```
         open (文件名)
         ```

   2. 修改文件:

      ```
      $ echo "(内容)“ >> (文件名)
      ```

### 命令的组合:

1.  命令的成功或失败:

    - 如果成功什么都不提示，如果失败会提示 error

2.  &&操作:

    - n 个命令组合，第一个成功后执行第二个，以此类推。
    - 例: `$ rm 1.txt && echo 成功`

3.  ;操作:

    - 不管当前命令是否执行，都会执行下一条
    - 例: `$ rm 1.txt ;echo 成功`
