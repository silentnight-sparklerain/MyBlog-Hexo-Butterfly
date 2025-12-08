---
title: 线性代数
categories:
  - Study
  - Math
comments: true
description: 线性代数笔记
mathjax: false
katex: true
highlight_shrink: true
swiper_index: 10
cover: /img/posts/linear_algebra.jpg
abbrlink: c23efd5b
date: 2025-11-24 00:00:00
updated: 2025-11-24 00:00:00
keywords:
top_img:
aside:
aplayer:
---


笔记是根据MIT18.06线性代数课程所记，若要了解更多详情，请参考Gilbert Strang教授的《线性代数导论》教材与网课[MIT 18.06](https://www.bilibili.com/video/BV1rH4y1N7BW/?spm_id_from=333.1007.top_right_bar_window_custom_collection.content.click&vd_source=9c38c1da8942e504cacc7af7904ed6a4)

## 第1章 向量导论

**1. 向量的点积（内积）**
向量 $\vec{v}=(v_1, v_2)$ 与 $\vec{w}=(w_1, w_2)$ 的点积或内积记为：
$$ \vec{v} \cdot \vec{w} = v_1w_1 + v_2w_2 $$

**2. n维向量 $\vec{v}$ 的长度 $||\vec{v}||$**
等于 $\vec{v} \cdot \vec{v}$ 的算术平方根：
$$ ||\vec{v}|| = \sqrt{\vec{v} \cdot \vec{v}} = (v_1^2 + v_2^2 + \dots + v_n^2)^{\frac{1}{2}} $$

**3. 单位向量**
若向量 $\vec{u}$ 的长度为1，即 $\vec{u} \cdot \vec{u} = 1$，则称 $\vec{u}$ 为单位向量。
$$ \vec{u} = \frac{\vec{v}}{||\vec{v}||} \text{ 是与 } \vec{v} \text{ 同向的单位向量} $$

**4. 余弦公式**
若 $\vec{v}$ 与 $\vec{w}$ 为非零向量，则：
$$ \frac{\vec{v} \cdot \vec{w}}{||\vec{v}|| \cdot ||\vec{w}||} = \cos\theta $$

**5. 重要不等式**
*   **施瓦茨不等式 (Schwarz Inequality)：** $| \vec{v} \cdot \vec{w} | \leqslant ||\vec{v}|| \cdot ||\vec{w}||$
*   **三角不等式 (Triangle Inequality)：** $||\vec{v} + \vec{w}|| \leqslant ||\vec{v}|| + ||\vec{w}||$

**6. 矩阵与向量 $Ax=b$**
$$ Ax = \begin{bmatrix} 1 & 2 \\ 3 & 4 \\ 5 & 6 \end{bmatrix} \begin{bmatrix} x_1 \\ x_2 \end{bmatrix} $$
是矩阵 $A$ 列向量组的一个**线性组合**：
$$ Ax = x_1 \begin{bmatrix} 1 \\ 3 \\ 5 \end{bmatrix} + x_2 \begin{bmatrix} 2 \\ 4 \\ 6 \end{bmatrix} $$

*计算示例（逐行计算）：*
$$ Ax = \begin{bmatrix} 1 & 2 \\ 3 & 4 \\ 5 & 6 \end{bmatrix} \begin{bmatrix} 7 \\ 8 \end{bmatrix} = \begin{bmatrix} 1\times7 + 2\times8 \\ 3\times7 + 4\times8 \\ 5\times7 + 6\times8 \end{bmatrix} = \begin{bmatrix} 23 \\ 53 \\ 83 \end{bmatrix} $$

> **※ 核心概念：** 矩阵 $A$ 作用于向量 $x$，所得结果 $Ax$ 是矩阵 $A$ **所有列向量的线性组合**。

**7. 线性无关与线性相关**
*   **线性无关 (Linearly Independent)：** 除 $0\cdot\vec{u} + 0\cdot\vec{v} + 0\cdot\vec{w} = \vec{0}$ 外，没有其他线性组合能生成向量 $\vec{0}$。
*   **线性相关 (Linearly Dependent)：** 还有其他线性组合能够生成向量 $\vec{0}$，即存在不全为0的系数使得 $a\cdot\vec{u} + b\cdot\vec{v} + c\cdot\vec{w} = \vec{0}$。

**8. 可逆矩阵**
*   $A$ 的列向量组**线性无关**：$Ax=0$ 有唯一解，$A$ 是可逆矩阵。
*   $A$ 的列向量组**线性相关**：$Ax=0$ 有无穷多解，$A$ 是奇异矩阵（不可逆矩阵）。

---

## 第2章 线性方程组的求解

**1. 线性方程组与矩阵形式**
$$ \begin{cases} x - 2y = 1 \\ 3x + 2y = 11 \end{cases} \rightarrow \text{系数矩阵 } A = \begin{bmatrix} 1 & -2 \\ 3 & 2 \end{bmatrix} $$
矩阵方程 $Ax=b$：
$$ \begin{bmatrix} 1 & -2 \\ 3 & 2 \end{bmatrix} \begin{bmatrix} x \\ y \end{bmatrix} = \begin{bmatrix} 1 \\ 11 \end{bmatrix} $$

**2. 线性方程组矩阵形式的理解**
$$ Ax=b: \begin{bmatrix} 1 & 2 & 3 \\ 2 & 5 & 2 \\ 6 & -3 & 1 \end{bmatrix} \begin{bmatrix} x \\ y \\ z \end{bmatrix} = \begin{bmatrix} 6 \\ 4 \\ 2 \end{bmatrix} $$
**逐列相乘：**
$$ Ax = x\begin{bmatrix} 1 \\ 2 \\ 6 \end{bmatrix} + y\begin{bmatrix} 2 \\ 5 \\ -3 \end{bmatrix} + z\begin{bmatrix} 3 \\ 2 \\ 1 \end{bmatrix} = \begin{bmatrix} 6 \\ 4 \\ 2 \end{bmatrix} $$
> **核心思想：** 将 $Ax$ 看成矩阵 $A$ 的**列向量的线性组合**。

**3. 单位矩阵**
$$ I = \begin{bmatrix} 1 & 0 & 0 \\ 0 & 1 & 0 \\ 0 & 0 & 1 \end{bmatrix} \quad (\text{三阶单位矩阵}) $$
满足 $Ix = x$。

**4. 高斯消元法 (Gaussian Elimination)**
消元的目标是得到一个**上三角形矩阵 $U$**。

*示例：*
$$ Ax=b: \begin{bmatrix} 2 & 4 & -2 \\ 4 & 9 & -3 \\ -2 & -3 & 7 \end{bmatrix} \begin{bmatrix} x \\ y \\ z \end{bmatrix} = \begin{bmatrix} 2 \\ 8 \\ 10 \end{bmatrix} $$

1.  **第1行第1列的数 $a_{11}$ 为第一个主元**。
2.  第2行减去第1行的2倍；第3行减去第1行的-1倍。
    *   记录乘数：$l_{21}=2, l_{31}=-1$
    *   得到：$\begin{bmatrix} 2 & 4 & -2 \\ 0 & 1 & 1 \\ 0 & 1 & 5 \end{bmatrix} \dots \begin{bmatrix} 2 \\ 4 \\ 12 \end{bmatrix}$
3.  **第2行第2列的数 $a_{22}$ 为第二个主元**。
4.  第3行减去第2行的1倍。
    *   记录乘数：$l_{32}=1$
    *   得到：$\begin{bmatrix} 2 & 4 & -2 \\ 0 & 1 & 1 \\ 0 & 0 & 4 \end{bmatrix} \dots \begin{bmatrix} 2 \\ 4 \\ 8 \end{bmatrix}$
5.  **第3行第3列的数 $a_{33}$ 为第三个主元**。

化为上三角形矩阵 $Ux=c$。

**消元注意事项：**
*   消元过程中若出现主元为0的情况，则**交换行**得到非0主元。
*   若不存在非0主元，则消元中止。

**消元矩阵与 $A=LU$ 分解初步：**
上一个例子中，将所记录的乘数的相反数按下标填入单位矩阵，得到消元矩阵：
$$ E_{21} = \begin{bmatrix} 1 & 0 & 0 \\ -2 & 1 & 0 \\ 0 & 0 & 1 \end{bmatrix}, \quad E_{31} = \begin{bmatrix} 1 & 0 & 0 \\ 0 & 1 & 0 \\ 1 & 0 & 1 \end{bmatrix}, \quad E_{32} = \begin{bmatrix} 1 & 0 & 0 \\ 0 & 1 & 0 \\ 0 & -1 & 1 \end{bmatrix} $$
消元矩阵用于辅助消元与分解：$A=LU$
$$ E_{32} \cdot E_{31} \cdot E_{21} \cdot A = U $$

**5. 矩阵乘法**
*   **可乘条件：** 若 $A$ 有 $n$ 列，则 $B$ 必须有 $n$ 行。$A_{m\times n} \cdot B_{n\times p} = C_{m\times p}$
*   **基本法则：** $(AB)C = A(BC)$。注意：$AB=BA$ 一般不成立。

**矩阵乘法的四种理解：**
1.  **第1种理解（元素）：** $AB$ 第 $i$ 行第 $j$ 列的元素是 ($A$ 的第 $i$ 行) $\cdot$ ($B$ 的第 $j$ 列) —— (2个向量的乘积)。
2.  **第2种理解（左乘各列）：** $A$ 左乘 $B$ 的每一列。
    *   记 $B$ 的每一列为一个向量 $b_i$，即 $B = [b_1 \ b_2 \ \dots \ b_n]$
    *   $AB = A[b_1 \ b_2 \ \dots \ b_n] = [Ab_1 \ Ab_2 \ \dots \ Ab_n]$
    > **※ $AB$ 的每一列是 $B$ 的列向量的线性组合。**
3.  **第3种理解（各行左乘）：** $A$ 的每一行左乘 $B$。
    *   例：$A$ 的第1行 $\begin{bmatrix} 1 & 2 & 3 \end{bmatrix}$ 乘 $B = \begin{bmatrix} 1 & 2 & 3 \\ 4 & 5 & 6 \\ 7 & 8 & 9 \end{bmatrix}$
    *   $1 \cdot [1\ 2\ 3] + 2 \cdot [4\ 5\ 6] + 3 \cdot [7\ 8\ 9] = [30\ 36\ 42]$ ($AB$ 的第1行)
4.  **第4种理解（列左乘行）：**
    $$ AB = [\text{第1列}](\text{第1行}) + [\text{第2列}](\text{第2行}) + \dots + [\text{第n列}](\text{第n行}) $$
    $$ = (\text{第1列})(\text{第1行}) + (\text{第2列})(\text{第2行}) + (\text{第3列})(\text{第3行}) $$
    *   **例子**：
        $$ \begin{bmatrix} a & b \\ c & d \end{bmatrix} \begin{bmatrix} E & F \\ G & H \end{bmatrix} = \begin{bmatrix} a \\ c \end{bmatrix} \begin{bmatrix} E & F \end{bmatrix} + \begin{bmatrix} b \\ d \end{bmatrix} \begin{bmatrix} G & H \end{bmatrix} $$
        $$ = \begin{bmatrix} aE & aF \\ cE & cF \end{bmatrix} + \begin{bmatrix} bG & bH \\ dG & dH \end{bmatrix} = \begin{bmatrix} aE+bG & aF+bH \\ cE+dG & cF+dH \end{bmatrix} $$
    *   **总结**：$A$ 的列左乘 $B$ 的行，再求和。

**6. 置换矩阵 (Permutation Matrix)**
用于交换矩阵中的部分行。
例：$P_{23} = \begin{bmatrix} 1 & 0 & 0 \\ 0 & 0 & 1 \\ 0 & 1 & 0 \end{bmatrix}$ 用于交换矩阵的第2行与第3行。
$$ P_{23} \cdot A = \begin{bmatrix} 1 & 0 & 0 \\ 0 & 0 & 1 \\ 0 & 1 & 0 \end{bmatrix} \begin{bmatrix} 2 & 4 & 1 \\ 0 & 0 & 3 \\ 0 & 6 & 5 \end{bmatrix} = \begin{bmatrix} 2 & 4 & 1 \\ 0 & 6 & 5 \\ 0 & 0 & 3 \end{bmatrix} $$

**7. 增广矩阵 (Augmented Matrix)**
$$ Ax=b \implies \text{增广矩阵 } [A \ b] = \begin{bmatrix} 2 & 4 & -2 & 2 \\ 4 & 9 & -3 & 8 \\ -2 & -3 & 7 & 10 \end{bmatrix} $$

**8. 逆矩阵 (Inverse Matrix)**
*   **前提：** $A$ 为方阵。
*   **条件：** 行列式 $\det A \neq 0 \iff n\times n$ 矩阵 $A$ 有 $n$ 个主元 $\iff A$ 的 $n$ 个列向量线性无关。
*   **结论：** 若 $A$ 可逆，则 $A \cdot A^{-1} = I$ 且 $A^{-1} \cdot A = I$ （双边可逆）。
*   **性质：**
    1.  设存在非零向量 $x$ 使 $Ax=0$，则 $A$ 不可逆（线性相关）。
    2.  若 $A$ 与 $B$ 同阶可逆，则 $AB$ 可逆且 $(AB)^{-1} = B^{-1} \cdot A^{-1}$ (**逆序相乘**)。
    3.  若矩阵 $A$ 可逆，则逆矩阵唯一。
    4.  若矩阵 $A$ 可逆，则方程组 $Ax=b$ 有唯一解 $x = A^{-1}b$。
    5.  当主对角线上的元素都不为0时，对角矩阵可逆。

*   **计算方法**：用消元法将 $[K \ I]$ 变为 $[I \ K^{-1}]$。
*   **例**：
    $$ [K \ I] = \left[ \begin{array}{ccc|ccc} 2 & -1 & 0 & 1 & 0 & 0 \\ -1 & 2 & -1 & 0 & 1 & 0 \\ 0 & -1 & 2 & 0 & 0 & 1 \end{array} \right] \xrightarrow{\text{消元}} \left[ \begin{array}{ccc|ccc} 2 & -1 & 0 & 1 & 0 & 0 \\ 0 & \frac{3}{2} & -1 & \frac{1}{2} & 1 & 0 \\ 0 & -1 & 2 & 0 & 0 & 1 \end{array} \right] $$
    $$ \xrightarrow{\text{继续消元}} \left[ \begin{array}{ccc|ccc} 2 & -1 & 0 & 1 & 0 & 0 \\ 0 & \frac{3}{2} & -1 & \frac{1}{2} & 1 & 0 \\ 0 & 0 & \frac{4}{3} & \frac{1}{3} & \frac{2}{3} & 1 \end{array} \right] \xrightarrow[\text{变为单位阵I}]{\text{向上回代}} \left[ \begin{array}{ccc|ccc} 1 & 0 & 0 & \frac{3}{4} & \frac{1}{2} & \frac{1}{4} \\ 0 & 1 & 0 & \frac{1}{2} & 1 & \frac{1}{2} \\ 0 & 0 & 1 & \frac{1}{4} & \frac{1}{2} & \frac{3}{4} \end{array} \right] = [I \ K^{-1}] $$

**9. $A=LU$ 分解**
$L$ 为下三角矩阵 (Lower triangular)，$U$ 为上三角矩阵 (Upper triangular)。
使用第4点所举的例子：$E_{32} \cdot E_{31} \cdot E_{21} \cdot A = U$
$E_{32}, E_{31}, E_{21}$ 可逆，则 $A = E_{21}^{-1} \cdot E_{31}^{-1} \cdot E_{32}^{-1} \cdot U$。
记 $L = E_{21}^{-1} \cdot E_{31}^{-1} \cdot E_{32}^{-1}$。

那么 $A=LU$：
$$ \begin{bmatrix} 2 & 4 & -2 \\ 4 & 9 & -3 \\ -2 & -3 & 7 \end{bmatrix} = \begin{bmatrix} 1 & 0 & 0 \\ 2 & 1 & 0 \\ -1 & 1 & 1 \end{bmatrix} \begin{bmatrix} 2 & 4 & -2 \\ 0 & 1 & 1 \\ 0 & 0 & 4 \end{bmatrix} $$

> **观察 L：** 就是将所记录的乘数填入同一个单位矩阵中（$l_{21}=2, l_{31}=-1, l_{32}=1$）。
> 乘数 $l_{ij}$ 都在 $L$ 的主对角线下方，$L$ 的主对角线元素全为1。

**10. 转置 (Transpose)**
$$ A^T(i, j) = A(j, i) $$
$A^T$ 的第 $i$ 行第 $j$ 列元素 = $A$ 的第 $j$ 行第 $i$ 列元素。

*   **性质：**
    *   $(A+B)^T = A^T + B^T$
    *   $(AB)^T = B^T A^T$
    *   $(A^{-1})^T = (A^T)^{-1}$
*   **对称矩阵：** $A^T = A$
*   **置换矩阵满足：** $P^{-1} = P^T$

---


## 第3章 向量空间与子空间

**1. 标准 n 维空间 $\mathbb{R}^n$**
是具有 $n$ 个分量的实列向量的全体。

**2. 封闭性**
若 $\vec{v}$ 与 $\vec{w}$ 在向量空间 $S$ 中，则每个线性组合 $c\vec{v} + d\vec{w}$ 也必在 $S$ 中。

**3. 单点空间 $Z$**
只包含 $\vec{x} = \vec{0}$。

**4. 直观理解**
*   向量空间 $\mathbb{R}^2$ 由通常的二维平面表示。$\mathbb{R}^2$ 中每个向量 $\vec{v}$ 有2个分量，即 $\vec{v} = (x, y)$。
*   $\mathbb{R}^3$ 中的向量对应三维空间中的点 $(x, y, z)$。

**5. 子空间 (Subspace)**
向量空间的子空间是指满足以下两个条件的向量（包括 $\vec{0}$）的集合：
若 $\vec{v}$ 和 $\vec{w}$ 都是子空间中的向量，$c$ 为任意标量，则有：
*   (i) $\vec{v} + \vec{w}$ 在子空间中（加法封闭）
*   (ii) $c\vec{v}$ 在子空间中（数乘封闭）

> **直观理解：** 三维空间 $\mathbb{R}^3$ 中选取一个**过原点 $(0,0,0)$ 的平面**。该平面就自身而言是一个向量空间。但该平面并非 $\mathbb{R}^2$：该平面中的向量均有三个分量，因而属于 $\mathbb{R}^3$，这个平面是 $\mathbb{R}^3$ 内的一个子空间。

**6. 每个子空间均含零向量**
子空间内向量的所有线性组合都包含在子空间中。

**7. $A$ 的列空间 (Column Space)**
矩阵 $A$ 的列空间 $C(A)$ 包含 $A$ 各列的全部线性组合。这些线性组合是所有可能的向量 $Ax$，它们充满列空间 $C(A)$。

> **※ 核心点：** 解 $Ax=b$ 就是将 $b$ 表示为 $A$ 各列的一个线性组合。
> 线性方程组 $Ax=b$ 是可解的，当且仅当 $b$ 在 $A$ 的列空间内。

*   设 $A$ 为 $m \times n$ 矩阵，它的列向量有 $m$ 个分量，故各列向量属于 $\mathbb{R}^m$。
*   $A$ 的列空间是 $\mathbb{R}^m$ 的子空间。

**8. $A$ 的零空间 (Null Space)**
零空间 $N(A)$ 由 $Ax=0$ 的**全部解**构成，这些解向量 $x$ 均在 $\mathbb{R}^n$ 中。
*   消元法不改变零空间：$N(A) = N(U) = N(R)$
*   **强调：** 解向量 $x$ 有 $n$ 个分量，这些向量都在 $\mathbb{R}^n$ 中，因此 $N(A)$ 是 $\mathbb{R}^n$ 的子空间。

**9. 主元列与自由列**
$$ Ax=0 \quad A = \begin{bmatrix} 1 & 2 & 2 & 4 \\ 3 & 8 & 6 & 16 \end{bmatrix} \xrightarrow{\text{高斯消元}} U = \begin{bmatrix} 1 & 2 & 2 & 4 \\ 0 & 2 & 0 & 4 \end{bmatrix} $$
*   含主元的列是**主元列**（第1、2列）。
*   不含主元的列是**自由列**（第3、4列）。

解向量 $x$ 有4个分量 $\vec{x} = (x_1, x_2, x_3, x_4)$：
$$ Ux = x_1\begin{bmatrix} 1 \\ 0 \end{bmatrix} + x_2\begin{bmatrix} 2 \\ 2 \end{bmatrix} + x_3\begin{bmatrix} 2 \\ 0 \end{bmatrix} + x_4\begin{bmatrix} 4 \\ 4 \end{bmatrix} $$
*   $x_1, x_2$ 为主元变量。
*   $x_3, x_4$ 为自由变量。

对于自由变量 $x_3$ 与 $x_4$，轮流取值 1 和 0：
*   令 $x_3=1, x_4=0 \implies x = \begin{bmatrix} -2 \\ 0 \\ 1 \\ 0 \end{bmatrix}$
*   令 $x_3=0, x_4=1 \implies x = \begin{bmatrix} 2 \\ -2 \\ 0 \\ 1 \end{bmatrix}$
*   $A$ 的零空间得到 2 个解。

**10. 最简行阶梯形矩阵 R (Reduced Row Echelon Form)**
$$ A = \begin{bmatrix} 1 & 2 & 2 & 4 \\ 3 & 8 & 6 & 16 \end{bmatrix} \xrightarrow{\text{消元}} U = \begin{bmatrix} 1 & 2 & 2 & 4 \\ 0 & 2 & 0 & 4 \end{bmatrix} \xrightarrow{\text{向上消元并单位化}} R = \begin{bmatrix} 1 & 0 & 2 & 0 \\ 0 & 1 & 0 & 2 \end{bmatrix} $$

举例：
$$ R = \begin{bmatrix} 1 & 0 & \times & \times & 0 & \times \\ 0 & 1 & \times & \times & 0 & \times \\ 0 & 0 & 0 & 0 & 1 & \times \\ 0 & 0 & 0 & 0 & 0 & 0 \end{bmatrix} \quad (\times \text{可表示任意实数}) $$
对于 $Rx=0$，$\vec{x} = (x_1, x_2, x_3, x_4, x_5, x_6, x_7)$
*   三个主元变量：$x_1, x_2, x_6$ (对应列有主元1)
*   四个自由变量：$x_3, x_4, x_5, x_7$
*   设定一个自由变量取1，其余自由变量取0，可得到 $Rx=0$ 的解向量。

**11. 矩阵的秩 (Rank)**
*   $A$ 的秩为主元的个数，记为 $\text{rank}(A) = r$。
*   $\text{rank}(A) = \text{rank}(U) = \text{rank}(R)$
*   **第二种理解：** $A, U, R$ 有 $r$ 个线性无关的行，有 $r$ 个线性无关的列。
*   **第三种理解：** $A$ 的秩 $r$ 是列空间 $C(A)$ 的维数，$n-r$ 是零空间 $N(A)$ 的维数。


**12. $Ax=b$ 的全解**
*   **※ 核心理解：** $Ax=b$ 的全解 $x = \text{特解 } x_p + \text{零空间中任意元素 } x_n$
*   下标理解：$x = x_{\text{particular}} + x_{\text{nullspace}}$
*   原因：$Ax_p = b, Ax_n = 0 \implies A(x_p + c x_n) = b$ ($c$为任意常数)。
*   **解 $Ax=b$ 的步骤：** 求出 $x_p, x_n$，相加即为 $x$。

**求解 $Ax_n=0$:**
用消元法将 $Ax=0$ 化为 $Rx=0$，再对自由变量赋值1和0计算特殊解。
例：$A = \begin{bmatrix} 1 & 3 & 0 & 2 \\ 0 & 0 & 1 & 4 \\ 1 & 3 & 1 & 6 \end{bmatrix} \xrightarrow{\text{消元}} \begin{bmatrix} 1 & 3 & 0 & 2 \\ 0 & 0 & 1 & 4 \\ 0 & 0 & 0 & 0 \end{bmatrix}$
*   $x_1, x_3$ 为主元变量，$x_2, x_4$ 为自由变量。
*   令 $x_2=1, x_4=0 \implies \vec{x}_1 = \begin{bmatrix} -3 \\ 1 \\ 0 \\ 0 \end{bmatrix}$
*   令 $x_2=0, x_4=1 \implies \vec{x}_2 = \begin{bmatrix} -2 \\ 0 \\ -4 \\ 1 \end{bmatrix}$
*   则 $A$ 的零空间可表示为 $x_n = C_1 \begin{bmatrix} -3 \\ 1 \\ 0 \\ 0 \end{bmatrix} + C_2 \begin{bmatrix} -2 \\ 0 \\ -4 \\ 1 \end{bmatrix}$ ($C_1, C_2$ 为任意常数)。

**求解 $Ax_p=b$:**
消元过程中作用于 $A$ 的行变换也会作用于 $b$，因此使用**增广矩阵**便于消元。
$$ [A \ b] = \begin{bmatrix} 1 & 3 & 0 & 2 & 1 \\ 0 & 0 & 1 & 4 & 6 \\ 1 & 3 & 1 & 6 & 7 \end{bmatrix} $$
消元后得到：$[R \ d] = \begin{bmatrix} 1 & 3 & 0 & 2 & 1 \\ 0 & 0 & 1 & 4 & 6 \\ 0 & 0 & 0 & 0 & 0 \end{bmatrix}$
$Rx_p=d \implies \begin{cases} x_1 + 3x_2 + 2x_4 = 1 \\ x_3 + 4x_4 = 6 \end{cases}$
为了得到一个简单的解 $x_p$，令自由变量取值为0，即 $x_2=x_4=0$。
解出 $x_1=1, x_3=6$。从而得到一个特解 $x_p = (1, 0, 6, 0)$。

因此，$Ax=b$ 的全解：
$$ x = x_p + x_n = \begin{bmatrix} 1 \\ 0 \\ 6 \\ 0 \end{bmatrix} + C_1 \begin{bmatrix} -3 \\ 1 \\ 0 \\ 0 \end{bmatrix} + C_2 \begin{bmatrix} -2 \\ 0 \\ -4 \\ 1 \end{bmatrix} $$
**总结：** $x_p$ 满足 $Ax_p=b$，$x_n$ 满足 $Ax_n=0$，$x=x_p+x_n$。$x_n$ 是 $n-r$ 个特殊解的线性组合。

**13. 列满秩**
$m \times n$ 矩阵 $A$ 的秩等于列数，即 $r=n$。
**性质：**
1.  $A$ 的各列均为主元列。
2.  没有自由变量或特殊解。
3.  零空间 $N(A)$ 只有 $\vec{x}=\vec{0}$。
4.  若 $Ax=b$ 有解（$Ax=b$ 可能无解），则只有**唯一解**。
    *   即：矩阵 $A$ 的各列线性无关。

**14. 行满秩**
$m \times n$ 矩阵 $A$ 的秩等于行数，即 $r=m$。
**性质：**
1.  各行均有主元，$R$ 没有全0行。
2.  对于任意常数项 $b$，方程组 $Ax=b$ **均有解**。
3.  列空间为整个 $\mathbb{R}^m$ 空间。
4.  $A$ 的零空间 $N(A)$ 包含 $n-r = n-m$ 个特殊解。

**15. 线性方程组根据系数矩阵的秩 $r$ 分为4种情形**
1.  $r=m=n$：$A$ 为可逆矩阵，$Ax=b$ 有唯一解。
2.  $r=m<n$：$A$ 为矮宽形矩阵，$Ax=b$ 有无穷多解。
3.  $r=n<m$：$A$ 为高瘦形矩阵，$Ax=b$ 无解或有唯一解。
4.  $r<m, r<n$：$A$ 不是满秩矩阵，$Ax=b$ 无解或有无穷多解。

**16. 线性无关**
$A$ 的各列线性无关等价于 $Ax=0$ 有唯一解 $x=0$，即零空间为 $Z$。
向量 $v_1, v_2, \dots, v_k$ 线性无关是指满足 $c_1v_1 + c_2v_2 + \dots + c_kv_k = 0$ 的系数 $c_1, c_2, \dots, c_k$ 只能取 0。

**17. 生成空间**
一组向量生成一个空间是指这些向量的线性组合充满整个空间。

**18. 行空间**
$m \times n$ 矩阵 $A$ 的行空间是 $\mathbb{R}^n$ 的子空间，它由各行所生成。
$A$ 的行空间等于 $A^T$ 的列空间，即 $C(A^T)$。

**19. 向量空间的基 (Basis)**
定义：向量空间的基是具有以下两条性质的一组向量：
1.  基向量**线性无关**。
2.  且**生成整个空间**。

> **理解：**
> *   2个三维向量即使线性无关，也不可能生成整个 $\mathbb{R}^3$。
> *   4个三维向量即使能生成 $\mathbb{R}^3$，也不可能线性无关。
> *   $\mathbb{R}^3$ 的一组基是3个线性无关的三维向量。

**20. 基的性质**
当一组向量 $v_1, v_2, \dots, v_n$ 正好是 $n \times n$ 可逆矩阵的列时，它们是 $\mathbb{R}^n$ 的一组基。
因此 $\mathbb{R}^n$ 中有无穷多组不同的基。

**21. 矩阵空间的基**
*   矩阵 $A$ 的**主元列**是列空间的一组基。
*   $A$ 的**主元行**是行空间的一组基。

**22. $A$ 与 $R$ 的关系**
$A$ 与 $R$ 列空间不相同，但**行空间相同**。

**23. 向量空间的维数**
向量空间 $V$ 的维数 $\dim(V)$ 是每组基中**向量的个数**。

**24. 四个基本子空间**
1.  $\mathbb{R}^n$ 的一个子空间：行空间 $C(A^T)$，维数为 $r$。
2.  $\mathbb{R}^m$ 的一个子空间：列空间 $C(A)$，维数为 $r$。
3.  $\mathbb{R}^n$ 的一个子空间：零空间 $N(A)$，维数为 $n-r$。
4.  $\mathbb{R}^m$ 的一个子空间：左零空间 $N(A^T)$，维数为 $m-r$。

*例：*
$$ R = \begin{bmatrix} 1 & 3 & 5 & 0 & 7 \\ 0 & 0 & 0 & 1 & 2 \\ 0 & 0 & 0 & 0 & 0 \end{bmatrix} $$
*   $m=3, n=5, r=2$。
*   主元行是 1, 2 行；主元列是 1, 4 列。
*   第 2, 3, 5 列为自由列，则 $Ax=b$ 有三个特殊解，$\dim N(A) = 5-2 = 3$。
*   同理，第 3 行为自由行，$\dim N(A^T) = 3-2 = 1$。

**25. 维数总结**
*   $A$ 的列空间的维数与行空间的维数都是 $r$。
*   **列秩 = 行秩**。
*   线性无关列的列数 = 线性无关行的行数。

---


## 第4章 正交性

**1. 向量点积**
当2个向量 $\vec{v}, \vec{w}$ 的点积为 0，即 $\vec{v} \cdot \vec{w} = v^T w = 0$ 时，称这两个向量正交（垂直）。

**2. 子空间的正交**
同一向量空间的两子空间 $V$ 与 $W$ 正交是指：$V$ 中任意向量 $\vec{v}$ 与 $W$ 中任意向量 $\vec{w}$ 垂直。
$$ v^T w = 0, \quad \forall \vec{v} \in V, \vec{w} \in W $$

**3. 四个基本子空间的正交关系**
对于 $A x = 0$：
*   **零空间 $N(A)$ 与 行空间 $C(A^T)$** 是 $\mathbb{R}^n$ 中的正交子空间。（零空间中的每个向量垂直于 $A$ 的每一行）。
*   **列空间 $C(A)$ 与 左零空间 $N(A^T)$** 是 $\mathbb{R}^m$ 中的正交子空间。（$A^T$ 的零空间中每个向量垂直于 $A$ 的每一列）。

**4. 正交补 (Orthogonal Complement)**
子空间 $V$ 的正交补是指垂直于 $V$ 的全体向量构成的子空间。$V$ 的这个正交子空间记作 $V^\perp$。

**5. 维数关系**
对 $m \times n$ 矩阵 $A$：
*   零空间 $N(A)$ 是行空间 $C(A^T)$ 的正交补（在 $\mathbb{R}^n$ 中）。
    $$ n = \dim N(A) + \dim C(A^T) $$
*   左零空间 $N(A^T)$ 是列空间 $C(A)$ 的正交补（在 $\mathbb{R}^m$ 中）。
    $$ m = \dim N(A^T) + \dim C(A) $$

**6. 投影 (Projection)**
将 $\vec{b}$ 投影到直线上，它的投影 $\vec{p}$ 是 $\vec{b}$ 分解到该直线方向上的部分。
如果将 $\vec{b}$ 投影到平面上，投影 $\vec{p}$ 是 $\vec{b}$ 分解到该平面上的部分。
$$ \vec{p} = P\vec{b} \quad (P \text{ 为投影矩阵}) $$

**7. 到直线上的投影**
现有一直线沿着 $\vec{a} = (a_1, a_2, \dots, a_m)$ 方向且过原点，求该直线上距离点 $\vec{b}=(b_1, \dots, b_m)$ 最近的点 $\vec{p}$（即 $\vec{b}$ 的投影）。

*   设 $\vec{p} = \hat{x}\vec{a}$ ($\hat{x}$ 是一个数，投影 $\vec{p}$ 是 $\vec{a}$ 的倍数)。
*   误差 $\vec{e} = \vec{b} - \vec{p}$。
*   利用正交性：$\vec{a} \cdot \vec{e} = 0 \implies \vec{a} \cdot (\vec{b} - \hat{x}\vec{a}) = 0$。
*   解得：$\hat{x} = \frac{\vec{a}^T \vec{b}}{\vec{a}^T \vec{a}}$。
*   投影向量：$\vec{p} = \hat{x}\vec{a} = \frac{\vec{a}^T \vec{b}}{\vec{a}^T \vec{a}} \vec{a}$。
*   投影矩阵：$\vec{p} = P\vec{b} = \frac{\vec{a} \vec{a}^T}{\vec{a}^T \vec{a}} \vec{b} \implies P = \frac{\vec{a} \vec{a}^T}{\vec{a}^T \vec{a}}$。

![图4-7](/img/post_article/线性代数/Chapter4.7.png)

**8. 到子空间上的投影**
问题：求出与给定向量 $\vec{b}$ 距离最近的线性组合 $\vec{p} = \hat{x}_1\vec{a}_1 + \hat{x}_2\vec{a}_2 + \dots + \hat{x}_n\vec{a}_n$。
相当于将 $\mathbb{R}^m$ 中的任意向量 $\vec{b}$ 投影到 $\vec{a}_1, \dots, \vec{a}_n$ 所生成的子空间中。

设 $m \times n$ 矩阵 $A$ 有 $n$ 列 $\vec{a}_1, \dots, \vec{a}_n$。
误差 $\vec{e} = \vec{b} - \vec{p} = \vec{b} - A\hat{x}$。
根据正交性，误差垂直于子空间中的每一个基向量：
$$ \begin{cases} a_1^T(b - A\hat{x}) = 0 \\ \vdots \\ a_n^T(b - A\hat{x}) = 0 \end{cases} \implies A^T(b - A\hat{x}) = 0 $$
$$ \implies A^T b - A^T A \hat{x} = 0 \implies A^T A \hat{x} = A^T b $$
$$ \hat{x} = (A^T A)^{-1} A^T b $$
$$ \vec{p} = A\hat{x} = A(A^T A)^{-1} A^T b $$

**9. 投影矩阵 P**
$$ P = A(A^T A)^{-1} A^T $$
性质：
1.  $P^T = P$ (对称矩阵)
2.  $P^2 = P$ (幂等矩阵)
3.  $P\vec{b} = \vec{p}$

**10. 最小二乘估计 (Least Squares)**
当 $Ax=b$ 无解时，用 $A^T$ 左乘两边并求解 $A^T A \hat{x} = A^T b$。
得到的 $\hat{x}$ 为与 $x$ 最接近的向量（使得误差平方和 $E = ||Ax-b||^2$ 最小）。

**11. 正交矩阵 Q**
如果向量组 $\vec{q}_1, \vec{q}_2, \dots, \vec{q}_n$ 满足：
$$ \vec{q}_i \cdot \vec{q}_j = \begin{cases} 0 & i \neq j \text{ (正交向量)} \\ 1 & i = j \text{ (单位向量)} \end{cases} $$
则 $\vec{q}_1, \dots, \vec{q}_n$ 是**标准正交向量组**。

令 $Q = [\vec{q}_1 \ \vec{q}_2 \ \dots \ \vec{q}_n]$，有 $Q^T Q = I$。($Q$ 不一定是方阵)
当 $Q$ 为方阵时，$Q^T Q = I \implies Q^T = Q^{-1}$，此时称 $Q$ 为**正交矩阵**。

**12. 每个置换矩阵都是正交矩阵**

**13. Q 的性质**
*   $Q$ 作用于向量时，保持向量的长度不变，即 $||Qx|| = ||x||$。
*   $Q$ 也能保持2个向量的内积不变 $(Qx)^T \cdot (Qy) = x^T y$。

**14. 利用标准正交基投影**
$Q$ 取代 $A$（假设基向量恰好是标准正交的）。
$A^T A$ 简化为 $Q^T Q = I$。
$$ P = Q(Q^T Q)^{-1} Q^T = Q Q^T $$
$$ \vec{p} = Q\hat{x} = Q Q^T \vec{b} $$

**15. 格拉姆-施密特方法 (Gram-Schmidt Process)**
三个线性无关向量 $\vec{a}, \vec{b}, \vec{c}$。计划构造三个正交向量 $\vec{A}, \vec{B}, \vec{C}$，然后归一化生成三个标准正交向量 $\vec{q}_1, \vec{q}_2, \vec{q}_3$。

1.  **选定 $\vec{A}$ 为 $\vec{a}$ 的方向**：$\vec{A} = \vec{a}$
2.  **$\vec{b}$ 投影到 $\vec{A}$ 为 $\vec{p}_1$，则 $\vec{B} = \vec{b} - \vec{p}_1$**
    核心思想：利用 $\vec{e} = \vec{b} - \vec{p}$，其中误差 $\vec{e}$ 与 $\vec{a}$ 正交。
    $$ \vec{p}_1 = \frac{\vec{A}^T \vec{b}}{\vec{A}^T \vec{A}} \vec{A} \implies \vec{B} = \vec{b} - \frac{\vec{A}^T \vec{b}}{\vec{A}^T \vec{A}} \vec{A} $$
3.  **$\vec{c}$ 投影到 $\vec{A}\vec{B}$ 的平面为 $\vec{p}_2$，则 $\vec{C} = \vec{c} - \vec{p}_2$**
    $$ \vec{p}_2 = \frac{\vec{A}^T \vec{c}}{\vec{A}^T \vec{A}} \vec{A} + \frac{\vec{B}^T \vec{c}}{\vec{B}^T \vec{B}} \vec{B} $$
    $$ \vec{C} = \vec{c} - \left( \frac{\vec{A}^T \vec{c}}{\vec{A}^T \vec{A}} \vec{A} + \frac{\vec{B}^T \vec{c}}{\vec{B}^T \vec{B}} \vec{B} \right) $$
4.  **单位化：**
    $$ \vec{q}_1 = \frac{\vec{A}}{||\vec{A}||}, \quad \vec{q}_2 = \frac{\vec{B}}{||\vec{B}||}, \quad \vec{q}_3 = \frac{\vec{C}}{||\vec{C}||} $$

---


## 第5章 行列式

**1. 三条基本性质**
1.  $\det I = 1$，n阶单位矩阵的行列式是 1。
2.  互换两行时行列式改变正负号。
3.  行列式对单独的每一行是一个线性函数（其他行固定不变）。
    *   $\begin{vmatrix} ka & kb \\ c & d \end{vmatrix} = k \begin{vmatrix} a & b \\ c & d \end{vmatrix}$
    *   $\begin{vmatrix} a+a' & b+b' \\ c & d \end{vmatrix} = \begin{vmatrix} a & b \\ c & d \end{vmatrix} + \begin{vmatrix} a' & b' \\ c & d \end{vmatrix}$

**2. 七条拓展性质**
4.  若 $A$ 中有2行元素对应相等，则 $\det A = 0$。
5.  从一行中减去另一行的倍数，行列式保持不变（消元操作）。
6.  若方阵 $A$ 某一行元素全为零，则 $\det A = 0$。
7.  若 $A = (a_{ij})_{n \times n}$ 是一个三角形矩阵，则 $\det A = a_{11} \cdot a_{22} \cdots a_{nn}$，为主对角线上元素的乘积。
8.  若 $A$ 为奇异（不可逆）矩阵，则 $\det A = 0$。若 $A$ 为可逆矩阵，则 $\det A \neq 0$。
9.  $|AB| = |A| \cdot |B|$。
10. $\det A = \det A^T$（转置行列式不变）。

**3. 主元公式**
利用消元分解得到 $A = LU$。
$\det A = \det L \cdot \det U = \det U$ (因为 $\det L = 1$)。
消元过程可能存在换行，$\det A = \pm d_1 \cdot d_2 \cdots d_n$ (主元乘积，符号取决于换行次数)。

**4. 计算行列式的基础公式**
*   二阶：$\begin{vmatrix} a & b \\ c & d \end{vmatrix} = ad - bc$
*   三阶展开：
    $$ \begin{vmatrix} a_{11} & a_{12} & a_{13} \\ a_{21} & a_{22} & a_{23} \\ a_{31} & a_{32} & a_{33} \end{vmatrix} = a_{11}a_{22}a_{33} + a_{12}a_{23}a_{31} + a_{13}a_{21}a_{32} - a_{11}a_{23}a_{32} - a_{12}a_{21}a_{33} - a_{13}a_{22}a_{31} $$
    (n阶行列式展开有 $n!$ 项，其中一半是正号，一半是负号)。

**5. 利用代数余子式计算行列式**
三阶行列式：
$$ |A| = a_{11}(a_{22}a_{33} - a_{23}a_{32}) + a_{12}(a_{23}a_{31} - a_{21}a_{33}) + a_{13}(a_{21}a_{32} - a_{22}a_{31}) $$
括号中的三组式子称“代数余子式”，是由第2行、第3行元素构成的二阶行列式。
记 $C_{11} = a_{22}a_{33} - a_{23}a_{32}$， $C_{12} = a_{23}a_{31} - a_{21}a_{33}$， $C_{13} = a_{21}a_{32} - a_{22}a_{31}$
$$ |A| = a_{11}C_{11} + a_{12}C_{12} + a_{13}C_{13} $$

直观理解：
$$ \begin{vmatrix} a_{11} & a_{12} & a_{13} \\ a_{21} & a_{22} & a_{23} \\ a_{31} & a_{32} & a_{33} \end{vmatrix} = \begin{vmatrix} a_{11} & 0 & 0 \\ a_{21} & a_{22} & a_{23} \\ a_{31} & a_{32} & a_{33} \end{vmatrix} + \begin{vmatrix} 0 & a_{12} & 0 \\ a_{21} & a_{22} & a_{23} \\ a_{31} & a_{32} & a_{33} \end{vmatrix} + \begin{vmatrix} 0 & 0 & a_{13} \\ a_{21} & a_{22} & a_{23} \\ a_{31} & a_{32} & a_{33} \end{vmatrix} $$
其中：
$$ C_{11} = \begin{vmatrix} a_{22} & a_{23} \\ a_{32} & a_{33} \end{vmatrix}, \quad C_{12} = - \begin{vmatrix} a_{21} & a_{23} \\ a_{31} & a_{33} \end{vmatrix}, \quad C_{13} = \begin{vmatrix} a_{21} & a_{22} \\ a_{31} & a_{32} \end{vmatrix} $$
$A$ 划去第 1 行和第 $j$ 列后得到 $n-1$ 阶子块 $M_{1j}$。
$$ \therefore C_{1j} = (-1)^{1+j} \det M_{1j} $$
$$ \det A = a_{11}C_{11} + a_{12}C_{12} + \dots + a_{1n}C_{1n} $$
对任意一行也都成立：
$$ C_{ij} = (-1)^{i+j} \det M_{ij} \quad (A \text{划去第} i \text{行和第} j \text{列后得到} n-1 \text{阶子块} M_{ij}) $$
$$ \det A = a_{i1}C_{i1} + a_{i2}C_{i2} + \dots + a_{in}C_{in} $$

**6. 克拉默法则 (Cramer's Rule)**
用于求解 $n \times n$ 方程组 $Ax=b$。

关键原理：构造矩阵 $B_j$，是将 $A$ 的第 $j$ 列换成向量 $b$ 所得的矩阵。

*   **以三阶为例**：
    $$ A \begin{bmatrix} x_1 & 0 & 0 \\ x_2 & 1 & 0 \\ x_3 & 0 & 1 \end{bmatrix} = \begin{bmatrix} b_1 & a_{12} & a_{13} \\ b_2 & a_{22} & a_{23} \\ b_3 & a_{32} & a_{33} \end{bmatrix} = B_1 $$
*   两边取行列式：
    $$ (\det A) \cdot x_1 = \det B_1 \implies x_1 = \frac{\det B_1}{\det A} $$
*   同理构造矩阵求 $x_2$：
    $$ A \begin{bmatrix} 1 & x_1 & 0 \\ 0 & x_2 & 0 \\ 0 & x_3 & 1 \end{bmatrix} = \begin{bmatrix} a_{11} & b_1 & a_{13} \\ a_{21} & b_2 & a_{23} \\ a_{31} & b_3 & a_{33} \end{bmatrix} = B_2 \implies x_2 = \frac{\det B_2}{\det A} $$

克拉默法则：若 $\det A \neq 0$，则：
$$ x_1 = \frac{\det B_1}{\det A}, \quad x_2 = \frac{\det B_2}{\det A}, \quad \dots, \quad x_n = \frac{\det B_n}{\det A} $$

**7. $n=3$ 时，利用求解 $Ax=(1,0,0)$ 来计算 $A^{-1}$ 中的元素**

$$ B_1 = \begin{vmatrix} 1 & a_{12} & a_{13} \\ 0 & a_{22} & a_{23} \\ 0 & a_{32} & a_{33} \end{vmatrix}, \quad B_2 = \begin{vmatrix} a_{11} & 1 & a_{13} \\ a_{21} & 0 & a_{23} \\ a_{31} & 0 & a_{33} \end{vmatrix}, \quad B_3 = \begin{vmatrix} a_{11} & a_{12} & 1 \\ a_{21} & a_{22} & 0 \\ a_{31} & a_{32} & 0 \end{vmatrix} $$
*   $B_i$ 的行列式为 $A$ 的代数余子式：
$$ |B_1| = C_{11} = a_{22}a_{33} - a_{23}a_{32} $$
$$ |B_2| = C_{12} $$
$$ |B_3| = C_{13} $$

*   结论：$A^{-1}$ 的 $(i,j)$ 元素是代数余子式 $C_{ji}$ (而非 $C_{ij}$) 除以 $\det A$
$$ (A^{-1})_{(i,j)} = \frac{C_{ji}}{\det A} \quad \therefore A^{-1} = \frac{C^T}{\det A} \quad A C^T = (\det A) \cdot I $$

直接证明：
$$ \begin{bmatrix} a_{11} & a_{12} & a_{13} \\ a_{21} & a_{22} & a_{23} \\ a_{31} & a_{32} & a_{33} \end{bmatrix} \begin{bmatrix} C_{11} & C_{21} & C_{31} \\ C_{12} & C_{22} & C_{32} \\ C_{13} & C_{23} & C_{33} \end{bmatrix} = \begin{bmatrix} \det A & 0 & 0 \\ 0 & \det A & 0 \\ 0 & 0 & \det A \end{bmatrix} \implies AC^T = (\det A) \cdot I $$

**8. 三角形的面积**
顶点是 $(x_1, y_1), (x_2, y_2), (x_3, y_3)$ 的三角形面积为 $\frac{1}{2} | \text{行列式} |$。
$$ S = \frac{1}{2} \left| \begin{matrix} x_1 & y_1 & 1 \\ x_2 & y_2 & 1 \\ x_3 & y_3 & 1 \end{matrix} \right| $$
(当 $(x_3, y_3) = (0,0)$ 时，$S = \frac{1}{2} |x_1 y_2 - x_2 y_1|$)。

**9. 平行六面体的体积**
由向量 $\vec{a}, \vec{b}, \vec{c}$ 构成的平行六面体。
$$ V = |\det A| $$
其中 $A$ 的行（或列）为这三个向量。

![图5-9](/img/post_article/线性代数/Chapter5.9.png)

**10. 叉积 (Cross Product)**
$\vec{u} = (u_1, u_2, u_3)$ 和 $\vec{v} = (v_1, v_2, v_3)$ 的叉积是向量 $\vec{u} \times \vec{v}$：
$$ \vec{u} \times \vec{v} = \begin{vmatrix} \vec{i} & \vec{j} & \vec{k} \\ u_1 & u_2 & u_3 \\ v_1 & v_2 & v_3 \end{vmatrix} = (u_2v_3 - u_3v_2) \vec{i} - (u_1v_3 - u_3v_1) \vec{j} + (u_1v_2 - u_2v_1) \vec{k} $$
性质：
*   $\vec{u} \times \vec{v}$ 与 $\vec{u}$ 和 $\vec{v}$ 都垂直。
*   $\vec{v} \times \vec{u} = - (\vec{u} \times \vec{v})$。
*   $\vec{u}$ 与 $\vec{v}$ 的叉积是一个长度为 $||\vec{u}|| \cdot ||\vec{v}|| \cdot |\sin\theta|$ 的向量（即平行四边形面积）。

**11. 三重积 (混合积) = 行列式 = 体积**
$$ (\vec{u} \times \vec{v}) \cdot \vec{w} = \begin{vmatrix} w_1 & w_2 & w_3 \\ u_1 & u_2 & u_3 \\ v_1 & v_2 & v_3 \end{vmatrix} $$

---


## 第6章 特征值与特征向量

**1. 基本方程 $Ax = \lambda x$**
*   数 $\lambda$ 是矩阵 $A$ 的**特征值**。
*   向量 $x$ 是矩阵 $A$ 的**特征向量**。

**2. 单位矩阵 $I$**
$Ix = x$，因此所有特征值都是 1，所有向量都是它的特征向量。

**3. 特征方程**
$$ Ax = \lambda x \rightarrow (A - \lambda I)x = 0 $$
矩阵 $A - \lambda I$ 满足 $(A - \lambda I)x = 0$，则 $A - \lambda I$ 为不可逆矩阵，$\det(A - \lambda I) = 0$。
由特征值方程 $\det(A - \lambda I) = 0$ 可解出特征值 $\lambda$。

**4. 性质**
*   若 $A$ 为不可逆矩阵，则 $\lambda = 0$ 是一个特征值。
*   若 $A$ 为对称矩阵，则特征向量正交。

**5. 位移性质**
一个矩阵减去单位矩阵 $I$ 后，每个特征值 $\lambda$ 也减 1（特征向量不变）。

**6. 求解步骤**
对每个特征值 $\lambda$，解 $(A - \lambda I)x = 0$ 或 $Ax = \lambda x$，可求出特征向量 $x$。

**7. 迹 (Trace)**
矩阵 $A$ 的对角元素之和称为矩阵 $A$ 的迹，记为 $\text{tr}(A)$。
$$ \text{tr}(A) = a_{11} + a_{22} + a_{33} + \dots + a_{nn} $$

**8. n阶方阵有 n 个特征值**
*   $n$ 个特征值之积等于行列式：$\lambda_1 \cdot \lambda_2 \cdots \lambda_n = \det A$
*   $n$ 个特征值之和等于迹：$\lambda_1 + \lambda_2 + \dots + \lambda_n = \text{tr}(A)$

**9. 特征值可能是虚数**
*   如：$90^\circ$ 旋转矩阵 $Q = \begin{bmatrix} 0 & -1 \\ 1 & 0 \end{bmatrix}$ 没有实特征值，它的特征值是 $i$ 和 $-i$。
*   对称矩阵 $A^T = A$，特征值为实数。
*   反称矩阵 $A^T = -A$，特征值为纯虚数。
*   **10. 三角形矩阵**：特征值为对角线上所有元素。

**11. 对角化 (Diagonalization)**
设 $n \times n$ 矩阵 $A$ 有 $n$ 个线性无关的特征向量 $x_1, x_2, \dots, x_n$。以它们为列构成特征向量矩阵 $X$，那么 $X^{-1}AX$ 是特征值矩阵 $\Lambda$ (对角矩阵)。

$$ X^{-1}AX = \Lambda = \begin{bmatrix} \lambda_1 & & & \\ & \lambda_2 & & \\ & & \ddots & \\ & & & \lambda_n \end{bmatrix} \quad (\text{空白处为0}) $$
*   特征向量矩阵 $X$
*   特征值矩阵 $\Lambda$

**12. 矩阵的幂**
$$ X^{-1}AX = \Lambda \implies AX = X\Lambda \implies A = X\Lambda X^{-1} $$
$$ A^2 = X\Lambda X^{-1} X\Lambda X^{-1} = X\Lambda^2 X^{-1} \rightarrow A^n = X \Lambda^n X^{-1} $$
结论：$A^n$ 的特征值为 $\lambda_1^n, \lambda_2^n, \dots, \lambda_n^n$，特征向量不变。

**13. $AX = X\Lambda$ 的理解**
$$ \begin{aligned} Ax_1 &= \lambda_1 x_1 \\ Ax_2 &= \lambda_2 x_2 \\ \vdots \\ Ax_n &= \lambda_n x_n \end{aligned} \implies AX = A[x_1 \ x_2 \ \dots \ x_n] = [\lambda_1 x_1 \ \lambda_2 x_2 \ \dots \ \lambda_n x_n] = X\Lambda $$

**14. 可对角化的前提**
特征向量矩阵 $X$ 可逆 $\rightarrow$ 任何没有重复特征值的矩阵均可对角化。
*可逆性与可对角化之间并无关联：*
1.  可逆性与特征值有关（不可逆则存在 $\lambda=0$）。
2.  可对角化与特征向量有关（数量是否足以构成 $X$）。
    *   可对角化的矩阵可能不可逆（有特征值为0，但没有重复特征值）。
    *   矩阵 $A$ 的对应 $n$ 个**不同**特征值的特征向量是线性无关的，此时 $A$ 可对角化。

**15. 相似矩阵：特征值相同**
假设特征值矩阵 $\Lambda$ 已固定，随着特征向量矩阵 $X$ 的变化，可得到一族形如 $A = X\Lambda X^{-1}$ 的矩阵（有相同特征值），所有这些矩阵具有相似关系。
推广到不可对角化矩阵：任意选一个常值矩阵 $C$，考察所有形如 $A = BCB^{-1}$ 的矩阵，其中要求 $B$ 为可逆矩阵。也称 $A$ 与 $C$ 相似。

*   **定义：** 所有形如 $A = BCB^{-1}$ 的矩阵都是“相似的”，它们共享 $C$ 的特征值。
*   所有相似矩阵具有相同特征值 $\lambda$，不同的、新的特征值 $Bx$。
    *   证：$(BCB^{-1})Bx = BCx = B\lambda x = \lambda (Bx)$。

**16. 斐波那契数 (特征值的应用)**
令 $u_k = \begin{bmatrix} F_{k+1} \\ F_k \end{bmatrix}$，由 $\begin{cases} F_{k+2} = F_{k+1} + F_k \\ F_{k+1} = F_{k+1} \end{cases}$ 得到 $u_{k+1} = A u_k$，其中 $A = \begin{bmatrix} 1 & 1 \\ 1 & 0 \end{bmatrix}$。
$$ u_0 = \begin{bmatrix} 1 \\ 0 \end{bmatrix}, u_1 = \begin{bmatrix} 1 \\ 1 \end{bmatrix}, u_2 = \begin{bmatrix} 2 \\ 1 \end{bmatrix} \dots u_n = A^n u_0 $$

**17. 矩阵的幂 $A^k$ 的求解步骤**
原理：由特征向量矩阵 $X$ 得到 $A = X\Lambda X^{-1}$，$A^k = X\Lambda^k X^{-1}$。
已知 $A$ 与 $u_0$，求解 $u_k$ ($u_k = X\Lambda^k X^{-1} u_0$)。
将计算 $X\Lambda^k X^{-1} u_0$ 分为三步进行：
1.  **将 $u_0$ 写为特征向量的线性组合：** $c_1 x_1 + c_2 x_2 + \dots + c_n x_n = Xc$ ($X$ 为特征向量矩阵，$c$ 为系数向量，$c = X^{-1}u_0$)。
2.  **用各 $\lambda_i^k$ 乘对应的特征向量 $x_i$：** 结果中的系数向量可写成矩阵 $\Lambda^k X^{-1} u_0$。
    $$ c_1 x_1 + \dots + c_n x_n \rightarrow c_1 \lambda_1^k x_1 + c_2 \lambda_2^k x_2 + \dots + c_n \lambda_n^k x_n $$
    $$ u_0 = Xc, c = X^{-1} u_0 \rightarrow u_k = A^k u_0 = X \Lambda^k X^{-1} u_0 = X \Lambda^k c $$
3.  **把 $c_i \lambda_i^k x_i$ 加起来，得到 $u_k = A^k u_0$。**
    $$ u_k = A^k u_0 = c_1 \lambda_1^k x_1 + c_2 \lambda_2^k x_2 + \dots + c_n \lambda_n^k x_n $$

*   **矩阵理解图示**：
    $$ u_0 = [x_1 \ x_2 \ \dots \ x_n] \begin{bmatrix} c_1 \\ c_2 \\ \vdots \\ c_n \end{bmatrix} = Xc $$
    $$ A^k u_0 = X \Lambda^k X^{-1} u_0 = X \Lambda^k c = [x_1 \ x_2 \ \dots \ x_n] \begin{bmatrix} \lambda_1^k & & \\ & \ddots & \\ & & \lambda_n^k \end{bmatrix} \begin{bmatrix} c_1 \\ c_2 \\ \vdots \\ c_n \end{bmatrix} = \sum_{i=1}^n c_i \lambda_i^k x_i $$

**18. 不可对角化矩阵**
设 $\lambda$ 为 $A$ 的一个特征值，可通过2种方式定义：
1.  **特征向量（几何角度）：** $Ax = \lambda x$ 有非零解。
2.  **特征值（代数角度）：** $A - \lambda I$ 的行列式为 0。

对于某些矩阵，特征值可重复出现，有2种不同方式计算其重数：
1.  **几何重数 (Geometric Multiplicity, GM)：** $\lambda$ 的线性无关特征向量的个数，即 $A-\lambda I$ 零空间维数。
2.  **代数重数 (Algebraic Multiplicity, AM)：** 特征值 $\lambda$ 的重复次数，只需观察 $\det(A-\lambda I)=0$ 的 $n$ 个根。
*   对于每个 $\lambda$，总有 $GM \leqslant AM$。
    *   $GM < AM$ 时，线性无关的特征向量数量不足，$A$ **不能**对角化。
    *   $GM = AM$ 时，每个特征值对应足够多的特征向量，$A$ **可**对角化。

**19. 将常系数微分方程(组)转化为能用线性代数求解的形式**
*   **$1 \times 1$ 形状：** 指数函数求解常微分方程 $\frac{du}{dt} = u$ 和 $\frac{du}{dt} = \lambda u$。
    *   $\frac{du}{dt} = u \rightarrow u(t) = Ce^t$
    *   $\frac{du}{dt} = \lambda u \rightarrow u(t) = Ce^{\lambda t}$
    *   $t=0$ 时，$u(0)=C \implies u(t) = u(0)e^{\lambda t}$
*   **$n \times n$ 形状：** $\frac{du}{dt} = Au$，未知数为向量函数 $u(t)$，初值为给定的向量 $u(0)$。
    *   $n$ 个方程蕴含 $n$ 阶方阵 $A$，由 $A$ 的 $n$ 个特征值入推出 $u(t)$ 中 $n$ 个 $e^{\lambda t}$。
    *   **类比 $\frac{du}{dt} = Au$ 的解 $u(t) = u(0)e^{\lambda t}$** (此处 $u(t)$ 和 $u(0)$ 为 $n$ 维向量)。
    1.  将 $u(0)$ 写成 $A$ 的特征向量的线性组合：$u(0) = c_1 x_1 + c_2 x_2 + \dots + c_n x_n$。
    2.  每个特征向量 $x_i$ 乘它的增长因子 $e^{\lambda_i t}$。
    3.  解就是各 $e^{\lambda_i t} x_i$ 的线性组合，其中系数由 $u(0)$ 决定。
        $$ \frac{du}{dt} = Au \implies u(t) = c_1 e^{\lambda_1 t} x_1 + c_2 e^{\lambda_2 t} x_2 + \dots + c_n e^{\lambda_n t} x_n $$

**20. 二阶微分方程**
*   **力学中最重要的方程：** $my'' + by' + ky = 0$
    设 $m=1$，将关于 $y''$ 的方程化为 $y$ 和 $y'$ 的向量方程：$\frac{du}{dt} = Au, u = \begin{bmatrix} y \\ y' \end{bmatrix}$。
    $$ \begin{cases} \frac{dy}{dt} = y' \\ \frac{dy'}{dt} = -ky - by' \end{cases} \rightarrow \frac{d}{dt} \begin{bmatrix} y \\ y' \end{bmatrix} = \begin{bmatrix} 0 & 1 \\ -k & -b \end{bmatrix} \begin{bmatrix} y \\ y' \end{bmatrix} \rightarrow \frac{du}{dt} = Au $$
    $A$ 的特征值为 $\lambda_1, \lambda_2$，特征向量为 $x_1 = \begin{bmatrix} 1 \\ \lambda_1 \end{bmatrix}, x_2 = \begin{bmatrix} 1 \\ \lambda_2 \end{bmatrix}$。
    通解 $u(t) = c_1 e^{\lambda_1 t} x_1 + c_2 e^{\lambda_2 t} x_2$。
    *   $u(t)$ 第一个分量：$y = c_1 e^{\lambda_1 t} + c_2 e^{\lambda_2 t}$
    *   若特征值中出现虚数，则利用欧拉公式 $e^{i\theta} = \cos\theta + i\sin\theta$ 计算。

**21. 马尔可夫矩阵 (Markov Matrix)**
*   **条件：** (1) 所有元素 $\geqslant 0$；(2) 按列相加和为 1。
*   **性质：** $\lambda = 1$ 是一个特征值。
*   **应用**：计算加州 (Cal) 和麻省 (Mass) 人口流动。
    *   $u_0 = \begin{bmatrix} u_C \\ u_M \end{bmatrix} = \begin{bmatrix} 0 \\ 1000 \end{bmatrix}$ (初始：加州0人，麻省1000人)。
    *   转移矩阵 $A = \begin{bmatrix} 0.9 & 0.2 \\ 0.1 & 0.8 \end{bmatrix}$。特征值 $\lambda_1=1, \lambda_2=0.7$。
    *   特征向量：$x_1 = \begin{bmatrix} 2 \\ 1 \end{bmatrix}$ (对应 $\lambda=1$), $x_2 = \begin{bmatrix} 1 \\ -1 \end{bmatrix}$ (对应 $\lambda=0.7$)。
    *   分解 $u_0$：$u_0 = \frac{1000}{3}x_1 - \frac{2000}{3}x_2$。
    *   $k$ 年后：$u_k = \frac{1000}{3} \cdot 1^k x_1 - \frac{2000}{3} \cdot (0.7)^k x_2$。
    *   **稳态 ($k \to \infty$)**：$(0.7)^k \to 0$，故 $u_\infty = \frac{1000}{3} \begin{bmatrix} 2 \\ 1 \end{bmatrix} = \begin{bmatrix} 2000/3 \\ 1000/3 \end{bmatrix}$。

**22. 讨论带有标准正交基的投影问题**
一组基向量 $q_1, q_2, \dots, q_n$。任意向量 $v$ 都由这组基构成 $v = x_1 q_1 + x_2 q_2 + \dots + x_n q_n$。
利用正交性：$q_1^T v = x_1, q_2^T v = x_2, \dots$。
矩阵形式：$[q_1 \ q_2 \ \dots \ q_n] \begin{bmatrix} x_1 \\ \vdots \\ x_n \end{bmatrix} = Qx = v \implies x = Q^{-1}v = Q^T v$。

**23. Fourier Series 傅里叶级数**
$$ f(x) = a_0 + a_1 \cos x + b_1 \sin x + a_2 \cos 2x + b_2 \sin 2x + \dots $$

*   (1) 2个无限维向量 $V=(V_1, V_2, \dots)$ 和 $W=(W_1, W_2, \dots)$ 的**自然点积是一个无穷级数**：
$$ V^T W = V_1 W_1 + V_2 W_2 + \dots $$

*   (2) **定义：** 向量 $v=(V_1, V_2, \dots)$ 和函数 $f(x)$ 在无限维的“希尔伯特空间”（分别记为 $l^2$ 和 $L^2$）中，**当且仅当它们的模 $||v||^2$ 和 $||f||^2$ 是有限的：**
$$ ||v||^2 = v^T v = V_1^2 + V_2^2 + \dots \quad \text{必须为有限数} $$
$$ ||f||^2 = (f, f) = \int_0^{2\pi} |f(x)|^2 dx \quad \text{必须为有限积分} $$
**研究函数情形的关键：用积分替换求和**

*   (3) 若 $v$ 与 $w$ 长度有限，则它们的点积的大小 $|v \cdot w| \leqslant ||v|| \cdot ||w||$ 有限。
**考虑函数：用积分替换求和**
$f(x)$ 与 $g(x)$ 的点积不再是无穷级数之和，而是 $f(x) \cdot g(x)$ 的积分。
**定义：** $f(x)$ 与 $g(x)$ 的内积，以及 $f(x)$ 的长度平方分别是：
$$ (f, g) = \int_0^{2\pi} f(x)g(x) dx, \quad ||f||^2 = \int_0^{2\pi} (f(x))^2 dx $$
区间 $[0, 2\pi]$ 可换为不同区间，如 $[0, 1]$ 或 $(-\infty, +\infty)$。
**重要的是：** $\sin x$ 与 $\cos x$ 在函数空间中正交：
$$ \int_0^{2\pi} \sin x \cdot \cos x dx = 0 $$

*   (4) 傅里叶级数 $f(x) = a_0 + a_1 \cos x + b_1 \sin x + a_2 \cos 2x + b_2 \sin 2x + \dots$
利用了一组正交基：$1, \cos x, \sin x, \cos 2x, \sin 2x, \dots$ (两两正交)。
**利用傅里叶级数可计算一般 $f(x)$ 的长度：**
$$ (f, f) = \int_0^{2\pi} (a_0 + a_1 \cos x + b_1 \sin x + a_2 \cos 2x + b_2 \sin 2x + \dots)^2 dx $$
$$ = \int_0^{2\pi} (a_0^2 + a_1^2 \cos^2 x + b_1^2 \sin^2 x + a_2^2 \cos^2 2x + b_2^2 \sin^2 2x + \dots) dx $$
**因为正交性，交叉项乘积的积分为 0。**
$$ ||f||^2 = 2\pi a_0^2 + \pi(a_1^2 + b_1^2 + a_2^2 + b_2^2 + \dots) $$
当向量希尔伯特空间 $l^2$ 包含 $f(x)$ 的傅里叶系数向量 $v=(a_0, a_1, b_1, a_2, b_2 \dots)$ 时，函数希尔伯特空间 $L^2$ 包含 $f(x)$。因此，二者都必须为有限长度。

*   (5) **求傅里叶系数的方法：利用正交性**
求 $a_1$ 的方法：两边乘 $\cos x$，再从 0 到 $2\pi$ 积分。
$$ \int_0^{2\pi} f(x) \cdot \cos x dx = \int_0^{2\pi} a_1 \cos^2 x dx = \pi a_1 $$
**类似地，得到**
$$ a_k = \frac{1}{\pi} \int_0^{2\pi} f(x) \cos kx dx, \quad b_k = \frac{1}{\pi} \int_0^{2\pi} f(x) \sin kx dx $$

*   (6) 设非零向量 $v_1, v_2, \dots, v_n$ 在 $R^n$ 中是正交的
则可将向量 $b$ 写为 $v_i$ 的线性组合：$b = c_1 v_1 + c_2 v_2 + \dots + c_n v_n$
可利用正交性（两边左乘 $v_i^T$）得到系数：
$$ c_i = \frac{v_i^T b}{v_i^T v_i} $$
当基向量标准正交时，以它们为列向量可构成正交矩阵 $Q, v_i^T v_i = 1, c_i = v_i^T b$
$$ \begin{bmatrix} v_1 & v_2 & \dots & v_n \end{bmatrix} \begin{bmatrix} c_1 \\ c_2 \\ \vdots \\ c_n \end{bmatrix} = b, \quad Qc = b, \quad c = Q^T b = Q^{-1} b $$
具体到每一项： $c_k = q_k^T b$

**24. 对称矩阵 S 的性质**
1.  对称矩阵仅有**实特征值**。
2.  对称矩阵的特征向量可选成**标准正交形式**。
    *   $S = X \Lambda X^{-1} \implies S^T = (X^{-1})^T \Lambda X^T$
    *   $S = S^T \implies X^{-1} = X^T$，特征向量矩阵 $X$ 为正交矩阵 $Q$。
    *   **※ $S$ 的各特征向量正交。**
    *   当选择标准正交特征向量时，通常将 $X$ 改写为 $Q$。

**25. 谱定理 (Spectral Theorem)**
每个对称矩阵 $S$ 有分解式 $S = Q \Lambda Q^T$，其中 $S$ 的实特征值就是 $\Lambda$ 的对角元素，而标准正交特征向量就是 $Q$ 的各列。

**26. 正定矩阵：仅具有正特征值的对称矩阵**
(1) 若 $n$ 阶对称矩阵 $S$ 满足下述五条性质之一，则它满足全部性质：
    1.  $S$ 的全部 $n$ 个主元都是正数。
    2.  全部 $n$ 个左上角行列式都是正数。
    3.  **$S$ 的全部 $n$ 个特征值都是正数。**
    4.  除了在 $x=0$ 处，$x^T S x$ 都是正数。
    5.  $S = A^T A$，其中 $A$ 的各列线性无关。

*   “左上角行列式”的形状为 $1 \times 1, 2 \times 2, \dots, n \times n$，最后一个就是矩阵 $S$ 自身的行列式。

(2) **椭圆 $ax^2 + 2bxy + cy^2 = 1$**
*   例：求出倾斜椭圆 $5x^2 + 8xy + 5y^2 = 1$ 的对称轴。
    
    ![图6-26](/img/post_article/线性代数/Chapter6.26.png)

    $$ \begin{bmatrix} x & y \end{bmatrix} \begin{bmatrix} 5 & 4 \\ 4 & 5 \end{bmatrix} \begin{bmatrix} x \\ y \end{bmatrix} = 1 \implies S = \begin{bmatrix} 5 & 4 \\ 4 & 5 \end{bmatrix}, \lambda_1 = 9, \lambda_2 = 1 $$
    *   $S$ 的特征向量为 $x_1 = \begin{bmatrix} 1 \\ 1 \end{bmatrix}, x_2 = \begin{bmatrix} 1 \\ -1 \end{bmatrix}$，除以 $\sqrt{2}$ 得到单位向量 $q_1, q_2$。
    *   分解 $S = Q \Lambda Q^T$。
    *   左乘 $x^T$，右乘 $x$：$x^T S x = x^T Q \Lambda Q^T x = (Q^T x)^T \Lambda (Q^T x)$。
    *   $x^T S x = 5x^2 + 8xy + 5y^2 = 9(\frac{x+y}{\sqrt{2}})^2 + 1(\frac{x-y}{\sqrt{2}})^2 = 1$。
    *   平方系数为 $\Lambda$ 中特征值 9 和 1。
    *   平方项里系数为特征向量 $q_1, q_2$。
    *   倾斜椭圆的对称轴指向特征向量方向。
    *   对齐过程：设 $\frac{x+y}{\sqrt{2}} = X, \frac{x-y}{\sqrt{2}} = Y$，则 $9X^2 + Y^2 = 1$ ($\lambda_1 X^2 + \lambda_2 Y^2 = 1$)。
    *   椭圆的2个半轴长为 $\frac{1}{\sqrt{\lambda_1}}$ 和 $\frac{1}{\sqrt{\lambda_2}}$。
    *   将倾斜椭圆 $x^T S x = 1$ 变换为对齐椭圆 $X^T \Lambda X = 1$ 的旋转矩阵就是特征向量矩阵 $Q$。

(3) **重要应用：最小值判别**
函数 $F(x, y)$ 在点 $(x_0, y_0)$ 处有 $\frac{\partial F}{\partial x} = \frac{\partial F}{\partial y} = 0$。
若**黑塞 (Hessian) 矩阵** $S = \begin{bmatrix} \frac{\partial^2 F}{\partial x^2} & \frac{\partial^2 F}{\partial x \partial y} \\ \frac{\partial^2 F}{\partial y \partial x} & \frac{\partial^2 F}{\partial y^2} \end{bmatrix}$ 为正定矩阵，则 $F(x, y)$ 在该点有最小值。

---

## 第7章 快速傅里叶变换

**1. 复向量 z 的长度**
$$ ||\vec{z}|| = \vec{z}^T \bar{z} = z^H z = \sqrt{|z_1|^2 + |z_2|^2 + \dots + |z_n|^2} $$
*   $A^H$ 为 $A$ 的共轭转置，$A^H = \bar{A}^T$。

**2. 复向量 u 与 v 的内积**
$$ u^H v = \bar{u}_1 v_1 + \bar{u}_2 v_2 + \dots + \bar{u}_n v_n $$

**3. 正交**
内积为 0 依旧表示复向量正交。

**4. 共轭转置性质**
$$ (AB)^H = B^H A^H $$

**5. 埃尔米特矩阵 (Hermitian Matrix) $S = S^H$**
1.  任意一个**实对称矩阵**都是埃尔米特矩阵。
2.  若 $S=S^H$ 且 $z$ 为任意的复列向量，则 $z^H S z$ 为**实数**。
    *   证明思路：$(z^H S z)^H = z^H S z$，一个数等于它的共轭转置，从而这个数一定是实数。
3.  埃尔米特矩阵 $S$ 的**每一个特征值都是实数**。
    *   $Sz = \lambda z \implies z^H S z = \lambda \cdot z^H z \implies \lambda = \frac{z^H S z}{z^H z}$ 为实数。
4.  埃尔米特矩阵 $S$ 的**特征向量是正交的**。
    *   若 $Sz = \lambda z$ 且 $Sy = \beta y$，则 $y^H z = 0$ ($\lambda \neq \beta$)。

**6. 酉矩阵 (Unitary Matrix)**
复空间中的标准正交矩阵 $Q$。
1.  $Q^H Q = I$
2.  若 $Q$ 为方阵，则 $Q$ 为酉矩阵，$Q^H = Q^{-1}$。

**7. 单位根与傅里叶矩阵**

![图7-7](/img/post_article/线性代数/Chapter7.7.png)

*   **单位根：**
    $\theta = \frac{2\pi}{8}$，则复数 $w = e^{i\theta} = e^{\frac{2\pi i}{8}}$。
    为凸显它是八次方根，用 $w_8$ 表示。
    $$ w = e^{\frac{2\pi i}{8}} = \cos\frac{2\pi}{8} + i\sin\frac{2\pi}{8} $$
    $$ w^n = 1, \quad w_n = e^{i\theta} = e^{i \frac{2\pi}{n}} = \cos\frac{2\pi}{n} + i\sin\frac{2\pi}{n} $$

*   **举例：4阶傅里叶矩阵** ($n=4, w=1, i, i^2, i^3$)
    $$ F = \begin{bmatrix} 1 & 1 & 1 & 1 \\ 1 & w & w^2 & w^3 \\ 1 & w^2 & w^4 & w^6 \\ 1 & w^3 & w^6 & w^9 \end{bmatrix} = \begin{bmatrix} 1 & 1 & 1 & 1 \\ 1 & i & i^2 & i^3 \\ 1 & i^2 & i^4 & i^6 \\ 1 & i^3 & i^6 & i^9 \end{bmatrix} $$
    *   **性质：** $F = F^T$ 但 $F \neq F^H$。
    *   $(\frac{1}{\sqrt{n}}F^H) \cdot (\frac{1}{\sqrt{n}}F) = I$，即 $\frac{1}{\sqrt{n}}F$ 为酉矩阵。
    *   $F$ 的逆矩阵 $F^{-1} = \frac{1}{n} F^H = \frac{1}{n} \bar{F}$。

输入输出关系：
$$ \begin{bmatrix} y_0 \\ y_1 \\ y_2 \\ y_3 \end{bmatrix} = F c = \begin{bmatrix} 1 & 1 & 1 & 1 \\ 1 & w & w^2 & w^3 \\ 1 & w^2 & w^4 & w^6 \\ 1 & w^3 & w^6 & w^9 \end{bmatrix} \begin{bmatrix} c_0 \\ c_1 \\ c_2 \\ c_3 \end{bmatrix} $$
*   **输入：** 4个复系数 $c_0, c_1, c_2, c_3$。
*   **输出：** 4个函数值 $y_0, y_1, y_2, y_3$。
*   $y_n$ 为傅里叶级数 $\sum_{k=0}^3 c_k e^{ikx}$ 在点 $x = \frac{2\pi n}{4}$ 处的值。

具体的展开式：
*   $y_0 = c_0 + c_1 + c_2 + c_3$
*   $y_1 = c_0 + c_1 e^{\frac{2\pi i}{4}} + c_2 e^{\frac{4\pi i}{4}} + c_3 e^{\frac{6\pi i}{4}} = c_0 + c_1 w + c_2 w^2 + c_3 w^3$
*   $y_2 = c_0 + c_1 e^{\frac{4\pi i}{4}} + c_2 e^{\frac{8\pi i}{4}} + c_3 e^{\frac{12\pi i}{4}} = c_0 + c_1 w^2 + c_2 w^4 + c_3 w^6$
*   $y_3 = c_0 + c_1 e^{\frac{6\pi i}{4}} + c_2 e^{\frac{12\pi i}{4}} + c_3 e^{\frac{18\pi i}{4}} = c_0 + c_1 w^3 + c_2 w^6 + c_3 w^9$

**$n \times n$ 傅里叶矩阵 $F$ (也记作 $F_n$)**
$$ y = \begin{bmatrix} y_0 \\ y_1 \\ \vdots \\ y_{n-1} \end{bmatrix} = F_n c = \begin{bmatrix} 1 & 1 & w & \dots & w^{n-1} \\ 1 & w & w^2 & \dots & w^{n(n-1)} \\ \vdots & \vdots & & \vdots \\ 1 & w^{n-1} & w^{2(n-1)} & \dots & w^{(n-1)^2} \end{bmatrix} \begin{bmatrix} c_0 \\ c_1 \\ \vdots \\ c_{n-1} \end{bmatrix} $$
*   $F_n$ 的列向量正交，$F_n \bar{F}_n = nI$。
*   $F_n^{-1} = \frac{\bar{F}_n}{n}$。

**8. 快速傅里叶变换 (Fast Fourier Transform, 简称 FFT)**
FFT 利用矩阵分解将 $n^2$ 次运算减少。

$$ F_4 = \begin{bmatrix} 1 & 0 & 1 & 0 \\ 0 & 1 & 0 & i \\ 1 & 0 & -1 & 0 \\ 0 & 1 & 0 & -i \end{bmatrix} \begin{bmatrix} 1 & 1 & 0 & 0 \\ 1 & i^2 & 0 & 0 \\ 0 & 0 & 1 & 1 \\ 0 & 0 & 1 & i^2 \end{bmatrix} [\text{偶奇置换}] $$
更一般的分解形式：
$$ F_{2n} = \begin{bmatrix} I & D_n \\ I & -D_n \end{bmatrix} \begin{bmatrix} F_n & 0 \\ 0 & F_n \end{bmatrix} \begin{bmatrix} \text{偶奇} \\ \text{置换} \end{bmatrix} $$
其中 $D_n = \text{diag}(1, w, \dots, w^{n-1})$。

*   **例如 $F_{1024}$ 的分解：**
    $$ F_{1024} = \begin{bmatrix} I_{512} & D_{512} \\ I_{512} & -D_{512} \end{bmatrix} \begin{bmatrix} F_{512} & 0 \\ 0 & F_{512} \end{bmatrix} \begin{bmatrix} \text{偶奇} \\ \text{置换} \end{bmatrix} $$

*   **计算量分析：**
    *   直接计算 $y = F_{1024} \cdot c$ 需计算 $1024^2$ 次。
    *   使用一次变换分解后，需计算 $2 \times 512^2 + 512$ 次（$2 \times F_{512}$ 加上对角矩阵乘法）。
    *   递归分解：
        $$ \begin{aligned} 1024^2 &\rightarrow 2 \times 512^2 + 512 \\ &\rightarrow 2 \times (2 \times 256^2 + 256) + 512 = 4 \times 256^2 + 512 \times 2 \\ &\rightarrow 4 \times (2 \times 128^2 + 128) + 512 \times 2 = 8 \times 128^2 + 512 \times 3 \end{aligned} $$
    *   前一项最终化为 $2^n \cdot 1^2 \approx n$，后一项为 $512 \times n$ (这里的 $n$ 对应分解层数 $\log_2 1024 = 10$)。

**结论：**
经历一次快速傅里叶变换，算法复杂度由 $n^2$ 降为 $\frac{1}{2} n \log_2 n$。



---

## 附录：常用矩阵字母表

| 符号 | 含义 | 英文对照 |
| :--- | :--- | :--- |
| **A** | 任意矩阵 | Arbitrary Matrix |
| **B** | 基矩阵 | Basis Matrix |
| **C** | 余子式矩阵 | Cofactor Matrix |
| **D** | 对角矩阵 | Diagonal Matrix |
| **E** | 消元矩阵 | Elimination Matrix |
| **F** | 傅里叶矩阵 | Fourier Matrix |
| **H** | 阿达马矩阵 | Hadamard Matrix |
| **I** | 单位矩阵 | Identity Matrix |
| **J** | 若尔当矩阵 | Jordan Matrix |
| **K** | 刚度矩阵 | Stiffness Matrix |
| **L** | 下三角形矩阵 | Lower Triangular Matrix |
| **M** | 马尔可夫矩阵 | Markov Matrix |
| **N** | 零空间矩阵 | Nullspace Matrix |
| **P** | 置换矩阵 / 投影矩阵 | Permutation / Projection Matrix |
| **Q** | 正交矩阵 | Orthogonal (Unitary) Matrix |
| **R** | 上三角形矩阵 / 最简行阶梯形矩阵 | Upper Triangular / RREF |
| **S** | 对称矩阵 | Symmetric Matrix |
| **T** | 线性变换的矩阵 | Transformation Matrix |
| **U** | 上三角形矩阵 / 左奇异向量矩阵 | Upper Triangular / Left Singular Vectors |
| **V** | 右奇异向量矩阵 | Right Singular Vectors |
| **X** | 特征向量矩阵 | Eigenvector Matrix |
| **$\Lambda$** | 特征值矩阵 | Eigenvalue Matrix (大写 Lambda) |
| **$\Sigma$** | 奇异值矩阵 | Singular Value Matrix (大写 Sigma) |

> **注：** 一般用**大写字母**表示矩阵，**小写字母**表示向量。