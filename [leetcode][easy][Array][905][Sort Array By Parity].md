## Sort Array By Parity

题目[链接](https://leetcode.com/problems/sort-array-by-parity/)

## 题目描述

给定一个非负整型数组`A`，返回一个数组，数组中靠前的位置是`A`中的偶数，靠后的位置是`A`中的奇数。偶数范围内顺序不限，奇数也是。

## 约定

```C
1 <= A.length <= 5000
0 <= A[i] <= 5000
```

## 示例

```text
Input: [3,1,2,4]
Output: [2,4,3,1]
The outputs [4,2,3,1], [2,4,1,3], and [4,2,1,3] would also be accepted.
```

----

## 解答

```C++
class Solution
{
public:
    vector<int> twoSum(vector<int>& nums, int target)
    {
        map<int, int> mapValIdx;
        for (int i = 0; i < nums.size(); i++)
        {
            map<int,int>::iterator iter = mapValIdx.find(target - nums[i]);
            if (iter != mapValIdx.end())
            {
                return { iter->second,i };
            }
            else
            {
                mapValIdx.insert(make_pair(nums[i], i));
            }
        }
    }
};
```