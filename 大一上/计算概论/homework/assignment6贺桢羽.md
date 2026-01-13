# Assignment #6: 矩阵、贪心

Updated 1432 GMT+8 Oct 14, 2025

2025 fall, Complied by <mark>贺桢羽、心理与认知科学学院</mark>



>**说明：**
>
>1. **解题与记录：**
>
>  对于每一个题目，请提供其解题思路（可选），并附上使用Python或C++编写的源代码（确保已在OpenJudge， Codeforces，LeetCode等平台上获得Accepted）。请将这些信息连同显示“Accepted”的截图一起填写到下方的作业模板中。（推荐使用Typora https://typoraio.cn 进行编辑，当然你也可以选择Word。）无论题目是否已通过，请标明每个题目大致花费的时间。
>
>2. 提交安排：**提交时，请首先上传PDF格式的文件，并将.md或.doc格式的文件作为附件上传至右侧的“作业评论”区。确保你的Canvas账户有一个清晰可见的本人头像，提交的文件为PDF格式，并且“作业评论”区包含上传的.md或.doc附件。
> 
>4. **延迟提交：**如果你预计无法在截止日期前提交作业，请提前告知具体原因。这有助于我们了解情况并可能为你提供适当的延期或其他帮助。  
>
>请按照上述指导认真准备和提交作业，以保证顺利完成课程要求。





## 1. 题目

### M18211: 军备竞赛

greedy, two pointers, http://cs101.openjudge.cn/pctbook/M18211



思路：学习了双指针的方法。（20分钟）

代码

```python
#M18211
p=int(input())
li=list(map(int,input().split()))
li.sort()
i,j,c=0,len(li)-1,0
while i<j:
    if li[i]<=p:
        p-=li[i]
        i+=1
        c+=1
    elif c:
        p+=li[j]
        j-=1
        c-=1
    else:
        break
print(c+(li[i]<=p))

```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![4a1577fa541db61128024269108fddb4](C:\Users\h1557\Desktop\计算概论\homework\h6截图\4a1577fa541db61128024269108fddb4.png)



### M21554: 排队做实验

greedy, http://cs101.openjudge.cn/pctbook/M21554/



思路：跟一道E题差不多。（10分钟）

代码

```python
#M21554
n=int(input())
time=list(map(int,input().split()))
k=[]
for i in range(n):
    k.append((time[i],i+1))
k.sort()
s=0
su=0
for m in range(n-1):
    s+=k[m][0]
    su+=s
ans_li=[]
for i in k:
    ans_li.append(str(i[1]))
print(" ".join(ans_li))
print(format(su/n,".2f"))

```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![a3428227f7cfe99d95f58cfba1df01d7](C:\Users\h1557\Desktop\计算概论\homework\h6截图\a3428227f7cfe99d95f58cfba1df01d7.png)



### E23555: 节省存储的矩阵乘法

implementation, matrices, http://cs101.openjudge.cn/pctbook/E23555



思路：拷贝问题



代码

```python
#E23555
n,m1,m2=map(int,input().split())
ma1=[[0]*n]*n
m_1=[row[:] for row in ma1]
ma2=[[0]*n]*n
m_2=[row[:] for row in ma2]
for _ in range(m1):
    x,y,z=map(int,input().split())
    m_1[x][y]=z
for _ in range(m2):
    x,y,z=map(int,input().split())
    m_2[x][y]=z
ans=[[0]*n]*n
ans=[row[:] for row in ans]
for i in range(n):
    for q in range(n):
        for s in range(n):
            ans[i][q]+=m_1[i][s]*m_2[s][q]
for h in range(n):
    for j in range(n):
        if ans[h][j]!=0:
            print(h,j,ans[h][j])


```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![284b5e7ad9ca300de678d8eabbfd8a9e](C:\Users\h1557\Desktop\计算概论\homework\h6截图\284b5e7ad9ca300de678d8eabbfd8a9e.png)



### M12558: 岛屿周⻓

matices, http://cs101.openjudge.cn/pctbook/M12558


思路：

先把周围扩充，再进行周长计算。（20分钟）

代码

```python
#M12558

n,m=map(int,input().split())
ma=[[0]*(m+2)]
for _ in range(n):
    a=[0]
    a.extend(list(map(int,input().split())))
    a.append(0)
    ma.append(a)

ma.append([0]*(m+2))

ans=0
for x in range(n+2):
    for y in range(m+2):
        if ma[x][y]:
            tj=[ma[x-1][y],ma[x][y-1],ma[x][y+1],ma[x+1][y]]

            ans+=tj.count(0)
print(ans)

```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![a3428227f7cfe99d95f58cfba1df01d7](C:\Users\h1557\Desktop\计算概论\homework\h6截图\a3428227f7cfe99d95f58cfba1df01d7.png)



### M01328: Radar Installation

greedy, http://cs101.openjudge.cn/practice/01328/



思路：感觉和校门外的数差不多，一个求交集，一个求并集。（20分钟）



代码

```python
#01328
import math
case=0
while 1:
    n,d=map(int,input().split())
    case+=1
    if n!=0 and d!=0:
        island=[]
        for i in range(n):
            x,y=map(int,input().split())
            island.append((x,y))
        check=0
        fw=[]
        for k,v in island:
            if v>d:
                print(f"Case {case}: -1")
                check=1
                break
            else:
                start=k-math.sqrt(d**2-v**2)
                end=k+math.sqrt(d**2-v**2)
                fw.append((start,end))
        if check==1:
            input()
        else:
            fw.sort()
            ans=[]
            start=fw[0][0]
            end=fw[0][1]
            for k,v in fw:
                if k<=end:
                    start=k
                    end=min(v,end)
                else:
                    ans.append((start,end))
                    start=k
                    end=v
            ans.append((start,end))
            ans_=len(ans)
            print(f"Case {case}: {ans_}")
            input()
    else:
        break
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![2d4571606b61e5338d08612c733fb09b](C:\Users\h1557\Desktop\计算概论\homework\h6截图\2d4571606b61e5338d08612c733fb09b.png)



### 545C. Woodcutters

dp, greedy, 1500, https://codeforces.com/problemset/problem/545/C



思路：感觉这个题挺简单的，突然有信心了。（10分钟）



代码

```python
#545C
n=int(input())
tree=[]
for i in range(n):
    x,h=map(int,input().split())
    tree.append((x,h))
last=float("-inf")
cnt=0
for i in range(n-1):
    x=tree[i][0]
    h=tree[i][1]
    x_=tree[i+1][0]
    if x-h>last:
        cnt+=1
        last=x
    else:
        if x+h<x_:
            last=x+h
            cnt+=1
        else:
            last=x
cnt+=1
print(cnt)
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![7caff67e34643c2f61da2e21c489f2c0](C:\Users\h1557\Desktop\计算概论\homework\h6截图\7caff67e34643c2f61da2e21c489f2c0.png)



## 2. 学习总结和收获

<mark>如果作业题目简单，有否额外练习题目，比如：OJ“计概2025fall每日选做”、CF、LeetCode、洛谷等网站题目。</mark>

比较系统地学习了贪心和矩阵，了解了双指针法。另外在继续刷M题的过程中也越来越熟悉各种算法。在做矩阵时第一次遇到了深拷贝和浅拷贝的问题，深入学习了解决方法，果然有些东西只听了没有用，还是需要自己去实践。6道题里面军备竞赛反倒卡了我很久，因为我没有理清楚逻辑，不过多想一会还是想通了。岛屿周长用到了加保护圈的方法，做完这道题我感觉以前的题也可以这么做。这次的雷达题感觉和月考的校门外的树没有差别，不过就是一个求交集一个求并集。最后一道题感觉不是很难。我的小笔记本也是记了几十页笔记了，要继续加油!



