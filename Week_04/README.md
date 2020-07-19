# 学习笔记
## 深度优先搜索（DFS）
以二叉树为例，递归示例代码：
```
def DFS(node):
    if node in visited:
        # already visited
        return
    visited.add(node)

    # process current node
    process(node, ...)
    DFS(node.left)
    DFS(node.right)
```
## 广度优先搜索（BFS）
广度优先搜索使用双端队列保存每层的节点。
```
def BFS(node):
    queue = []
    queue.append(node)
    visited.add(node)

    while queue:
        node = queue.pop()
        visited.add(node)

        process(node)

        nodes = generate_related_nodes(node)
        queue.push(nodes)
```
## 贪心算法
贪心算法是一种在每一步选择中都采取在当前状态下最好或最优（即最有利）的选择，从而希望导致结果是全局最好或最优的算法。

贪心法可以解决一些最优化问题，如：求图中的最小生成树、求哈夫曼编码等。然而对于工程和生活中的问题，贪心法一般不能得到我们所要求的答案。

一旦一个问题可以通过贪心法来解决，那么贪心法一般是解决这个问题的最好办法。由于贪心法的高效性以及其所求得的答案比较接近最优结果，贪心法也可以用作辅助算法或者直接解决一些要求结果不特别精确的问题。
### vs 动态规划
贪心算法与动态规划的不同在于它对每个子问题的解决方案都做出选择，不能回退。动态规划则会保存以前的运算结果，并根据以前的结果对当前进行选择，有回退功能。

### 应用场景
问题能够分解成子问题来解决，子问题的最优解能递推到最终问题的最优解。这种子问题最优解称为最优子结构。

## 二分查找
时间复杂度：O(long(n))
### 前提
- 目标函数单调性
- 存在上下界
- 能够通过索引访问

代码模板：
```
left, right = 0, len(array) - 1
    while left <= right:
        mid = (left + right) / 2
        if array[mid] == target:
            # find the target!!
            break or return result
        elif array[mid] < target:
            left = mid + 1
        else:
            right = mid - 1
```