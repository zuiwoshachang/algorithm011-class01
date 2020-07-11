# 学习笔记
## 递归
c++代码模板:
```
void recur(int level, int param) {
    // terminator
    if (level > MAX_LEVEL) {
        // process result
        return;
    }

    // process current logic
    process(level, param);

    // drill down
    recur(level + 1, newParam);

    // restore current status
}
```
### 思维要点
- 不要人肉进行递归
- 找到最近最简方法，将其拆解为可重复解决的问题（重复子问题）
- 书序归纳法思维

## 分治
c++代码模板:
```
void divide_conquer(problem, param1, param2) {
    // terminator
    if (problem is null) {
        // process result
        return;
    }

    // prepare data
    data = prepare_data(problem);
    subproblems = split_problem(problem, data)
    // conquer subproblems
    subresult1 = divide_conquer(subproblems[0], p1, ...);
    subresult2 = divide_conquer(subproblems[1], p1, ...);
    subresult3 = divide_conquer(subproblems[2], p1, ...);
    ...
    // process and generate the final result
    result = process_result(subresult1, subresult2, subresult3, ...);

    // revert the current level states
}
```
## 回溯Backtracking
回溯法采用试错的思想，它尝试分步的去解决一个问题。在分步解决问题的过程
中，当它通过尝试发现现有的分步答案不能得到有效的正确的解答的时候，它将
取消上一步甚至是上几步的计算，再通过其它的可能的分步解答再次尝试寻找问
题的答案。
回溯法通常用最简单的递归方法来实现，在反复重复上述的步骤后可能出现两种
情况：
- 找到一个可能存在的正确的答案；
- 在尝试了所有可能的分步方法后宣告该问题没有答案。
在最坏的情况下，回溯法会导致一次复杂度为指数时间的计算。

c++代码模板：
```
result = []
void backtrack(路径, 选择列表) {
    if (满足结束条件) {
        result.add(路径);
        return;
    }
    
    for (选择 : 选择列表) {
        做选择;
        backtrack(路径, 选择列表);
        撤销选择;
    }
}
```