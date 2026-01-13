# Assignment #4: T-primes + 贪心

Updated 1814 GMT+8 Sep 30, 2025

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

### 34B. Sale

greedy, sorting, 900, https://codeforces.com/problemset/problem/34/B



思路：思路简单。5分钟。



代码

```python
#34B
li=list(map(int,input().split()))
n=li[0]
m=li[1]
ans=0
ansli=[]
li1=list(map(int,input().split()))
for i in li1:
    if i < 0:
        ansli.append(i)
ansli.sort()
if len(ansli)>=m:
    for x in range(m):
        ans+=-ansli[x]
else:
    ans+=-sum(ansli)
print(ans)

```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![image-20251002100506534](C:\Users\h1557\AppData\Roaming\Typora\typora-user-images\image-20251002100506534.png)



### 160A. Twins

greedy, sortings, 900, https://codeforces.com/problemset/problem/160/A



思路：5分钟。



代码

```python
#160A
n=int(input())
li=list(map(int,input().split()))
li.sort(reverse=True)
s=sum(li)
asum=0
ans=0
for i in range(n):
    asum+=li[i]
    if asum>s-asum:
        print(i+1)
        break
    else:
        continue

```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![image-20251002101756819](C:\Users\h1557\AppData\Roaming\Typora\typora-user-images\image-20251002101756819.png)



### 1879B. Chips on the Board

constructive algorithms, greedy, 900, https://codeforces.com/problemset/problem/1879/B



思路：数学思路。10分钟



代码

```python
#1879B
a=int(input())
for _ in range(a):
    n=int(input())
    ans=0
    x=list(map(int,input().split()))
    y=list(map(int,input().split()))
    ans1=sum(x)+min(y)*n
    ans2=sum(y)+min(x)*n
    if ans1<=ans2:
        print(ans1)
    else:
        print(ans2)
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![08cbc3a02767872e6076951fe359b264](C:\Users\h1557\Desktop\计算概论\homework\h4截图\08cbc3a02767872e6076951fe359b264.png)



### M01017: 装箱问题

greedy, http://cs101.openjudge.cn/pctbook/M01017/


思路：哎，又做复杂了。。这个很像taxi，但是感觉要难很多。提交了很多次，一直WA，不断debug才改对。看题解用列表解决else if较多的问题真的十分巧妙，感觉自己很笨。40分钟



代码

```python
#M01017
while 1:
    li=list(map(int,input().split()))
    if li!=[0,0,0,0,0,0]:
        ans=0
        ans+=li[5]
        if li[4]>=li[0]/11:
            ans+=li[4]
            li[0]=0
        else:
            ans+=li[4]
            li[0]=li[0]-li[4]*11
        if li[3]>=li[1]/5:
            ans+=li[3]
            rest=li[3]*20-li[1]*4
            li[1]=0
            if li[0]>0:
                if rest>=li[0]:
                    li[0]=0
                else:
                    li[0]=li[0]-rest
            li[3]=0
        else:
            ans+=li[3]
            li[1]=li[1]-li[3]*5
            li[3]=0
        if li[2]%4==0:
            ans+=li[2]/4
            li[2]=0
        elif li[2]%4==1:
            ans+=int(li[2]/4)+1
            li[2]=0
            if li[1]<5:
                if li[0]>=27-4*li[1]:
                    li[0]=li[0]-(27-4*li[1])
                else:
                    li[0]=0
                li[1]=0
            else:
                li[1]=li[1]-5
                if li[0]>=7:
                    li[0]=li[0]-7
                else:
                    li[0]=0
        elif li[2]%4==2:
            ans+=int(li[2]/4)+1
            li[2]=0
            if li[1] < 3:
                if li[0] >= 18 - 4 * li[1]:
                    li[0] = li[0]-(18 - 4 * li[1])
                else:
                    li[0] = 0
                li[1] = 0
            else:
                li[1] = li[1] - 3
                if li[0] >= 6:
                    li[0] = li[0] - 6
                else:
                    li[0] = 0
        elif li[2] % 4 == 3:
            ans += int(li[2] / 4)+1
            li[2]=0
            if li[1] < 1:
                if li[0] >= 9 - 4 * li[1]:
                    li[0] = li[0]-(9 - 4 * li[1])
                else:
                    li[0] = 0
                li[1] = 0
            else:
                li[1] = li[1] - 1
                if li[0] >= 5:
                    li[0] = li[0] - 5
                else:
                    li[0] = 0
        if li[1]==0:
            if li[0]%36==0:
                ans+=li[0]/36
            else:
                ans+=int(li[0]/36)+1
        else:
            if li[1]%9==0:
                ans+=li[1]/9
                li[1]=0
                if li[0]%36==0:
                    ans+=li[0]/36
                else:
                    ans+=int(li[0]/36)+1
            else:
                ans+=int(li[1]/9)+1
                rest=36-(li[1]%9)*4
                if li[0]<=rest:
                    ans=ans
                else:
                    li[0]=li[0]-rest
                    if li[0] % 36 == 0:
                        ans += li[0] / 36
                    else:
                        ans +=int(li[0]/36)+1
        print(int(ans))
    else:
        break


```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![f02eaec5a77733f2aa6babd602570fa4](C:\Users\h1557\Desktop\计算概论\homework\h4截图\f02eaec5a77733f2aa6babd602570fa4.png)



### M01008: Maya Calendar

implementation, http://cs101.openjudge.cn/practice/01008/



思路：

主要有两个问题：1.未考虑边缘情况2.忘记第一行要输出n了。。（30分钟）

代码

```python
#01008
n=int(input())
dic_Haab={"pop":0,"no":1,"zip":2,"zotz":3,"tzec":4,"xul":5,"yoxkin":6,"mol":7,"chen":8,"yax":9,"zac":10,"ceh":11,"mac":12
    ,"kankin":13,"muan":14,"pax":15,"koyab":16,"cumhu":17,"uayet":18}
li=["imix","ik","akbal","kan","chicchan","cimi","manik","lamat","muluk","ok","chuen","eb","ben","ix","mem","cib",
    "caban","eznab","canac","ahau"]
ans=[]
for i in range(n):
    date=input().split()
    day=int(date[0].replace(".",""))
    month=date[1]
    year=int(date[2])
    number=day+20*dic_Haab[month]+year*365
    year_=number//260
    days=number-year_*260
    dayfirst=days%13+1
    daysecond=li[days%20]
    ans.append(f"{dayfirst} {daysecond} {year_}")
print(n)
print("\n".join(ans))
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![3229b7f1e8cd8796cd613d0eea84bff4](C:\Users\h1557\Desktop\计算概论\homework\h4截图\3229b7f1e8cd8796cd613d0eea84bff4.png)



### 230B. T-primes（选做）

binary search, implementation, math, number theory, 1300, http://codeforces.com/problemset/problem/230/B



思路：先找出1-10**6的所有质数，判断题目数据是否等于这些质数的平方



代码

```python
#230B
n=int(input())
li=list(map(int,input().split()))
is_prime = [True] * (1000000+1)
is_prime[1]= False
primes = []
for i in range(2, 1000000 + 1):
    if is_prime[i]:
        primes.append(i)
    for p in primes:
        if i * p > 1000000:
            break
        is_prime[i * p] = False
        if i % p == 0:
            break
for q in li:
    root=int(q**0.5)
    if root*root==q and is_prime[root]:
        print("YES")
    else:
        print("NO")

```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![d023c75a3b56736f4f812721a1bdb528](C:\Users\h1557\Desktop\计算概论\homework\h4截图\d023c75a3b56736f4f812721a1bdb528.png)



## 2. 学习总结和收获

<mark>如果作业题目简单，有否额外练习题目，比如：OJ“计概2025fall每日选做”、CF、LeetCode、洛谷等网站题目。</mark>

这次的题目感觉做着很吃力，前前后后也做了一整天的时间，不知道月考会变成什么惨样。但是对于零基础，收获还是很多。逐渐开始接触贪心算法，有了更多的了解。代码优化这一块也是在这次作业里面的一次巨大收获，比如知道了用列表加循环可以巧妙避免很多的else-if。玛雅日历这道题，最开始一直不能AC，原来是忽略了边界请况，感觉做了很多这种有坑的题目了，下次一定要注意。通过T-primes这个题目，系统学习了埃氏筛和欧拉筛，替代了我以前做哥德巴赫猜想的判断质数方法，受益匪浅！



