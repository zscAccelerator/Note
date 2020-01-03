[toc]

# Typora简单教程

## 目录

```
[toc]
```

## 标题

```
#       一级标题
##      二级标题
###     三级标题
####    四级标题
```

## 引用

```
>    引用内容一
>>   引用内容二
>>>  引用内容三
```

## 代码

### 单行代码

```
`String str = "hello world";`
```

### 多行代码

~~~
不指定语言
​~~~
或```
指定语言
​~~~java
```c++
~~~

## 列表

### 无序列表

~~~
单行
*
或+
或-
多行
*
TAB*
TABTAB*
~~~

### 有序列表

~~~
1.
2.
3.
~~~

### 任务列表

~~~
-[]吃饭
-[x]睡觉
~~~

## 表格

~~~
|姓名|性别|年龄|
|:---|---|---:|
|zsc|male|22|
|zsj|male|21|
|wcc|male|20|
~~~

## 图片

**ps ： 使用本地图片方式上传github显示错误，因为github不支持绝对路径方式**

~~~
网络图片
！[随便填什么](图片的链接地址)
~~~

**ps : 可以通过将图片统一上传至github上某一文件夹，然后复制链接地址，使用上面语法插入图片**

## 超链接

**ps：按住ctrl，点击相应位置即可跳转访问**

~~~
隐藏url
[随便填什么][要访问的网址]
不隐藏url
<要访问的网址>
~~~

## 文字格式

### 斜体

~~~
*要倾斜的文字*
或_要倾斜的文字_
~~~

### 加粗

~~~
**要加粗的文字**
__要加粗的文字__
~~~

### 下划线

~~~
<u>加下划线的文字</u>
~~~

### 删除线

~~~
~~要删除的文字~~
~~~

### 分割线

~~~
***
或者---

~~~

## 注脚

~~~
要注释的词语[^1]
[^1]对词语的解释
~~~

## 上下标

~~~
n<sup>2</sup>   上标
n<sub>2</sub>   下标
~~~

## 跳转

**ps：按住ctrl点击跳转**

~~~
仅能跳转到标题处
[任意文字](#标题名称)
跳转到任意位置
<a name = "anchor">Anchor</a>
<a href = "#anchor">Link to Anchor</a>
~~~

## 数学公式

~~~
$$
特定格式的数学公式
$$
其中格式有
x^2  				 			上标
x_2  				 			下标
1/2  				 			分式
\frac{1}{2}  		 			分式
\cdots  			 			省略号
\sqrt{x}       		 			根号x
\vec{a}              			向量a
\int{x}dx            			x的不定积分
\int_{1}^{2}{x}dx    			x在1~2之间的积分
\lim{a+b}			 			a+b的极限

\lim_{n\rightarrow+\infty}{a}   当n趋近于正无穷时a的极限
\lim_{n\rightarrow0}{a}			当n趋近于0时a的极限
\sum{a}							累加
\sum_{n=1}^{100}{a_n}			数列从第一项累加至一百项
\prod{x}						累乘
\prod_{n=1}^{99}{x_n}			数列从第一项累乘至一百项
\sin							三角函数正弦
\ln2							ln2
\log_28							以2为底8的对数
\lg10							lg10

y(x)=
\begin{cases}
\sqrt\frac{1}{x}， x=0     \\
\sqrt\frac{2}{x}， x\neq0
\end{cases}						分段函数,效果如下

~~~


$$
y(x)=
\begin{cases}
\sqrt\frac{1}{x}， x=0     \\
\sqrt\frac{2}{x}， x\neq0
\end{cases}
$$

## 希腊字母

| 大写 | md       | 小写 | md          |
| ---- | -------- | ---- | ----------- |
| *A*  | A        | *α*  | \alpha      |
| *B*  | B        | *β*  | \beta       |
| Γ    | \Gamma   | *γ*  | \gamma      |
| Δ    | \Delta   | *δ*  | \delta      |
| *E*  | E        | *ϵ*  | \epsilon    |
|      |          | *ε*  | \varepsilon |
| *Z*  | Z        | *ζ*  | \zeta       |
| *H*  | H        | *η*  | \eta        |
| Θ    | \Theta   | *θ*  | \theta      |
| *I*  | I        | *ι*  | \iota       |
| *K*  | K        | *κ*  | \kappa      |
| Λ    | \Lambda  | *λ*  | \lambda     |
| *M*  | M        | *μ*  | \mu         |
| *N*  | N        | *ν*  | \nu         |
| Ξ    | \Xi      | *ξ*  | \xi         |
| *O*  | O        | *ο*  | \omicron    |
| Π    | \Pi      | *π*  | \pi         |
| *P*  | P        | *ρ*  | \rho        |
| Σ    | \Sigma   | *σ*  | \sigma      |
| *T*  | T        | *τ*  | \tau        |
| Υ    | \Upsilon | *υ*  | \upsilon    |
|      |          | *φ*  | \varphi     |
| *X*  | X        | *χ*  | \chi        |
| Ψ    | \Psi     | *ψ*  | \psi        |
| Ω    | \Omega   | *ω*  | \omega      |

## 关系运算符

| 运算符 | md     |
| ------ | ------ |
| ±      | \pm    |
| \times | \times |
| ⋅      | \cdot  |
| ÷      | \div   |
| \neq   | \neq   |
| ≡      | \equiv |
| ≤      | \leq   |
| ≥      | \geq   |



## 其他特殊字符

| 符号 | md         |
| ---- | ---------- |
| ∀    | \forall    |
| ∞    | \infty     |
| ∅    | \emptyset  |
| ∃    | \exists    |
| ∇    | \nabla     |
| ⊥    | \bot       |
| ∠    | \angle     |
| ∵    | \because   |
| ∴    | \therefore |
|      | \quad      |

## 行内公式

~~~
$公式内容$
~~~

