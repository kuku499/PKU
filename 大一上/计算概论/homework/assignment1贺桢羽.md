# Assignment #1: 自主学习

Updated 1427 GMT+8 Sep 9, 2025

2025 fall, Complied by ==贺桢羽、心理与认知科学学院==



**作业的各项评分细则及对应的得分**

| 标准                                 | 等级                                                         | 得分 |
| ------------------------------------ | ------------------------------------------------------------ | ---- |
| 按时提交                             | 完全按时提交：1分<br/>提交有请假说明：0.5分<br/>未提交：0分  | 1 分 |
| 源码、耗时（可选）、解题思路（可选） | 提交了4个或更多题目且包含所有必要信息：1分<br/>提交了2个或以上题目但不足4个：0.5分<br/>少于2个：0分 | 1 分 |
| AC代码截图                           | 提交了4个或更多题目且包含所有必要信息：1分<br/>提交了2个或以上题目但不足4个：0.5分<br/>少于：0分 | 1 分 |
| 清晰头像、PDF文件、MD/DOC附件        | 包含清晰的Canvas头像、PDF文件以及MD或DOC格式的附件：1分<br/>缺少上述三项中的任意一项：0.5分<br/>缺失两项或以上：0分 | 1 分 |
| 学习总结和个人收获                   | 提交了学习总结和个人收获：1分<br/>未提交学习总结或内容不详：0分 | 1 分 |
| 总得分： 5                           | 总分满分：5分                                                |      |

>
>
>
>**说明：**
>
>1. **解题与记录：**
>
>   对于每一个题目，请提供其解题思路（可选），并附上使用Python或C++编写的源代码（确保已在OpenJudge， Codeforces，LeetCode等平台上获得Accepted）。请将这些信息连同显示“Accepted”的截图一起填写到下方的作业模板中。（推荐使用Typora https://typoraio.cn 进行编辑，当然你也可以选择Word。）无论题目是否已通过，请标明每个题目大致花费的时间。
>
>2. **课程平台：**课程网站位于Canvas平台（https://pku.instructure.com ）。该平台将在<mark>第2周</mark>选课结束后正式启用。在平台启用前，请先完成作业并将作业妥善保存。待Canvas平台激活后，再上传你的作业。
>
>3. **提交安排：**提交时，请首先上传PDF格式的文件，并将.md或.doc格式的文件作为附件上传至右侧的“作业评论”区。确保你的Canvas账户有一个清晰可见的本人头像，提交的文件为PDF格式，并且“作业评论”区包含上传的.md或.doc附件。
>
>4. **延迟提交：****如果你预计无法在截止日期前提交作业，请提前告知具体原因。这有助于我们了解情况并可能为你提供适当的延期或其他帮助。  
>
>请按照上述指导认真准备和提交作业，以保证顺利完成课程要求。





## 1. 题目

### E02733: 判断闰年

http://cs101.openjudge.cn/pctbook/E02733/



思路：



代码

```python
#1
y=input()
y=int(y)
if y%4==0:
    if y%100==0:
        if y%400!=0 or y%3200==0:
            print("N")
        else :
            print("Y")
    else:
        print("Y")
else:
    print("N")
```



代码运行截图 ==（至少包含有"Accepted"）==

![](C:\Users\h1557\Desktop\计算概论\homework\h1截图\微信图片_20250909162111_10_34.png)



### E02750: 鸡兔同笼

http://cs101.openjudge.cn/pctbook/E02750/



思路：



代码

```python
#2
a=input()
a=int(a)
if a%2!=0:
    print("0"+" "+"0")
else:
    max=a/2
    if a%4==0:
        min=a/4
    else:
        min=(a+2)/4
    print(str(int(min))+" "+str(int(max)))

```



代码运行截图 ==（至少包含有"Accepted"）==

![](C:\Users\h1557\Desktop\计算概论\homework\h1截图\微信图片_20250909165346_11_34.png)



### 50A. Domino piling

greedy, math, 800, http://codeforces.com/problemset/problem/50/A



思路：



代码

```python
#3
a=input()
b=a.split(" ")
M=int(b[0])
N=int(b[1])
if M%2==0 or N%2==0:
    k=M*N/2
else:
    k=M*N//2
print(str(int(k)))

```



代码运行截图 ==（至少包含有"Accepted"）==

![](C:\Users\h1557\Desktop\计算概论\homework\h1截图\微信图片_20250909173449_13_34.png)

### 1A. Theatre Square

math, 1000, https://codeforces.com/problemset/problem/1/A



思路：



代码

```python
#4
import math
a=input()
b=a.split(" ")
n=int(b[0])
m=int(b[1])
a=int(b[2])
x=math.ceil(m/a)
y=math.ceil(n/a)
s=x*y
print(str(s))

```



代码运行截图 ==（至少包含有"Accepted"）==

![](C:\Users\h1557\Desktop\计算概论\homework\h1截图\微信图片_20250909174821_15_34.png)



### 112A. Petya and Strings

implementation, strings, 1000, http://codeforces.com/problemset/problem/112/A



思路：



代码

```python
#5
A=input()
B=input()
A=A.upper()
B=B.upper()
if A>B:
    print("1")
if A<B:
    print("-1")
if A==B:
    print("0")
```



代码运行截图 ==（至少包含有"Accepted"）==

![](C:\Users\h1557\Desktop\计算概论\homework\h1截图\微信图片_20250909174821_15_34.png)

### 231A. Team

bruteforce, greedy, 800, http://codeforces.com/problemset/problem/231/A



思路：



代码

```python
#6
n=input()
n=int(n)
s=int(0)
for i in range(n):
    x=input()
    list=x.split()
    a=int(list[0])
    b=int(list[1])
    c=int(list[2])
    if a+b+c>=2:
        s+=1
    else:
        s=s
print(s)


```



代码运行截图 ==（至少包含有"Accepted"）==

![](C:\Users\h1557\Desktop\计算概论\homework\h1截图\微信图片_20250909194952_16_34.png)



## 2. 学习总结和收获

==如果作业题目简单，有否额外练习题目，比如：OJ“计概2025fall每日选做”、CF、LeetCode、洛谷等网站题目。==

零基础，自从预选闫老师的课后开始学习语法，感觉作业题目比较简单，但是OJ上的easy题做起来还是很吃力。。

![](C:\Users\h1557\Desktop\计算概论\homework\h1截图\baeff92d45cd0df1ffc6e0baca7f21fd.png)

![d142a20bc8a190d128074d1b98661b4e](C:\Users\h1557\Desktop\计算概论\homework\h1截图\d142a20bc8a190d128074d1b98661b4e.png)

![80d7262e862f0d5760d49412a48d8894](C:\Users\h1557\Desktop\计算概论\homework\h1截图\80d7262e862f0d5760d49412a48d8894.png)

![2d36ddf578d6a3fe9b3caf6001c88144](C:\Users\h1557\Desktop\计算概论\homework\h1截图\2d36ddf578d6a3fe9b3caf6001c88144.png)

![9ff684a75e1f8c949b109897f4c62669](C:\Users\h1557\Desktop\计算概论\homework\h1截图\9ff684a75e1f8c949b109897f4c62669.jpg)

![a2a957a7b148eb721e9d160858d7b6c1](C:\Users\h1557\Desktop\计算概论\homework\h1截图\a2a957a7b148eb721e9d160858d7b6c1.png)

![微信图片_20250909162111_10_34](C:\Users\h1557\Desktop\计算概论\homework\h1截图\微信图片_20250909162111_10_34.png)

![微信图片_20250910195412_26_34](C:\Users\h1557\Desktop\计算概论\homework\h1截图\微信图片_20250910195412_26_34.png)

![微信图片_20250910194706_25_34](C:\Users\h1557\Desktop\计算概论\homework\h1截图\微信图片_20250910194706_25_34.png)

![微信图片_20250909234354_21_34](C:\Users\h1557\Desktop\计算概论\homework\h1截图\微信图片_20250909234354_21_34.png)

![微信图片_20250909224456_20_34](C:\Users\h1557\Desktop\计算概论\homework\h1截图\微信图片_20250909224456_20_34.png)
