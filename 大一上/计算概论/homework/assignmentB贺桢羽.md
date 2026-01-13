# Assignment #B: dp

Updated 1448 GMT+8 Nov 18, 2025

2025 fall, Complied by <mark>贺桢羽，心理与认知科学学院</mark>



**说明：**

1）请把每个题目解题思路（可选），源码Python, 或者C++（已经在Codeforces/Openjudge上AC），截图（包含Accepted），填写到下面作业模版中（推荐使用 typora https://typoraio.cn ，或者用word）。AC 或者没有AC，都请标上每个题目大致花费时间。

2）提交时候先提交pdf文件，再把md或者doc文件上传到右侧“作业评论”。Canvas需要有同学清晰头像、提交文件有pdf、"作业评论"区有上传的md或者doc附件。

3）如果不能在截止前提交作业，请写明原因。



## 1. 题目

### LuoguP1255 数楼梯

dp, bfs, https://www.luogu.com.cn/problem/P1255

思路：斐波拉契数列

代码：

```python
a=0
b=1
n=int(input())
for i in range(n):
    a,b=b,a+b
print(b)
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![2a7d3ab1d48ec5a2b7cdc6ae10ef6b8d](C:\Users\h1557\Desktop\计算概论\homework\hB截图\2a7d3ab1d48ec5a2b7cdc6ae10ef6b8d.png)



### 27528: 跳台阶

dp, http://cs101.openjudge.cn/practice/27528/

思路：dp

代码：

```python
n=int(input())
dp=[0 for _ in range(n+1)]
if n>=3:
    dp[1]=1
    dp[2]=2
    for i in range(3,n+1):
        dp[i]=sum(dp[:i])+1
    print(dp[n])
if n==2:
    print(2)
if n==1:
    print(1)
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![e8a946bcb8b8d54e2a1ba5c3ded9273d](C:\Users\h1557\Desktop\计算概论\homework\hB截图\e8a946bcb8b8d54e2a1ba5c3ded9273d.png)



### M23421:《算法图解》小偷背包问题

dp, http://cs101.openjudge.cn/pctbook/M23421/

思路：倒着分析，每次计算都是在没有加这一钟物品最优情况下，再去寻找最优解。

代码：

```python
n,b=map(int,input().split())
pri=list(map(int,input().split()))
wei=list(map(int,input().split()))
dp=[0 for _ in range(b+1)]
for s in range(n):
    w=wei[s]
    p=pri[s]
    for i in range(b,w-1,-1):
        dp[i]=max(dp[i],dp[i-w]+p)
print(dp[b])
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![dd383739817ca4d25c2e3fb8c3792cd8](C:\Users\h1557\Desktop\计算概论\homework\hB截图\dd383739817ca4d25c2e3fb8c3792cd8.png)



### M5.最长回文子串

dp, two pointers, string, https://leetcode.cn/problems/longest-palindromic-substring/

思路：双指针。



代码：

```python
class Solution:
    def longestPalindrome(self, s: str) -> str:
        n=len(s)
        if n==1:
            return str(s)
        if n==2:
            if s[0]==s[1]:
                return s
            else:
                return s[0]
        else:
            temp=0
            ans=s[0]
            for i in range(n-1):
                check=0
                a=float("-inf")
                b=float("-inf")
                if i+2<=n-1 and s[i]==s[i+2]:
                    a=i
                    b=i+2
                    check=1
                while a>=1 and b<=n-2 and check:
                    a-=1
                    b+=1
                    if s[a]!=s[b]:
                        a+=1
                        b-=1
                        break
                if b-a+1>temp:
                    temp=b-a+1
                    ans=s[a:b+1]
                if s[i]==s[i+1]:
                    a=i
                    b=i+1
                    check=1
                while a>=1 and b<=n-2 and check:
                    a-=1
                    b+=1
                    if s[a]!=s[b]:
                        a+=1
                        b-=1
                        break
                if b-a+1>temp:
                    temp=b-a+1
                    ans=s[a:b+1]
            return ans

```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![da28b8e44e977dd8970bbc3bf5a35482](C:\Users\h1557\Desktop\计算概论\homework\hB截图\da28b8e44e977dd8970bbc3bf5a35482.png)





### 474D. Flowers

dp, 1700 https://codeforces.com/problemset/problem/474/D

思路：最开始一直超时，最终使用预处理+前缀和处理才通过。



代码：

```python
t,k=map(int,input().split())
dp = [0] * (100000 + 1)
dp[0] = 1
dp[1] = 1
for i in range(1, 100000+ 1):
    if i - k >= 0:
        dp[i] = (dp[i - 1] + dp[i - k] ) % (1000000007)
    else:
        dp[i] = (dp[i - 1])
sum=[0] * (100000 + 1)
for p in range(1,100000+ 1):
    sum[p]=(dp[p]+sum[p-1])% (1000000007)
for _ in range(t):
    a, b = map(int, input().split())
    print((sum[b]-sum[a-1])% (1000000007))
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![c6ec9dc27dd0a67fcd5eb0c5c4ebcf16](C:\Users\h1557\Desktop\计算概论\homework\hB截图\c6ec9dc27dd0a67fcd5eb0c5c4ebcf16.png)



### M198.打家劫舍

dp, https://leetcode.cn/problems/house-robber/

思路：注意边界的处理。

代码：

```python
class Solution:
    def rob(self, nums: List[int]) -> int:
        dp=[0]*len(nums)
        dp[0]=nums[0]
        for i in range(1,len(nums)):
            temp=dp[i-1]
            if i-1>0:
                for x in range(i-1):
                    if dp[x]+nums[i]>temp:
                        temp=dp[x]+nums[i]
                dp[i]=temp
            if i-1==0:
                if nums[1]>nums[0]:
                    dp[i]=nums[1]
                else:
                    dp[i]=nums[0]
        return dp[len(nums)-1]

```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![a1c3e0803c5187e1ca712f8a54a478c6](C:\Users\h1557\Desktop\计算概论\homework\hB截图\a1c3e0803c5187e1ca712f8a54a478c6.png)



## 2. 学习总结和收获

<mark>如果作业题目简单，有否额外练习题目，比如：OJ“计概2024fall每日选做”、CF、LeetCode、洛谷等网站题目。</mark>

这周学习dp，个人感觉比dfs好理解很多，只是需要一个精巧的数学递推公式构造就可以很简单地做出来。然后，做了这么多dp题，发现最开始递推那几项一定要谨慎，很多时候都是边界条件没有考虑导致WA和RE。然后在做Flower这个题时又使用了数组前缀和进行优化，这次是一维数组，上次做垃圾炸弹那道题目时用到的是二维数组前缀和。最长回文子串没有使用dp，感觉直接使用双指针也可以思路比较清晰地解决。在处理背包问题时，发现一定要考虑dp从前往后和从后往前解决，不然会出错。

另外，我发现了老师布置在其他网站的题目可以清楚地看到测试数据，这样也很方便就能debug出来了，但是OJ上的题只要以RE或者WA就只能自己一点一点地debug，要是考试的时候有测试数据就好了呜呜呜。



