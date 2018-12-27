## Subdomain Visit Count

## 子域访问次数

题目 [链接](https://leetcode.com/problems/subdomain-visit-count/)

## 题目描述

形如 “discuss.leetcode.com” 域名包含很多子域。它的顶级是：“com", 次级是“leetcode.com”，最低级：“discuss.leetcode.com”。当我们访问一个像 “discuss.leetcode.com” 的域时，我们事实上也会隐含地访问 “leetcode.com” 和“com”。

现在，我们定义一种数据格式：“count-paired domain”。其中，“count” 代表此域被访问的次数，它后面跟一个空格，再后边是地址。例如 “9001 discuss.leetcode.com”。

现有一个 `cpdomains` 的序列（list），每个元素都是一个 “count-paired domain”。请输出一个与输入序列格式相同的 list，分别统计访问每个子域的数量，顺序不限。

## 约定

- `cpdomains` 的长度不超过 100。
- 每个域的名字长度不超过 100.
- 每个地址有 `1` 或 `2` 个 “.” 字符。
- 输入中，任何 “count-paired domain” 的访问次数不超过 10000.
- 最终的输出顺序不限。

## 示例

```text
Input:
["9001 discuss.leetcode.com"]
Output:
["9001 discuss.leetcode.com", "9001 leetcode.com", "9001 com"]
Explanation:
We only have one website domain: "discuss.leetcode.com". As discussed above, the subdomain "leetcode.com" and "com" will also be visited. So they will all be visited 9001 times.

Example 2:
Input:
["900 google.mail.com", "50 yahoo.com", "1 intel.mail.com", "5 wiki.org"]
Output:
["901 mail.com","50 yahoo.com","900 google.mail.com","5 wiki.org","5 org","1 intel.mail.com","951 com"]
Explanation:
We will visit "google.mail.com" 900 times, "yahoo.com" 50 times, "intel.mail.com" once and "wiki.org" 5 times. For the subdomains, we will visit "mail.com" 900 + 1 = 901 times, "com" 900 + 50 + 1 = 951 times, and "org" 5 times.
```

----

## 解答

```C++
#include<vector>
#include<map>
#include<iostream>

using namespace std;
class Solution
{
public:
    vector<string> subdomainVisits(vector<string>& cpdomains)
    {
        map<string,int> m;
        for (int i = 0; i < cpdomains.size(); i++)
        {
            map<string, int>::iterator it_map = m.begin();
            it_map = m.find(cpdomains.at(i));
            if (it_map == m.end())
            {

            }
                
            
            string domin = cpdomains.at(i);
            int idx1 = domin.find_first_of('.');
            string firstDomin = domin.substr(0,idx1);
            
            cout << firstDomin.c_str();
        }
        return cpdomains;
    }
};


int main()
{
    Solution s;
    vector<string> v{ "900 google.mail.com", "50 yahoo.com", "1 intel.mail.com", "5 wiki.org" };
    s.subdomainVisits(v);
    getchar();
}
```