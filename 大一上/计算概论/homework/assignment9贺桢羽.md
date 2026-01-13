# Assignment #9: Mock Exam立冬前一天

Updated 1658 GMT+8 Nov 6, 2025

2025 fall, Complied by <mark>同学的姓名、院系</mark>



>**说明：**
>
>1. Nov⽉考： AC4<mark>（请改为同学的通过数）</mark> 。考试题⽬都在“题库（包括计概、数算题目）”⾥⾯，按照数字题号能找到，可以重新提交。作业中提交⾃⼰最满意版本的代码和截图。
>
>2. 解题与记录：对于每一个题目，请提供其解题思路（可选），并附上使用Python或C++编写的源代码（确保已在OpenJudge， Codeforces，LeetCode等平台上获得Accepted）。请将这些信息连同显示“Accepted”的截图一起填写到下方的作业模板中。（推荐使用Typora https://typoraio.cn 进行编辑，当然你也可以选择Word。）无论题目是否已通过，请标明每个题目大致花费的时间。
>
>3. 提交安排：提交时，请首先上传PDF格式的文件，并将.md或.doc格式的文件作为附件上传至右侧的“作业评论”区。确保你的Canvas账户有一个清晰可见的本人头像，提交的文件为PDF格式，并且“作业评论”区包含上传的.md或.doc附件。
> 
>4. 延迟提交：如果你预计无法在截止日期前提交作业，请提前告知具体原因。这有助于我们了解情况并可能为你提供适当的延期或其他帮助。  
>
>请按照上述指导认真准备和提交作业，以保证顺利完成课程要求。





## 1. 题目

### E29982:一种等价类划分问题

hashing, http://cs101.openjudge.cn/practice/29982

思路：考试的时候读题读错了，然后对字典键的大小排序也掌握得不清楚，导致WA了10次。。。



代码

```python
from collections import defaultdict
m,n,k=map(int,input().split(","))
dic=defaultdict(list)
for i in range(m+1,n):
        s=str(i)
        s=list(s)
        s=list(map(int,s))
        ans=sum(s)
        if ans/k==int(ans/k):
            dic[ans].append(str(i))
dic1=dict(sorted(dic.items(), key=lambda x:x[0]))
for v in dic1.values():
    print(",".join(v))
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![92de525c7291a6fca345d05326f8d337](C:\Users\h1557\Desktop\计算概论\homework\h9截图\92de525c7291a6fca345d05326f8d337.png)



### E30086:dance

greedy, http://cs101.openjudge.cn/practice/30086

思路：这个题是月考里面最简单的了吧。



代码

```python
N,D=map(int,input().split())
li=list(map(int,input().split()))
li.sort()
check=0
for i in range(1,2*N,2):
    if li[i]-li[i-1]>D:
        check=1
if check==1:
    print('No')
else:
    print('Yes')
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![8170760682b9e036cea77ee496c0efd9](C:\Users\h1557\Desktop\计算概论\homework\h9截图\8170760682b9e036cea77ee496c0efd9.png)



### M25570: 洋葱

matrices, http://cs101.openjudge.cn/practice/25570

思路：感觉自己矩阵掌握得不错，不过还是做得很复杂。



代码

```python
n=int(input())
ma=[]
for _ in range(n):
    ma.append(list(map(int,input().split())))
ans=[]
if n/2==int(n/2):
    for i in range(int(n/2)):
        s = sum(ma[i][i:n - i]) + sum(ma[n - i - 1][i:n - i])
        for j in range(i + 1, n - i - 1):
            s += ma[j][i] + ma[j][n - i - 1]
        ans.append(s)
else:
    for i in range(int(n/2)):
        s = sum(ma[i][i:n - i]) + sum(ma[n - i - 1][i:n - i])
        for j in range(i + 1, n - i - 1):
            s += ma[j][i] + ma[j][n - i - 1]
        ans.append(s)
    ans.append(ma[int(n/2)][int(n/2)])
ans.sort()
print(ans[-1])
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![e90dbb8d4f3ce0ebf9c2ae6c8fdeb1bc](C:\Users\h1557\Desktop\计算概论\homework\h9截图\e90dbb8d4f3ce0ebf9c2ae6c8fdeb1bc.png)



### M28906:数的划分

dfs, dp, http://cs101.openjudge.cn/practice/28906

思路：将这个问题拆解，拆解为是否含有1这个划分的情况：如果1不在划分中，那就把所有划分减1，最后再在这个划分的情况下，将剩下的部分划分；如果1在划分中，那么就先挑一个划分为1，剩下n-1进行k-1的划分。最后使用dp，可以计算出答案。



代码

```python
n,k=map(int,input().split())
dp=[[0 for _ in range(k+1)]for _ in range(n+1)]
dp[0][0]=1
for i in range(1,n+1):
    for j in range(1,min(i,k)+1):
        dp[i][j]=dp[i-j][j]+dp[i-1][j-1]
print(dp[n][k])
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![3015fff9be9f6ac62b155d006c99194d](D:\weixin\xwechat_files\wxid_wg6sc5apx61g12_cc23\temp\RWTemp\2025-11\9e20f478899dc29eb19741386f9343c8\3015fff9be9f6ac62b155d006c99194d.png)



### M29896:购物

greedy, http://cs101.openjudge.cn/practice/29896

思路：考试时是从大往小考虑的，然后就会使答案变大，考虑重复，后来发现从小往大考虑非常不错。

代码

```python
x, n = map(int, input().split())
li0 = list(map(int, input().split()))
if 1 not in li0:
    print(-1)
else:
    li0.sort()
    current = 0
    count = 0
    while current < x:
        max_coin = 1
        for coin in li0:
            if coin <= current + 1:
                max_coin = coin
            else:
                break
        current += max_coin
        count += 1
    print(count)
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![8fc47ff24176249b33bc4f6af784dc98](C:\Users\h1557\Desktop\计算概论\homework\h9截图\8fc47ff24176249b33bc4f6af784dc98.png)

### T25353:排队

greedy, http://cs101.openjudge.cn/practice/25353

思路：听完老师的讲解，再看了题解跟着写了一遍，也是搞明白了相当于找出所有可以互相交换的连通组再进行排序，这样才能做到字典序最小。



代码

```python
n,d=map(int,input().split())
height=[0]*n
check=[False]*n
for i in range(n):
    height[i]=int(input())
ans=[]
while False in check:
    i,l=0,len(height)
    buffer=[]
    while i<l:
        if check[i]:
            i+=1
            continue
        if len(buffer)==0:
            buffer.append(height[i])
            maxh=height[i]
            minh=height[i]
            check[i]=True
            i+=1
            continue
        maxh=max(height[i],maxh)
        minh=min(height[i],minh)
        if maxh-height[i]<=d and height[i]-minh<=d:
            buffer.append(height[i])
            check[i]=True
        i+=1
    buffer.sort()
    ans.extend(buffer)
for i in ans:
    print(i)
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![26333fcc85d88ff63ad3dbf12dce5f38](C:\Users\h1557\Desktop\计算概论\homework\h9截图\26333fcc85d88ff63ad3dbf12dce5f38.png)



## 2. 学习总结和收获

如果作业题目简单，有否额外练习题目，比如：OJ“计概2025fall每日选做”、CF、LeetCode、洛谷等网站题目。

本周也是期中考试周，不过好在周末就考完了。把前面的八皇后和汉诺塔的题目完成了，期中结束还得好好把前面的递归和回溯再试图弄懂一下。。



