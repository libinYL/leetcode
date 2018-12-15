## Two Sum

题目[链接](https://leetcode.com/problems/two-sum/)

## 题目描述

给定一个`int`类型数组，要求返回其中两个数字的索引，使得它们的和为指定的目标值。

## 约定

1. 每个给定输入有且只有1种结果。
2. 返回的两个索引不能为同一个值。

## 示例

```text
Given nums = [2, 7, 11, 15], target = 9,

Because nums[0] + nums[1] = 2 + 7 = 9,
return [0, 1].
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