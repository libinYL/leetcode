## Array Partition I

题目[链接](https://leetcode.com/problems/array-partition-i/)

## 题目描述

给定大小为 2n 的整型数组，你的任务是将这些整数分为`n`组，即 (a<sub>1</sub>,b<sub>1</sub>), (a<sub>2</sub>, b<sub>2</sub>),...,(a<sub>n</sub>, b<sub>n</sub>)，使得所有的 min(a<sub>i</sub>,b<sub>i</sub>) 之和最大，其中i的值为从1到n。

输出上述要求中的**和**。

## 约定

1. `n`是一个正数，范围是 [1,10000]。
2. 数组中的整数范围是 [-1000,10000]。

## 示例

```text
Input: [1,4,3,2]

Output: 4
Explanation: n is 2, and the maximum sum of pairs is 4 = min(1, 2) + min(3, 4).
```

----

## 解答

一般解法:排序，每隔一个取值作和。

```C++
class Solution
{
public:
    int arrayPairSum(vector<int>& nums)
    {
        std::sort(nums.begin(), nums.end());
        int sum = 0;
        for (int i = 0; i < nums.size(); i+=2)
        {
            sum += nums[i];
        }
        return sum;
    }
};
```

极限解法

由于给定范围，可考虑用桶排序加快速度。

```C++
/*
       =
       =        =  =  =  =
       =  =     =  =  =  =     =
       =  =     =  =  =  =  =  =
bucket[0][1][2][3][4][5][6][7][8]

*/
class Solution
{
public:
    int arrayPairSum(vector<int>& nums)
    {
        int sum = 0;

        //bucket[i]即为某个值的数量
        vector<int> bucket(20001, 0);
        for (int i = 0; i < nums.size(); i++)
        {
            bucket[nums[i] + 10000]++;
        }
        int flag = 0;
        int i = 0;
        while (i < bucket.size())
        {
            if (bucket[i] > 0 && flag == 0)
            {
                sum += (i - 10000);
                bucket[i]--;
                flag = 1;
            }
            else if (bucket[i] > 0 && flag == 1)
            {
                bucket[i]--;
                flag = 0;
            }
            else
            {
                i++;
            }
        }
        return sum;
    }
};
```