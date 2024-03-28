---
layout: post
title: Python use: argparse
categories: [Python, usage]
description: Python自带的库argparse的使用，实验结果
keywords: Python, Usage
mermaid: false
sequence: false
flow: false
mathjax: false
mindmap: false
mindmap2: false
typora-root-url: ../
---

argsparse是python的命令行解析的标准模块，内置于python，不需要安装。这个库可以让我们直接在命令行中就可以向程序中传入参数并让程序运行。

```python
import sys
print(sys.argv)
source = sys.argv[1]
target = sys.argv[2]
```

在命令行程序中，经常需要获取命令行参数。Python内置的`sys.argv`保存了完整的参数列表，我们可以从中解析出需要的参数。这种方式能应付简单的参数，但对复杂的参数会比较麻烦

## 相关链接

[argparse模块用法实例详解](https://zhuanlan.zhihu.com/p/56922793)

[廖雪峰-argparse](https://www.liaoxuefeng.com/wiki/1016959663602400/1529653965619235)

[python--argparse之action用法](https://blog.csdn.net/qq_35140742/article/details/120607823)

[**Python 命令行之旅：深入 argparse （一）**](https://zhuanlan.zhihu.com/p/79710926)

---

- [Python 命令行之旅：初探 argparse](https://zhuanlan.zhihu.com/p/79710598)
- [Python 命令行之旅：深入 argparse （一）](https://zhuanlan.zhihu.com/p/79710926)
- [Python 命令行之旅：深入 argparse（二）](https://zhuanlan.zhihu.com/p/80042771)
- [Python 命令行之旅：使用 argparse 实现 git 命令](https://zhuanlan.zhihu.com/p/81103133)
- [Python 命令行之旅：初探 docopt](https://zhuanlan.zhihu.com/p/85748569)
- [Python 命令行之旅：深入 docopt](https://zhuanlan.zhihu.com/p/88083190)
- [Python 命令行之旅：使用 docopt 实现 git 命令](https://zhuanlan.zhihu.com/p/89351466)
- [Python 命令行之旅：初探 click](https://zhuanlan.zhihu.com/p/90307978)
- [Python 命令行之旅：深入 click 之参数篇](https://zhuanlan.zhihu.com/p/92649559)
- [Python 命令行之旅：深入 click 之选项篇](https://zhuanlan.zhihu.com/p/92650388)
- [Python 命令行之旅：深入 click 之命令篇](https://zhuanlan.zhihu.com/p/93738095)
- [Python 命令行之旅：深入 click 之增强功能](https://zhuanlan.zhihu.com/p/96935131)
- [Python 命令行之旅：使用 click 实现 git 命令](https://zhuanlan.zhihu.com/p/97984420)
- [Python 命令行之旅：初探 fire](https://zhuanlan.zhihu.com/p/99629342)
- [Python 命令行之旅：深入 fire（一）](https://zhuanlan.zhihu.com/p/100459723)
- [Python 命令行之旅：深入 fire（二）](https://zhuanlan.zhihu.com/p/101708876)
- [Python 命令行之旅：fire 实现 git 命令](https://zhuanlan.zhihu.com/p/103149624)
- [Python 命令行之旅：argparse、docopt、click 和 fire 总结篇](https://zhuanlan.zhihu.com/p/106967825)

## 使用方案

先建立一个最简单的DEMO：

```python
import argparse
# 定义一个ArgumentParser实例
parser = argparse.ArgumentParser(
	prog='test', # 程序名
    description='命令行参数的解析描述，会显示在-h或--help上', # 描述
    epilog='Copyright(r), 2024' # 说明信息
)
# 添加参数
'''
# default表示默认值
# type是要传入的参数的数据类型
# help是该参数的提示信息, string
# required是是否为必须, True or False
'''
## 第一个是位置参数，'arg01'是参数的名词
parser.add_argument('arg01', type=str, help='第1个参数')
## 定义关键字参数，也就是可选参数，使用时必须加上名词'--name'
parser.add_argument('--arg02', type=str, help='第2个参数')
## 允许添加简写'-a3'，类似'--help'的简写'-h'
parser.add_argument('-a3', '--arg03', type=str, help='第3个参数')
## 使用action的参数不需要数据，只要出现或者不出现就表示相应信息。举例两个状态：store_true和store_false，当状态为store_true时，出现表示True，不出现表示False，and vice versa
parser.add_argument('-gz', '--gzcompress', action='store_true', required=False, help='第4个参数')


# 解析参数
args = parser.parse_args()

# 打印参数
## args是个字典，key为参数名词
print(args)
```



## 各参数意义

### type

`参数类型` 就是解析器参数值是要作为什么类型去解析，默认情况下是 `str` 类型。我们可以通过 `type` 入参来指定参数类型。

`argparse` 所支持的参数类型多种多样，可以是 `int`、`float`、`bool`等，比如：

```python3
>>> parser.add_argument('-i', type=int)
>>> parser.add_argument('-f', type=float)
>>> parser.add_argument('-b', type=bool)
>>> parser.parse_args(['-i', '1', '-f', '2.1', '-b', '0'])
Namespace(b=False, f=2.1, i=1)
```

更厉害的是，`type` 入参还可以是可调用(`callable`)对象。这就给了我们很大的想象空间，可以指定 `type=open` 来把参数值作为文件进行处理，也可以指定自定义函数来进行类型检查和类型转换。

作为文件进行处理：

```python3
>>> parser.add_argument('--file', type=open)
>>> parser.parse_args(['--file', 'README.md'])
Namespace(b=None, f=None, file=<_io.TextIOWrapper name='README.md' mode='r' encoding='cp936'>, i=None)
```

使用自定义函数进行处理，入参为参数值，需返回转换后的结果。 比如，对于参数 `--num`，我们希望当其值小于 1 时则返回 1，大于 10 时则返回 10：

```sh
>>> def limit(string):
...   num = int(string)
...   if num < 1:
...     return 1
...   if num > 10:
...     return 10
...   return num
...
>>> parser.add_argument('--num', type=limit)
>>> parser.parse_args(['--num', '-1'])  # num 小于1，则取1
Namespace(num=1)
>>> parser.parse_args(['--num', '15'])  # num 大于10，则取10
Namespace(num=10)
>>> parser.parse_args(['--num', '5'])  # num 在1和10之间，则取原来的值
Namespace(num=5)
```



### action

```python
parser.add_argument('-gz', '--gzcompress', action='store_true', required=False, help='第4个参数')
```

当我们在命令行输入一串参数后，对于不同类型的参数是希望做不同的处理的。 那么 `参数动作` 其实就是告诉解析器，我们希望对应的参数该被如何处理。

`参数动作` 被分成了如下 8 个类别：

- `store` —— 保存参数的值，这是默认的参数动作。它通常用于给一个参数指定值，如指定名字：

```python3
>>> parser.add_argument('--name')
>>> parser.parse_args(['--name', 'Eric'])
Namespace(name='Eric')
```

- `store_const` —— 保存被 `const` 命名的固定值。当我们想通过是否给定参数来起到标志的作用，给定就取某个值，就可以使用该参数动作，如：

```python3
>>> parser.add_argument('--sum', action='store_const', const=sum)
>>> parser.parse_args(['--sum'])
Namespace(sum=<built-in function sum>)
>>> parser.parse_args([])
Namespace(sum=None)
```

- `store_true` 和 `store_false` —— 是 `store_const` 的特殊情况，用来分别保存 True 和 False。如果为指定参数，则其默认值分别为 False 和 True，如：

```python3
>>> parser.add_argument('--use', action='store_true')
>>> parser.add_argument('--nouse', action='store_false')
>>> parser.parse_args(['--use', '--nouse'])
Namespace(nouse=False, use=True)
>>> parser.parse_args([])
Namespace(nouse=True, use=False)
```

- `append` —— 将参数值追加保存到一个列表中。它常常用于命令行中允许多个相同选项，如：

```python3
>>> parser.add_argument('--file', action='append')
>>> parser.parse_args(['--file', 'f1', '--file', 'f2'])
Namespace(file=['f1', 'f2'])
```

- `append_const` —— 将 `const` 命名的固定值追加保存到一个列表中（`const` 的默认值为 `None`）。它常常用于将多个参数所对应的固定值都保存在同一个列表中，相应的需要 `dest` 入参来配合，以放在同一个列表中，如：

不指定 `dest` 入参，则固定值保存在以参数名命名的变量中

```python3
>>> parser.add_argument('--int', action='append_const', const=int)
>>> parser.add_argument('--str', action='append_const', const=str)
>>> parser.parse_args(['--int', '--str'])
Namespace(int=[<class 'int'>], str=[<class 'str'>])
```

指定 `dest` 入参，则固定值保存在 `dest` 命名的变量中

```python3
>>> parser.add_argument('--int', dest='types', action='append_const', const=int)
>>> parser.add_argument('--str', dest='types', action='append_const', const=str)
>>> parser.parse_args(['--int', '--str'])
Namespace(types=[<class 'int'>, <class 'str'>])
```

- `count` —— 计算参数出现次数，如：

```python3
>>> parser.add_argument('--increase', '-i', action='count')
>>> parser.parse_args(['--increas', '--increase'])
Namespace(increase=2)
>>>parser.parse_args(['-iii'])
Namespace(increase=3)
```

- `help` —— 打印解析器中所有选项和参数的完整帮助信息，然后退出。
- `version` —— 打印命令行版本，通过指定 `version` 入参来指定版本，调用后退出。如：

```python3
>>> parser = argparse.ArgumentParser(prog='CMD')
>>> parser.add_argument('--version', action='version', version='%(prog)s 1.0')
>>> parser.parse_args(['--version'])
CMD 1.0
```

