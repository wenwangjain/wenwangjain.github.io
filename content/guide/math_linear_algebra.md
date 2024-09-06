---
title: 线性代数
weight: 102
#next: /step1
prev: /guide
#editURL: "https://example.com/edit/this/page"
type: "docs"
toc: true
math: true
---



### 1、定义

<font color=DarkCyan face=Georgia>***1.1、一般形式***</font>：
- 一个 $m\times n$ 的矩阵 $\boldsymbol{A}$ 可以表示为：
$\boldsymbol{A}=\begin{bmatrix}a_{11}&a_{12}&\cdots&a_{1n} \\\ a_{21}&a_{22}&\cdots&a_{2n} \\\ \vdots&\vdots&\ddots&\vdots \\\ a_{m1}&a_{m2}&\cdots&a_{mn}\end{bmatrix}$
，其中 $a_{ij}$ 或 $\boldsymbol{A}_{ij}$ 表示矩阵 $\boldsymbol{A}$ 的第 $i$ 行第 $j$ 列的元素。

<font color=DarkCyan face=Georgia>***1.2、特殊矩阵：***</font>
- 方阵：当矩阵的行数 $m$ 等于列数 $n$ 时，称为 $n$ 阶方阵
- 零矩阵：所有元素都为 0 的矩阵，记为 $\boldsymbol{O}$
- 单位矩阵：主对角线元素都为 1，其余元素都为 0 的方阵，记为 $\boldsymbol{I}$（或 $\boldsymbol{E}$ ）。对于 $n$ 阶单位矩阵，通常表示为 $\boldsymbol{I}_n$


<br><br><br>


### 2、基本运算

<font color=DarkCyan face=Georgia>***2.1、数乘***</font>：
- 标量 $c$ 与矩阵 $\boldsymbol{A}$ 的数乘，$c\boldsymbol{A}$ 中的元素是 $\boldsymbol{A}$ 的对应元素与 $c$ 的乘积，


<br><br>


<font color=DarkCyan face=Georgia>***2.2、转置***</font>：
- 一个 $m \times n$ 的矩阵 $\boldsymbol{A}$ 的转置，是一个 $n\times m$ 的矩阵，记作 $\boldsymbol{A}^T$，转置矩阵 $\boldsymbol{A}^T$ 第 $i$ 行第 $j$ 列的元素是原矩阵 $\boldsymbol{A}$ 第 $j$ 行第 $i$ 列的元素（行列互换）。
$$\begin{bmatrix}1&4&3 \\\ 0&-5&7\end{bmatrix}^T=\begin{bmatrix}1&0 \\\ 4&-5 \\\ 3&7\end{bmatrix}$$
<br>
$$c(\boldsymbol{A}^T) = c(\boldsymbol{A})^T$$


<br><br>


<font color=DarkCyan face=Georgia>***2.3、加（减）法***</font>：
- $m \times n$ 矩阵 $\boldsymbol{A}$ 和 $\boldsymbol{B}$ 的加（减）：$\boldsymbol{A} \pm \boldsymbol{B} = \boldsymbol{C}$ 为一个 $m\times n$ 矩阵，其中 $\boldsymbol{C}$ 中的元素是 $\boldsymbol{A}$ 和 $\boldsymbol{B}$ 相应元素的加（减）：$c_{ij} = a_{ij} + b_{ij}$，$1 \leq i \leq m$，$1 \leq j \leq n$。
$$\begin{bmatrix}1&3&1 \\\ 1&0&0\end{bmatrix}+\begin{bmatrix}1&0&5 \\\ 7&5&0\end{bmatrix}=\begin{bmatrix}1+1&3+0&1+5 \\\ 1+7&0+5&0+1\end{bmatrix}=\begin{bmatrix}2&3&6 \\\ 8&5&0\end{bmatrix}$$
<br>
$$\boldsymbol{A} + \boldsymbol{B} = \boldsymbol{B} + \boldsymbol{A}$$
$$(\boldsymbol{A} + \boldsymbol{B})^T = \boldsymbol{A}^T + \boldsymbol{B}^T$$
$$c(\boldsymbol{A} + \boldsymbol{B}) = c\boldsymbol{A} + c\boldsymbol{B}$$















