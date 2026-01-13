# Assignment #2: 语法练习

Updated 1335 GMT+8 Sep 16, 2025

2025 fall, Complied by <mark>贺桢羽、心理与认知科学学院</mark>



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
>4. **延迟提交：**如果你预计无法在截止日期前提交作业，请提前告知具体原因。这有助于我们了解情况并可能为你提供适当的延期或其他帮助。  
>
>请按照上述指导认真准备和提交作业，以保证顺利完成课程要求。





## 1. 题目

### 263A. Beautiful Matrix

implementation, 800, https://codeforces.com/problemset/problem/263/A



思路：感觉做的有点蠢蠢的，不过零基础小白做出来就很开心啦



代码

```python
# #1
l1=input().split()
l2=input().split()
l3=input().split()
l4=input().split()
l5=input().split()
step=0
if "1" in l1:
    step+=2
elif "1" in l2:
    step+=1
elif "1" in l4:
    step+=1
elif "1" in l5:
    step+=2

if int(l1[0]) or int(l2[0]) or int(l3[0]) or int(l4[0]) or int(l5[0]) or int(l1[4]) or int(l2[4]) or int(l3[4]) or int(l4[4]) or int(l5[4]) :
    step+=2
elif int(l1[1]) or int(l2[1]) or int(l3[1]) or int(l4[1]) or int(l5[1]) or int(l1[3]) or int(l2[3]) or int(l3[3]) or int(l4[3]) or int(l5[3]) :
    step+=1
print(step)


```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![e8c4d005207fee5c937e11cbc7220f75](C:\Users\h1557\Desktop\计算概论\homework\h2截图\e8c4d005207fee5c937e11cbc7220f75.png)



### 1328A. Divisibility Problem

math, 800, https://codeforces.com/problemset/problem/1328/A



思路：最开始的代码一直超时，感觉自己老是觉得计算机的计算能力十分强大，根本没有用适当的数学方法将解答过程进行简化。做完这道题和上周的某道题之后，发现很多时候做题还是得先考虑使用数学思维进行简化。



代码

```python
#2
t=int(input())
for i in range(t):
    list=input().split()
    a=int(list[0])
    b=int(list[1])
    n=0
    if a%b!=0:
          n=(a//b+1)*b-a
          print(n)
    else:
        print(n)
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![9a5acdd8ef153f65d0035fc4efdc6ae8](D:\weixin\xwechat_files\wxid_wg6sc5apx61g12_cc23\temp\RWTemp\2025-09\9e20f478899dc29eb19741386f9343c8\9a5acdd8ef153f65d0035fc4efdc6ae8.png)





### 427A. Police Recruits

implementation, 800, https://codeforces.com/problemset/problem/427/A



思路：正常思路。



代码

```python
#3
n=int(input())
lis=list(map(int,input().split()))
a=0
now=0
ans=0
for t in lis:
        if t+now<0:
            ans+=1
        else:
            now+=t

print(ans)
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![c5b7a9aa149e43b3198cbc10ded2eeac](C:\Users\h1557\Desktop\计算概论\homework\h2截图\c5b7a9aa149e43b3198cbc10ded2eeac.png)



### E02808: 校门外的树

implementation, http://cs101.openjudge.cn/pctbook/E02808/


思路：使用了集合的加减法，感觉做得比较巧妙。



代码

```python
#4
LM=list(map(int,input().split()))
L=LM[0]
M=LM[1]
L_list=[]
for m in range(L+1):
    L_list.append(m)
L_set=set(L_list)
for i in range(M):
    l=list(map(int,input().split()))
    be=l[0]
    en=l[1]
    li=[]
    for num in range(be,en+1):
        li.append(num)
    li_set=set(li)
    L_set=L_set-li_set
print(len(L_set))

```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![def4704da49b3b47970ddf1dade6d00e](C:\Users\h1557\Desktop\计算概论\homework\h2截图\def4704da49b3b47970ddf1dade6d00e.png)





### sy60: 水仙花数II

implementation, https://sunnywhy.com/sfbj/3/1/60



思路：



代码

```python
#5
n=input().split()
a=int(n[0])
b=int(n[1])
answer=[]
for num in range(a,b+1):
    st=str(num)
    num1=int(st[0])
    num2=int(st[1])
    num3=int(st[2])
    if num==num1**3+num2**3+num3**3:
        answer.append(str(num))
if answer:
    print(" ".join(answer))
else:
    print("NO")
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>



![16a4677ea8203c781d3a8406734e9ab7](C:\Users\h1557\Desktop\计算概论\homework\h2截图\16a4677ea8203c781d3a8406734e9ab7.png)

### M01922: Ride to School

implementation, http://cs101.openjudge.cn/pctbook/M01922/



思路：数学问题。



代码

```python
#M01922
import math
while True:
        n=int(input())
        lis1=[]
        if n!=0:
           for i in range(n):
               a=list(map(int,input().split()))
               v=a[0]
               t=a[1]

               ts=4500/v*3.6
               T=t+ts
               if t>=0:
                   lis1.append(math.ceil(T))
               else:
                  continue
           lis1.sort()
           print(lis1[0])
        else:
            break

```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![aa045b0aaef9cc423a68298de94969a0](C:\Users\h1557\Desktop\计算概论\homework\h2截图\aa045b0aaef9cc423a68298de94969a0.png)



## 2. 学习总结和收获

<mark>如果作业题目简单，有否额外练习题目，比如：OJ“计概2025fall每日选做”、CF、LeetCode、洛谷等网站题目。</mark>

感觉有一些进步了，刷OJ上的easy题越来越得心应手了。主要收获如下：

1.做本周作业的第六题明白了浮点数在内部的存储导致两次除法会有误差，解决办法是直接列出总的计算式子。

2.学会了使用try：except EOFError：解决部分presentation error的问题。

3.会使用f-string解决格式问题。

4.学会了更多函数，比如：ord() chr() index() map()等

5.认识到更多取整方式 ，比如：直接使用math.ceil()，int()，round(x,n)，math.floor()，f"{x:.nf}"

6.通过验证哥德巴赫猜想，学会了判断质数的方法。

7.学会了处理矩阵的部分方法。

8.E02899矩阵交换行那道题看了大佬和老师们在群里的解答还是没搞懂为何出现presentation error的问题。。。也不知道咋搞，代码贴到下面了。

希望自己能继续加油！！

![image-20250917230616221](C:\Users\h1557\AppData\Roaming\Typora\typora-user-images\image-20250917230616221.png)

![微信图片_20250918160721_59_34](C:\Users\h1557\Desktop\计算概论\homework\h2截图\微信图片_20250918152335_57_34.png)![d5b775a249261845e60f467f0fd8e3d2](C:\Users\h1557\Desktop\计算概论\homework\h2截图\d5b775a249261845e60f467f0fd8e3d2.png)![微信图片_20250918164947_60_34](C:\Users\h1557\Desktop\计算概论\homework\h2截图\微信图片_20250918164947_60_34.png)![21205902749d297690bba21271f876e2](C:\Users\h1557\Desktop\计算概论\homework\h2截图\21205902749d297690bba21271f876e2.png)

![微信图片_20250921150817_70_34](C:\Users\h1557\Desktop\计算概论\homework\h2截图\微信图片_20250921150817_70_34.png)![微信图片_20250918193228_65_34](C:\Users\h1557\Desktop\计算概论\homework\h2截图\微信图片_20250918193228_65_34.png)![微信图片_20250919093430_67_34](C:\Users\h1557\Desktop\计算概论\homework\h2截图\微信图片_20250919094104_68_34.png)![微信图片_20250918201228_66_34](C:\Users\h1557\Desktop\计算概论\homework\h2截图\微信图片_20250918201228_66_34.png)![微信图片_20250918184831_62_34](C:\Users\h1557\Desktop\计算概论\homework\h2截图\微信图片_20250918184831_62_34.png)![微信图片_20250918192405_64_34](C:\Users\h1557\Desktop\计算概论\homework\h2截图\微信图片_20250918192405_64_34.png)![微信图片_20250918190216_63_34](C:\Users\h1557\Desktop\计算概论\homework\h2截图\微信图片_20250918190216_63_34.png)![微信图片_20250918170746_61_34](C:\Users\h1557\Desktop\计算概论\homework\h2截图\微信图片_20250918170746_61_34.png)![微信图片_20250919095037_69_34](C:\Users\h1557\Desktop\计算概论\homework\h2截图\微信图片_20250919095037_69_34.png)
