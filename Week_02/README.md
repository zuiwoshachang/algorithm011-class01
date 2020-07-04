# 学习笔记
## 哈希表
哈希表（Hash table），也叫散列表，是根据关键码值（Keyvalue）而直接进行访问的数据结构。
它通过把关键码值映射到表中一个位置来访问记录，以加快查找的速度。
这个映射函数叫作散列函数（Hash Function），存放记录的数组叫作哈希表（或散列表）。
### 实现
c++ STL中，可用的模板类为std::unordered_map、std::unordered_multimap。
另两个支持保存Key-Value的常用模板类是std::map、std::multimap，它们基于红黑树实现，不能作为哈希表，具有O(logn)的查找、插入、删除时间复杂度。
### 时间复杂度
|访问|查找|插入|删除|
|--|--|--|--|
|-|O(1)|O(1)|O(1)|
## 集合
c++ STL中，可用的模板类有set、multiset、unordered_set、unordered_multiset.

set、multiset基于红黑树实现，具有O(logn)的查找、插入、删除时间复杂度；

unordered_set、unordered_multiset基于哈希函数实现，具有O(1)的查找、插入、删除时间复杂度。
## 二叉树
### 实现
```
struct TreeNode {
    int val;
    TreeNode *left;
    TreeNode *right;
    TreeNode(int x) : val(x), left(NULL), right(NULL) {}
}
```
### 遍历
树的定义是按照递归的方式定义的。树的遍历通常按照递归的方式遍历。
#### 前序遍历
根-左-右.

实例代码：
```
void preorder(TreeNode* root) {
    if (root) {
        visit(root->val);
        preorder(root->left);
        preorder(root->right);
    }
}
```
#### 中序遍历
左-中-右.

实例代码：
```
void inorder(TreeNode* root) {
    if (root) {
        inorder(root->left);
        visit(root->val);
        inorder(root->right);
    }
}
```
#### 后序遍历
左-右-中.

实例代码：
```
void postorder(TreeNode* root) {
    if (root) {
        postorder(root->left);
        postorder(root->right);
        visit(root->val);
    }
}
```
### 二叉搜索树（BST）
二叉搜索树，也称二叉搜索树、有序二叉树（Ordered Binary Tree）、排序二叉树（Sorted Binary Tree），是指一棵空树或者具有下列性质的二叉树：
1. 左子树上所有结点的值均小于它的根结点的值；
2. 右子树上所有结点的值均大于它的根结点的值；
3. 以此类推：左、右子树也分别为二叉查找树。

中序遍历二叉搜索树，得到节点的升序排列。
最坏情况下，可能退化为单链表。
#### 平均时间复杂度
|访问|查找|插入|删除|
|--|--|--|--|
|O(log(n))|O(log(n))|O(log(n))|O(log(n))|
#### 最坏时间复杂度
|访问|查找|插入|删除|
|--|--|--|--|
|O(n)|O(n)|O(n)|O(n)|
### 平衡二叉树（AVL）
它或者是一颗空树，或者具有以下性质的二叉排序树：
1. 它的左子树和右子树的深度之差(平衡因子)的绝对值不超过1；
2. 它的左子树和右子树都是一颗平衡二叉树。
#### 平均时间复杂度
|访问|查找|插入|删除|
|--|--|--|--|
|O(log(n))|O(log(n))|O(log(n))|O(log(n))|
#### 最坏时间复杂度
|访问|查找|插入|删除|
|--|--|--|--|
|O(log(n))|O(log(n))|O(log(n))|O(log(n))|
### 平衡多路查找树
B-Tree B+Tree B*Tree.
数据库中多用平衡多路查找树(Inno DB索引用到B+树)创建索引，降低树的高度，减小磁盘IO次数，提高查询效率。
#### 平均时间复杂度
|访问|查找|插入|删除|
|--|--|--|--|
|O(log(n))|O(log(n))|O(log(n))|O(log(n))|
#### 最坏时间复杂度
|访问|查找|插入|删除|
|--|--|--|--|
|O(log(n))|O(log(n))|O(log(n))|O(log(n))|
## 堆
可以迅速找到一堆数中的最大或者最小值的数据结构。
将根节点最大的堆叫做大顶堆或大根堆，根节点最小的堆叫做小顶堆或小根堆。
常见的堆有二叉堆、斐波那契堆等。
### 二叉堆
通过完全二叉树实现。
二叉堆（大顶）满足下列性质：
1. 是一颗完全二叉树；
2. 树中任意节点的值总是大于等于其子节点的值；

c++ STL中，可用优先队列priority_queue模板类，它基于vector实现。
#### 实现
一般通过“数组”实现。
假设第一个元素在数组中的索引为0的话，则父节点和子节点的位置关系如下：
1. 索引为i的左孩子的索引是(2*i+1);
2. 索引为i的右孩子的索引是(2*i+2);
3. 索引为i的父节点的索引是floor((i-1)/2);
   
##### 插入操作
1. 新元素一律先插入到堆的尾部；
2. 依次向上调整整个堆的结构，一直到根即可；[HeapifyUp]
##### 删除堆顶操作
1. 将堆尾元素替换到顶部；
2. 依次从根部向下调整整个堆的结构，一直到堆尾即可；[HeapifyDown]
#### 时间复杂度
|访问|查找|插入|删除|
|--|--|--|--|
|-|O(1)|O(log(n))/O(1)|O(1)|
### 图
#### 图的实现
1. 邻接矩阵（Adjacency matrix）,c++中可用vector\<vector\<T>>；
2. 邻接链表（Adjacency list）,c++中可用vector\<vector\<pair\<T1,T2>>>;