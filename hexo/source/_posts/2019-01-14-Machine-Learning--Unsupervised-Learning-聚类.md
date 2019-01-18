---
layout:     post                    # 使用的布局（不需要改）
title:      Machine Learning--Unsupervised Learning                 # 标题 
date:       2019-01-14              # 时间
categories: Machine Learning - Ng                       # 是否归档
tags:                               #标签
    - Machine Learning
---

### 聚类（Clustering）

* Market segmentation
* Social network analysis
* Organize computing cluters
* Astronomical data analysis

#### 1. K-Means算法
输入：<br>
&emsp;K个聚类中心，用于表示最后分成K类；<br>
&emsp;训练集：<br>
$$
[x^{(i)}, x^{(i)},..., x^{(m)}] \qquad 其中，x^{(i)}\in R^{n}, \quad x_0=1
$$
```
算法流程：簇分配、移动聚类中心
	随机初始化K个聚类中心，mu_1, mu_2, ..., mu_k \in R^n
	Repeat{
        for i = 1 to m
        	c^i := 表示样本x^i与聚类中心之间距离最近的那个聚类中心的索引，1~k
        for k = 1 to K
        	mu_k := 属于第k个聚类中心的所有样本的均值
	}
```

注意：没有样本被分到某个聚类中心(一般不会遇到)，一是删除该聚类中心，变成K-1个簇；二是重新找一个聚类中心。

#### 2. 目标函数(Optimization objective)

```
x_i：表示第i个样本的位置
c^i：表示样本x^i所属于的聚类中心编号，取值1,2,..., K
mu_k：表示第k个聚类中心的位置
mu_c^i：表示样本x_i所属于的聚类中心的位置
```

目标函数：
$$
J(c^{(i)}, ..., c^{(m)}, \mu_1, ..., \mu_K) = \dfrac{1}{m}\sum_{i=1}^{m}\left\|x^{i}-\mu_{c^{(i)}}\right\|^2 \\
\mathop{min}\limits_{c^{(i)},..., c^{(m)}, \mu_1, ..., \mu_K} \quad J(c{(1)}, ..., c^{(m)}, \mu_1, ..., \mu_K)
$$


目标函数随着迭代过程分解了两个阶段：

```
算法流程：
	Step 1：簇分配
		for i = 1 to m
        	c^i := 表示样本x^i与聚类中心之间距离最近的那个聚类中心的索引，1~k
```

其实，就是优化：
$$
minimize \quad J(..) \quad wrt \quad c^{(1)},..., c^{(m)}\\
holding\ on \quad \mu_1, ..., \mu_K
$$

```
算法流程：
	Step 2：移动聚类中心
		for k = 1 to K
        	mu_k := 属于第k个聚类中心的所有样本的均值
```

其实，就是优化：
$$
minimize \quad J(..) \quad wrt \quad \mu_1, ..., \mu_K \\
holding\ on \quad c^{(1)},..., c^{(m)}
$$








