## Flipping an Image

题目[链接](https://leetcode.com/problems/flipping-an-image/)

## 题目描述

给定一个二维矩阵`A`。翻转它，并取反，返回结果。

注：

- 翻转：颠倒图片每行。例如`[1, 1, 0]`变为 `[0, 1, 1]`。
- 取反：所有的`0`换成1，所有的`1`换成0。


## 约定

```C
1 <= A.length = A[0].length <= 20
0 <= A[i][j] <= 1
```

## 示例

```text
Example 1

Input: 
[[1,1,0],
 [1,0,1],
 [0,0,0]]

Output: 
[[1,0,0],
 [0,1,0],
 [1,1,1]]

Explanation: First reverse each row: 
[[0,1,1],
 [1,0,1],
 [0,0,0]].
Then, invert the image: 
[[1,0,0],
 [0,1,0],
 [1,1,1]]

Example 2

Input: 
[[1,1,0,0],
 [1,0,0,1],
 [0,1,1,1],
 [1,0,1,0]]

Output: 
[[1,1,0,0],
 [0,1,1,0],
 [0,0,0,1],
 [1,0,1,0]]

Explanation: First reverse each row: 
[[0,0,1,1],
[1,0,0,1],
[1,1,1,0],
[0,1,0,1]].
Then invert the image: 
[[1,1,0,0],
[0,1,1,0],
[0,0,0,1],
[1,0,1,0]]
```

----

## 解答

解答1

```C++

class Solution
{
public:
    vector<vector<int>> flipAndInvertImage(vector<vector<int>>& A)
    {
        int rowNum = A.size();
        int colNum = A[0].size();
        int colMid = (colNum+1)/2;
        //按行遍历
        for (int rowIndex = 0; rowIndex < rowNum; rowIndex++)
        {
            for (int colIndex = 0; colIndex < colMid; colIndex++)
            {
                int temp = A[rowIndex][colIndex];
                A[rowIndex][colIndex] = A[rowIndex][colNum - colIndex - 1] == 1 ? 0 : 1;
                A[rowIndex][colNum - colIndex - 1] = temp == 1 ? 0 : 1;
            }
        }
        return A;
    }
};
```

以上代码比较简洁，耗时16ms。


解答2

```C++
class Solution
{
public:
    vector<vector<int>> flipAndInvertImage(vector<vector<int>>& A)
    {
        flip(A);
        invert(A);
        return A;
    }
private:
    void flip(vector<vector<int>>& A)
    {
        int rowNum = A.size();
        int colNum = A[0].size();
        //按行遍历
        for (int rowIndex = 0; rowIndex < rowNum; rowIndex++)
        {
            for (int colIndex = 0; colIndex < colNum/2; colIndex++)
            {
                int temp = A[rowIndex][colIndex];
                A[rowIndex][colIndex] = A[rowIndex][colNum - colIndex - 1];
                A[rowIndex][colNum - colIndex - 1] = temp;
            }
        }
    }
    void invert(vector<vector<int>>& A)
    {
        int rowNum = A.size();
        int colNum = A[0].size();
        for (int rowIndex = 0; rowIndex < rowNum; rowIndex++)
        {
            for (int colIndex = 0; colIndex < colNum; colIndex++)
            {
                A[rowIndex][colIndex] = A[rowIndex][colIndex] == 1 ? 0 : 1;
            }
        }
    }
};
```

此种方法不太简洁，但耗时8ms，超过99.5%。