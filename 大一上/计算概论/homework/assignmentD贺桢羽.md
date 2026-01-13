# Assignment #D: Mock Exam下元节

Updated 1729 GMT+8 Dec 4, 2025

2025 fall, Complied by <mark>贺桢羽、心理与认知科学学院</mark>



>**说明：**
>
>1. Dec⽉考： AC4<mark>（请改为同学的通过数）</mark> 。考试题⽬都在“题库（包括计概、数算题目）”⾥⾯，按照数字题号能找到，可以重新提交。作业中提交⾃⼰最满意版本的代码和截图。
>
>2. 解题与记录：对于每一个题目，请提供其解题思路（可选），并附上使用Python或C++编写的源代码（确保已在OpenJudge， Codeforces，LeetCode等平台上获得Accepted）。请将这些信息连同显示“Accepted”的截图一起填写到下方的作业模板中。（推荐使用Typora https://typoraio.cn 进行编辑，当然你也可以选择Word。）无论题目是否已通过，请标明每个题目大致花费的时间。
>
>3. 提交安排：提交时，请首先上传PDF格式的文件，并将.md或.doc格式的文件作为附件上传至右侧的“作业评论”区。确保你的Canvas账户有一个清晰可见的本人头像，提交的文件为PDF格式，并且“作业评论”区包含上传的.md或.doc附件。
> 
>4. 延迟提交：如果你预计无法在截止日期前提交作业，请提前告知具体原因。这有助于我们了解情况并可能为你提供适当的延期或其他帮助。  
>
>请按照上述指导认真准备和提交作业，以保证顺利完成课程要求。





## 1. 题目

### E29945:神秘数字的宇宙旅行 

implementation, http://cs101.openjudge.cn/practice/29945

思路：简单题



代码

```python
n=int(input())
while n!=1:
    if n%2==0:
        n_=int(n/2)
        print(f"{n}/2={n_}")
        n=n_
    else:
        n_=n*3+1
        print(f"{n}*3+1={n_}")
        n=n_
print("End")
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![3b46393e7708bbafe9ea0ee90293a002](C:\Users\h1557\Desktop\计算概论\homework\hD截图\3b46393e7708bbafe9ea0ee90293a002.png)



### E29946:删数问题

monotonic stack, greedy, http://cs101.openjudge.cn/practice/29946

思路：单调栈。最开始一直没做出来，后来突然想起来。



代码

```python
n=int(input())
k=int(input())
li=list(str(n))
stack=[]
for digit in li:
    while k > 0 and stack and stack[-1] > digit:
        stack.pop()
        k -= 1
    stack.append(digit)
if k > 0:
    stack = stack[:-k]
result = int("".join(stack))
print(result)
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![image-20251208162953028](C:\Users\h1557\AppData\Roaming\Typora\typora-user-images\image-20251208162953028.png)



### E30091:缺德的图书馆管理员

greedy, http://cs101.openjudge.cn/practice/30091

思路：这道greedy还是比较好想。



代码

```python
l=int(input())
n=int(input())
li=list(map(int,input().split()))
li1=[]
for i in li:
    li1.append(min(i,l+1-i))
t_max=max(l+1-li[0],li[-1])
t_min=max(li1)
print(t_min,t_max
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![2907226f0b5290aee37c0a60c6638202](D:\weixin\xwechat_files\wxid_wg6sc5apx61g12_cc23\temp\RWTemp\2025-12\9e20f478899dc29eb19741386f9343c8\2907226f0b5290aee37c0a60c6638202.png)



### M27371:Playfair密码

simulation，string，matrix, http://cs101.openjudge.cn/practice/27371


思路：好难写，写了一个小时。。导致后面两个题都没时间看了，虽然看了也可能不会。

代码

```python
from collections import deque
word="abcdefghiklmnopqrstuvwxyz"
word=list(word)
st=list(input())
st_=deque()
for i in st:
    if i=="j":
        i="i"
    if i not in st_:
        st_.append(i)
        word.remove(i)
st_.extend(word)
ma=[]
for _ in range(5):
    li=[]
    for i in range(5):
        li.append(st_.popleft())
    ma.append(li)
mas={}
for x in range(5):
    for y in range(5):
        mas[ma[x][y]]=(x,y)
n=int(input())
for _ in range(n):
    k=input()
    res=[c if c != 'j' else 'i' for c in k]
    a=[]
    i=0
    while i < len(res):
        c1=res[i]
        if i == len(res)-1:
            p="q" if c1=="x" else "x"
            a.append((c1,p))
            i+=1
        else:
            c2=res[i+1]
            if c1!=c2:
                a.append((c1,c2))
                i+=2
            else:
                p="q" if c1=="x" else "x"
                a.append((c1,p))
                i+=1
    ans=[]
    for i in a:
        l=i[0]
        r=i[1]
        lx,ly=mas[l]
        rx,ry=mas[r]
        if rx==lx:
            ans.append(ma[lx][(ly+1)%5])
            ans.append(ma[rx][(ry+1)%5])
        elif ry==ly:
            ans.append(ma[(lx+1)%5][ly])
            ans.append(ma[(rx+1)%5][ry])
        else:
            ans.append(ma[lx][ry])
            ans.append(ma[rx][ly])
    print("".join(ans))
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![c9289a729fea99ee4bb0ab74394045f2](C:\Users\h1557\Desktop\计算概论\homework\hD截图\c9289a729fea99ee4bb0ab74394045f2.png)



### T30201:旅行售货商问题

dp,dfs, http://cs101.openjudge.cn/practice/30201

思路：对着AI给的代码学习了一下，但是感觉状压dp还是很难，有点超出我能掌握的范围了。



代码

```python
n = int(input())
cost = [list(map(int, input().split())) for _ in range(n)]
INF = float('inf')
dp = [[INF] * n for _ in range(1 << n)]
dp[1 << 0][0] = 0 
for mask in range(1 << n):
    for u in range(n):
        if dp[mask][u] == INF:
            continue
        for v in range(n):
            if not (mask & (1 << v)):
                new_mask = mask | (1 << v)
                if dp[new_mask][v] > dp[mask][u] + cost[u][v]:
                    dp[new_mask][v] = dp[mask][u] + cost[u][v]
full_mask = (1 << n) - 1
min_cost = INF
for u in range(n):
    min_cost = min(min_cost, dp[full_mask][u] + cost[u][0])
print(min_cost)
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![image-20251208163938127](C:\Users\h1557\AppData\Roaming\Typora\typora-user-images\image-20251208163938127.png)



### T30204:小P的LLM推理加速

greedy, http://cs101.openjudge.cn/practice/30204

思路：这个题没有第五题难，只要想到了贪心算法，并且使用前缀和优化就比较简单了。



代码

```python
n,m=map(int,input().split())
x=[]
t=[]
for _ in range(n):
    x1,y1=map(int,input().split())
    x.append(x1)
    t.append(x1+y1)
x.sort()
mi=min(t)
ans=0
pr=[0]
for i in x:
    pr.append(pr[-1]+i)
for i in range(len(pr)):
    ans=max(ans,((m-pr[i])//mi)*2+i)
print(ans)
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![94c673917f6431d15f3b72bb8c8a24c2](C:\Users\h1557\Desktop\计算概论\homework\hD截图\94c673917f6431d15f3b72bb8c8a24c2.png)



## 2. 学习总结和收获

如果作业题目简单，有否额外练习题目，比如：OJ“计概2025fall每日选做”、CF、LeetCode、洛谷等网站题目。

本次月考AC4，拼尽全力与T4战斗了一个小时，T4就像把五六个E题融合成一道题的感觉，而花费很多时间说明基础掌握得非常不牢固，现在就是很焦虑，看到新题总是要想很久，即使知道思路，完成这个思路的语法也很难写对。现在属于简单题做很久，难题做不出来的状态，希望期末机考能状态好一点。。。。。。最近继续练习洛谷上的题目，还是收获不少。



