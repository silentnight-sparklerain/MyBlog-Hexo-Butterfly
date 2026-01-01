---
title: 数据结构与基础算法（3）树结构
categories:
  - Programming
  - Theory
comments: true
description: 树结构（树与二叉树、图）
series: 数据结构与基础算法
hide: true
highlight_shrink: true
cover: /img/posts/DataStructures_and_Algorithm.jpg
toc:
  enable: true
  list_number: true
abbrlink: e8c44c4c
date: 2025-12-18 00:00:00
updated: 2025-12-18 00:00:00
---

## 一、树与二叉树 (Trees and Binary Trees)

### 1.1 树的基本概念与术语

*   **定义**：树是 $n$ 个结点的有限集。$n = 0$ 时称为空树。
*   **结点的度 (Degree of Node)**：结点拥有的子树个数。
*   **树的度 (Degree of Tree)**：树内各结点度的最大值。
*   **叶子结点 (Leaf/Terminal Node)**：度为 0 的结点。
*   **分支结点 (Branch/Internal Node)**：度大于 0 的结点（除根结点外也称内部结点）。
*   **结点的层次 (Level)**：从根开始定义，根为第 1 层。
*   **树的深度/高度 (Depth/Height)**：树中结点的最大层次。
*   **路径与路径长度**：两个结点之间的路径由结点序列组成，路径长度为路径上**边的数目**。
*   **有序树与无序树**：子树从左到右是否有次序。

### 1.2 二叉树 (Binary Tree)

二叉树是每个结点最多只有两个子树的有序树。

#### 1.2.1 特殊二叉树
*   **满二叉树 (Full Binary Tree)**：高度为 $h$ 且有 $2^h - 1$ 个结点，每层都填满。
*   **完全二叉树 (Complete Binary Tree)**：除了最后一层外，其他层均满，且最后一层结点集中在左侧。
*   **二叉排序树 (BST)**：左子树 < 根 < 右子树。
*   **平衡二叉树 (AVL)**：任一结点左右子树高度差绝对值 $\le 1$。

#### 1.2.2 存储结构
*   **顺序存储**：用数组存储，仅适用于完全二叉树（否则空间浪费严重）。
*   **链式存储**：最常用的方式。
*   `[此处插入代码：二叉树链式存储结构体定义 (BiTNode)]`

### 1.3 遍历 (Traversal)

#### 1.3.1 先序遍历 (Preorder)
*   **思路**：访问根结点 $\rightarrow$ 先序遍历左子树 $\rightarrow$ 先序遍历右子树。
*   `[此处插入代码：先序遍历递归实现]`
*   `[此处插入代码：先序遍历非递归实现（利用栈）]`

#### 1.3.2 中序遍历 (Inorder)
*   **思路**：中序遍历左子树 $\rightarrow$ 访问根结点 $\rightarrow$ 中序遍历右子树。
*   `[此处插入代码：中序遍历递归实现]`
*   `[此处插入代码：中序遍历非递归实现（利用栈）]`

#### 1.3.3 后序遍历 (Postorder)
*   **思路**：后序遍历左子树 $\rightarrow$ 后序遍历右子树 $\rightarrow$ 访问根结点。
*   `[此处插入代码：后序遍历递归实现]`
*   `[此处插入代码：后序遍历非递归实现（利用栈）]`

#### 1.3.4 层序遍历 (Level Order)
*   **思路**：利用**队列**实现。
    1. 根结点入队。
    2. 循环执行：出队一个结点 $\rightarrow$ 访问该结点 $\rightarrow$ 将其左、右孩子（若有）依次入队。
*   `[此处插入代码：层序遍历实现]`

#### 1.3.5 遍历构造二叉树
*   仅知“先序+后序”无法唯一确定一棵树。
*   **唯一确定**：中序 + (先序 / 后序 / 层序) 均可。

### 1.4 线索二叉树 (Threaded Binary Tree)

*   **初衷**：利用二叉链表中的空指针域（共 $n+1$ 个）来存放指向前驱和后继的指针。
*   **核心术语**：
    *   **线索**：指向前驱或后继的指针。
    *   **tag 标志位**：`0` 表示指向孩子，`1` 表示指向线索。
*   **构造思路**：在中序遍历的过程中，记录一个 `pre` 指针。若当前结点的左指针为空，令其指向 `pre`；若 `pre` 的右指针为空，令其指向当前结点。
*   `[此处插入代码：线索二叉树结构体定义与中序线索化算法]`
*   `[此处插入代码：在中序线索二叉树中寻找前驱、后继并遍历]`

### 1.5 树、森林与二叉树的转换

#### 1.5.1 树的存储
*   **双亲表示法**：用数组存放结点，每个结点保存其双亲的下标。
*   **孩子表示法**：每个结点的孩子用单链表链接。
*   **孩子兄弟表示法 (CST)**：左孩子指向第一个孩子，右孩子指向下一个兄弟。这是转换的基础。
*   `[此处插入代码：孩子兄弟表示法结构体定义]`

#### 1.5.2 相互转换
*   **树 $\rightarrow$ 二叉树**：左孩子不变，右孩子指向兄弟。
*   **森林 $\rightarrow$ 二叉树**：各树先转二叉树，第一棵树根作总根，其余树作总根的右子树。
*   **遍历对应关系**：
    *   树的先根遍历 = 对应二叉树的先序遍历。
    *   树的后根遍历 = 对应二叉树的**中序**遍历。

### 1.6 哈夫曼树 (Huffman Tree)

*   **结点的带权路径长度 (WPL)**：结点权值 $\times$ 根到该结点的路径长度。
*   **定义**：在含有 $n$ 个带权叶结点的二叉树中，$WPL$ 最小的树（最优二叉树）。
*   **构造算法思路 (Greedy)**：
    1. 在森林中选取两棵根结点权值最小的树作为左右子树。
    2. 构造一棵新树，根权值为两者之和。
    3. 从森林中删去原两棵树，加入新树，重复直至剩一棵。
*   **性质**：只有度为 0 和 2 的结点，没有度为 1 的结点。
*   **哈夫曼编码**：左分支为 0，右分支为 1。属于**前缀编码**。
*   `[此处插入代码：哈夫曼树构造算法]`

### 1.7 并查集 (Disjoint Set Union - DSU)

*   **用途**：处理不相交集合的合并 (Union) 与查找 (Find) 问题。
*   **存储**：通常使用数组实现的**双亲表示法**。`S[i]` 存储父结点下标，根结点存储 `-1` 或集合大小。
*   **基本操作**：
    1. **Find**：寻找根结点。
    2. **Union**：将一棵树的根指向另一棵树的根。
*   **优化算法**：
    *   **Union 优化（按秩合并）**：让小树合并到大树下，控制树高。
    *   **Find 优化（路径压缩）**：在查找过程中，直接将被查找路径上所有结点指向根结点。
*   `[此处插入代码：并查集初始化、Find 与 Union 基本实现]`
*   `[此处插入代码：带路径压缩和按秩合并的优化实现]`

---

## 二、图 (Graphs)

### 2.1 图的基本概念与术语

*   **定义**：图 $G$ 由顶点集 $V$ 和边集 $E$ 组成，记为 $G=(V, E)$。
    *   **注意**：图不能为空（顶点集 $V$ 必须非空）。
*   **有向图与无向图**：边是否有方向。有向边也称为**弧 (Arc)**。
*   **简单图与多重图**：408 主要讨论**简单图**（无重复边、无自环）。
*   **完全图 (Complete Graph)**：
    *   **无向完全图**：任意两顶点间均有边，共 $n(n-1)/2$ 条边。
    *   **有向完全图**：任意两顶点间均有方向相反的两条弧，共 $n(n-1)$ 条弧。
*   **连通性相关**：
    *   **连通图**：无向图中任意两个顶点都是连通的。
    *   **强连通图**：有向图中任意两个顶点 $v_i, v_j$ 之间都有双向路径。
    *   **连通/强连通分量**：图中的**极大**连通/强连通子图。
*   **生成树 (Spanning Tree)**：包含图中全部顶点的一个**极小**连通子图。$n$ 个顶点对应 $n-1$ 条边。
*   **顶点的度 (Degree)**：
    *   **无向图**：全部顶点度之和 $= 2 \times$ 边数。
    *   **有向图**：入度 (In-degree) 与 出度 (Out-degree) 之和。
*   **距离 (Distance)**：两顶点间最短路径的长度。

### 2.2 图的存储 (Graph Storage)

#### 2.2.1 邻接矩阵 (Adjacency Matrix)
*   **思路**：使用一个一维数组存储顶点，一个二维数组存储边的信息。
*   **特点**：适合存储稠密图；查找边的时间复杂度为 $O(1)$。

```C++
class Graph
{
private:
    int numVertices;  // 顶点数量
    vector<vector<int>> adjMatrix;  // 邻接矩阵
public:
    // 构造函数
    Graph(int vertices)
    {
        numVertices = vertices;
        adjMatrix.resize(vertices, vector<int>(vertices, 0));
    }
    // 添加边
    void AddEdge(int u, int v)
    {
        if(u >= 0 && u < numVertices && v >= 0 && v < numVertices)
        {
            adjMatrix[u][v] = 1;
            adjMatrix[v][u] = 1;  // 无向图添加两条边，有向图不用加
        }
        else
        {
            cout << "输入边的数据错误" << endl;
        }
    }
};
```

#### 2.2.2 邻接表 (Adjacency List)
*   **思路**：为每个顶点建立一个单链表，存储所有与其相连的边。
*   **特点**：适合存储稀疏图；空间复杂度为 $O(V+E)$。

```C++
class Graph
{
private:
    int numVertices;  // 顶点数量
    vector<vector<int>> adjList;  // 邻接表
public:
    Graph(int vertices)
    {
        numVertices = vertices;
        adjList.resize(vertices);
    }
    void AddEdge(int u, int v)  
    {
        if(u < 0 || u >= numVertices || v < 0 || v >= numVertices)
        {
            cout << "输入边的数据错误" << endl;
            return;
        }
        for(int i = 0; i < adjList[u].size(); i++)
        {
            if(adjList[u][i] == v)
            {
                cout << "边 " << u << " -> " << v << " 已经存在" << endl;
                return;
            }
        }
        adjList[u].push_back(v);
    }
};
```

#### 2.2.3 十字链表 (Orthogonal List)
*   **思路**：专门用于**有向图**。解决了邻接表难以查找入度的问题。

#### 2.2.4 邻接多重表 (Adjacency Multilist)
*   **思路**：专门用于**无向图**。每条边对应一个结点，避免同一条边重复出现。

### 2.3 图的遍历 (Graph Traversal)

#### 2.3.1 广度优先搜索 (BFS)
*   **算法思路**：借助队列和辅助数组 `visited[]`。
    1. 从起始点 $v$ 开始，访问 $v$ 并入队。
    2. 当队列非空时，出队一个顶点，访问其所有未被访问的邻接点并入队。
*   **复杂度**：邻接矩阵 $O(V^2)$，邻接表 $O(V+E)$。
*   `[此处插入代码：BFS 算法实现]`

#### 2.3.2 深度优先搜索 (DFS)
*   **算法思路**：类似于先序遍历，采用递归或栈实现。
    1. 访问起始点 $v$，标记已访问。
    2. 递归访问 $v$ 的未被访问的邻接点。
*   **复杂度**：邻接矩阵 $O(V^2)$，邻接表 $O(V+E)$。
*   `[此处插入代码：DFS 算法实现]`

### 2.4 最小生成树 (Minimum Spanning Tree, MST)

#### 2.4.1 Prim 算法 (普里姆)
*   **思路**：从顶点开始，每次选择距离当前生成树最近的顶点加入。
*   **特点**：侧重于“点”，适合**稠密图**。时间复杂度为 $O(V^2)$。
*   `[此处插入代码：Prim 算法实现]`

[1584. 连接所有点的最小费用（1857分）](https://leetcode.cn/problems/min-cost-to-connect-all-points/)

#### 2.4.2 Kruskal 算法 (克鲁斯卡尔)
*   **思路**：按权值从小到大排序边，每次选择不形成回路的最小边加入。
*   **特点**：侧重于“边”，适合**稀疏图**。时间复杂度为 $O(E \log E)$。
*   `[此处插入代码：Kruskal 算法实现]`

### 2.5 最短路径 (Shortest Path)

#### 2.5.1 Dijkstra 算法 (迪杰斯特拉)
*   **思路**：单源最短路径。通过“松弛操作”不断更新距离。
*   **限制**：边权不能为负。
*   `[此处插入代码：Dijkstra 算法实现]`

[743. 网络延迟时间](https://leetcode.cn/problems/network-delay-time/description/?envType=problem-list-v2&envId=shortest-path)
[787. K站中转内最便宜的航班（1786分）](https://leetcode.cn/problems/cheapest-flights-within-k-stops/?envType=problem-list-v2&envId=shortest-path)
[1514. 概率最大的路径（1846分）](https://leetcode.cn/problems/path-with-maximum-probability/description/?envType=problem-list-v2&envId=shortest-path)
[1334. 阈值距离内邻居最少的城市（1855分）](https://leetcode.cn/problems/find-the-city-with-the-smallest-number-of-neighbors-at-a-threshold-distance/description/)
[1631. 最小体力消耗路径（1947分）](https://leetcode.cn/problems/path-with-minimum-effort/description/)
[1976. 到达目的地的方案数（2094分）](https://leetcode.cn/problems/number-of-ways-to-arrive-at-destination/)

#### 2.5.2 Floyd 算法 (弗洛伊德)
*   **思路**：所有顶点间的最短路径。动态规划思想，三层循环嵌套。
*   **限制**：可以有负边权，但不能有负环。
*   `[此处插入代码：Floyd 算法实现]`

### 2.6 拓扑排序 (Topological Sort)
*   **应用**：针对有向无环图 (DAG)，应用于 **AOV网**。
*   **思路**：不断输出入度为 0 的顶点并删除其引出的边。
*   **判断**：若输出顶点数 < 总顶点数，则图中存在回路。
*   `[此处插入代码：拓扑排序算法实现]`

[207. 课程表](https://leetcode.cn/problems/course-schedule/description/?envType=problem-list-v2&envId=topological-sort)
[210. 课程表II](https://leetcode.cn/problems/course-schedule-ii/?envType=problem-list-v2&envId=topological-sort)
[310. 最小高度树](https://leetcode.cn/problems/minimum-height-trees/description/?envType=problem-list-v2&envId=topological-sort)
[1557. 可以到达所有点的最少数目（1512分）](https://leetcode.cn/problems/minimum-number-of-vertices-to-reach-all-nodes/description/)
[1466. 重新规划路线（1633分）](https://leetcode.cn/problems/reorder-routes-to-make-all-paths-lead-to-the-city-zero/description/)
[1462. 课程表IV（1692分）](https://leetcode.cn/problems/course-schedule-iv/description/?envType=problem-list-v2&envId=topological-sort)
[802. 找到最终的安全状态（1962分）](https://leetcode.cn/problems/find-eventual-safe-states/description/?envType=problem-list-v2&envId=topological-sort)
[1203. 项目管理（2418分）](https://leetcode.cn/problems/sort-items-by-groups-respecting-dependencies/description/?envType=problem-list-v2&envId=topological-sort)

### 2.7 关键路径 (Critical Path Method)
*   **应用**：针对带权有向无环图，应用于 **AOE网**。
*   **术语**：
    *   **$ve(k)$**：事件最早发生时间（取前驱 $\max$）。
    *   **$vl(k)$**：事件最迟发生时间（取后继 $\min$）。
    *   **关键活动**：时间余量为 0 的活动（$e=l$）。
*   **关键路径**：从源点到汇点路径长度最长的路径。
*   `[此处插入代码：关键路径算法实现]`