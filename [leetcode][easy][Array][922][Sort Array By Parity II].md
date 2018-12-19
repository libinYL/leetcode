## Sort Array By Parity II

题目 [链接](https://leetcode.com/problems/sort-array-by-parity-ii/)

## 题目描述

给定一个非负整型数组 `A` , 此数组中的整数奇偶参半。

请将此数组排序，使得任意 `A[i]` 奇偶性都与 `i` 的奇偶性相同。

## 约定

1. 2 <= A.length <= 20000
2. A.length % 2 == 0
3. 0 <= A[i] <= 1000

## 示例

```text
Input: [4,2,5,7]
Output: [4,5,2,7]
Explanation: [4,7,2,5], [2,5,4,7], [2,7,4,5] would also have been accepted.
```

----

## 解答

借鉴了快速排序的思想

```C++
class Solution
{

    // 0 1 2 3  size = 4
    // 偶奇偶奇
public:
    vector<int> sortArrayByParityII(vector<int>& A)
    {
        int oddInx = 0;
        int evenInx = A.size() - 1;
        while (oddInx < A.size() && evenInx >= 0)//控制退出条件
        {
            while (oddInx < A.size() && A[oddInx] % 2 == 0) { oddInx += 2; };//i寻找下一个奇数
            while (evenInx >= 0 && A[evenInx] % 2 != 0) { evenInx -= 2; }//j寻找下一个偶数
            if (oddInx < A.size() && evenInx >= 0)
                swap(A[oddInx], A[evenInx]);
        }

        return A;
    }
};
```