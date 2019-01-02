## Univalued Binary Tree

题目[链接](https://leetcode.com/problems/univalued-binary-tree/)

## 题目描述

如果一棵树里的每个节点的值都相等，我们称它为“全局同值”。

给定一棵树，如果它是“全局同值”的树，返回true。

## 约定

1. 给定树的节点数量范围为 [1,100]
2. 每个节点值的范围是 [0,99]。
## 示例

例1：

![](https://assets.leetcode.com/uploads/2018/12/28/unival_bst_1.png)

```text
Input: [1,1,1,1,1,null,1]
Output: true
```

例2：

![](https://assets.leetcode.com/uploads/2018/12/28/unival_bst_2.png)

```text
Input: [2,2,2,5,2]
Output: false
```

----

## 解答

//丑陋的写法
```C++

class Solution
{
private:
    int defaultVal = 0;
    bool result = true;
    void _isUnivalTree(TreeNode* node)
    {
        if (NULL == node)
            return;

        if (defaultVal != node->val)
        {
            result = false;
            return;
        }
        _isUnivalTree(node->left);
        _isUnivalTree(node->right);

    }
public:

    bool isUnivalTree(TreeNode* root)
    {
        defaultVal = root->val;
        _isUnivalTree(root);
        return result;
    }
};
```

优化点：事实上不必都与root的值做比较，每个节点只需与其父节点做比较即可。这样就避免了全局变量。