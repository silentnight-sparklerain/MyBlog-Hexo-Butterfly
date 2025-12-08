---
title: 数据结构与基础算法
categories:
  - Programming
  - Theory
comments: true
description: 数据结构（线性结构、栈、队列、并查集、树、图、哈希表）与基础算法（基础思维与技巧、排序与查找、图论、动态规划、字符串算法、数论）
highlight_shrink: true
swiper_index: 1
cover: /img/posts/DataStructures_and_Algorithm.jpg
abbrlink: f0be246
date: 2025-11-15 00:00:00
updated: 2025-12-08 00:00:00
keywords:
top_img:
mathjax:
katex:
aside:
aplayer:
---

本文囊括了一些最基础的数据结构与算法，此页为目录，详细介绍请看右侧边栏。
如果你有更好的想法或者我没有收录进来的数据结构或算法，请在评论区留言，方便我做出修改，谢谢！

---

## 0.建议的学习路线

### 阶段一：必须掌握（基础）

* 数组、字符串、链表
* 栈 / 队列 / 双端队列
* 哈希表（unordered_map / unordered_set）
* 二叉树遍历（递归/非递归）
* 堆（priority_queue）
* 图：DFS / BFS
* 最短路：Dijkstra（非负权）
* 最小生成树：Prim / Kruskal
* 基本 DP（背包、LCS）

### 阶段二：提升能力（进阶）

* 二叉搜索树、平衡树（概念）
* 树状数组 / 线段树
* 拓扑排序（Kahn + DFS）
* 强连通分量：Tarjan / Kosaraju
* Bellman-Ford / SPFA
* 多源最短路径：Floyd-Warshall
* 区间 DP、树形 DP、状态压缩 DP
* KMP、Manacher

### 阶段三：高级算法（挑战）

* 网络流（Dinic、ISAP、费用流）
* LCA（倍增 / Tarjan）
* 树链剖分（HLD）
* AC 自动机
* DP 优化（斜率优化、四边形不等式）
* 数论进阶（逆元、CRT、筛法优化）

---

## 1. 数据结构（Data Structures）

### 1.1 线性结构（Linear Structures）

* 数组（Array）
* 字符串（String）
* 链表（Linked List）
* 栈（Stack）
* 队列（Queue）
* 双端队列（Deque）
* **哈希表（Hash Table）**

  * unordered_map
  * unordered_set
  * 哈希冲突处理：链式/开放地址

### 1.2 树结构（Trees）

#### 基础树（Basic Trees）

* 二叉树（Binary Tree）
* 二叉搜索树（BST）
* 树的遍历：先序/中序/后序/层序

#### 高级树（Advanced Trees）

* AVL 树（概念）
* 红黑树（概念）
* Trie 字典树
* 并查集（Union-Find）

#### 区间结构

* 树状数组（Fenwick Tree）
* 线段树（Segment Tree）

  * 区间和、区间最值
  * 懒标记（Lazy Propagation）

---

## 2. 数学与数论（Math & Number Theory）

### 2.1 基础

* 最大公约数 GCD（欧几里得算法）
* 最小公倍数 LCM
* 快速幂（快速指数）
* 排列组合

### 2.2 数论进阶

* 质数判断：试除 / Miller–Rabin
* 欧拉函数 φ(n)
* 线性筛（Euler sieve）
* 模运算（加减乘幂取模）
* 逆元

  * 扩展欧几里得
  * 费马小定理（mod 为质数）
* 中国剩余定理（CRT）
* Lucas 定理

---

## 3. 排序 & 查找（Sorting & Searching）

### 3.1 排序

* 冒泡 / 插入 / 选择（基础）
* 快速排序（重点）
* 归并排序（重点）
* 堆排序（理解 + 应用）
* 桶排序 / 基数排序（大数据场景）

### 3.2 查找

* 二分查找

  * 标准版
  * 左边界 / 右边界
* 二分答案（Binary Search on Answer）

---

## 4. 图论（Graph Theory）

### 4.1 图的基本表示

* 邻接表（Adjacency List）
* 邻接矩阵（Adjacency Matrix）
* 有向图 / 无向图
* 带权图 / 不带权图

---

### 4.2 图的遍历（基础）

* 深度优先搜索（DFS）
* 广度优先搜索（BFS）
* 连通性判定
* 拓扑排序
  * Kahn 算法（BFS）
  * DFS 版本（逆后序输出）

---

### 4.3 最小生成树（MST）

* **Prim 算法**

  * 适用稠密图 / 邻接矩阵
  * Dijkstra 类似思想
* **Kruskal 算法**

  * 适用稀疏图 / 边集
  * 并查集判断成环

---

### 4.4 最短路径（Shortest Path）

#### 单源最短路

* **Dijkstra（非负边）**

  * 邻接表：O((V+E)logV)
  * 邻接矩阵：O(V²)
* Bellman-Ford（可负权）
* SPFA（Bellman-Ford 的优化）

#### 多源最短路

* Floyd–Warshall（O(V³)）

#### 所有点对最短路（稀疏图）

* Johnson 算法（Bellman-Ford + Dijkstra）

---

### 4.5 强连通分量（SCC）

* **Tarjan 算法**（基于 DFS）
* **Kosaraju 算法**（两次 DFS）

---

### 4.6 无向图中特殊点与边

* 割点（Articulation Points）
* 桥 / 割边（Bridges）
* 双连通分量（BCC）

---

### 4.7 网络流（高级）

* Dinic（分层图）
* ISAP（当前弧优化）
* 最小费用最大流（SPFA + 费用）

---

## 5. 字符串算法（String Algorithms）

### 5.1 模式匹配

* KMP（重点）
* Sunday 算法
* Rabin–Karp

### 5.2 高级字符串算法

* 最长回文子串：Manacher 算法
* 后缀数组（SA）
* Trie 树
* AC 自动机（多模匹配）

---

## 6. 动态规划（Dynamic Programming）

### 6.1 基础 DP

* 斐波那契（递推）
* 背包 DP（0/1、完全、多重）
* LIS（最长上升子序列）
* LCS（最长公共子序列）

### 6.2 区间 DP

* 石子合并
* 矩阵链乘法

### 6.3 树形 DP

* 树上路径
* 子树信息 DP

### 6.4 状态压缩 DP

* 集合 DP（TSP 类）
* 子集枚举

### 6.5 DP 优化（进阶）

* 斜率优化（Convex Hull Trick）
* 四边形不等式优化
* Knuth 优化

---

## 7. 混合技巧（Hybrid Techniques）

* 双指针（Two Pointers）
* 滑动窗口（Sliding Window）
* 区间合并
* 分治（Divide & Conquer）
* 贪心（Greedy）
* 单调栈 / 单调队列

