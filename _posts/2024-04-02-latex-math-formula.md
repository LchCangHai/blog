---
layout: post
title: latex中公式使用及规则
categories: [Tutorial, latex]
description: 数学公式
keywords: formula, latex, Tutorial
mermaid: false
sequence: false
flow: false
mathjax: true
mindmap: false
mindmap2: false
typora-root-url: ../
---

本文主要内容转自 <https://blog.csdn.net/ViatorSun/article/details/82826664>

[更多特殊符号](https://zhuanlan.zhihu.com/p/510451940)

### 两种模式

LaTeX 的数学模式有两种：

- 行内模式(inline)
- 行间模式(display)

前者在正文的行文中，插入数学公式；后者独立排列单独成行。

在行文中，使用 `$ ... $` 能够插入行内公式，使用 `$$ ... $$` 能够插入行间公式，若是须要对行间公式进行编号，可使用 equation 环境。

```markdown
这是行内公式: $a=b$   # 在blog中，行内和行间都是使用$$...$$
行间公式 $$a=b$$
```

这是行内公式:  $$ a=b $$  

行间公式：

 $$ a=b $$





### 公式加粗、更改颜色、添加序号

对公式加粗需要用 \bm{ …… }加之包含其中即可

```markdown
$\bm{ .... }$
```

更改公式字母颜色：
如果只更改个别字母，那个后面的需要用黑色再改下

```markdown
\color{red}  
\color{green}   
\color{back}

\color{green}。。。。。\color{back}。。。。

```

$$ \color{red}red \color{green}green \color{black}black \color{blue}blue $$

给公式添加序号：在公式最后添加 \tag{…}

```markdown
$$ ... \tag1$$
$$ ... \tag{1.1}$$	# 多位序号记得用{}扩起来
```

$$ formula1.1 \tag{1.1}$$

### 希腊字母

| LaTex表达形式 | 对应的希腊字母 | LaTex表达形式 | MathJax表达式 | 对应的希腊字母 |
| :-----------: | :------------: | :-----------: | :------------: | :------------: |
| `\alpha`       | $$\alpha $$    | `\Alpha  `     | `A` | $$A$$   |
| `\beta   `     | $$ \beta $$    | `\Beta   `     | `B`  | $$B$$      |
| `\gamma  `     | $$\gamma$$     | `\Gamma  `     |      | $$\Gamma $$    |
| `\delta  `     | $$\delta $$    | `\Delta  `     |      | $$\Delta $$    |
| `\epsilon`     | $$\epsilon $$  | `\Epsilon`     | `E`  | $$E$$  |
| `\zeta   `     | $$\zeta $$     | `\Zeta   `     | `Z`  | $$Z$$  |
| `\eta    `     | $$\eta $$      | `\Eta    `     | `H` | $$H$$  |
| `\theta  `     | $$\theta $$    | `\Theta  `     |      | $$\Theta $$    |
| `\iota   `     | $$\iota $$     | `\Iota   `     | `I`  | $$I $$  |
| `\kappa  `     | $$\kappa $$    | `\Kappa  `     | `K`  | $$K$$    |
| `\lambda `     | $$\lambda $$   | `\Lambda `     |   | $$\Lambda $$   |
| `\mu     `     | $$\mu $$       | `\Mu     `     | `M`  | $$M$$       |
| `\nu     `     | $$\nu $$       | `\Nu     `     | `N`  | $$N$$      |
| `\xi     `     | $$\xi $$       | `\Xi     `     |      | $$\Xi $$       |
| `\omicron`     | $$\omicron $$  | `\Omicron`     | `O`  | $$O $$ |
| `\pi     `     | $$\pi $$       | `\Pi     `     |      | $$\Pi $$       |
| `\rho    `     | $$\rho $$      | `\Rho    `     | `P`  | $$P$$      |
| `\sigma  `     | $$\sigma $$    | `\Sigma  `     |      | $$\Sigma $$    |
| `\tau    `     | $$\tau $$      | `\Tau    `     | `T`  | $$T $$     |
| `\upsilon`     | $$\upsilon $$  | `\Upsilon`     |      | $$\Upsilon $$  |
| `\varphi `     | $$\varphi $$   | `\Phi    `     |      | $$\Phi $$      |
| `\chi    `     | $$\chi $$      | `\Chi    `     | `X`  | $$X $$      |
| `\psi    `     | $$\psi $$      | `\Psi    `     |      | $$\Psi $$      |
| `\omega  `     | $$\omega $$    | `\Omega  `     |      | $$\Omega $$    |

### 运算符 & 空格

普通字符在数学公式中含义一样，除了 # $ % & ~ \_ ^ \\ { } 若要在数学环境中表示这些符号# $ % & \_ { } ，需要分别表示为 # $ % & \_ { } ，即在个字符前加上\\ 。

| LaTex 表达式         | 字体效果           |
| :------------------: | :----------------: |
| 单空格 ： `a \\quad b` | $$a \quad b  $$ |
| 双空格： `a \\qquad b` |$$ a \qquad b$$ |
| 乘号：`\\times`      | $$\times  $$      |
| `#`                  | $$ \#  $$          |
| `\$`                |$$ \$   $$          |
| `\%`                 |$$ \%    $$         |
| `\&`                | $$\&   $$          |
| `\_`               | $$ \_   $$      |
| `\{ \}`           |$$ \{ \}    $$        |

### 上下标

对于下标使用下划线表示“ \_ ” ；对于上标使用 “ ^ ”表示：

> 比如 x\_i\^2 的LaTex表达式为 $$x_i^2$$ 。

LaTex表达式中的上下标可以叠加的，就比如$${x^y}^z$$的LaTex表达式为 \{x\^y\}\^z 或者 x\^\{y\^z\}

> LaTex表达式**默认**的是 “ \_ ” “ ^ ” 之后的一位才是上下标的内容，对于超过一个字母的上下标需要使用 { } 将它括起来，比如$$x_{2i}^{2+b}$$的LaTex表达式为x\_\{2i\}\^\{2+b\}。

| Latex 表达式  |    实现     |   Latex 表达式    |      实现       |
| :-----------: | :---------: | :---------------: | :-------------: |
|   $$x_i^2$$   |   `x\i^2`   | $$x_{2i}^{2+b}$$  | `x_{2i}^{2+b}`  |
|  $$\hat{a}$$  |  `\hat{a}`  |   $$\acute{a}$$   |   `\acute{a}`   |
| $$\grave{a}$$ | `\grave{a}` |   $$\breve{a}$$   |   `\breve{a}`   |
|  $$\bar{a}$$  |  `\bar{a}`  | $$\widetilde{a}$$ | `\widetilde{a}` |
| $$\check{a}$$ | `\check{a}` |   $$\tilde{a}$$   |   `\tilde{a}`   |
|  $$\dot{a}$$  | `\ddot{a}`  |   $$\ddot{a}$$    |   `\ddot{a}`    |
|  $$\vec{a}$$  |  `\vec{a}`  |  $$\widehat{a}$$  |  `\widehat{a}`  |

###   log

$\log$的表达式会稍微简单点，`\log` 就是它的LaTex表达式，同样的对于需要下标的同样使用下划线表示 “ \_ ” ， 对于多个字符组成的需要添加 { } 将其包括。

|  LaTex表达形式   |      实际效果      |
| :--------------: | :----------------: |
| `\log_{21} {xy}` | $$\log_{21} {xy}$$ |

### 括号

LaTex表达式中的 `( )` 、 `[ ]` 均可以正常使用，但是对于 `{ }` 需要使用转义字符使用，即使用 `“{”` 和 `“}”` 表示 `{ }`

| LaTex表达形式                                                |                           实际效果                           |
| :----------------------------------------------------------- | :----------------------------------------------------------: |
| `\left(…\right)`                                             |                      $$\left(…\right)$$                      |
| `\vert`                                                      |                          $$\vert$$                           |
| `\Vert`                                                      |                          $$\Vert$$                           |
| `\langle`                                                    |                         $$\langle$$                          |
| `\rangle`                                                    |                         $$\rangle$$                          |
| `\lceil`                                                     |                          $$\lceil$$                          |
| `\rceil`                                                     |                          $$\rceil$$                          |
| `\lfloor`                                                    |                         $$\lfloor$$                          |
| `\rfloor`                                                    |                         $$\rfloor$$                          |
| `\Biggl(\biggl(\Bigl(\bigl((x)\bigr)\Bigr)\biggr)\Biggr)`    | $$\Biggl(\biggl(\Bigl(\bigl((x)\bigr)\Bigr)\biggr)\Biggr)$$  |
| `\vert x \vert`                                              |                      $$\vert x \vert$$                       |
| `f(x)=\begin{cases} x = \cos(t) \\y = \sin(t) \\ z = \frac xy \end{cases}` | $$f(x)=\begin{cases} x = \cos(t) \\y = \sin(t) \\ z = \frac xy \end{cases}$$ |
| `f(x)=\begin{cases} 0& \text{x=0}\\1& \text{x!=0} \end{cases}` | $$f(x)=\begin{cases} 0& \text{x=0}\\1& \text{x!=0} \end{cases}$$ |

对于个别符号，如 ()、\[\]等，如果想要变大，可以在 这些符号前面添加即可

```python
\Biggl   \biggl   \Bigl   \bigl   左符号
\Biggr   \biggr   \Bigr   \bigr   右符号
```

###   矩阵

| Latex表达式                                       | 效果                                                |
| ------------------------------------------------- | --------------------------------------------------- |
| `\begin{matrix} 0 & 1 \\ 1 & 0 \end{matrix}`      | $$\begin{matrix} 0 & 1 \\ 1 & 0 \end{matrix}$$      |
| `\begin{pmatrix} 0 & -i \\ i & 0 \end{pmatrix}\\` | $$\begin{pmatrix} 0 & -i \\ i & 0 \end{pmatrix}\\$$ |
| `\begin{bmatrix} 0 & -1 \\ 1 & 0 \end{bmatrix}`   | $$\begin{bmatrix} 0 & -1 \\ 1 & 0 \end{bmatrix}$$   |
| `\begin{Bmatrix} 1 & 0 \\ 0 & -1 \end{Bmatrix}`   | {$$\begin{Bmatrix} 1 & 0 \\ 0 & -1 \end{Bmatrix}$$  |
| `\begin{vmatrix} a & b \\ c & d \end{vmatrix}`    | $$\begin{vmatrix} a & b \\ c & d \end{vmatrix}$$    |
| `\begin{Vmatrix} i & 0 \\ 0 & -i \end{Vmatrix}`   | $$\begin{Vmatrix} i & 0 \\ 0 & -i \end{Vmatrix}$$   |

  


### 求和与积分

| LaTex 表达式            | 实际效果                  |
| ----------------------- | ------------------------- |
| `\sum`                  | $$\sum$$                  |
| `\int`                  | $$\int$$                  |
| `\sum_1^n`              | $$\sum_1$$                |
| `\sum_{i=0}^\infty i^2` | $$\sum_{i=0}^\infty i^2$$ |
| `\prod_{k=1}^n k = n!`  | $$\prod_{k=1}^n k = n!$$  |
| `\infty`                | $$\infty$$                |
| `\bigcup`               | $$\bigcup$$               |
| `\bigcap`               | $$\bigcap$$               |
| `\iint`                 | $$\iint$$                 |
| `\iiint`                | $$\iiint$$                |

  


### 开方

| LaTex 表达式         | 实际效果               |
| -------------------- | ---------------------- |
| `\sqrt{x^3}`         | $$\sqrt{x^3}$$         |
| `\sqrt[3]{\frac xy}` | $$\sqrt[3]{\frac xy}$$ |

  


### 分数

| LaTex 表达式      | 实际效果            |
| ----------------- | ------------------- |
| `\frac ab`        | $$\frac ab$$        |
| `\frac{a+1}{b+1}` | $$\frac{a+1}{b+1}$$ |
| `{a+1\over b+1}`  | $${a+1\over b+1}$$  |
| `\cfrac{a}{b}`    | $$\cfrac{a}{b}$$    |

  


### 特殊函数

| LaTex 表达式    | 实际效果          |
| --------------- | ----------------- |
| `\lim`          | $$\lim$$          |
| `\lim_{x\to 0}` | $$\lim_{x\to 0}$$ |
| `\sin`              | $$\sin$$          |
| `\cos`              | $$ \cos$$          |
| `\sin x`              | $$\sin x $$          |
| `\cos x`              | $$\cos x $$          |
| `\hat x`              | $$\hat x $$          |
| `\widehat{xy}`              | $$\widehat{xy} $$          |
| `\bar x`              | $$ \bar x$$          |
| `\overline{xyz}`              | $$\overline{xyz} $$          |
| `\vec x`              | $$\vec x $$          |
| `\overrightarrow{xyz}`              | $$\overrightarrow{xyz} $$          |
| `\overleftrightarrow{xyz}`              | $$\overleftrightarrow{xyz} $$          |
| `\stackrel{F.T}{\longrightarrow}`              | $$\stackrel{F.T}{\longrightarrow} $$          |
| `\dot x`              | $$ \dot x$$          |
| `\ddot x`              | $$ \ddot x$$          |

  


### 导数、极限、积分

|      | LaTex表达式 | 实际效果 |
| ---- | ----------- | -------- |
| 导数 |  `{f}'(x) = x^2 + x`           |   ${f}'(x) = x^2 + x$       |
| 极限 |  `\lim_{x \to 0} \frac {3x ^2 +7x^3} {x^2 +5x^4} = 3`           |   $\lim_{x \to 0} \frac {3x ^2 +7x^3} {x^2 +5x^4} = 3$       |

  


### 积分

积分中，需要注意的是，在多重积分内 dx 和 dy 之间 使用一个斜杠加一个逗号 , 来增大稍许间距。同样，在两个积分号之间使用一个斜杠加一个感叹号 ! 来减小稍许间距。使之更美观。

```markdown
\int_a^b f(x) dx 
```

$$\int_a^b f(x) dx $$

```c
\int_0^{+\infty} x^n e^{-x} dx = n! 
```

$$\int_0^{+\infty} x^n e^{-x} dx = n! $$

```c
\int_{x^2 + y^2 \leq R^2}   f(x,y) dx dy = 
\int_{\theta=0}^{2\pi}    \int_{r=0}^R    f(r\cos\theta,r\sin\theta) r dr d\theta
```

$$\int_{x^2 + y^2 \leq R^2}   f(x,y) dx dy = 
\int_{\theta=0}^{2\pi}    \int_{r=0}^R    f(r\cos\theta,r\sin\theta) r dr d\theta$$

```c
\int \!\!\! \int_D f(x,y)dxdy  \int \int_D f(x,y)dxdy
```

$$ \int \!\!\! \int_D f(x,y)dxdy  \int \int_D f(x,y)dxdy $$

```c
i\hbar\frac{\partial \varphi } {\partial {t}} = \frac{-\hbar^2}{2m} 
\left( \frac{\partial^2}{\partial x^2} + \frac{\partial^2}{\partial y^2} + 
\frac{\partial^2}{\partial z^2} \right) \varphi  + V \varphi
```

$$i\hbar\frac{\partial \varphi } {\partial {t}} = \frac{-\hbar^2}{2m} 
\left( \frac{\partial^2}{\partial x^2} + \frac{\partial^2}{\partial y^2} + 
\frac{\partial^2}{\partial z^2} \right) \varphi  + V \varphi$$

```c
\frac{d}{dt} \int \!\!\! \int \!\!\! \int_{\textbf{R}^3} 
\left | \varphi (r,t) \right|^2 dx dy dz = 0
```

$$\frac{d}{dt} \int \!\!\! \int \!\!\! \int_{\textbf{R}^3} 
\left | \varphi (r,t) \right|^2 dx dy dz = 0$$

  


### 特殊符号和符号

| LaTex 表达式       | 实际效果                                       | LaTex表达式      | 实际效果                               |
| ------------------ | ---------------------------------------------- | ---------------- | -------------------------------------- |
| `\lt              ` | $$ \lt             $$                        | `\gt           `  | $$\gt          $$                       |
| `\le              ` | $$ \le             $$                        | `\leq          `  | $$\leq         $$                       |
| `\leqq            ` | $$ \leqq           $$                        | `\leqslant     `  | $$\leqslant    $$                       |
| `\ge              ` | $$ \ge             $$                        | `\geq          `  | $$\geq         $$                       |
| `\geqq            ` | $$ \geqq           $$                        | `\geqslant     `  | $$\geqslant    $$                       |
| `\neq             ` | $$ \neq            $$                        | `\not\lt       `  | $$\not\lt      $$                       |
| `\not             ` | 在几乎所有的                                  | 符号上划出         | 一个斜线                               |
| `\times           ` | $$ \times          $$                        | `\div          `  | $$\div   $$                        |
| `\pm              ` | $$ \pm             $$                        | `\mp           `  | $$\mp    $$                        |
| `\cdot            ` | $$ \cdot           $$                        | `              `  |                                        |
| `\cup             ` | $$ \cup            $$                        | `\cap          `  | $$\cap          $$                     |
| `\setminus        ` | $$ \setminus       $$                        | `\subset       `  | $$\subset       $$                     |
| `\subseteq        ` | $$ \subseteq       $$                        | `\subsetneq    `  | $$\subsetneq    $$                     |
| `\supset          ` | $$ \supset         $$                        | `\in           `  | $$\in           $$                     |
| `\notin           ` | $$ \notin          $$                        | `\emptyset     `  | $$\emptyset     $$                     |
| `\varnothing      ` | $$ \varnothing     $$                        |                   |                                        |
| `{n+1 \choose 2k} ` | $$ {n+1 \choose 2k}$$                        | `\binom{n+1}{2k}` | $$\binom{n+1}{2k}$$                |
| `\to              ` | $$ \to             $$                        | `\rightarrow    ` | $$\rightarrow    $$               |
| `\leftarrow       ` | $$ \leftarrow      $$                        | `\Rightarrow    ` | $$\Rightarrow    $$               |
| `\Leftarrow       ` | $$ \Leftarrow      $$                        | `\mapsto        ` | $$\mapsto        $$               |
| `\land            ` | $$ \land           $$                        | `\lor           ` | $$\lor           $$               |
| `\lnot            ` | $$ \lnot           $$                        | `\forall        ` | $$\forall        $$               |
| `\exists          ` | $$ \exists         $$                        | `\top           ` | $$\top           $$               |
| `\bot             ` | $$ \bot            $$                        | `\vdash         ` | $$\vdash         $$               |
| `\vDash           ` | $$ \vDash          $$                        |                   |                                        |
| `\star            ` | $$ \star           $$                        | `\ast    `        | $$ \ast $$                            |
| `\oplus           ` | $$ \oplus          $$                        | `\circ   `        | $$ \circ$$                            |
| `\bullet          ` | $$ \bullet         $$                        |                   |                                        |
| `\approx          ` | $$ \approx         $$                        | `\sim          `  | $$ \sim         $$                 |
| `\simeq           ` | $$ \simeq          $$                        | `\cong         `  | $$ \cong        $$                 |
| `\equiv           ` | $$ \equiv          $$                        | `\prec         `  | $$ \prec        $$                 |
| `\lhd             ` | $$ \lhd            $$                        | `\therefore    `  | $$ \therefore   $$                 |
| `\infty           ` | $$ \infty          $$                        | `\aleph_0      `  | $$ \aleph_0     $$                  |
| `\nabla           ` | $$ \nabla          $$                        | `\partial      `  | $$ \partial     $$                 |
| `\Im              ` | $$ \Im             $$                        | `\Re           `  | $$ \Re          $$                 |
| `a\equiv b\pmod n ` | $$ a\equiv b\pmod n$$                        |                   |                                        |
| `\ldots           ` | $$ \ldots          $$                        | `\cdots      `    | $$ \cdots     $$                      |
| `\epsilon         ` | $$ \epsilon        $$                        | `\varepsilon `    | $$ \varepsilon$$                      |
| `\phi             ` | $$ \phi            $$                        | `\varphi     `    | $$ \varphi    $$                      |
| `\ell             ` | $$ \ell            $$                        |                   |                                        |

  


### 字体

| LaTex 表达式      | 字体效果                          | LaTex表达式      | 字体效果                         |
| ----------------- | --------------------------------- | ---------------- | -------------------------------- |
| `\mathbb{ABCDE}  ` | $$ \mathbb{ABCDE}   $$          | `\Bbb{ABCDEF}    `| $$  \Bbb{ABCDEF}    $$ |
| `\mathbf{abcde}  ` | $$ \mathbf{abcde}   $$          | `\mathtt{ABCDE}  `| $$  \mathtt{ABCDE}  $$ |
| `\mathrm{ABCDE}  ` | $$ \mathrm{ABCDE}   $$          | `\mathsf{ABCDE}  `| $$  \mathsf{ABCDE}  $$ |
| `\mathcal{ABCDE} ` | $$ \mathcal{ABCDE}  $$          | `\mathscr{ABCDE} `| $$  \mathscr{ABCDE} $$ |
| `\mathfrak{ABCDE}` | $$ \mathfrak{ABCDE} $$          |                  |                                  |



### 集合符号

| 特征              |                 语法 |             效果 |
| ----              |                 ---- |             ---- |
| 菱形 |     `\Diamond`                |   $$\Diamond$$             |
| 正方形 |    `\Box`                  |   $$\Box$$               |
| 三角-Delta |    `\Delta`                  |   $$\Delta$$               |
| 三角图形 |  `\triangle`                    |    $$\triangle$$              |
| 角名 |  `\angle\Alpha\Beta\Gamma`                    |   $$\angle\Alpha\Beta\Gamma$$               |
| 角度 | `\sin\!\frac{\pi}{3}=\sin60^\circ=\frac{\sqrt{3}}{2}` | $$\sin\!\frac{\pi}{3}=\sin60^\circ=\frac{\sqrt{3}}{2}$$ |
| 垂直 | `\perp` | $$\perp$$ |













## 学习链接

[LaTeX数学公式、常用符号大全](https://zhuanlan.zhihu.com/p/510451940)

[超详细 LaTex数学公式](https://blog.csdn.net/ViatorSun/article/details/82826664)

