## 3Sum

题目[链接](https://leetcode.com/problems/3sum/)

## 题目描述



## 约定



## 示例

```text

```

----

## 解答

```C++
class Solution
{
public:
    vector<vector<int>> threeSum(vector<int>& nums)
    {
        vector<vector<int>> result;
        sort(nums.begin(),nums.end());

        for (int i = 0; i < nums.size(); i++)
        {
            while ((i > 0) && (nums[i] == nums[i - 1]))
                i++;
            int targetSum = 0 - nums[i];
            int l = i + 1;
            int r = nums.size() - 1;
            while (l < r)
            {
                int tmpSum = nums[l] + nums[r];
                if (tmpSum > targetSum)
                {
                    r--;
                }
                else if (tmpSum < targetSum)
                {
                    l++;
                }
                else
                {
                    result.push_back(vector<int> {nums[i], nums[l], nums[r]});
                    while (nums[l] == nums[l + 1]) { l++; }
                    while (nums[r] == nums[r - 1]) { r--; };
                    l++;
                    r--;
                }
            }
        }
        return result;
    }
};

```