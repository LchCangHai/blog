---
layout: post
title: Anaconda的基本使用
categories: [Tutorial, Anaconda]
description: Anaconda的基本使用
keywords: Anaconda, Tutorial, software, python
mermaid: false
sequence: false
flow: false
mathjax: false
mindmap: false
mindmap2: false
typora-root-url: ../
---

Anaconda的基本使用，包括安装、环境配置、镜像等基础操作

 > [Anaconda使用教程一（新手友好）](https://zhuanlan.zhihu.com/p/348120084)
 > [使用Anaconda创建虚拟环境并添加到Jupyter Notebook](https://blog.csdn.net/hongguihuang/article/details/108566702)

## 遇到问题

使用 pycharm 配置出现 Conda executable path is empty 问题
> https://blog.csdn.net/qq_43750301/article/details/126937553
> 配置好 conda executable，在 conda executable 这里选择的是本机安装 conda 的位置（一定要选到_conda. exe）

查看安装的库的列表：
pip list：只看列表
conda list：还可以看版本

```sh

#创建环境
conda create -n 环境名

#查看所有环境
conda info --envs

#激活环境
Conda activate 环境名
Source activate 环境名
activate + 环境名

#在环境中安装包（使用conda或pip）
Conda install 包名称
或者pip install 包名称 -i https://pypi.tuna.tsinghua.edu.cn/simple（清华镜像）
或者pip install 包名称 -i  https://pypi.doubanio.com/simple/ （豆瓣镜像）

#查看环境中现有的包
Conda list
pip list

#退出环境
deactivate 环境名

#删除环境
conda remove -n 环境名 --all

```
![image.png](/images/posts/2023-09-15-basic-use-of-anaconda/20230531162524.png)

## 镜像操作

[[镜像]]
`conda config --show` 将会显示conda的配置信息，找到channel, 对应的就是我们的镜像配置

```sh
# 添加新镜像源
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main/
# 设置搜索时显示通道地址
conda config --set show_channel_urls yes

```

因为有科学上网工具，所以选择切换回默认镜像源，命令一行搞定：

$ conda config --remove-key channels
另外删除单个链接命令如下：

$ conda config --remove channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free

## 使用Anaconda创建虚拟环境并添加到Jupyter Notebook

jupyter Notebook确保IPython内核可用，但是您必须手动添加具有其他版本的Python或虚拟环境的内核。首先，您需要激活虚拟环境。接下来，安装ipykernel，它为Jupyter提供IPython内核：

```
pip install --user ipykernel
```

接下来，您可以通过输入以下内容将虚拟环境添加到Jupyter：

```
python -m ipykernel install --user --name=mypytorch
```

如果打印

```
Installed kernelspec mypytorch in /home/user/.local/share/jupyter/kernels/mypytorch
```

说明已经成功了。