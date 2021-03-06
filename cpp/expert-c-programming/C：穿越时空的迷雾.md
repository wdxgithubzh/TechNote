<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [C的史前阶段](#c%E7%9A%84%E5%8F%B2%E5%89%8D%E9%98%B6%E6%AE%B5)
- [C的早期体验](#c%E7%9A%84%E6%97%A9%E6%9C%9F%E4%BD%93%E9%AA%8C)
- [标准I/O库和C预处理器](#%E6%A0%87%E5%87%86io%E5%BA%93%E5%92%8Cc%E9%A2%84%E5%A4%84%E7%90%86%E5%99%A8)
- [K&R C](#kr%C2%A0c)
- [今日之ANSI C](#%E4%BB%8A%E6%97%A5%E4%B9%8Bansi%C2%A0c)
- [它很棒，但符合标准吗](#%E5%AE%83%E5%BE%88%E6%A3%92%E4%BD%86%E7%AC%A6%E5%90%88%E6%A0%87%E5%87%86%E5%90%97)
- [编译限制](#%E7%BC%96%E8%AF%91%E9%99%90%E5%88%B6)
- [ANSI C标准的结构](#ansi%C2%A0c%E6%A0%87%E5%87%86%E7%9A%84%E7%BB%93%E6%9E%84)
- [阅读ANSI C标准](#%E9%98%85%E8%AF%BBansi%C2%A0c%E6%A0%87%E5%87%86)
- [安静的改变](#%E5%AE%89%E9%9D%99%E7%9A%84%E6%94%B9%E5%8F%98)
- [导航](#%E5%AF%BC%E8%88%AA)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# C的史前阶段

C语言体现的“小即是美”。

C和Unix，是先有鸡还是先有蛋的问题。

对编译器而言，效率就是一切。编译器的效率包括两个方面：运行效率和编译效率。

 

# C的早期体验

C语言排斥强类型，允许程序员需要时可以在不同类型的对象间赋值。

C中，根据编译器设计者的思路而发展形成的语言特性有：

1. 数组下标从0开始，因为偏移量的概念。

2. C的基本数据类型直接与硬件底层相对应。

3. auto关键字显然是摆设：它只对创建符号表入口的编译器设计者有意义，意思是：进入程序块时自动进行内存分配（与全局静态分配或在堆上动态分配恰好相反）。

4. 表达式中的数组名可以看作指针。

5. float被自动扩展为double。

6. 不允许嵌套函数（函数内部包含另一个函数的定义）。

7. register关键字，将变量放到寄存器中。

 

# 标准I/O库和C预处理器

C预处理器的主要功能是：字符串替换（#define），头文件包含，通用代码模版的扩展（宏）。

宏扩展中，空格会对扩展的结果产生很大的影响。

宏最好只用于命名常量，并为一些适当的结构提供简捷的记法。宏名应该大写。

 

# K&R C

The C Programming Language这本书的C语言被成为K&R C。

 

# 今日之ANSI C

任何学习或使用C语言的人都应当使用ANSI C。

ANSI采用的C标准就是ISO C。

 

# 它很棒，但符合标准吗

不可移植的代码：由编译器定义的或未确定的。

坏代码：未定义的，约束条件。

标准规定编译器只有在违反语法规则和约束条件的情况下才产生错误信息！这意味着所有不属于约束条件的语义规则你都可以不遵循。

可移植的代码：

1. 严格遵循标准的

1.1 只使用确定的特性

1.2 不突破任何由编译器实现的限制

1.3 不产生任何由编译器定义的或未确定的或未定义的特性的输出

程序的可移植性是非常重要的，所以在编码中，应该始终保证加上必要的类型转换、返回值等

一个遵循标准的程序可以依赖于一些某种编译器特有的不可移植的特性

 

# 编译限制

ANSI C对能够编译的程序的最小长度做了限制。

一个数据名称最多能有多少个字符，一个数组最多能有多少维度，函数调用的实参数量，函数定义的形参数量，一行源代码最多有多少个字符，表达式的括号最多有多少层嵌套。

这些必须并不是约束条件，当编译器发现违反上述规定时，不一定产生错误信息。

一个优秀的编译器不应该有任何预设的限制，而应该只受一些外部因素的限制，如内存、硬盘。

 

# ANSI C标准的结构

主要包括四个部分：术语的介绍，支持C的系统，C语言，C运行库。

ANSI C最重要的特性就是原型（函数签名），它是函数声明的扩展，不仅函数名和返回值已知，所有的形参类型也是已知的。

 

# 阅读ANSI C标准

每个实参都应该具有自己的类型，这样它的值就可以赋值给它对应的形参类型的对象（该对象的类型不能含有限定符），所以，除非char**的值可以赋给const char**，否则会出现诊断信息。

赋值的约束条件：两个操作数都是指向有限定符或无限定符的相容类型的指针，左边指针所指向的类型必须具有右边指针所指向类型的全部限定符。

 

# 安静的改变

当执行算术运算时，操作数的类型如果不同，就会发生转换。数据类型一般会朝着浮点精度更高、长度更长的方向转换。整数型如果转为signed不丢失信息，就转为signed，否则转为unsigned。

# 导航

[目录](README.md)

下一章：[2. 这不是bug，而是语特性](2. 这不是bug，而是语言特性.md)
