# Assignment #5: 20251009 cs101 Mock Exam寒露第二天

Updated 1651 GMT+8 Oct 9, 2025

2025 fall, Complied by <mark>同学的姓名、院系</mark>



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

### E29895: 分解因数

implementation, http://cs101.openjudge.cn/practice/29895/



思路：比较简单



代码

```python
 n=int(input())
for i in range(2,int(n**0.5)+1):
    if n%i==0:
        print(int(n/i))
        break
    else:
        continue

```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![5fbedf68a57f4d0c46f12c99b0507747](C:\Users\h1557\Desktop\计算概论\homework\h5截图\5fbedf68a57f4d0c46f12c99b0507747.png)



### E29940: 机器猫斗恶龙

greedy, http://cs101.openjudge.cn/practice/29940/



思路：比较简单。看题解学会了float（‘inf’）表示无穷



代码

```python
n=int(input())
a=list(map(int,input().split()))
li=[]
q=0
for i in a:
    q+=i
    li.append(q)
li.sort()
if li[0]>=0:
    print(1)
else:
    print(-li[0]+1)
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![image-20251009192400588](C:\Users\h1557\AppData\Roaming\Typora\typora-user-images\image-20251009192400588.png)





### M29917: 牛顿迭代法

implementation, http://cs101.openjudge.cn/practice/29917/



思路：考试的时候忘记了牛顿迭代法是什么，没有进行尝试，但其实是很简单的。



代码

```python
#29917
while 1:
    try:
        n=float(input())
        a=1
        b=1
        while abs(n**0.5-a)>1e-6:
            a=a-(a**2-n)/(2*a)
            b+=1
        print(b,format(a,".2f"))
    except EOFError:
        break
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![4396fb5bfc7988e0a96bfc674a35f0c3](C:\Users\h1557\Desktop\计算概论\homework\h5截图\4396fb5bfc7988e0a96bfc674a35f0c3.png)



### M29949: 贪婪的哥布林

greedy, http://cs101.openjudge.cn/practice/29949/


思路：

考试的时候做复杂了，感觉对字典和字典键，值的本质还没有理解透彻，要多练习！看完题解，感觉自己太蠢了。

代码

```python
li=list(map(int,input().split()))
n=li[0]
m=li[1]
di={}
ans=0
w=0
for i in range(n):
    li1=list(map(int,input().split()))
    di[f"{li1[0]} {li1[1]}"]=li1[0]/li1[1]
dic1=sorted(di.items(), key=lambda x: x[1], reverse=True)
for s in dic1:
    k=s[0]
    v=s[1]
    k=list(map(int,k.split()))
    if w+k[1]<=m:
        ans+=k[0]
        w+=k[1]
    else:
        ans+=(m-w)*v
        break
print(format(ans,'.2f'))

```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![769d903a0465d4fa8b5d4aec99efa71b](C:\Users\h1557\Desktop\计算概论\homework\h5截图\769d903a0465d4fa8b5d4aec99efa71b.png)



### M29918: 求亲和数

implementation, http://cs101.openjudge.cn/practice/29918/



思路：最开始使用普通的方法，超时。考完之后，看群里的讨论，逐渐理解了筛法，又类似于用因数标记某些数字。



代码

```python
n = int(input())
div_sum = [0] * (n + 1)
for i in range(1, n + 1):
    div_sum[i] = 1
for i in range(2, int(n**0.5) + 1):
    for j in range(i * i, n + 1, i):
        if j // i != i:
            div_sum[j] += i + j // i
        else:
            div_sum[j] += i
for x in range(2, n + 1):
    y = div_sum[x]
    if y <= n and x < y and div_sum[y] == x:
        print(x, y)
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![357da5572c2fbddfcf9885292e84d623](C:\Users\h1557\Desktop\计算概论\homework\h5截图\357da5572c2fbddfcf9885292e84d623.png)



### T29947:校门外的树又来了（选做）

http://cs101.openjudge.cn/practice/29947/



思路：考试的时候运行内存爆了，后来下来优化了。。。



代码

```python
#299947
l,m=map(int,input().split())
li=[]
su=0
for _ in range(m):
    a,b=map(int,input().split())
    li.append((a,b))
li.sort()
ans=[]
start,end=li[0]
for (k,v) in li:
    if k<=end+1:
        end=max(end,v)
    else:
        ans.append((start,end))
        start,end=k,v
ans.append((start,end))
for m in ans:
    su+=m[1]-m[0]+1
an=l-su
print(an+1)
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![03bb40cb2072695f145619fb6230f135](C:\Users\h1557\Desktop\计算概论\homework\h5截图\03bb40cb2072695f145619fb6230f135.png)



## 2. 学习总结和收获

<mark>如果作业题目简单，有否额外练习题目，比如：OJ“计概2025fall每日选做”、CF、LeetCode、洛谷等网站题目。</mark>

这次月考只AC了三道，说实话当时很难过的，感觉自己平时的努力也有点白费了。不过说实话，这次的失败让我长了很多教训，比如保留小数这种小问题上，我在平时练习时用了AI解决问题但是并没有真正让知识进入脑子，只是肤浅地使用，导致考试的时候记不起来语法。另外，对题解的学习我一定要提上日程，以前做过的AC的题也可以再看一遍题解，优化算法，减短代码长度。最近逐渐对时间复杂度有了理解，对超时问题的解决方法掌握程度增加（包括打表哈哈哈哈哈），筛法也更熟练了。E题已经刷完了，开始M题了！



