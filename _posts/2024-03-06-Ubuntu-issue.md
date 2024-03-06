---
layout: post
title: Ubuntu issue - Jekyll
categories: [Ubuntu, issue]
description: 本地运行GitHub Pages时遇到的一些问题, Jekyll, Gem, Ruby
keywords: Ubuntu, Issue, Jekyll
mermaid: false
sequence: false
flow: false
mathjax: false
mindmap: false
mindmap2: false
typora-root-url: ../
---

## GitHub API authentication

### 问题描述

```bash
GitHub Metadata: No GitHub API authentication could be found. Some fields may be missing or have incorrect data.
```

解释：缺失了GitHub的访问令牌，需要重新到github上生成。注意：token有效期最长一年（可以无限期，但不建议），**之后遇到token过期则去重新生成**

### 解决方案

#### 详解

先打开`https://github.com/settings/tokens/new`，权限不用选，默认是`public repository` 。生成token

在git bash上运行：

```bash
JEKYLL_GITHUB_TOKEN=your_token jekyll serve
```

如果是windows用户，可以把变量增加到系统的环境变量中。

---

如果报错如下：

```bash
 Incremental build: disabled. Enable with --incremental
      Generating...
   GitHub Metadata: No internet connection. GitHub metadata may be missing or incorrect.
   GitHub Metadata: No internet connection. GitHub metadata may be missing or incorrect.
   GitHub Metadata: No internet connection. GitHub metadata may be missing or incorrect.
   GitHub Metadata: No internet connection. GitHub metadata may be missing or incorrect.
   GitHub Metadata: No internet connection. GitHub metadata may be missing or incorrect.
   GitHub Metadata: No internet connection. GitHub metadata may be missing or incorrect.
   GitHub Metadata: No internet connection. GitHub metadata may be missing or incorrect.
   GitHub Metadata: No internet connection. GitHub metadata may be missing or incorrect.
   GitHub Metadata: No internet connection. GitHub metadata may be missing or incorrect.
       Jekyll Feed: Generating feed for posts
  Liquid Exception: undefined method `map' for false:FalseClass Did you mean? tap in /_layouts/post.html
                    ------------------------------------------------
      Jekyll 4.0.0   Please append `--trace` to the `serve` command
                     for any additional information or backtrace.
                    ------------------------------------------------
```

那么在`_config.yml`中添加`github: [metadata]`

#### 相关链接：

[GitHub Token生成](https://github.com/settings/tokens/new)

[Jekyll github-metadata-blob-main-dos 文档-authentication部分](https://github.com/jekyll/github-metadata/blob/main/docs/authentication.md)

[博客01-正确对应](https://last2win.com/2020/02/23/github-error-jekyll/)

[github pages-gem issues -- No GitHub API authentication error](https://github.com/github/pages-gem/issues/399)

[博客02](https://blog.csdn.net/yufei_email/article/details/104120285)



## Error:  Permission denied - bind(2) for 127.0.0.1:4000

### 问题描述

```
Error:  Permission denied - bind(2) for 127.0.0.1:4000
D:/4.studyFile/3.blog/1.rubyInstaller/Ruby31-x64/lib/ruby/3.1.0/socket.rb:201:in `bind': Permission denied - bind(2) for 127.0.0.1:4000 (Errno::EACCES)
```

这个是由于127.0.0.1：4000这个端口被占用引起的

### 解决方案

**第一步**：找到4000端口被哪个进程占用了

在cmd运行：

```shell
netstat -aon | findstr "4000"
```

结果为：

```sh
TCP    127.0.0.1:4000         0.0.0.0:0              LISTENING       13688
```

最后一项是使用了`4000`端口的进程的`PID`

**第二步**：打开任务管理器 `ctrl+shift+esc`

点击`服务`选项，寻找对应的`PID`的进程，`右键-停止服务`

再运行 `bundle exec jekyll serve`

### 相关链接

[博客](https://segmentfault.com/q/1010000010483290)







