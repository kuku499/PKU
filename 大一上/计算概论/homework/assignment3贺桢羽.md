# Assignment #3: 语法练习

Updated 1440 GMT+8 Sep 23, 2025

2025 fall, Complied by <mark>贺桢羽，心理与认知科学学院</mark>



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

### E28674:《黑神话：悟空》之加密

http://cs101.openjudge.cn/pctbook/E28674/



思路：继续熟悉ASCII码（20分钟）



代码

```python
#E28674
k_=int(input())
k=k_%26
s=input()
ans=""
for i in s:
    m=ord(i)
    if m<97:
        if m-k<65:
            an=chr(m-k+26)
        else:
            an=chr(m-k)
    else:
        if m-k<97:
            an = chr(m - k + 26)
        else:
            an=chr(m-k)
    ans+=an
print(ans)
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>



![0e6883dee174c2c09725e025f80be74d](C:\Users\h1557\Desktop\计算概论\homework\h3截图\0e6883dee174c2c09725e025f80be74d.png)

### E28691: 字符串中的整数求和

http://cs101.openjudge.cn/pctbook/E28691/



思路：

依旧做复杂了。（5分钟）

answer=int(words [0] [:2])+int(words[1] [:2])

代码

```python
#E28691
words=input().split()
w11=int(words[0][0])
w12=int(words[0][1])
w1=w11*10+w12
w21=int(words[1][0])
w22=int(words[1][1])
w2=w21*10+w22
w=w1+w2
print(w)
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![695b25e21f1494211056b9ebb3ebbb1d](C:\Users\h1557\Desktop\计算概论\homework\h3截图\695b25e21f1494211056b9ebb3ebbb1d.png)



### M28664: 验证身份证号 

http://cs101.openjudge.cn/pctbook/M28664/



思路：5分钟



代码

```python
#M28664
n=int(input())
li=[7,9,10,5,8,4,2,1,6,3,7,9,10,5,8,4,2]
lis=[1,0,"X",9,8,7,6,5,4,3,2]
for _ in range(n):
    id=input()
    sum=0
    for i in range(17):
        sum+=int(id[i])*li[i]
    m=sum%11
    if id[-1]!="X":
        if lis[m]==int(id[-1]):
            print("YES")
        else:
            print("NO")
    else:
        if lis[m]==id[-1]:
            print("YES")
        else:
            print("NO")
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>



![30a8bd89b2bf3c8831b9744f5d1a9cf0](C:\Users\h1557\Desktop\计算概论\homework\h3截图\30a8bd89b2bf3c8831b9744f5d1a9cf0.png)

### M28678: 角谷猜想

http://cs101.openjudge.cn/pctbook/M28678/


思路：8分钟



代码

```python
#M286(78
n=int(input())
def zwz(x):
    y=x*3+1
    print(f"{x}*3+1={y}")
    return y
def psq(z):
    w=int(z/2)
    print(f"{z}/2={w}")
    return w
while n>1:
    if n%2==0:
        n=psq(n)
    else:
        n=zwz(n)
print("End")
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>



![7b7baf8e2b1af3ea4fdd976092c161cd](C:\Users\h1557\Desktop\计算概论\homework\h3截图\7b7baf8e2b1af3ea4fdd976092c161cd.png)

### M28700: 罗马数字与整数的转换

http://cs101.openjudge.cn/pctbook/M28700/



思路：首先考虑的是由整数转化为罗马数字，后面偷懒了，整数转罗马数字做好之后，直接创建了个对应的字典，罗马数字再转化为整数就方便了。（35分钟）



代码

```python
#M28770
def cz(s):
    try:
        int(s)
        return True
    except ValueError:
        return False
def zwz(n):
    ans=""
    n=int(n)
    if n >=1000:
        a1=n//1000
        ans+=f"{'M'*a1}"
        n=n-(n//1000)*1000
    if n>=100:
        if n//100==9:
            ans+="CM"
        elif n//100==4:
            ans+="CD"
        elif 5 <= n//100 <= 8:
            a2=n//100
            ans+=f"D{'C'*(a2-5)}"
        elif 1<= n//100 <= 3:
            a2=n//100
            ans+=f"{'C'*a2}"
        n=n-(n//100)*100
    if n>=10:
        if n//10==9:
            ans+="XC"
        elif n//10==4:
            ans+="XL"
        elif 5<= n//10 <=8:
            a3=n//10
            ans+=f"L{'X'*(a3-5)}"
        elif 1<= n//10 <=3:
            a3=n//10
            ans+=f"{'X'*a3}"
        n=n-(n//10)*10
    if n>=1:
        if n == 9:
            ans += "IX"
        elif n  == 4:
            ans += "IV"
        elif 5 <= n  <= 8:
            a4 = n
            ans += f"V{'I' * (a4 - 5)}"
        elif 1 <= n  <= 3:
            a4 = n
            ans += f"{'I' * a4}"
    return ans
q=input()
if cz(q):
    print(zwz(q))
else:
    dic={}
    for i in range(1,4000):
        dic[zwz(i)]=i
    print(dic[q])

```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![c67e9ac86160f892e942d488be3e0e48](C:\Users\h1557\Desktop\计算概论\homework\h3截图\c67e9ac86160f892e942d488be3e0e48.png)



### 158B. Taxi

*special problem, greedy, implementation, 1100,  https://codeforces.com/problemset/problem/158/B



思路：数学思维解决吧，听闫老师说这个题不简单，但是零基础在十分钟之内解决了，真的特别兴奋！！！！做完这个题再准备去做一下闫老师推荐的另外几个题。



代码

```python
#158B
import math
n=input()
li=list(map(int,input().split()))
a1=li.count(1)
a2=li.count(2)
a3=li.count(3)
a4=li.count(4)
ans=0
ans+=a4
if a3 <= a1:
    ans+=a3
    a1-=a3
    if 2*a2>=a1:
        ans+=a2
        ans+=math.ceil((a1-2*a2)/4)
    else:
        ans+=math.ceil(a1/2)
        ans+=math.ceil((a2-math.ceil(a1/2))/2)
else:
    ans+=a1
    a3-=a1
    ans+=a3
    ans+=math.ceil(a2/2)
print(ans)
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![93345b18b3f3ceb0c41672e7f6f39260](C:\Users\h1557\Desktop\计算概论\homework\h3截图\93345b18b3f3ceb0c41672e7f6f39260.png)





## 2. 学习总结和收获

<mark>如果作业题目简单，有否额外练习题目，比如：OJ“计概2025fall每日选做”、CF、LeetCode、洛谷等网站题目。</mark>

作业最后两道题感觉比较难，因为零基础，为了不断加强语法的掌握程度，仍然选择刷OJ的E题，争取在10.1前刷完E题，刷完之后准备开始学习算法，然后不再局限于OJ的题，可以刷一些如LeetCode的题目。然后我发现自己有个不好的习惯，就是在自己刷完题目AC之后，不会选择再去看题解，参考题解的做法，感觉这样收获会减少很多，所以本周开始了对题解的学习，通过学习题解找到更好的方法。希望继续加油吧！



