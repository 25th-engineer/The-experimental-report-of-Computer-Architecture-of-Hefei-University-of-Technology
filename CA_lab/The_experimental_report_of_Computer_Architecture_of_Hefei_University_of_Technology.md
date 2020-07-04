<h1 align=center>合肥工业大学《计算机体系结构》实验报告（2020年版）</h1>
&emsp;&emsp;内容有点多。<br>
&emsp;&emsp;在用<b>matlab</b>绘图时时间比较紧（赶在deadline之前），因此横纵坐标与图例的英文描述可能有些语法错误或者用词不当，但博主懒得重新再跑一遍程序了（图有点多）。在报告末尾附了绘图的<b>matlab</b>代码，有需要的朋友可以自己改一改。<br>
&emsp;&emsp;2017级的学生应该都已经交实验报告了吧，如果有人来抄博主这个写得稀烂的报告，弄不好两个都得零分，害怕……（愿2017级的校友同学昨天[2020-07-03]就已经提交了）<br>
&emsp;&emsp;博主在安装Simplescalar时也遇到了许多坑，改天找时间写个简单的教程；之前在CSDN上搜索的时候，没发现啥有帮助的资料，最后还得自己摸索。<br>
&emsp;&emsp;发现有任何错误或者疑问欢迎在评论区（或者<a href="mailto:u25th_engineer@163.com?&bcc=u25th_engineer@mail2tor.com&subject=Hello DFZ&body=Nice%20to%20meet%20you!" target="_top">E-mail</a>）反馈。


[TOC]


# 实验一 流水线相关与指令调度
## 1 实验内容
### 1.1 流水线相关
>&emsp;&emsp;a. 用WinMIPS64模拟器执行下列三个程序（任选一个）：
&emsp;&emsp;求阶乘程序factorial.s
&emsp;&emsp;插入排序程序isort.s
&emsp;&emsp;乘法计算程序mult.s
&emsp;&emsp;分别以步进、连续、设置断点的方式运行程序，观察程序在流水线中的执行情况，观察CPU中寄存器和存储器的内容。
&emsp;&emsp;掌握WinMIPS64的操作和使用。
&emsp;&emsp;b. 用MIPS64汇编语言编写代码文件*.s，程序中应包括结构相关。用WinMIPS64模拟器运行你编写的程序，通过模拟：
> * 找出存在结构相关的指令对以及相应的结构相关的部件；
> * 记录由结构相关引起的暂停时钟周期数，计算暂停时钟周期数占总执行周期数的百分比；

>&emsp;&emsp;论述结构相关对 CPU 性能的影响，讨论解决结构相关的方法。

>&emsp;&emsp;c. 用MIPS64汇编语言编写代码文件*.s，程序中应包括数据相关。在不采用定向技术的情况下，用WinMIPS64/WinDLX模拟器运行存在数据相关的程序。记录数据相关引起的暂停时钟周期数以及程序执行的总时钟周期数，计算暂停时钟周期数占总执行周期数的百分比。
&emsp;&emsp;d. 在采用定向技术的情况下，用WinMIPS64模拟器再次运行程序。重复上述3中的工作，并计算采用定向技术后性能提高的倍数。

### 1.2 指令调度
>&emsp;&emsp;a. 用指令调度技术解决流水线中的结构相关与数据相关
>>&emsp;&emsp;i. 用MIPS64汇编语言编写代码文件*.s，程序中应包括数据相关与结构相关（你可以自己设置各个功能单元的延迟时间）
&emsp;&emsp;ii.  用WinMIPS64模拟器运行你所写的程序。记录程序执行过程中各种相关发生的次数、发生相关的指令组合，以及程序执行的总时钟周期数；
&emsp;&emsp;iii. 采用指令调度技术对程序进行指令调度，消除相关（手工调度^_^）；
&emsp;&emsp;iv. 用WinMIPS64模拟器运行调度后的程序，观察程序在流水线中的执行情况，记录程序执行的总时钟周期数；
&emsp;&emsp;v. 根据记录结果，比较调度前和调度后的性能。论述指令调度对于提高CPU性能的意义。

>&emsp;&emsp;b. 用循环展开、寄存器换名以及指令调度提高性能
>>&emsp;&emsp;i. 用MIPS64汇编语言编写代码文件*.s，程序中包含一个循环次数为4的整数倍的简单循环；
&emsp;&emsp;ii. 用WinMIPS64模拟器运行该程序。记录执行过程中各种相关发执行的时钟周期数；
&emsp;&emsp;iii. 将循环展开3次，将4个循环体组成的代码代替原来的循环的修改。然后,对新的循环体进行寄存器换名和指令调度；
&emsp;&emsp;iv. 用WinMIPS64模拟器运行修改后的程序，记录执行过程中各种及程序执行的总时钟周期数；
&emsp;&emsp;v. 根据记录结果，比较循环展开、指令调度前后的性能。
## 2 实验方法
>&emsp;&emsp;借助WinMIPS64模拟器运行MIPS汇编代码。
## 3 结果与分析
### 3.1流水线相关
**执行程序**
<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src="https://img-blog.csdnimg.cn/20200704000616622.png">
    <br>
    <div style="color:orange; border-bottom: 1px solid #d9d9d9;
    display: inline-block;
    color: #999;
    padding: 2px;">图 1 架构1</div>
</center>

<br>

>&emsp;&emsp;插入排序程序i```sort.s```
>&emsp;&emsp;**步进：**

<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src="https://img-blog.csdnimg.cn/20200704000722953.png">
    <br>
    <div style="color:orange; border-bottom: 1px solid #d9d9d9;
    display: inline-block;
    color: #999;
    padding: 2px;">图 2 single cycle</div>
</center>

<br>

<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src="https://img-blog.csdnimg.cn/20200704100615152.png">
    <br>
    <div style="color:orange; border-bottom: 1px solid #d9d9d9;
    display: inline-block;
    color: #999;
    padding: 2px;">图 3 multiple cycle</div>
</center>

<br>

>&emsp;&emsp;**连续：**
<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src="https://img-blog.csdnimg.cn/20200704100835283.png">
    <br>
    <div style="color:orange; border-bottom: 1px solid #d9d9d9;
    display: inline-block;
    color: #999;
    padding: 2px;">图 4 连续</div>
</center>

<br>

>**设置断点：**
<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src="https://img-blog.csdnimg.cn/2020070410102938.png">
    <br>
    <div style="color:orange; border-bottom: 1px solid #d9d9d9;
    display: inline-block;
    color: #999;
    padding: 2px;">图 5 break point_single cycle_1</div>
</center>

<br>

<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src="https://img-blog.csdnimg.cn/20200704101842111.png">
    <br>
    <div style="color:orange; border-bottom: 1px solid #d9d9d9;
    display: inline-block;
    color: #999;
    padding: 2px;">图 6 break point_single cycle_2</div>
</center>
<br>
<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src="https://img-blog.csdnimg.cn/2020070410193979.png">
    <br>
    <div style="color:orange; border-bottom: 1px solid #d9d9d9;
    display: inline-block;
    color: #999;
    padding: 2px;">图 7 break point_single cycle_3</div>
</center>
<br>

<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src="https://img-blog.csdnimg.cn/20200704102024872.png">
    <br>
    <div style="color:orange; border-bottom: 1px solid #d9d9d9;
    display: inline-block;
    color: #999;
    padding: 2px;">图 8 break point_single cycle_4</div>
</center>
<br>

<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src="https://img-blog.csdnimg.cn/20200704102102775.png">
    <br>
    <div style="color:orange; border-bottom: 1px solid #d9d9d9;
    display: inline-block;
    color: #999;
    padding: 2px;">图 9 break point_single cycle_5</div>
</center>
<br>

<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src="https://img-blog.csdnimg.cn/20200704102132687.png">
    <br>
    <div style="color:orange; border-bottom: 1px solid #d9d9d9;
    display: inline-block;
    color: #999;
    padding: 2px;">图 10 break point_single cycle_6</div>
</center>
<br>

**结构相关**
>&emsp;&emsp;``data_and_structure_stalls_1.s``<br>
&emsp;&emsp;执行方式：<br>
&emsp;&emsp;```single cycle```

<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src="https://img-blog.csdnimg.cn/20200704102348818.png">
    <br>
    <div style="color:orange; border-bottom: 1px solid #d9d9d9;
    display: inline-block;
    color: #999;
    padding: 2px;">图 11 架构2</div>
</center>
<br>

<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src="https://img-blog.csdnimg.cn/20200704102418480.png">
    <br>
    <div style="color:orange; border-bottom: 1px solid #d9d9d9;
    display: inline-block;
    color: #999;
    padding: 2px;">图 12 structural stall in EX（cycle 20）</div>
</center>
<br>

>&emsp;&emsp;指令对：
>>ADD.D F3,F3,F1	#norm+=coeff[0];<br>
jal coeff_one         ; call coeff_one<br>
daddi r2,r0,8   ; r2 = 8<br>
L.D F1,coeff(r2)  # F1=coeff[1]

>&emsp;&emsp;相关部件：
>>EX

<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src="https://img-blog.csdnimg.cn/20200704102550471.png">
    <br>
    <div style="color:orange; border-bottom: 1px solid #d9d9d9;
    display: inline-block;
    color: #999;
    padding: 2px;">图 13 structural stall in EX（cycle 28）</div>
</center>
<br>

>&emsp;&emsp;指令对：
>>ADD.D F3,F3,F1	#norm+=coeff[1];<br>
jal coeff_two         ; call coeff_two<br>
daddi r2,r0,16   ; r2 = 16<br>
L.D F1,coeff(r2)  # F1=coeff[2]

>&emsp;&emsp;相关部件：
>>EX

<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src="https://img-blog.csdnimg.cn/20200704102644385.png">
    <br>
    <div style="color:orange; border-bottom: 1px solid #d9d9d9;
    display: inline-block;
    color: #999;
    padding: 2px;">图 14 structural stall in EX（cycle 37）</div>
</center>
<br>

>&emsp;&emsp;指令对：
>>ADD.D F3,F3,F1	#norm+=coeff[2];<br>
jal go_result         ; call go_result<br>
go_result:	halt<br>
out:    halt

>&emsp;&emsp;相关部件：
>>EX

>&emsp;&emsp;**总周期数：```41```<br>
&emsp;&emsp;结构相关周期数：```3```<br>
&emsp;&emsp;占比：```3 / 41 ≈ 7.32%```**

>&emsp;&emsp;解决结构相关的方法：
>>&emsp;&emsp;为了避免结构相关，可以考虑采用资源重复的方法，比如在流水线机器中设置相互独立的指令存储器和数据存储器，也可以将cache分割成指令cache和数据cache。

**数据相关**
>&emsp;&emsp;架构同架构2。

>&emsp;&emsp;```data_stalls_3.s```<br>
>&emsp;&emsp;执行方式：<br>
>&emsp;&emsp;```single cycle```<br>
&emsp;&emsp;不采用**Forwarding**：

<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src="https://img-blog.csdnimg.cn/20200704103017425.png">
    <br>
    <div style="color:orange; border-bottom: 1px solid #d9d9d9;
    display: inline-block;
    color: #999;
    padding: 2px;">图 15 RAW stall in ID（R10，cycle 47）</div>
</center>
<br>

>&emsp;&emsp;**总周期：```53```<br>
&emsp;&emsp;指令数：```26```<br>
&emsp;&emsp;CPI：```2.038```<br>
&emsp;&emsp;数据相关周期：```18```<br>
&emsp;&emsp;占比：```18 / 53 ≈ 33.96%```**

>&emsp;&emsp;采用**Forwarding**：<br>
>&emsp;&emsp;**总周期：```42```<br>
&emsp;&emsp;指令数：```26```<br>
&emsp;&emsp;CPI：```1.615```<br>
&emsp;&emsp;数据相关周期：```7```<br>
&emsp;&emsp;占比：``7 / 42 ≈ 16.67%``**

>&emsp;&emsp;可见通过定向技术， 减少了数据相关， 缩短了程序的执行周期， 整个性能为原来的``1.26``倍。

### 3.2 指令调度与循环展开
>&emsp;&emsp;架构：

<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src="https://img-blog.csdnimg.cn/20200704103435879.png">
    <br>
    <div style="color:orange; border-bottom: 1px solid #d9d9d9;
    display: inline-block;
    color: #999;
    padding: 2px;">图 16 架构3</div>
</center>
<br>

>&emsp;&emsp;初始代码：``lab3_0_init.s``<br>
&emsp;&emsp;采用前向技术

<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src="https://img-blog.csdnimg.cn/20200704103539900.png">
    <br>
    <div style="color:orange; border-bottom: 1px solid #d9d9d9;
    display: inline-block;
    color: #999;
    padding: 2px;">图 17 执行初始代码</div>
</center>
<br>

>&emsp;&emsp;**总周期：``163``<br>
&emsp;&emsp;指令数：``85``<br>
&emsp;&emsp;CPI：``1.918``<br>
&emsp;&emsp;数据相关：``121（121 RAW stalls）``<br>
&emsp;&emsp;结构相关：``12``<br>
&emsp;&emsp;分支冲突：``7（Branch Taken Stalls）``**

>&emsp;&emsp;分支优化代码：``lab3_1_branch_optimised.s``
&emsp;&emsp;采用前向技术

<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src="https://img-blog.csdnimg.cn/20200704103721831.png">
    <br>
    <div style="color:orange; border-bottom: 1px solid #d9d9d9;
    display: inline-block;
    color: #999;
    padding: 2px;">图 18 执行分支优化代码</div>
</center>
<br>

>&emsp;&emsp;**总周期：``153``<br>
&emsp;&emsp;指令数：``78``<br>
&emsp;&emsp;CPI：``1.962``<br>
&emsp;&emsp;数据相关：``120（120 RAW stalls）``<br>
&emsp;&emsp;结构相关：``12``<br>
&emsp;&emsp;分支冲突：``5（5 Branch Taken Stalls）``**

>&emsp;&emsp;可见通过分支优化，缩短了程序的执行周期，整个性能为原来的1.07倍。

>&emsp;&emsp;调度代码：``lab3_2_scheduled.s``<br>
&emsp;&emsp;采用前向技术

<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src="https://img-blog.csdnimg.cn/20200704103858942.png">
    <br>
    <div style="color:orange; border-bottom: 1px solid #d9d9d9;
    display: inline-block;
    color: #999;
    padding: 2px;">图 19 执行指令调度代码</div>
</center>
<br>

>&emsp;&emsp;**总周期：``135``<br>
&emsp;&emsp;指令数：``78``<br>
&emsp;&emsp;CPI：``1.731``<br>
&emsp;&emsp;数据相关：``78（78 RAW stalls）``<br>
&emsp;&emsp;结构相关：``6``<br>
&emsp;&emsp;分支冲突：``5（Branch Taken Stalls）``**

>&emsp;&emsp;可见通过指令调度，缩短了程序的执行周期，整个性能为原来的``1.21``倍。

>&emsp;&emsp;循环展开代码：``lab3_3_unrolled.s``<br>
&emsp;&emsp;采用前向技术

<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src="https://img-blog.csdnimg.cn/20200704104039784.png">
    <br>
    <div style="color:orange; border-bottom: 1px solid #d9d9d9;
    display: inline-block;
    color: #999;
    padding: 2px;">图 20 执行循环展开代码</div>
</center>
<br>

>&emsp;&emsp;**总周期：``141``<br>
&emsp;&emsp;指令数：``72``<br>
&emsp;&emsp;CPI：``1.958``<br>
&emsp;&emsp;数据相关：``117（117 RAW stalls）``<br>
&emsp;&emsp;结构相关：``12``<br>
&emsp;&emsp;分支冲突：``2（Branch Taken Stalls）``**

>&emsp;&emsp;可见通过循环展开，缩短了程序的执行周期，整个性能为原来的``1.16``倍。

>&emsp;&emsp;循环展开且调度代码：``lab3_4_unrolled_and_scheduled.s``<br>
&emsp;&emsp;采用前向技术

<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src="https://img-blog.csdnimg.cn/20200704104222233.png">
    <br>
    <div style="color:orange; border-bottom: 1px solid #d9d9d9;
    display: inline-block;
    color: #999;
    padding: 2px;">图 21 执行循环展开且指令调度代码</div>
</center>
<br>

>&emsp;&emsp;**总周期：``108``<br>
&emsp;&emsp;指令数：``72``<br>
&emsp;&emsp;CPI：``1.5``<br>
&emsp;&emsp;数据相关：``36（36 RAW stalls）``<br>
&emsp;&emsp;结构相关：``18``<br>
&emsp;&emsp;分支冲突：``2（Branch Taken Stalls）``**

>&emsp;&emsp;可见通过循环展开与指令调度，缩短了程序的执行周期，整个性能为原来的``1.51``倍。

## 4 关键程序代码
&emsp;&emsp;（1）执行程序

```MIPS
#
# Insertion sort algorithm
# See http://www.cs.ubc.ca/spider/harrison/Java/InsertionSortAlgorithm.java.html
# Note use of MIPS register pseudo-names, and # for comments
#
      .data 
array: .word  0x4F6961869342DC99,0x7A0B67101C85D9EE,0x5EF87A2B37CA911D,0x47EF58E8B7E01DD9
       .word  0x79A74EAB20CB53C9,0x6D26753D06F8E483,0x70F313AF126C0B47,0x745232A4035F1EF5
       .word  0x46036BDDE8D095FD,0x4DE3F1D89B5A43EA,0x5279659D102EABBA,0x4496CDA949E29089
       .word  0x6D594E2009B7D04A,0x4CE57C0D55905DE5,0x4115A0AC78A1848B,0x5051DAA648B3BDA6
       .word  0x71C3730CE11593C0,0x425A9FAE68370FC5,0x6B265F8485354426,0x4E935A849C713D01
       .word  0x773110588E5170D7,0x5B133F183803A780,0x49A52D37525C362C,0x4A0C150C49D8A123
       .word  0x7962EC77A41FB066,0x5D3A087AF3417D04,0x7076F96031DC3B2E,0x404EC3D105D02FDD
       .word  0x5484F578189A7A8B,0x65EA86F819037E03,0x4367E6F2AE35B27A,0x63C1CF869394DB43
       .word  0x59421109269E583C,0x6B9F1B529C8598EF,0x4C877DCC129AF1BD,0x58401EDBF56D884F
       .word  0x754C5475E3F8BFCF,0x1111111111111111,0x786213BFF3FAE203,0x53F6C77223F8D4B5
       .word  0x5304A0C74815DFBF,0x701BFCF2B7E84DED,0x72C3DEDE1BA476AD,0x557C05371C0A436C
       .word  0x741CECCDBAEBBBB3,0x577156E9E5C72202,0x641D1FEFF6E59822,0x623B6D2C45E6AFC6
       .word  0x6976994C37A754F0,0x4CE48C6E6963A020,0x4EDDBCD1CF3CD3AC,0x706AAA8FC1AE08E4
       .word  0x674DE62D8E4ACB59,0x791423B583AF7749,0x4589009608F70D0A,0x55159D9A3430F238
       .word  0x70BD250BE3048518,0x6D1B60128C603831,0x5397AB7F0E29CEE8,0x58EF0102374A9A97
       .word  0x625D9DBD94D1E2D1,0x5E8439437165FDF6,0x4F621F3A37353266,0x426B3ACC1149F170
       .word  0x59D789FA7FA3F476,0x4C4353E0D30D6D4B,0x492F120FA02F0B1C,0x720DFD78A97CFF59
       .word  0x5BC2140E14551D39,0x68718C039D4656B9,0x7FFFFFFFFFFFFFFF,0x48F63330CBC9A739
       .word  0x6E47955AFD5F8C20,0x44972B6AD10F9D2A,0x46578121CA1151A1,0x46281A1E7672B320
       .word  0x4094CC803E05BD98,0x5FF5B63C7812A363,0x6AF41E217F7612C5,0x4B7B4452B1E208AC
       .word  0x750F8A67FA5E72E4,0x51C8ECF29B5E8AD1,0x580550353D81B486,0x668CD4C5F3970ABF
       .word  0x480BEE00A16715AD,0x4888D5AC9EE02467,0x77C3DDBA62669040,0x48D55CDF7F706867
       .word  0x720670341FE6E445,0x6CAE4383191C2CC9,0x4F9E28BAD0270344,0x46DAD4328A8A3979
       .word  0x55B7AEB598729716,0x76D0F139C5FF97C5,0x4B876EB39C2DC380,0x781ADC2AD91E6FDF
       .word  0x53BDEAF8F4AA0625,0x624D7EA5B9A73772,0x75A02137A787850D,0x4259BDE1C33A32E6
       
len:  .word 100


        .text
        daddi $t0,$zero,8  # $t0 = i = 8
        ld $t1,len($zero)  # $t1 = len
        dsll $t1,$t1,3     # $t1 = len*8
for:    slt $t2,$t0,$t1    # i < len?
        beqz $t2,out       # yes - exit
        dadd $t3,$zero,$t0 # $t3=j=i
        ld $t4,array($t0)  # $t4=B=a[i]
loop:   slt $t2,$zero,$t3  # j>0 ?
        beqz $t2,over      # no -exit
        daddi $t5,$t3,-8   # $t5=j-1
        ld $t6,array($t5)  # get $t6=a[j-1]
        slt $t2,$t6,$t4    # >B ?
        beqz $t2,over	 
        sd $t6,array($t3)  # a[j]=a[j-1]
        dadd $t3,$zero,$t5 # j--
        j loop

over:   sd $t4,array($t3)  # a[j] = B
        daddi $t0,$t0,8    # i++
        j for
out:    halt
   

```

<br>
&emsp;&emsp;（2）结构相关

```MIPS
 .data 
N_COEFFS:  .word 3
coeff: .double 5.0,2.0,-3.0
N_SAMPLES: .word 3
sample: .double 1,2,3,4,5,6,7,8,9,10
result: .double 0,0,0,0,0,0,0,0,0,0
C_ZERO: .double 0.0
        .text


start:	ld r1,N_COEFFS(r0)  # r1 = N_COEFFS
	ld r2,N_SAMPLES(r0)  # r2 = N_SAMPLES
	slt r3,r1,r2    # N_COEFFS < N_SAMPLES?
        bnez r3,smooth       # yes - go to smooth
	beq r1,r2,smooth # branch N_COEFFS = N_SAMPLES        
	halt

smooth:    
	L.D F3,C_ZERO(r0)  # F3=norm=0.0;
	daddu r2,r0,r0   ; r2 = 0
    ld r1,N_COEFFS(r2)  # r1 = N_COEFFS
    L.D F1,coeff(r2)  # F1=coeff[0]
    L.D F0,C_ZERO(r0)  # F0=0

	c.lt.d F1,F0	#coeff[0]<0	c.lt.d freg,freg - set FP flag if less than
	bc1t neg_coeff_zero 	#- branch to address if FP flag is true
	ADD.D F3,F3,F1	#norm+=coeff[0];
	jal coeff_one         ; call coeff_one

neg_coeff_zero: 
	SUB.D F3,F3,F1	#norm-=coeff[0];
	jal coeff_one         ; call coeff_one

coeff_one:
	daddi r2,r0,8   ; r2 = 8
	L.D F1,coeff(r2)  # F1=coeff[1]
	c.lt.d F1,F0	#coeff[1]<0	c.lt.d freg,freg - set FP flag if less than
	bc1t neg_coeff_one 	#- branch to address if FP flag is true
	ADD.D F3,F3,F1	#norm+=coeff[1];
	jal coeff_two         ; call coeff_two

neg_coeff_one: 
	SUB.D F3,F3,F1	#norm-=coeff[1];
	jal coeff_two         ; call coeff_two

coeff_two:
	daddi r2,r0,16   ; r2 = 16
	L.D F1,coeff(r2)  # F1=coeff[2]
	c.lt.d F1,F0	#coeff[2]<0	c.lt.d freg,freg - set FP flag if less than
	bc1t neg_coeff_two 	#- branch to address if FP flag is true
	ADD.D F3,F3,F1	#norm+=coeff[2];
	jal go_result         ; call go_result

neg_coeff_two: 
	SUB.D F3,F3,F1	#norm-=coeff[2];
	jal go_result         ; call go_result

go_result:	halt

out:    halt
```
<br>
&emsp;&emsp;（3）数据相关

```MIPS
.data 
N_COEFFS:  .word 3
coeff: .double 1.0,25.0,3.0
N_SAMPLES: .word 3
sample: .double 1,2,3,4,5,6,7,8,9,10
result: .double 0,0,0,0,0,0,0,0,0,0

        .text


start:	ld r1,N_COEFFS(r0)  # r1 = N_COEFFS
	ld r2,N_SAMPLES(r0)  # r2 = N_SAMPLES
	slt $t2,r1,r2    # N_COEFFS < N_SAMPLES?
        bnez $t2,smooth       # yes - go to smooth
	beq r1,r2,smooth # branch N_COEFFS = N_SAMPLES        
	halt

smooth:    
	daddu r2,r0,r0   ; r2 = 0
        ld r1,N_COEFFS(r2)  # r1 = N_COEFFS
        dsll r1,r1,3     # r1 = N_COEFFS*8
for:    slt $t2,r2,r1    # i < N_COEFFS?
        beqz $t2,out       # yes - exit
        ld r5,coeff(r2)  # r5=a[i]
        daddi r2,r2,8    # i++
        j for
out:    halt
```
<br>
&emsp;&emsp;（4）指令调度与循环展开

```MIPS
# lab3_0_init.s
.data
a: .double 1.0, 2.0, 3.0, 4.0, 5.0, 6.0
b: .double 2.0, 3.0, 4.0, 5.0, 6.0, 7.0
c: .double 0.0, 0.0, 0.0, 0.0, 0.0, 0.0
d: .double 0.0, 0.0, 0.0, 0.0, 0.0, 0.0

.text
main:
	daddi r1, r0, 6		#r1 now contains n = 6
	daddi r2, r0, 10	#r2 now contains 10
	mtc1 r2, f1			#f1 now contains alpha = 10.0
	dadd r2, r0, r0		#r2 now contains i = 0	

loop:
	slt r5, r2, r1		#r5 = r2<r1 (i<n)
	beq r5, r0, exit	#if r5 = 0, exit
	dsll r3, r2, 3		#r3 now contains 8*i or 8*r2
	l.d f2, a(r3)		#f2 contains a[i]
	l.d f3, b(r3)		#f3 contains b[i]
	l.d f5, d(r3)		#f5 contains d[i]
	mul.d f6, f2, f3	#f6 has a[i]*b[i]
	s.d f6, c(r3)		#c[i] = a[i]*b[i]
	mul.d f7, f6, f1	#f7 has c[i]*alpha
	add.d f8, f5, f7	#f8 now has d[i] + c[i]*alpha
	s.d f8, d(r3)		#successfully stored f8 to d[i]
	daddi r2, r2, 1 	#i++
	j loop

exit:
halt
```

<br>

```MIPS
# lab3_1_branch_optimised.s
.data
a: .double 1.0, 2.0, 3.0, 4.0, 5.0, 6.0
b: .double 2.0, 3.0, 4.0, 5.0, 6.0, 7.0
c: .double 0.0, 0.0, 0.0, 0.0, 0.0, 0.0
d: .double 0.0, 0.0, 0.0, 0.0, 0.0, 0.0

.text
main:
	daddi r1, r0, 6		#r1 now contains n = 6
	daddi r2, r0, 10	#r2 now contains 10
	mtc1 r2, f1			#f1 now contains alpha = 10.0
	dadd r2, r0, r0		#r2 now contains i = 0	
	daddi r4, r1, -1

loop:
	dsll r3, r2, 3		#r3 now contains 8*i or 8*r2
	l.d f2, a(r3)		#f2 contains a[i]
	l.d f3, b(r3)		#f3 contains b[i]
	l.d f5, d(r3)		#f5 contains d[i]
	mul.d f6, f2, f3	#f6 has a[i]*b[i]
	s.d f6, c(r3)		#c[i] = a[i]*b[i]
	mul.d f7, f6, f1	#f7 has c[i]*alpha
	add.d f8, f5, f7	#f8 now has d[i] + c[i]*alpha
	s.d f8, d(r3)		#successfully stored f8 to d[i]
	daddi r2, r2, 1 	#i++
	slt r5, r4, r2		#r5 = r4<r2 (n-1<i)
	beq r5, r0, loop	#if r5 = 0, loop

exit:
halt
```

<br>

```MIPS
# lab3_2_scheduled.s
.data
a: .double 1.0, 2.0, 3.0, 4.0, 5.0, 6.0
b: .double 2.0, 3.0, 4.0, 5.0, 6.0, 7.0
c: .double 0.0, 0.0, 0.0, 0.0, 0.0, 0.0
d: .double 0.0, 0.0, 0.0, 0.0, 0.0, 0.0

.text
main:
	daddi r1, r0, 6		#r1 now contains n = 6
	daddi r2, r0, 10	#r2 now contains 10
	mtc1 r2, f1			#f1 now contains alpha = 10.0
	dadd r2, r0, r0		#r2 now contains i = 0	
	daddi r4, r1, -1

loop:
	dsll r3, r2, 3		#r3 now contains 8*i or 8*r2
	#get values
	l.d f2, a(r3)		#f2 contains a[i]
	l.d f3, b(r3)		#f3 contains b[i]
	l.d f5, d(r3)		#f5 contains d[i]
	mul.d f6, f2, f3	#f6 has a[i]*b[i]
	#loop meta
	daddi r2, r2, 1 	#i++
	slt r5, r4, r2		#r5 = r4<r2 (n-1<i)
	#end of loop meta
	mul.d f7, f6, f1	#f7 has c[i]*alpha
	add.d f8, f5, f7	#f8 now has d[i] + c[i]*alpha
	s.d f6, c(r3)		#stored f6 to c[i]
	s.d f8, d(r3)		#successfully stored f8 to d[i]
	beq r5, r0, loop	#if r5 = 0, loop

exit:
halt
```
<br>

```MIPS
#lab3_3_unrolled.s
.data
a: .double 1.0, 2.0, 3.0, 4.0, 5.0, 6.0
b: .double 2.0, 3.0, 4.0, 5.0, 6.0, 7.0
c: .double 0.0, 0.0, 0.0, 0.0, 0.0, 0.0
d: .double 0.0, 0.0, 0.0, 0.0, 0.0, 0.0

.text
main:
	daddi r1, r0, 6		#r1 now contains n = 6
	daddi r2, r0, 10	#r2 now contains 10
	mtc1 r2, f1			#f1 now contains alpha = 10.0
	dadd r2, r0, r0		#r2 now contains i = 0	
	daddi r4, r1, -1

loop:
	dsll r3, r2, 3		#r3 now contains 8*i or 8*r2
	l.d f2, a(r3)		#f2 contains a[i]
	l.d f3, b(r3)		#f3 contains b[i]
	l.d f5, d(r3)		#f5 contains d[i]
	mul.d f6, f2, f3	#f6 has a[i]*b[i]
	s.d f6, c(r3)		#c[i] = a[i]*b[i]
	mul.d f7, f6, f1	#f7 has c[i]*alpha
	add.d f8, f5, f7	#f8 now has d[i] + c[i]*alpha
	s.d f8, d(r3)		#successfully stored f8 to d[i]
	daddi r2, r2, 1 	#i++
	dsll r3, r2, 3		#r3 now contains 8*i or 8*r2
	l.d f2, a(r3)		#f2 contains a[i]
	l.d f3, b(r3)		#f3 contains b[i]
	l.d f5, d(r3)		#f5 contains d[i]
	mul.d f6, f2, f3	#f6 has a[i]*b[i]
	s.d f6, c(r3)		#c[i] = a[i]*b[i]
	mul.d f7, f6, f1	#f7 has c[i]*alpha
	add.d f8, f5, f7	#f8 now has d[i] + c[i]*alpha
	s.d f8, d(r3)		#successfully stored f8 to d[i]
	daddi r2, r2, 1 	#i++
	slt r5, r4, r2		#r5 = r4<r2 (n-1<i)
	beq r5, r0, loop	#if r5 = 0, loop

exit:
halt
```

<br>

```MIPS
# lab3_4_unrolled_and_scheduled.s
.data
a: .double 1.0, 2.0, 3.0, 4.0, 5.0, 6.0
b: .double 2.0, 3.0, 4.0, 5.0, 6.0, 7.0
c: .double 0.0, 0.0, 0.0, 0.0, 0.0, 0.0
d: .double 0.0, 0.0, 0.0, 0.0, 0.0, 0.0

.text
main:
	daddi r1, r0, 6		#r1 now contains n = 6
	daddi r2, r0, 10	#r2 now contains 10
	mtc1 r2, f1			#f1 now contains alpha = 10.0
	dadd r2, r0, r0		#r2 now contains i = 0	
	daddi r4, r1, -1

loop:
	dsll r3, r2, 3		#r3 now contains 8*i or 8*r2
	l.d f2, a(r3)		#f2 contains a[i]
	l.d f3, b(r3)		#f3 contains b[i]
	l.d f5, d(r3)		#f5 contains d[i]
	mul.d f6, f2, f3	#f6 has a[i]*b[i]
	#loop meta
	daddi r2, r2, 1 	#i++
	dsll r3, r2, 3		#r3 now contains 8*i or 8*r2
	#end of loop meta
	mul.d f7, f6, f1	#f7 has c[i]*alpha
	l.d f2, a(r3)		#f2 contains a[i]
	l.d f3, b(r3)		#f3 contains b[i]
	add.d f8, f5, f7	#f8 now has d[i] + c[i]*alpha	#This is the part between muli and addi that needs a stall and cannot be optimised by scheduling
	s.d f6, c(r3)		#stored f6 to c[i]
	mul.d f6, f2, f3	#f6 has a[i]*b[i]
	s.d f8, d(r3)		#successfully stored f8 to d[i]
	l.d f5, d(r3)		#f5 contains d[i]
	mul.d f7, f6, f1	#f7 has c[i]*alpha
	#loop meta
	daddi r2, r2, 1 	#i++
	slt r5, r4, r2		#r5 = r4<r2 (n-1<i)
	#end of loop meta
	add.d f8, f5, f7	#f8 now has d[i] + c[i]*alpha	#This is the part between muli and addi that needs a stall and cannot be optimised by scheduling
	s.d f6, c(r3)		#stored f6 to c[i]
	s.d f8, d(r3)		#successfully stored f8 to d[i]
	beq r5, r0, loop	#if r5 = 0, loop

exit:
halt

```
<br>

## 5. 实验心得
>&emsp;&emsp;本次实验借助WinMIPS64进行。<br>
&emsp;&emsp;通过本次实验，我掌握了WinMIPS64模拟器的使用，加深对计算机流水线基本概念的理解，进一步了解MIPS基本流水线各段的功能以及基本操作，同时加深对数据相关、 构相关的理解，了解相关对CPU性能的影响，学会了解决数据相关的方法，掌握如何使用定向技术来减少数据相关带来的暂停。加深对循环级并行性、指令调度技术、循环展开技术的理解，可以用循环展开、指令调度等技术来解决流水线中的相关问题以及了解了其对CPU性能的改进。<br>
&emsp;&emsp;在使用指令调度消除相关的过程中，我也加深了对指令相关的影响的理解，同时大致掌握了各种消除相关的算法思想。

<br>
<br>
<br>
<br>

#  实验二 分支预测
## 1 实验内容
>&emsp;&emsp;本次实验使用分支预测模拟器sim-bpred，在4种预测器类型及不同的参数配置下运行测试程序，并比较、分析结果，使大家加深对动态分支预测机制的理解，并了解各种分支预测实现方式的优劣。

## 2 实验方法
> &emsp;&emsp; SimpleScalar分支预测的实现方法：先进行分支方向探测，即是否采取分支（当然跳转指令和调用返回指令不用作这一步），接着是生成分支地址，对于调返指令，直接在RAS上作相关操作，普通分支指令则要利用BTB来进行地址探测，命中则生成地址。然后对两步综合，地址命中且分支预测为采取，返回分支目标地址；地址不命中且分支预测为采取，返回1;只要分支预测为不采取，就返回0。<br>
&emsp;&emsp;重点分析针对条件分支指令的方向探测方法，主要有6种，三种静态：taken,nottanken,perfect;三种动态：bimod,2-level,combined。静态的方法顾名思义，只是perfect这种，按它的原意是不预测，直接把真正采取的下一条指令填入npc，而且它确实不需要调用。<br>
&emsp;&emsp;对于三种动态方法，分别说明如下：<br>
&emsp;&emsp;bimod是最普通的，即采用一个2bit宽的分支方向预测表，按分支地址查找，2bit分支预测器的判断和更新与课本上的一致。这种方式只有一个参数，就是分支预测表的长度。<br>
&emsp;&emsp;2-level要复杂一些，它采用两级表格式，第一级是分支历史表，存放各组分支历史寄存器的值，第二级是全局/局部分支模式表，（全局或局部应是由表长相对于分支历史寄存器的长决定），它存放各分支历史模式的2bit预测器。在判断时用当前分支指令对应的历史寄存器值去索引二级表得到相应预测器值。更新时，把当前分支的方向左移入历史寄存器，并对使用过的2bit预测器作更新。它有四个参数，前三个是一级表长度，二级表长度，历史寄存器宽度，最后一个是异或标志。如果为1，则将历史寄存器的值与当前分支指令地址异或，用其结果再去索引二级模式表。

## 3 结果与分析
>&emsp;&emsp;**博主不是在虚拟机上做的，而是在阿里云云``服务器``上操作。**

<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src="https://img-blog.csdnimg.cn/20200704105659413.png">
    <br>
    <div style="color:orange; border-bottom: 1px solid #d9d9d9;
    display: inline-block;
    color: #999;
    padding: 2px;">图 22 操作系统内核版本与服务器硬件配置</div>
</center>
<br>

>&emsp;&emsp;下面展示的是服务器操作Linux内核版本、服务器硬件配置与操作系统类型（Ubuntu 18.04.4）。

<font size=20 color=red>敏感信息懒得遮住了，求大佬手下留情别攻击博主服务器……</font>

```bash
root@iZwz9bj4ryzwisxega006tZ:/home# clear                                                                                                                                                                root@iZwz9bj4ryzwisxega006tZ:/home# uname -a
Linux iZwz9bj4ryzwisxega006tZ 4.15.0-48-generic #51-Ubuntu SMP Wed Apr 3 08:28:49 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux
root@iZwz9bj4ryzwisxega006tZ:/home# dmidecode |more
# dmidecode 3.1
Getting SMBIOS data from sysfs.
SMBIOS 2.8 present.
9 structures occupying 429 bytes.
Table at 0x000F5850.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
        Vendor: SeaBIOS
        Version: 8c24b4c
        Release Date: 04/01/2014
        Address: 0xE8000
        Runtime Size: 96 kB
        ROM Size: 64 kB
        Characteristics:
                BIOS characteristics not supported
                Targeted content distribution is supported
        BIOS Revision: 0.0

Handle 0x0100, DMI type 1, 27 bytes
System Information
        Manufacturer: Alibaba Cloud
        Product Name: Alibaba Cloud ECS
        Version: pc-i440fx-2.1
        Serial Number: aaa22528-980a-4893-9b5f-a692b99af30b
        UUID: AAA22528-980A-4893-9B5F-A692B99AF30B
        Wake-up Type: Power Switch
        SKU Number: Not Specified
        Family: Not Specified

Handle 0x0300, DMI type 3, 21 bytes
Chassis Information
        Manufacturer: Alibaba Cloud
        Type: Other
        Lock: Not Present
        Version: pc-i440fx-2.1
        Serial Number: Not Specified
        Asset Tag: Not Specified
        Boot-up State: Safe
        Power Supply State: Safe
        Thermal State: Safe
        Security Status: Unknown
        OEM Information: 0x00000000
        Height: Unspecified
        Number Of Power Cords: Unspecified
        Contained Elements: 0

Handle 0x0400, DMI type 4, 42 bytes
Processor Information
        Socket Designation: CPU 0
        Type: Central Processor
        Family: Other
        Manufacturer: Alibaba Cloud
        ID: 54 06 05 00 FF FB 8B 0F
        Version: pc-i440fx-2.1
        Voltage: Unknown
        External Clock: Unknown
        Max Speed: Unknown
        Current Speed: Unknown
        Status: Populated, Enabled
        Upgrade: Other
        L1 Cache Handle: Not Provided
        L2 Cache Handle: Not Provided
        L3 Cache Handle: Not Provided
        Serial Number: Not Specified
        Asset Tag: Not Specified
        Part Number: Not Specified
        Core Count: 1
        Core Enabled: 1
        Thread Count: 2
        Characteristics: None

Handle 0x1000, DMI type 16, 23 bytes
Physical Memory Array
        Location: Other
        Use: System Memory
        Error Correction Type: Multi-bit ECC
        Maximum Capacity: 2 GB
        Error Information Handle: Not Provided
        Number Of Devices: 1

Handle 0x1100, DMI type 17, 40 bytes
Memory Device
        Array Handle: 0x1000
        Error Information Handle: Not Provided
        Total Width: Unknown
        Data Width: Unknown
        Size: 2048 MB
        Form Factor: DIMM
        Set: None
        Locator: DIMM 0
        Bank Locator: Not Specified
        Type: RAM
        Type Detail: Other
        Speed: Unknown
        Manufacturer: Alibaba Cloud
        Serial Number: Not Specified
        Asset Tag: Not Specified
        Part Number: Not Specified
        Rank: Unknown
        Configured Clock Speed: Unknown
        Minimum Voltage: Unknown
        Maximum Voltage: Unknown
        Configured Voltage: Unknown

Handle 0x1300, DMI type 19, 31 bytes
Memory Array Mapped Address
        Starting Address: 0x00000000000
        Ending Address: 0x0007FFFFFFF
        Range Size: 2 GB
        Physical Array Handle: 0x1000
        Partition Width: 1

Handle 0x2000, DMI type 32, 11 bytes
System Boot Information
        Status: No errors detected

Handle 0x7F00, DMI type 127, 4 bytes
End Of Table
root@iZwz9bj4ryzwisxega006tZ:/home#  head -n 1 /etc/issue
Ubuntu 18.04.4 LTS \n \l
```
<br>

>&emsp;&emsp;所选测试数据集：gcc、mcf、vortex、vpr。

>&emsp;&emsp;运行gcc数据集示例如图23所示。

<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src="https://img-blog.csdnimg.cn/20200704114951572.png">
    <br>
    <div style="color:orange; border-bottom: 1px solid #d9d9d9;
    display: inline-block;
    color: #999;
    padding: 2px;">图 23 运行gcc数据集示例</div>
</center>
<br>

>&emsp;&emsp;运行gcc测试数据集实验所得数据表1所示。

<div  style="text-align:center" >
<table style="width: 80%;margin:auto" border="2">
<caption>表1 运行gcc测试数据集实验所得数据</caption>
<tr>
<td>		</td>
<td>Always taken</td>
<td>always not taken</td>
<td>bimod(512))</td>
<td>Bimod(1024)</td>
<td>Two level (1,1024,8,0)</td>
<td>Two level (1,64,6,1)</td>
</tr>
<tr>
  <td>	sim_total_insn	</td>
<td>	200000000	</td>
<td>	200000000	</td>
<td>	200000000	</td>
<td>	200000000	</td>
<td>	200000000	</td>
<td>	200000000	</td>
</tr>
<tr>
<td>	sim_total_refs	</td>
<td>	82299557	</td>
<td>	82299557	</td>
<td>	82299557	</td>
<td>	82299557	</td>
<td>	82299557	</td>
<td>	82299557	</td>
</tr>
<tr>
<td>	sim_elapsed_time	</td>
<td>	9	</td>
<td>	9	</td>
<td>	12	</td>
<td>	12	</td>
<td>	12	</td>
<td>	12	</td>
</tr>
<tr>
<td>	sim_inst_rate	</td>
<td>	22222222.22	</td>
<td>	22222222.2222	</td>
<td>	16666666.6667	</td>
<td>	16666666.6667	</td>
<td>	16666666.6667	</td>
<td>	16666666.6667	</td>
</tr>
<tr>
<td>	sim_num_branches	</td>
<td>	38932651	</td>
<td>	38932651	</td>
<td>	38932651	</td>
<td>	38932651	</td>
<td>	38932651	</td>
<td>	38932651	</td>
</tr>
<tr>
<td>	sim_IPB	</td>
<td>	5.1371	</td>
<td>	5.1371	</td>
<td>	5.1371	</td>
<td>	5.1371	</td>
<td>	5.1371	</td>
<td>	5.1371	</td>
</tr>
<tr>
<td>	bpred_bimod.lookups	</td>
<td>	38932651	</td>
<td>	38932651	</td>
<td>	38932651	</td>
<td>	38932651	</td>
<td>	38932651	</td>
<td>	38932651	</td>
</tr>
<tr>
<td>	bpred_bimod.updates	</td>
<td>	38932651	</td>
<td>	38932651	</td>
<td>	38932651	</td>
<td>	38932651	</td>
<td>	38932651	</td>
<td>	38932651	</td>
</tr>
<tr>
<td>	bpred_bimod.addr_hits	</td>
<td>	24896713	</td>
<td>	22021899	</td>
<td>	33168606	</td>
<td>	33826488	</td>
<td>	34264216	</td>
<td>	34264216	</td>
</tr>
<tr>
<td>	bpred_bimod.dir_hirts	</td>
<td>	24896713	</td>
<td>	22021899	</td>
<td>	33796352	</td>
<td>	34459270	</td>
<td>	34903457	</td>
<td>	34903457	</td>
</tr>
<tr>
<td>	bpred_bimod.misses	</td>
<td>	14035938	</td>
<td>	16910752	</td>
<td>	5136299	</td>
<td>	4473381	</td>
<td>	4029194	</td>
<td>	4029194	</td>
</tr>
<tr>
<td>	bpred_bimod.jr_hits	</td>
<td>	3392575	</td>
<td>	3392575	</td>
<td>	2722268	</td>
<td>	2722268	</td>
<td>	2722268	</td>
<td>	2722268	</td>
</tr>
<tr>
<td>	bpred_bimod.jr_seen	</td>
<td>	3392575	</td>
<td>	3392575	</td>
<td>	3392575	</td>
<td>	3392575	</td>
<td>	3392575	</td>
<td>	3392575	</td>
</tr>
<tr>
<td>	bpred_bimod.jr_non_ras_hits.PP	</td>
<td>	3392575	</td>
<td>	3392575	</td>
<td>	338933	</td>
<td>	338933	</td>
<td>	338933	</td>
<td>	338933	</td>
</tr>
<tr>
<td>	bpred_bimod.jr_non_ras_seen.PP	</td>
<td>	3392575	</td>
<td>	3392575	</td>
<td>	999722	</td>
<td>	999722	</td>
<td>	999722	</td>
<td>	999722	</td>
</tr>
<tr>
<td>	bpred_bimod.bpred_addr_rate	</td>
<td>	0.6395	</td>
<td>	0.5656	</td>
<td>	0.8519	</td>
<td>	0.8688	</td>
<td>	0.8801	</td>
<td>	0.8801	</td>
</tr>
<tr>
<td>	bpred_bimod.bpred_dir_rate	</td>
<td>	0.6395	</td>
<td>	0.5656	</td>
<td>	0.8681	</td>
<td>	0.8851	</td>
<td>	0.8965	</td>
<td>	0.8965	</td>
</tr>
<tr>
<td>	bpred_bimod.bpred_jr_rate	</td>
<td>	1.0000	</td>
<td>	1.0000	</td>
<td>	0.8024	</td>
<td>	0.8024	</td>
<td>	0.8024	</td>
<td>	0.8024	</td>
</tr>
<tr>
<td>	bpred_bimod.bpred_jr_non_ras_rate.PP	</td>
<td>	1.0000	</td>
<td>	1.0000	</td>
<td>	0.3390	</td>
<td>	0.3390	</td>
<td>	0.3390	</td>
<td>	0.3390	</td>
</tr>
<tr>
<td>	bpred_bimod.retstack_pushes	</td>
<td>	0	</td>
<td>	0	</td>
<td>	2392862	</td>
<td>	2392862	</td>
<td>	2392862	</td>
<td>	2392862	</td>
</tr>
<tr>
<td>	bpred_bimod.retstack_pops	</td>
<td>	0	</td>
<td>	0	</td>
<td>	2392853	</td>
<td>	2392853	</td>
<td>	2392853	</td>
<td>	2392853	</td>
</tr>
<tr>
<td>	bpred_bimod.used_ras.PP	</td>
<td>	0	</td>
<td>	0	</td>
<td>	2392853	</td>
<td>	2392853	</td>
<td>	2392853	</td>
<td>	2392853	</td>
</tr>
<tr>
<td>	bpred_bimod.ras_hits.PP	</td>
<td>	0	</td>
<td>	0	</td>
<td>	2383335	</td>
<td>	2383335	</td>
<td>	2383335	</td>
<td>	2383335	</td>
</tr>
<tr>
<td>	bpred_bimod.ras_rate.PP	</td>
<td>	<error: divide by zero>	</td>
<td>	<error: divide by zero>	</td>
<td>	0.9960	</td>
<td>	0.9960	</td>
<td>	0.9960	</td>
<td>	0.9960	</td>
</tr>
</table>
</div>

<br>

>&emsp;&emsp;运行gcc数据集所得数据对比图如图24所示

<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src="https://img-blog.csdnimg.cn/20200704114853178.png">
    <br>
    <div style="color:orange; border-bottom: 1px solid #d9d9d9;
    display: inline-block;
    color: #999;
    padding: 2px;">图 24 运行gcc测试数据集数据对比</div>
</center>
<br>

>运行mfc测试数据集示例如图25所示。

<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src="https://img-blog.csdnimg.cn/20200704120046563.png">
    <br>
    <div style="color:orange; border-bottom: 1px solid #d9d9d9;
    display: inline-block;
    color: #999;
    padding: 2px;">图 25 运行mcf数据集示例</div>
</center>
<br>
<br>

>&emsp;&emsp;运行mcf测试数据集所得数据如表2所示

<div  style="text-align:center" >
<table style="width: 80%;margin:auto" border="2">
<caption>表2 运行mcf测试数据集所得数据</caption>
<col width='260' style='mso-width-source:userset;width:195pt'>
 <col width='155' span='2' style='mso-width-source:userset;width:116.25pt'>
 <col width='105' span='2' style='mso-width-source:userset;width:78.75pt'>
 <col width='154' style='mso-width-source:userset;width:115.5pt'>
 <col width='138' style='mso-width-source:userset;width:103.5pt'>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r0'>
<td height='18' class='x22' width='260' style='height:14.1pt;width:195pt;'></td>
<td class='x21' width='155' style='width:116.25pt;'>Always taken</td>
<td class='x21' width='155' style='width:116.25pt;'>always not taken</td>
<td class='x21' width='105' style='width:78.75pt;'>bimod(512) </td>
<td class='x21' width='105' style='width:78.75pt;'>Bimod(1024) </td>
<td class='x21' width='154' style='width:115.5pt;'>Two level (1,1024,8,0)</td>
<td class='x21' width='138' style='width:103.5pt;'>Two level (1,64,6,1)</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r1'>
<td height='18' class='x21' style='height:14.1pt;'>sim_total_insn</td>
<td class='x23'>277504665</td>
<td class='x23'>277504665</td>
<td class='x23'>200000000</td>
<td class='x23'>200000000</td>
<td class='x23'>200000000</td>
<td class='x23'>200000000</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r2'>
<td height='18' class='x21' style='height:14.1pt;'>sim_total_refs</td>
<td class='x23'>100392784</td>
<td class='x23'>100392784</td>
<td class='x23'>100392784</td>
<td class='x23'>74877495</td>
<td class='x23'>74877495</td>
<td class='x23'>74877495</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r3'>
<td height='18' class='x21' style='height:14.1pt;'>sim_elapsed_time</td>
<td class='x23'>11</td>
<td class='x23'>12</td>
<td class='x23'>10</td>
<td class='x23'>11</td>
<td class='x23'>11</td>
<td class='x23'>11</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r4'>
<td height='18' class='x21' style='height:14.1pt;'>sim_inst_rate</td>
<td class='x23'>25227696.8182</td>
<td class='x23'>23125388.7500</td>
<td class='x23'>20000000.0000</td>
<td class='x23'>18181818.1818</td>
<td class='x23'>18181818.1818</td>
<td class='x23'>18181818.1818</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r5'>
<td height='18' class='x21' style='height:14.1pt;'>sim_num_branches</td>
<td class='x23'>56703872</td>
<td class='x23'>56703872</td>
<td class='x23'>37825248</td>
<td class='x23'>37825248</td>
<td class='x23'>37825248</td>
<td class='x23'>37825248</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r6'>
<td height='18' class='x21' style='height:14.1pt;'>sim_IPB</td>
<td class='x23'>4.8939</td>
<td class='x23'>4.8939</td>
<td class='x23'>5.2875</td>
<td class='x23'>5.2875</td>
<td class='x23'>5.2875</td>
<td class='x23'>5.2875</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r7'>
<td height='18' class='x21' style='height:14.1pt;'>bpred_bimod.lookups</td>
<td class='x23'>56703872</td>
<td class='x23'>56703872</td>
<td class='x23'>37825248</td>
<td class='x23'>37825248</td>
<td class='x23'>37825248</td>
<td class='x23'>37825248</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r8'>
<td height='18' class='x21' style='height:14.1pt;'>bpred_bimod.updates</td>
<td class='x23'>56703872</td>
<td class='x23'>56703872</td>
<td class='x23'>37825248</td>
<td class='x23'>37825248</td>
<td class='x23'>37825248</td>
<td class='x23'>37825248</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r9'>
<td height='18' class='x21' style='height:14.1pt;'>bpred_bimod.addr_hits</td>
<td class='x23'>39760075</td>
<td class='x23'>41303028</td>
<td class='x23'>31592697</td>
<td class='x23'>31627566</td>
<td class='x23'>31627870</td>
<td class='x23'>31627870</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r10'>
<td height='18' class='x21' style='height:14.1pt;'>bpred_bimod.dir_hirts</td>
<td class='x23'>39760075</td>
<td class='x23'>41303028</td>
<td class='x23'>31603605</td>
<td class='x23'>31638461</td>
<td class='x23'>31638767</td>
<td class='x23'>31638767</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r11'>
<td height='18' class='x21' style='height:14.1pt;'>bpred_bimod.misses</td>
<td class='x23'>16943797</td>
<td class='x23'>15400844</td>
<td class='x23'>6221643</td>
<td class='x23'>6186787</td>
<td class='x23'>6186481</td>
<td class='x23'>6186481</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r12'>
<td height='18' class='x21' style='height:14.1pt;'>bpred_bimod.jr_hits</td>
<td class='x23'>5313258</td>
<td class='x23'>5313258</td>
<td class='x23'>3085664</td>
<td class='x23'>3085664</td>
<td class='x23'>3085664</td>
<td class='x23'>3085664</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r13'>
<td height='18' class='x21' style='height:14.1pt;'>bpred_bimod.jr_seen</td>
<td class='x23'>5313258</td>
<td class='x23'>5313258</td>
<td class='x23'>3100112</td>
<td class='x23'>3100112</td>
<td class='x23'>3100112</td>
<td class='x23'>3100112</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r14'>
<td height='18' class='x21' style='height:14.1pt;'>bpred_bimod.jr_non_ras_hits.PP</td>
<td class='x23'>5313258</td>
<td class='x23'>5313258</td>
<td class='x23'>19993</td>
<td class='x23'>19993</td>
<td class='x23'>19993</td>
<td class='x23'>19993</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r15'>
<td height='18' class='x21' style='height:14.1pt;'>bpred_bimod.jr_non_ras_seen.PP</td>
<td class='x23'>5313258</td>
<td class='x23'>5313258</td>
<td class='x23'>24071</td>
<td class='x23'>24071</td>
<td class='x23'>24071</td>
<td class='x23'>24071</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r16'>
<td height='18' class='x21' style='height:14.1pt;'>bpred_bimod.bpred_addr_rate</td>
<td class='x23'>0.7012</td>
<td class='x23'>0.7284</td>
<td class='x23'>0.8352</td>
<td class='x23'>0.8361</td>
<td class='x23'>0.8362</td>
<td class='x23'>0.8362</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r17'>
<td height='18' class='x21' style='height:14.1pt;'>bpred_bimod.bpred_dir_rate</td>
<td class='x23'>0.7012</td>
<td class='x23'>0.7284</td>
<td class='x23'>0.8355</td>
<td class='x23'>0.8364</td>
<td class='x23'>0.8364</td>
<td class='x23'>0.8364</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r18'>
<td height='18' class='x21' style='height:14.1pt;'>bpred_bimod.bpred_jr_rate</td>
<td class='x23'>1.0000</td>
<td class='x23'>1.0000</td>
<td class='x23'>0.9953</td>
<td class='x23'>0.9953</td>
<td class='x23'>0.9953</td>
<td class='x23'>0.9953</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r19'>
<td height='18' class='x21' style='height:14.1pt;'>bpred_bimod.bpred_jr_non_ras_rate.PP</td>
<td class='x23'>1.0000</td>
<td class='x23'>1.0000</td>
<td class='x23'>0.8306</td>
<td class='x23'>0.8306</td>
<td class='x23'>0.8306</td>
<td class='x23'>0.8306</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r20'>
<td height='18' class='x21' style='height:14.1pt;'>bpred_bimod.retstack_pushes</td>
<td class='x23'>0</td>
<td class='x23'>0</td>
<td class='x23'>3076045</td>
<td class='x23'>3076045</td>
<td class='x23'>3076045</td>
<td class='x23'>3076045</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r21'>
<td height='18' class='x21' style='height:14.1pt;'>bpred_bimod.retstack_pops</td>
<td class='x23'>0</td>
<td class='x23'>0</td>
<td class='x23'>3076041</td>
<td class='x23'>3076041</td>
<td class='x23'>3076041</td>
<td class='x23'>3076041</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r22'>
<td height='18' class='x21' style='height:14.1pt;'>bpred_bimod.used_ras.PP</td>
<td class='x23'>0</td>
<td class='x23'>0</td>
<td class='x23'>3076041</td>
<td class='x23'>3076041</td>
<td class='x23'>3076041</td>
<td class='x23'>3076041</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r23'>
<td height='18' class='x21' style='height:14.1pt;'>bpred_bimod.ras_hits.PP</td>
<td class='x23'>0</td>
<td class='x23'>0</td>
<td class='x23'>3065671</td>
<td class='x23'>3065671</td>
<td class='x23'>3065671</td>
<td class='x23'>3065671</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r24'>
<td height='18' class='x21' style='height:14.1pt;'>bpred_bimod.ras_rate.PP</td>
<td class='x23'>&lt;error: divide by zero&gt;</td>
<td class='x23'>&lt;error: divide by zero&gt;</td>
<td class='x23'>0.9966</td>
<td class='x23'>0.9966</td>
<td class='x23'>0.9966</td>
<td class='x23'>0.9966</td>
 </tr>
</table>
</div>
<br>

>&emsp;&emsp;运行mcf测试数据集所得数据对比图如图25所示

<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src="https://img-blog.csdnimg.cn/20200704115839315.png">
    <br>
    <div style="color:orange; border-bottom: 1px solid #d9d9d9;
    display: inline-block;
    color: #999;
    padding: 2px;">图 26 运行mcf测试数据集数据对比</div>
</center>
<br>

>&emsp;&emsp;运行vortex测试数据集示例如图27所示。
<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src="https://img-blog.csdnimg.cn/202007041202296.png">
    <br>
    <div style="color:orange; border-bottom: 1px solid #d9d9d9;
    display: inline-block;
    color: #999;
    padding: 2px;">图 27 运行vortex测试数据集示例</div>
</center>
<br>

>&emsp;&emsp;运行vortex测试数据集所得数据如表3所示。

<div  style="text-align:center" >
<table style="width: 80%;margin:auto" border="2">
<caption>表3 运行vortex测试数据集所得数据</caption>
<col width='260' style='mso-width-source:userset;width:195pt'>
 <col width='155' span='2' style='mso-width-source:userset;width:116.25pt'>
 <col width='105' span='2' style='mso-width-source:userset;width:78.75pt'>
 <col width='154' style='mso-width-source:userset;width:115.5pt'>
 <col width='138' style='mso-width-source:userset;width:103.5pt'>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r0'>
<td height='18' class='x22' width='260' style='height:14.1pt;width:195pt;'></td>
<td class='x21' width='155' style='width:116.25pt;'>Always taken</td>
<td class='x21' width='155' style='width:116.25pt;'>always not taken</td>
<td class='x21' width='105' style='width:78.75pt;'>bimod(512) </td>
<td class='x21' width='105' style='width:78.75pt;'>Bimod(1024) </td>
<td class='x21' width='154' style='width:115.5pt;'>Two level (1,1024,8,0)</td>
<td class='x21' width='138' style='width:103.5pt;'>Two level (1,64,6,1)</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r1'>
<td height='18' class='x21' style='height:14.1pt;'>sim_total_insn</td>
<td class='x23'>437835</td>
<td class='x23'>437835</td>
<td class='x23'>437835</td>
<td class='x23'>437835</td>
<td class='x23'>437835</td>
<td class='x23'>437835</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r2'>
<td height='18' class='x21' style='height:14.1pt;'>sim_total_refs</td>
<td class='x23'>159898</td>
<td class='x23'>159898</td>
<td class='x23'>159898</td>
<td class='x23'>159898</td>
<td class='x23'>159898</td>
<td class='x23'>159898</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r3'>
<td height='18' class='x21' style='height:14.1pt;'>sim_elapsed_time</td>
<td class='x23'>1</td>
<td class='x23'>1</td>
<td class='x23'>1</td>
<td class='x23'>1</td>
<td class='x23'>1</td>
<td class='x23'>1</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r4'>
<td height='18' class='x21' style='height:14.1pt;'>sim_inst_rate</td>
<td class='x23'>437835.0000</td>
<td class='x23'>437835.0000</td>
<td class='x23'>437835.0000</td>
<td class='x23'>437835.0000</td>
<td class='x23'>437835.0000</td>
<td class='x23'>437835.0000</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r5'>
<td height='18' class='x21' style='height:14.1pt;'>sim_num_branches</td>
<td class='x23'>91210</td>
<td class='x23'>91210</td>
<td class='x23'>91210</td>
<td class='x23'>91210</td>
<td class='x23'>91210</td>
<td class='x23'>91210</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r6'>
<td height='18' class='x21' style='height:14.1pt;'>sim_IPB</td>
<td class='x23'>4.8003</td>
<td class='x23'>4.8003</td>
<td class='x23'>4.8003</td>
<td class='x23'>4.8003</td>
<td class='x23'>4.8003</td>
<td class='x23'>4.8003</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r7'>
<td height='18' class='x21' style='height:14.1pt;'>bpred_bimod.lookups</td>
<td class='x23'>91210</td>
<td class='x23'>91210</td>
<td class='x23'>91210</td>
<td class='x23'>91210</td>
<td class='x23'>91210</td>
<td class='x23'>91210</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r8'>
<td height='18' class='x21' style='height:14.1pt;'>bpred_bimod.updates</td>
<td class='x23'>91210</td>
<td class='x23'>91210</td>
<td class='x23'>91210</td>
<td class='x23'>91210</td>
<td class='x23'>91210</td>
<td class='x23'>91210</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r9'>
<td height='18' class='x21' style='height:14.1pt;'>bpred_bimod.addr_hits</td>
<td class='x23'>64600</td>
<td class='x23'>41900</td>
<td class='x23'>83463</td>
<td class='x23'>84030</td>
<td class='x23'>84476</td>
<td class='x23'>84476</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r10'>
<td height='18' class='x21' style='height:14.1pt;'>bpred_bimod.dir_hirts</td>
<td class='x23'>64600</td>
<td class='x23'>41900</td>
<td class='x23'>84487</td>
<td class='x23'>85055</td>
<td class='x23'>85500</td>
<td class='x23'>85500</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r11'>
<td height='18' class='x21' style='height:14.1pt;'>bpred_bimod.misses</td>
<td class='x23'>26610</td>
<td class='x23'>49310</td>
<td class='x23'>6723</td>
<td class='x23'>6155</td>
<td class='x23'>5710</td>
<td class='x23'>5710</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r12'>
<td height='18' class='x21' style='height:14.1pt;'>bpred_bimod.jr_hits</td>
<td class='x23'>4799</td>
<td class='x23'>4799</td>
<td class='x23'>4540</td>
<td class='x23'>4540</td>
<td class='x23'>4540</td>
<td class='x23'>4540</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r13'>
<td height='18' class='x21' style='height:14.1pt;'>bpred_bimod.jr_seen</td>
<td class='x23'>4799</td>
<td class='x23'>4799</td>
<td class='x23'>4799</td>
<td class='x23'>4799</td>
<td class='x23'>4799</td>
<td class='x23'>4799</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r14'>
<td height='18' class='x21' style='height:14.1pt;'>bpred_bimod.jr_non_ras_hits.PP</td>
<td class='x23'>4799</td>
<td class='x23'>4799</td>
<td class='x23'>289</td>
<td class='x23'>289</td>
<td class='x23'>289</td>
<td class='x23'>289</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r15'>
<td height='18' class='x21' style='height:14.1pt;'>bpred_bimod.jr_non_ras_seen.PP</td>
<td class='x23'>4799</td>
<td class='x23'>4799</td>
<td class='x23'>520</td>
<td class='x23'>520</td>
<td class='x23'>520</td>
<td class='x23'>520</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r16'>
<td height='18' class='x21' style='height:14.1pt;'>bpred_bimod.bpred_addr_rate</td>
<td class='x23'>0.7083</td>
<td class='x23'>0.4594</td>
<td class='x23'>0.9151</td>
<td class='x23'>0.9213</td>
<td class='x23'>0.9262</td>
<td class='x23'>0.9262</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r17'>
<td height='18' class='x21' style='height:14.1pt;'>bpred_bimod.bpred_dir_rate</td>
<td class='x23'>0.7083</td>
<td class='x23'>0.4594</td>
<td class='x23'>0.9263</td>
<td class='x23'>0.9325</td>
<td class='x23'>0.9374</td>
<td class='x23'>0.9374</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r18'>
<td height='18' class='x21' style='height:14.1pt;'>bpred_bimod.bpred_jr_rate</td>
<td class='x23'>1.0000</td>
<td class='x23'>1.0000</td>
<td class='x23'>0.9460</td>
<td class='x23'>0.9460</td>
<td class='x23'>0.9460</td>
<td class='x23'>0.9460</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r19'>
<td height='18' class='x21' style='height:14.1pt;'>bpred_bimod.bpred_jr_non_ras_rate.PP</td>
<td class='x23'>1.0000</td>
<td class='x23'>1.0000</td>
<td class='x23'>0.5558</td>
<td class='x23'>0.5558</td>
<td class='x23'>0.5558</td>
<td class='x23'>0.5558</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r20'>
<td height='18' class='x21' style='height:14.1pt;'>bpred_bimod.retstack_pushes</td>
<td class='x23'>0</td>
<td class='x23'>0</td>
<td class='x23'>4281</td>
<td class='x23'>4281</td>
<td class='x23'>4281</td>
<td class='x23'>4281</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r21'>
<td height='18' class='x21' style='height:14.1pt;'>bpred_bimod.retstack_pops</td>
<td class='x23'>0</td>
<td class='x23'>0</td>
<td class='x23'>4279</td>
<td class='x23'>4279</td>
<td class='x23'>4279</td>
<td class='x23'>4279</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r22'>
<td height='18' class='x21' style='height:14.1pt;'>bpred_bimod.used_ras.PP</td>
<td class='x23'>0</td>
<td class='x23'>0</td>
<td class='x23'>4279</td>
<td class='x23'>4279</td>
<td class='x23'>4279</td>
<td class='x23'>4279</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r23'>
<td height='18' class='x21' style='height:14.1pt;'>bpred_bimod.ras_hits.PP</td>
<td class='x23'>0</td>
<td class='x23'>0</td>
<td class='x23'>4251</td>
<td class='x23'>4251</td>
<td class='x23'>4251</td>
<td class='x23'>4251</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r24'>
<td height='18' class='x21' style='height:14.1pt;'>bpred_bimod.ras_rate.PP</td>
<td class='x23'>&lt;error: divide by zero&gt;</td>
<td class='x23'>&lt;error: divide by zero&gt;</td>
<td class='x23'>0.9935</td>
<td class='x23'>0.9935</td>
<td class='x23'>0.9935</td>
<td class='x23'>0.9935</td>
 </tr>
 </tr>
</table>
</div>
<br>
<br>

>&emsp;&emsp;运行vortex测试数据集所得数据对比图如图28所示。

<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src="https://img-blog.csdnimg.cn/20200704120821660.png">
    <br>
    <div style="color:orange; border-bottom: 1px solid #d9d9d9;
    display: inline-block;
    color: #999;
    padding: 2px;">图 28 运行vortex测试数据集数据对比图</div>
</center>
<br>

>&emsp;&emsp;运行vpr测试数据集示例如图29所示。
<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src="https://img-blog.csdnimg.cn/20200704121009906.png">
    <br>
    <div style="color:orange; border-bottom: 1px solid #d9d9d9;
    display: inline-block;
    color: #999;
    padding: 2px;">图 29 运行vpr测试数据集示例</div>
</center>
<br>

>运行vpr测试数据集所得数据如表4所示。
<div  style="text-align:center" >
<table style="width: 80%;margin:auto" border="2">
<caption>表4 运行vpr测试数据集所得数据</caption>
<col width='260' style='mso-width-source:userset;width:195pt'>
 <col width='155' span='2' style='mso-width-source:userset;width:116.25pt'>
 <col width='105' span='2' style='mso-width-source:userset;width:78.75pt'>
 <col width='154' style='mso-width-source:userset;width:115.5pt'>
 <col width='138' style='mso-width-source:userset;width:103.5pt'>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r0'>
<td height='18' class='x22' width='260' style='height:14.1pt;width:195pt;'></td>
<td class='x21' width='155' style='width:116.25pt;'>Always taken</td>
<td class='x21' width='155' style='width:116.25pt;'>always not taken</td>
<td class='x21' width='105' style='width:78.75pt;'>bimod(512) </td>
<td class='x21' width='105' style='width:78.75pt;'>Bimod(1024) </td>
<td class='x21' width='154' style='width:115.5pt;'>Two level (1,1024,8,0)</td>
<td class='x21' width='138' style='width:103.5pt;'>Two level (1,64,6,1)</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r1'>
<td height='18' class='x21' style='height:14.1pt;'>sim_total_insn</td>
<td class='x23'>27991</td>
<td class='x23'>27991</td>
<td class='x23'>27991</td>
<td class='x23'>27991</td>
<td class='x23'>27991</td>
<td class='x23'>27991</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r2'>
<td height='18' class='x21' style='height:14.1pt;'>sim_total_refs</td>
<td class='x23'>9772</td>
<td class='x23'>9772</td>
<td class='x23'>9772</td>
<td class='x23'>9772</td>
<td class='x23'>9772</td>
<td class='x23'>9772</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r3'>
<td height='18' class='x21' style='height:14.1pt;'>sim_elapsed_time</td>
<td class='x23'>1</td>
<td class='x23'>1</td>
<td class='x23'>1</td>
<td class='x23'>1</td>
<td class='x23'>1</td>
<td class='x23'>1</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r4'>
<td height='18' class='x21' style='height:14.1pt;'>sim_inst_rate</td>
<td class='x23'>27991.0000</td>
<td class='x23'>27991.0000</td>
<td class='x23'>27991.0000</td>
<td class='x23'>27991.0000</td>
<td class='x23'>27991.0000</td>
<td class='x23'>27991.0000</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r5'>
<td height='18' class='x21' style='height:14.1pt;'>sim_num_branches</td>
<td class='x23'>5286</td>
<td class='x23'>5286</td>
<td class='x23'>5286</td>
<td class='x23'>5286</td>
<td class='x23'>5286</td>
<td class='x23'>5286</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r6'>
<td height='18' class='x21' style='height:14.1pt;'>sim_IPB</td>
<td class='x23'>5.2953</td>
<td class='x23'>5.2953</td>
<td class='x23'>5.2953</td>
<td class='x23'>5.2953</td>
<td class='x23'>5.2953</td>
<td class='x23'>5.2953</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r7'>
<td height='18' class='x21' style='height:14.1pt;'>bpred_bimod.lookups</td>
<td class='x23'>5286</td>
<td class='x23'>5286</td>
<td class='x23'>5286</td>
<td class='x23'>5286</td>
<td class='x23'>5286</td>
<td class='x23'>5286</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r8'>
<td height='18' class='x21' style='height:14.1pt;'>bpred_bimod.updates</td>
<td class='x23'>5286</td>
<td class='x23'>5286</td>
<td class='x23'>5286</td>
<td class='x23'>5286</td>
<td class='x23'>5286</td>
<td class='x23'>5286</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r9'>
<td height='18' class='x21' style='height:14.1pt;'>bpred_bimod.addr_hits</td>
<td class='x23'>3361</td>
<td class='x23'>2794</td>
<td class='x23'>4489</td>
<td class='x23'>4549</td>
<td class='x23'>4590</td>
<td class='x23'>4590</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r10'>
<td height='18' class='x21' style='height:14.1pt;'>bpred_bimod.dir_hirts</td>
<td class='x23'>3361</td>
<td class='x23'>2794</td>
<td class='x23'>4710</td>
<td class='x23'>4769</td>
<td class='x23'>4806</td>
<td class='x23'>4806</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r11'>
<td height='18' class='x21' style='height:14.1pt;'>bpred_bimod.misses</td>
<td class='x23'>1925</td>
<td class='x23'>2492</td>
<td class='x23'>576</td>
<td class='x23'>517</td>
<td class='x23'>480</td>
<td class='x23'>480</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r12'>
<td height='18' class='x21' style='height:14.1pt;'>bpred_bimod.jr_hits</td>
<td class='x23'>359</td>
<td class='x23'>359</td>
<td class='x23'>342</td>
<td class='x23'>342</td>
<td class='x23'>342</td>
<td class='x23'>342</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r13'>
<td height='18' class='x21' style='height:14.1pt;'>bpred_bimod.jr_seen</td>
<td class='x23'>359</td>
<td class='x23'>359</td>
<td class='x23'>359</td>
<td class='x23'>359</td>
<td class='x23'>359</td>
<td class='x23'>359</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r14'>
<td height='18' class='x21' style='height:14.1pt;'>bpred_bimod.jr_non_ras_hits.PP</td>
<td class='x23'>359</td>
<td class='x23'>359</td>
<td class='x23'>0</td>
<td class='x23'>0</td>
<td class='x23'>0</td>
<td class='x23'>0</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r15'>
<td height='18' class='x21' style='height:14.1pt;'>bpred_bimod.jr_non_ras_seen.PP</td>
<td class='x23'>359</td>
<td class='x23'>359</td>
<td class='x23'>14</td>
<td class='x23'>14</td>
<td class='x23'>14</td>
<td class='x23'>14</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r16'>
<td height='18' class='x21' style='height:14.1pt;'>bpred_bimod.bpred_addr_rate</td>
<td class='x23'>0.6358</td>
<td class='x23'>0.5286</td>
<td class='x23'>0.8492</td>
<td class='x23'>0.8606</td>
<td class='x23'>0.8683</td>
<td class='x23'>0.8683</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r17'>
<td height='18' class='x21' style='height:14.1pt;'>bpred_bimod.bpred_dir_rate</td>
<td class='x23'>0.6358</td>
<td class='x23'>0.5286</td>
<td class='x23'>0.8910</td>
<td class='x23'>0.9022</td>
<td class='x23'>0.9092</td>
<td class='x23'>0.9092</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r18'>
<td height='18' class='x21' style='height:14.1pt;'>bpred_bimod.bpred_jr_rate</td>
<td class='x23'>1.0000</td>
<td class='x23'>1.0000</td>
<td class='x23'>0.9526</td>
<td class='x23'>0.9526</td>
<td class='x23'>0.9526</td>
<td class='x23'>0.9526</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r19'>
<td height='18' class='x21' style='height:14.1pt;'>bpred_bimod.bpred_jr_non_ras_rate.PP</td>
<td class='x23'>1.0000</td>
<td class='x23'>1.0000</td>
<td class='x23'>0.0000</td>
<td class='x23'>0.0000</td>
<td class='x23'>0.0000</td>
<td class='x23'>0.0000</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r20'>
<td height='18' class='x21' style='height:14.1pt;'>bpred_bimod.retstack_pushes</td>
<td class='x23'>0</td>
<td class='x23'>0</td>
<td class='x23'>349</td>
<td class='x23'>349</td>
<td class='x23'>349</td>
<td class='x23'>349</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r21'>
<td height='18' class='x21' style='height:14.1pt;'>bpred_bimod.retstack_pops</td>
<td class='x23'>0</td>
<td class='x23'>0</td>
<td class='x23'>345</td>
<td class='x23'>345</td>
<td class='x23'>345</td>
<td class='x23'>345</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r22'>
<td height='18' class='x21' style='height:14.1pt;'>bpred_bimod.used_ras.PP</td>
<td class='x23'>0</td>
<td class='x23'>0</td>
<td class='x23'>345</td>
<td class='x23'>345</td>
<td class='x23'>345</td>
<td class='x23'>345</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r23'>
<td height='18' class='x21' style='height:14.1pt;'>bpred_bimod.ras_hits.PP</td>
<td class='x23'>0</td>
<td class='x23'>0</td>
<td class='x23'>342</td>
<td class='x23'>342</td>
<td class='x23'>342</td>
<td class='x23'>342</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r24'>
<td height='18' class='x21' style='height:14.1pt;'>bpred_bimod.ras_rate.PP</td>
<td class='x23'>&lt;error: divide by zero&gt;</td>
<td class='x23'>&lt;error: divide by zero&gt;</td>
<td class='x23'>0.9913</td>
<td class='x23'>0.9913</td>
<td class='x23'>0.9913</td>
<td class='x23'>0.9913</td>
</table>
</div>

>运行vpr测试数据集所得数据对比图如图30所示。
<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src="https://img-blog.csdnimg.cn/20200704121429968.png">
    <br>
    <div style="color:orange; border-bottom: 1px solid #d9d9d9;
    display: inline-block;
    color: #999;
    padding: 2px;">图 30 运行vpr测试数据集数据对比</div>
</center>
<br>

>&emsp;&emsp;从图24、图26、图28与图30可知，一般地，采用always not taken 方式程序的分支预测错误概率相较而言最高，always taken方式次之，其余的bimod方式与two-level adaptive方式不论参数如何，性能大致相当。

<br>

## 4 关键程序代码

>&emsp;&emsp;本次实验所用命令如下所示。

```bash
#gcc taken
sim-bpred -bpred taken -max:inst 200000000 ../../../cc1.ss -O2 ./cccp.i
#gcc no taken
sim-bpred -bpred nottaken -max:inst 200000000 ../../../cc1.ss -O2 ./cccp.i
#gcc bimod(512)
sim-bpred -bpred:bimod 512 -max:inst 200000000 ../../../cc1.ss -O2 ./cccp.i
# gcc Bimod(1024) 
sim-bpred -bpred:bimod 1024 -max:inst 200000000 ../../../cc1.ss -O2 ./cccp.i
#gcc Two level (1,1024,8,0)
sim-bpred -bpred:2lev 1 1024 8 0 -max:inst 200000000 ../../../cc1.ss -O2 ./cccp.i
#gcc Two level (1,64,6,1)
sim-bpred -bpred:2lev 1 64 6 1 -max:inst 200000000 ../../../cc1.ss -O2 ./cccp.i

#mcf taken
sim-bpred -bpred taken -max:inst 2000000000 ./mcf.ss ./inp.in
#mcf no taken
sim-bpred -bpred nottaken -max:inst 2000000000 ./mcf.ss ./inp.in
#mcf bimod(512)
sim-bpred -bpred:bimod 512 -max:inst 200000000 ./mcf.ss ./inp.in
#mcf Bimod(1024)
sim-bpred -bpred:bimod 1024 -max:inst 200000000 ./mcf.ss ./inp.in
#mcf Two level (1,1024,8,0)
sim-bpred -bpred:2lev 1 1024 8 0 -max:inst 200000000 ./mcf.ss ./inp.in
#mcf Two level (1,64,6,1)
sim-bpred -bpred:2lev 1 64 6 1 -max:inst 200000000 ./mcf.ss ./inp.in

#vortex taken
sim-bpred -bpred taken -max:inst 2000000000 ../../../../../Simplescalar-master/spec95-little/vortex.ss ./bendian.raw ./bendian.rnv  ./bendian.wnv  ./lendian.raw  ./lendian.rnv  ./lendian.wnv  ./persons.1k
#vortex no taken
sim-bpred -bpred nottaken -max:inst 2000000000 ../../../../../Simplescalar-master/spec95-little/vortex.ss ./bendian.raw ./bendian.rnv  ./bendian.wnv  ./lendian.raw  ./lendian.rnv  ./lendian.wnv  ./persons.1k
#vortex bimod(512)
sim-bpred -bpred:bimod 512 -max:inst 200000000 ../../../../../Simplescalar-master/spec95-little/vortex.ss ./bendian.raw ./bendian.rnv  ./bendian.wnv  ./lendian.raw  ./lendian.rnv  ./lendian.wnv  ./persons.1k
#vortex Bimod(1024)
sim-bpred -bpred:bimod 1024 -max:inst 200000000 ../../../../../Simplescalar-master/spec95-little/vortex.ss ./bendian.raw ./bendian.rnv  ./bendian.wnv  ./lendian.raw  ./lendian.rnv  ./lendian.wnv  ./persons.1k
#vortex Two level (1,1024,8,0)
sim-bpred -bpred:2lev 1 1024 8 0 -max:inst 200000000 ./vortex.ss ./bendian.raw ./bendian.rnv  ./bendian.wnv  ./lendian.raw  ./lendian.rnv  ./lendian.wnv  ./persons.1k
#vortex Two level (1,64,6,1)
sim-bpred -bpred:2lev 1 64 6 1 -max:inst 200000000 ../../../../../Simplescalar-master/spec95-little/vortex.ss ./bendian.raw ./bendian.rnv  ./bendian.wnv  ./lendian.raw  ./lendian.rnv  ./lendian.wnv  ./persons.1k

#vpr taken
sim-bpred -bpred taken -max:inst 2000000000 ./vpr.ss ./arch.in ./net.in ./place.in
#vpr no taken
sim-bpred -bpred nottaken -max:inst 2000000000 -max:inst 200000000 ./vpr.ss ./arch.in ./net.in ./place.in
#vpr bimod(512)
sim-bpred -bpred:bimod 512 -max:inst 200000000 ./vpr.ss ./arch.in ./net.in ./place.in
#vpr Bimod(1024)
sim-bpred -bpred:bimod 1024 -max:inst 200000000 ./vpr.ss ./arch.in ./net.in ./place.in
#vpr Two level (1,1024,8,0)
sim-bpred -bpred:2lev 1 1024 8 0 -max:inst 200000000 ./vpr.ss ./arch.in ./net.in ./place.in
#vpr Two level (1,64,6,1)
sim-bpred -bpred:2lev 1 64 6 1 -max:inst 200000000  ./vpr.ss ./arch.in ./net.in ./place.in

```

## 5 实验心得
>&emsp;&emsp;在本次实验中，使用分支预测模拟器sim-bpred，在4种预测器类型及不同的参数配置下运行测试程序，并比较、分析结果，我加深对动态分支预测机制的理解，并了解各种分支预测实现方式的优劣。

<br>
<br>
<br>

# 实验三 缓存性能分析
## 1 实验内容
>&emsp;&emsp;通过实验和结果分析，理解缓存的各种参数对缓存性能的影响。

<br>
<br>
<br>

## 2 实验方法
>&emsp;&emsp;（1）安装和测试SimpleScalar模拟器(利用模拟器自带的测试程序进行测试)。<br>
&emsp;&emsp;（2）在基本配置情况下运行SPEC2000基准测试集下面的4个程序(请指明自己选的是哪些测试程序)统计Cache失效次数，并统计L2缓存的失效次数（注：配置二级缓存结构，
指令和数据合在一起）。<br>
&emsp;&emsp;（3）改变Cache容量（*2，*4，*8，*64），运行相同的测试程序，并统计L2缓存的失效次数计算失效率，并对结果进行总结分析。<br>
&emsp;&emsp;（4）改变Cache的相联度（2路，4路，8路，16路，64路），运行1中所选择的测试程序，并统计L2缓存的失效次数计算失效率，并对结果进行分析。<br>
&emsp;&emsp;（5）改变Cache块大小（*2，*4，*8，*64），运行1中所选择的测试程序，并统计L2缓存的失效次数计算失效率，并进行分析。

<br>
<br>
<br>

## 3 结果与分析
>&emsp;&emsp;我所选择的4个数据集分别为：bzip2、mcf、vortex与vpr。

>&emsp;&emsp;运行bzip2测试数据集示例如图31所示。
<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src="https://img-blog.csdnimg.cn/20200704122514466.png">
    <br>
    <div style="color:orange; border-bottom: 1px solid #d9d9d9;
    display: inline-block;
    color: #999;
    padding: 2px;">图 31 运行bzip2测试数据集示例</div>
</center>
<br>

>&emsp;&emsp;选定不同的Cache相联度对bzip2测试数据集进行测试所得数据如表5所示。（CSDN的Markdown不完全支持HTML，所以没办法绘制``table斜线``）

<table border='0' cellpadding='0' cellspacing='0' width='495' style='border-collapse: 
 collapse;table-layout:fixed;width:371pt'>
 <col width='175' style='mso-width-source:userset;width:131.25pt'>
 <caption>表 5 选定不同的Cache相联度对bzip2测试数据集进行测试所得数据</caption>
 <col width='64' span='5' style='width:48pt'>
 <tr height='48' style='mso-height-source:userset;height:36pt' id='r0'>
<td height='46' class='x21' width='175' style='height:34.5pt;width:131.25pt;'><font class="font2"><div align=right>Cache 相联度</div><span style='mso-spacerun:yes;'>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </span></font><font class="font3"><br><div align=left>指标</div><span style='mso-spacerun:yes;white-space:nowrap;'>&nbsp; </span></font></td>
<td class='x22' width='64' style='width:48pt;'>⨉2</td>
<td class='x22' width='64' style='width:48pt;'>⨉4</td>
<td class='x22' width='64' style='width:48pt;'>⨉8</td>
<td class='x22' width='64' style='width:48pt;'>⨉16</td>
<td class='x22' width='64' style='width:48pt;'>⨉64</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r1'>
<td height='18' class='x23' style='height:14.1pt;'>accesses</td>
<td class='x24'>50780 </td>
<td class='x24'>50780 </td>
<td class='x24'>50780 </td>
<td class='x24'>50780 </td>
<td class='x25'>50780</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r2'>
<td height='18' class='x23' style='height:14.1pt;'>hits</td>
<td class='x24'>47440 </td>
<td class='x24'>47391 </td>
<td class='x24'>47232 </td>
<td class='x24'>46993 </td>
<td class='x25'>46993</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r3'>
<td height='18' class='x23' style='height:14.1pt;'>misses</td>
<td class='x24'>3340 </td>
<td class='x24'>3389 </td>
<td class='x24'>3548 </td>
<td class='x24'>3787 </td>
<td class='x25'>3787</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r4'>
<td height='18' class='x23' style='height:14.1pt;'>replacements</td>
<td class='x24'>2316 </td>
<td class='x24'>2365 </td>
<td class='x24'>2524 </td>
<td class='x24'>2763 </td>
<td class='x25'>2763</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r5'>
<td height='18' class='x23' style='height:14.1pt;'>writebacks</td>
<td class='x24'>1958 </td>
<td class='x24'>1956 </td>
<td class='x24'>2025 </td>
<td class='x24'>2032 </td>
<td class='x25'>2041</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r6'>
<td height='18' class='x23' style='height:14.1pt;'>invalidations</td>
<td class='x24'>0 </td>
<td class='x24'>0 </td>
<td class='x24'>0 </td>
<td class='x24'>0 </td>
<td class='x25'>0</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r7'>
<td height='18' class='x23' style='height:14.1pt;'>miss_rate</td>
<td class='x24'>0.0658 </td>
<td class='x24'>0.0667 </td>
<td class='x24'>0.0699 </td>
<td class='x24'>0.0746 </td>
<td class='x25'>0.0746</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r8'>
<td height='18' class='x23' style='height:14.1pt;'>repl_rate</td>
<td class='x26'>0.0456</td>
<td class='x24'>0.0466 </td>
<td class='x24'>0.0497 </td>
<td class='x24'>0.0544 </td>
<td class='x25'>0.0544</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r9'>
<td height='18' class='x23' style='height:14.1pt;'>wb_rate</td>
<td class='x24'>0.0386 </td>
<td class='x24'>0.0385 </td>
<td class='x24'>0.0399 </td>
<td class='x24'>0.0400 </td>
<td class='x25'>0.0402</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r10'>
<td height='18' class='x23' style='height:14.1pt;'>inv_rate</td>
<td class='x24'>0.0000 </td>
<td class='x24'>0.0000 </td>
<td class='x24'>0.0000 </td>
<td class='x24'>0.0000 </td>
<td class='x24'>0.0000 </td>
 </tr>
</table>
<br>
<br>

>&emsp;&emsp;选定不同的Cache相联度对bzip2测试数据集进行测试所得数据对比如图49所示。

<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src="https://img-blog.csdnimg.cn/20200704143102950.png">
    <br>
    <div style="color:orange; border-bottom: 1px solid #d9d9d9;
    display: inline-block;
    color: #999;
    padding: 2px;">图 32 选定不同的Cache相联度对bzip2测试数据集进行测试所得数据对比</div>
</center>
<br>

>&emsp;&emsp;选定不同的Cache块大小对bzip2测试数据集进行测试所得数据如表6所示。

<table border='0' cellpadding='0' cellspacing='0' width='495' style='border-collapse: 
 collapse;table-layout:fixed;width:371pt'>
 <col width='175' style='mso-width-source:userset;width:131.25pt'>
 <caption>表 6 选定不同的Cache块大小对bzip2测试数据集进行测试所得数据</caption>
 <col width='64' span='5' style='width:48pt'>
 <tr height='48' style='mso-height-source:userset;height:36pt' id='r0'>
<td height='46' class='x21' width='175' style='height:34.5pt;width:131.25pt;'><font class="font2"><div align=right>Cache 块大小</div><span style='mso-spacerun:yes;'>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </span></font><font class="font3"><br><div align=left>指标</div><span style='mso-spacerun:yes;white-space:nowrap;'>&nbsp; </span></font></td>
<td class='x22' width='64' style='width:48pt;'>⨉2</td>
<td class='x22' width='64' style='width:48pt;'>⨉4</td>
<td class='x22' width='64' style='width:48pt;'>⨉8</td>
<td class='x22' width='64' style='width:48pt;'>⨉64</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r1'>
<td height='18' class='x23' style='height:14.1pt;'>accesses</td>
<td class='x24'>50780 </td>
<td class='x24'>50780 </td>
<td class='x24'>50780 </td>
<td class='x25'>50780</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r2'>
<td height='18' class='x23' style='height:14.1pt;'>hits</td>
<td class='x24'>37826 </td>
<td class='x24'>44230 </td>
<td class='x24'>47440 </td>
<td class='x25'>49067</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r3'>
<td height='18' class='x23' style='height:14.1pt;'>misses</td>
<td class='x24'>2954 </td>
<td class='x24'>6550 </td>
<td class='x24'>3340 </td>
<td class='x25'>1713</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r4'>
<td height='18' class='x23' style='height:14.1pt;'>replacements</td>
<td class='x24'>8858 </td>
<td class='x24'>4502 </td>
<td class='x24'>2316 </td>
<td class='x25'>1201</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r5'>
<td height='18' class='x23' style='height:14.1pt;'>writebacks</td>
<td class='x24'>7617 </td>
<td class='x24'>3851 </td>
<td class='x24'>1958 </td>
<td class='x25'>1003</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r6'>
<td height='18' class='x23' style='height:14.1pt;'>invalidations</td>
<td class='x24'>0 </td>
<td class='x24'>0 </td>
<td class='x24'>0 </td>
<td class='x25'>0</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r7'>
<td height='18' class='x23' style='height:14.1pt;'>miss_rate</td>
<td class='x24'>0.2551 </td>
<td class='x24'>0.1290 </td>
<td class='x24'>0.0658 </td>
<td class='x25'>0.0337</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r8'>
<td height='18' class='x23' style='height:14.1pt;'>repl_rate</td>
<td class='x26'>0.1744</td>
<td class='x24'>0.0887 </td>
<td class='x24'>0.0456 </td>
<td class='x25'>0.0237</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r9'>
<td height='18' class='x23' style='height:14.1pt;'>wb_rate</td>
<td class='x24'>0.1500 </td>
<td class='x24'>0.0758 </td>
<td class='x24'>0.0386 </td>
<td class='x25'>0.0198</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r10'>
<td height='18' class='x23' style='height:14.1pt;'>inv_rate</td>
<td class='x24'>0.0000 </td>
<td class='x24'>0.0000 </td>
<td class='x24'>0.0000 </td>
<td class='x24'>0.0000 </td>
 </tr>
</table>
<br>

>&emsp;&emsp;选定不同的Cache块大小对bzip2测试数据集进行测试所得数据对比如图33所示
<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src="https://img-blog.csdnimg.cn/20200704144120997.png">
    <br>
    <div style="color:orange; border-bottom: 1px solid #d9d9d9;
    display: inline-block;
    color: #999;
    padding: 2px;">图 33 选定不同的Cache块大小对bzip2测试数据集进行测试所得数据对比</div>
</center>
<br>

>&emsp;&emsp;选定不同的Cache容量对bzip2测试数据集进行测试所得数据如下表所示。
<table border='0' cellpadding='0' cellspacing='0' width='495' style='border-collapse: 
 collapse;table-layout:fixed;width:371pt'>
 <col width='175' style='mso-width-source:userset;width:131.25pt'>
 <caption>表 7 选定不同的Cache容量对bzip2测试数据集进行测试所得数据</caption>
 <col width='64' span='5' style='width:48pt'>
 <tr height='48' style='mso-height-source:userset;height:36pt' id='r0'>
<td height='46' class='x21' width='175' style='height:34.5pt;width:131.25pt;'><font class="font2"><div align=right>Cache 容量</div><span style='mso-spacerun:yes;'>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </span></font><font class="font3"><br><div align=left>指标</div><span style='mso-spacerun:yes;white-space:nowrap;'>&nbsp; </span></font></td>
<td class='x22' width='64' style='width:48pt;'>⨉2</td>
<td class='x22' width='64' style='width:48pt;'>⨉4</td>
<td class='x22' width='64' style='width:48pt;'>⨉8</td>
<td class='x22' width='64' style='width:48pt;'>⨉64</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r1'>
<td height='18' class='x23' style='height:14.1pt;'>accesses</td>
<td class='x24' x:num="50780">50780</td>
<td class='x24'>50780</td>
<td class='x24'>50780</td>
<td class='x24'>50780</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r2'>
<td height='18' class='x23' style='height:14.1pt;'>hits</td>
<td class='x24' x:num="46487">46487</td>
<td class='x24'>46533</td>
<td class='x24'>46560</td>
<td class='x24'>47786</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r3'>
<td height='18' class='x23' style='height:14.1pt;'>misses</td>
<td class='x24' x:num="4293">4293</td>
<td class='x24'>4247</td>
<td class='x24'>4220</td>
<td class='x24'>2994</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r4'>
<td height='18' class='x23' style='height:14.1pt;'>replacements</td>
<td class='x24' x:num="4229">4229</td>
<td class='x24'>4119</td>
<td class='x24'>3964</td>
<td class='x24'>946</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r5'>
<td height='18' class='x23' style='height:14.1pt;'>writebacks</td>
<td class='x24' x:num="2990">2990</td>
<td class='x24'>2910</td>
<td class='x24'>2766</td>
<td class='x24'>917</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r6'>
<td height='18' class='x23' style='height:14.1pt;'>invalidations</td>
<td class='x24' x:num="0">0</td>
<td class='x24' x:num="0">0</td>
<td class='x24'>0</td>
<td class='x24'>0</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r7'>
<td height='18' class='x23' style='height:14.1pt;'>miss_rate</td>
<td class='x24'>0.0845</td>
<td class='x24'>0.0836</td>
<td class='x24'>0.0831</td>
<td class='x24'>0.0590</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r8'>
<td height='18' class='x23' style='height:14.1pt;'>repl_rate</td>
<td class='x25'>0.0833</td>
<td class='x24'>0.0811</td>
<td class='x24'>0.0781</td>
<td class='x24'>0.0186</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r9'>
<td height='18' class='x23' style='height:14.1pt;'>wb_rate</td>
<td class='x24'>0.0589</td>
<td class='x24'>0.0573</td>
<td class='x24'>0.0545</td>
<td class='x24'>0.0181</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r10'>
<td height='18' class='x23' style='height:14.1pt;'>inv_rate</td>
<td class='x24'>0.0000</td>
<td class='x24'>0.0000</td>
<td class='x24'>0.0000</td>
<td class='x24'>0.0000</td>
 </tr>
</table>
<br>

>&emsp;&emsp;选定不同的Cache容量对bzip2测试数据集进行测试所得数据对比如图34所示。
<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src="https://img-blog.csdnimg.cn/20200704144624565.png">
    <br>
    <div style="color:orange; border-bottom: 1px solid #d9d9d9;
    display: inline-block;
    color: #999;
    padding: 2px;">图 34 选定不同的Cache容量对bzip2测试数据集进行测试所得数据对比</div>
</center>
<br>

>选定不同的Cache相联度对mcf测试数据集进行测试所得数据如表8所示。
<table border='0' cellpadding='0' cellspacing='0' width='495' style='border-collapse: 
 collapse;table-layout:fixed;width:371pt'>
 <col width='175' style='mso-width-source:userset;width:131.25pt'>
 <caption>表 8 选定不同的Cache相联度对mcf测试数据集进行测试所得数据</caption>
 <col width='64' span='5' style='width:48pt'>
 <tr height='48' style='mso-height-source:userset;height:36pt' id='r0'>
<td height='46' class='x21' width='175' style='height:34.5pt;width:131.25pt;'><font class="font2"><div align=right>Cache 相联度</div><span style='mso-spacerun:yes;'>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </span></font><font class="font3"><br><div align=left>指标</div><span style='mso-spacerun:yes;white-space:nowrap;'>&nbsp; </span></font></td>
<td class='x22' width='128' style='width:96pt;'>⨉2</td>
<td class='x22' width='86' style='width:64.5pt;'>⨉4</td>
<td class='x22' width='116' style='width:87pt;'>⨉8</td>
<td class='x22' width='139' style='width:104.25pt;'>⨉16</td>
<td class='x22' width='93' style='width:69.75pt;'>⨉64</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r1'>
<td height='18' class='x23' style='height:14.1pt;'>accesses</td>
<td class='x24'>100435002 </td>
<td class='x24'>100435002 </td>
<td class='x24'>100435002 </td>
<td class='x24'>100435002 </td>
<td class='x25' x:num="100435002">100435002</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r2'>
<td height='18' class='x23' style='height:14.1pt;'>hits</td>
<td class='x24'>91282103 </td>
<td class='x24'>91974221 </td>
<td class='x24'>92047776 </td>
<td class='x24'>92101882 </td>
<td class='x25' x:num="92022155">92022155</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r3'>
<td height='18' class='x23' style='height:14.1pt;'>misses</td>
<td class='x24'>9152899 </td>
<td class='x24'>8460781 </td>
<td class='x24'>8387226 </td>
<td class='x24'>8333120 </td>
<td class='x25' x:num="8412847">8412847</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r4'>
<td height='18' class='x23' style='height:14.1pt;'>replacements</td>
<td class='x24'>9151875 </td>
<td class='x24'>8459757 </td>
<td class='x24'>8386202 </td>
<td class='x24'>8332096 </td>
<td class='x25' x:num="8411823">8411823</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r5'>
<td height='18' class='x23' style='height:14.1pt;'>writebacks</td>
<td class='x24'>4234344 </td>
<td class='x24'>4122739 </td>
<td class='x24'>4091243 </td>
<td class='x24'>4078597 </td>
<td class='x25' x:num="4084706">4084706</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r6'>
<td height='18' class='x23' style='height:14.1pt;'>invalidations</td>
<td class='x24'>0 </td>
<td class='x24'>0 </td>
<td class='x24'>0 </td>
<td class='x24'>0 </td>
<td class='x25' x:num="0">0</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r7'>
<td height='18' class='x23' style='height:14.1pt;'>miss_rate</td>
<td class='x24'>0.0911 </td>
<td class='x24'>0.0842 </td>
<td class='x24'>0.0835 </td>
<td class='x24'>0.0830 </td>
<td class='x25' x:num="0.083799999999999999">0.0838</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r8'>
<td height='18' class='x23' style='height:14.1pt;'>repl_rate</td>
<td class='x24' x:num="0.0911">0.0911</td>
<td class='x24'>0.0842 </td>
<td class='x24'>0.0835 </td>
<td class='x24'>0.0830 </td>
<td class='x25' x:num="0.083799999999999999">0.0838</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r9'>
<td height='18' class='x23' style='height:14.1pt;'>wb_rate</td>
<td class='x24'>0.0422 </td>
<td class='x24'>0.0410 </td>
<td class='x24'>0.0407 </td>
<td class='x24'>0.0406 </td>
<td class='x25' x:num="0.0407">0.0407</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r10'>
<td height='18' class='x23' style='height:14.1pt;'>inv_rate</td>
<td class='x24'>0.0000 </td>
<td class='x24'>0.0000 </td>
<td class='x24'>0.0000 </td>
<td class='x24'>0.0000 </td>
<td class='x24'>0.0000 </td>
 </tr>
</table>
<br>

>选定不同的Cache相联度对mcf测试数据集进行测试所得数据对比如图35所示。
<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src="https://img-blog.csdnimg.cn/20200704145051820.png">
    <br>
    <div style="color:orange; border-bottom: 1px solid #d9d9d9;
    display: inline-block;
    color: #999;
    padding: 2px;">图 35 选定不同的Cache相联度对mcf测试数据集进行测试所得数据对比</div>
</center>
<br>

>&emsp;&emsp;选定不同的Cache块大小对mcf测试数据集进行测试所得数据如表9所示。
<table border='0' cellpadding='0' cellspacing='0' width='495' style='border-collapse: 
 collapse;table-layout:fixed;width:371pt'>
 <col width='175' style='mso-width-source:userset;width:131.25pt'>
 <caption>表 9 选定不同的Cache块大小对mcf测试数据集进行测试所得数据</caption>
 <col width='64' span='5' style='width:48pt'>
 <tr height='48' style='mso-height-source:userset;height:36pt' id='r0'>
<td height='46' class='x21' width='175' style='height:34.5pt;width:131.25pt;'><font class="font2"><div align=right>Cache 块大小</div><span style='mso-spacerun:yes;'>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </span></font><font class="font3"><br><div align=left>指标</div><span style='mso-spacerun:yes;white-space:nowrap;'>&nbsp; </span></font></td>
<td class='x22' width='132' style='width:99pt;'>⨉2</td>
<td class='x22' width='111' style='width:83.25pt;'>⨉4</td>
<td class='x22' width='98' style='width:73.5pt;'>⨉8</td>
<td class='x22' width='129' style='width:96.75pt;'>⨉64</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r1'>
<td height='18' class='x23' style='height:14.1pt;'>accesses</td>
<td class='x24'>100435002 </td>
<td class='x24'>100435002 </td>
<td class='x24'>100435002 </td>
<td class='x24'>100435002 </td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r2'>
<td height='18' class='x23' style='height:14.1pt;'>hits</td>
<td class='x24'>78211037 </td>
<td class='x24'>85942231 </td>
<td class='x24'>91282103 </td>
<td class='x24'>92680384 </td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r3'>
<td height='18' class='x23' style='height:14.1pt;'>misses</td>
<td class='x24'>22223965 </td>
<td class='x24'>14492771 </td>
<td class='x24'>9152899 </td>
<td class='x24'>7754618 </td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r4'>
<td height='18' class='x23' style='height:14.1pt;'>replacements</td>
<td class='x24'>22219869 </td>
<td class='x24'>14490723 </td>
<td class='x24'>9151875 </td>
<td class='x24'>7754106 </td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r5'>
<td height='18' class='x23' style='height:14.1pt;'>writebacks</td>
<td class='x24'>13542641 </td>
<td class='x24'>17396647 </td>
<td class='x24'>14234344 </td>
<td class='x24'>2670910 </td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r6'>
<td height='18' class='x23' style='height:14.1pt;'>invalidations</td>
<td class='x24'>0 </td>
<td class='x24'>0 </td>
<td class='x24'>0 </td>
<td class='x24'>0 </td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r7'>
<td height='18' class='x23' style='height:14.1pt;'>miss_rate</td>
<td class='x24'>0.2213 </td>
<td class='x24'>0.1443 </td>
<td class='x24'>0.0911 </td>
<td class='x24'>0.0772 </td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r8'>
<td height='18' class='x23' style='height:14.1pt;'>repl_rate</td>
<td class='x25'>0.2212</td>
<td class='x24'>0.1443 </td>
<td class='x24'>0.0911 </td>
<td class='x24'>0.0772 </td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r9'>
<td height='18' class='x23' style='height:14.1pt;'>wb_rate</td>
<td class='x24'>0.1348 </td>
<td class='x24'>0.0736 </td>
<td class='x24'>0.0422 </td>
<td class='x24'>0.0266 </td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r10'>
<td height='18' class='x23' style='height:14.1pt;'>inv_rate</td>
<td class='x24'>0.0000 </td>
<td class='x24'>0.0000 </td>
<td class='x24'>0.0000 </td>
<td class='x24'>0.0000 </td>
 </tr>
</table>
<br>

>&emsp;&emsp;选定不同的Cache块大小对mcf测试数据集进行测试所得数据对比如图36所示。
<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src="https://img-blog.csdnimg.cn/20200704145531303.png">
    <br>
    <div style="color:orange; border-bottom: 1px solid #d9d9d9;
    display: inline-block;
    color: #999;
    padding: 2px;">图 36 选定不同的Cache块大小对mcf测试数据集进行测试所得数据对比</div>
</center>
<br>

>&emsp;&emsp;选定不同的Cache容量对mcf测试数据集进行测试所得数据如10表所示。
<table border='0' cellpadding='0' cellspacing='0' width='495' style='border-collapse: 
 collapse;table-layout:fixed;width:371pt'>
 <col width='175' style='mso-width-source:userset;width:131.25pt'>
 <caption>表 10 选定不同的Cache容量对mcf测试数据集进行测试所得数据</caption>
 <col width='64' span='5' style='width:48pt'>
 <tr height='48' style='mso-height-source:userset;height:36pt' id='r0'>
<td height='46' class='x21' width='175' style='height:34.5pt;width:131.25pt;'><font class="font2"><div align=right>Cache 容量</div><span style='mso-spacerun:yes;'>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </span></font><font class="font3"><br><div align=left>指标</div><span style='mso-spacerun:yes;white-space:nowrap;'>&nbsp; </span></font></td>
<td class='x22' width='93' style='width:69.75pt;'>⨉2</td>
<td class='x22' width='101' style='width:75.75pt;'>⨉4</td>
<td class='x22' width='91' style='width:68.25pt;'>⨉8</td>
<td class='x22' width='79' style='width:59.25pt;'>⨉64</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r1'>
<td height='18' class='x23' style='height:14.1pt;'>accesses</td>
<td class='x24'>100435002</td>
<td class='x24'>100435002</td>
<td class='x24'>100435002</td>
<td class='x24'>100435002</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r2'>
<td height='18' class='x23' style='height:14.1pt;'>hits</td>
<td class='x24'>84950662</td>
<td class='x24'>86770503</td>
<td class='x24'>88204005</td>
<td class='x24'>93203363</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r3'>
<td height='18' class='x23' style='height:14.1pt;'>misses</td>
<td class='x24'>15484340</td>
<td class='x24'>13664499</td>
<td class='x24'>12230997</td>
<td class='x24'>7231639</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r4'>
<td height='18' class='x23' style='height:14.1pt;'>replacements</td>
<td class='x24'>15484276</td>
<td class='x24'>13664371</td>
<td class='x24'>12230741</td>
<td class='x24'>7229591</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r5'>
<td height='18' class='x23' style='height:14.1pt;'>writebacks</td>
<td class='x24'>5473601</td>
<td class='x24'>5245317</td>
<td class='x24'>4947506</td>
<td class='x24'>3926368</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r6'>
<td height='18' class='x23' style='height:14.1pt;'>invalidations</td>
<td class='x24'>0</td>
<td class='x24'>0</td>
<td class='x24'>0</td>
<td class='x24'>0</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r7'>
<td height='18' class='x23' style='height:14.1pt;'>miss_rate</td>
<td class='x24'>0.1542</td>
<td class='x24'>0.1361</td>
<td class='x24'>0.1218</td>
<td class='x24'>0.0720</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r8'>
<td height='18' class='x23' style='height:14.1pt;'>repl_rate</td>
<td class='x25'>0.1542</td>
<td class='x24'>0.1361</td>
<td class='x24'>0.1218</td>
<td class='x24'>0.0720</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r9'>
<td height='18' class='x23' style='height:14.1pt;'>wb_rate</td>
<td class='x24'>0.0545</td>
<td class='x24'>0.0522</td>
<td class='x24'>0.0493</td>
<td class='x24'>0.0391</td>
 </tr>
 <tr height='20' style='mso-height-source:userset;height:15.6pt' id='r10'>
<td height='18' class='x23' style='height:14.1pt;'>inv_rate</td>
<td class='x24'>0.0000</td>
<td class='x24'>0.0000</td>
<td class='x24'>0.0000</td>
<td class='x24'>0.0000</td>
 </tr>
</table>
<br>

>&emsp;&emsp;选定不同的Cache容量对mcf测试数据集进行测试所得数据对比如图37所示。
<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src="https://img-blog.csdnimg.cn/20200704145958546.png">
    <br>
    <div style="color:orange; border-bottom: 1px solid #d9d9d9;
    display: inline-block;
    color: #999;
    padding: 2px;">图 37 选定不同的Cache容量对mcf测试数据集进行测试所得数据对比</div>
</center>
<br>

>&emsp;&emsp;选定不同的Cache相联度对vortex测试数据集进行测试所得数据如表11所示。
<table border='0' cellpadding='0' cellspacing='0' width='495' style='border-collapse: 
 collapse;table-layout:fixed;width:371pt'>
 <col width='175' style='mso-width-source:userset;width:131.25pt'>
 <caption>表 11 选定不同的Cache相联度对vortex测试数据集进行测试所得数据</caption>
 <col width='64' span='5' style='width:48pt'>
 <tr height='48' style='mso-height-source:userset;height:36pt' id='r0'>
<td height='46' class='x21' width='175' style='height:34.5pt;width:131.25pt;'><font class="font2"><div align=right>Cache 相联度</div><span style='mso-spacerun:yes;'>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </span></font><font class="font3"><br><div align=left>指标</div><span style='mso-spacerun:yes;white-space:nowrap;'>&nbsp; </span></font></td>
<td class=xl66 width=131 style='border-left:none;width:98pt'>⨉2</td>
  <td class=xl66 width=89 style='border-left:none;width:67pt'>⨉4</td>
  <td class=xl66 width=119 style='border-left:none;width:89pt'>⨉8</td>
  <td class=xl66 width=143 style='border-left:none;width:107pt'>⨉16</td>
  <td class=xl66 width=95 style='border-left:none;width:71pt'>⨉64</td>
 </tr>
 <tr height=21 style='height:15.6pt'>
  <td height=21 class=xl67 style='height:15.6pt;border-top:none'>accesses</td>
  <td class=xl68 style='border-top:none;border-left:none'>179276<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>179276<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>179276<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>179276<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl69 style='border-top:none;border-left:none'>179276<span
  style='mso-spacerun:yes'> </span></td>
 </tr>
 <tr height=21 style='height:15.6pt'>
  <td height=21 class=xl67 style='height:15.6pt;border-top:none'>hits</td>
  <td class=xl68 style='border-top:none;border-left:none'>172023<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>172065<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>172007<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>171994<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl69 style='border-top:none;border-left:none'>171981<span
  style='mso-spacerun:yes'> </span></td>
 </tr>
 <tr height=21 style='height:15.6pt'>
  <td height=21 class=xl67 style='height:15.6pt;border-top:none'>misses</td>
  <td class=xl68 style='border-top:none;border-left:none'>7253<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>7211<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>7269<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>7282<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl69 style='border-top:none;border-left:none'>7295<span
  style='mso-spacerun:yes'> </span></td>
 </tr>
 <tr height=21 style='height:15.6pt'>
  <td height=21 class=xl67 style='height:15.6pt;border-top:none'>replacements</td>
  <td class=xl68 style='border-top:none;border-left:none'>6229<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>6187<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>6245<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>6258<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl69 style='border-top:none;border-left:none'>6271<span
  style='mso-spacerun:yes'> </span></td>
 </tr>
 <tr height=21 style='height:15.6pt'>
  <td height=21 class=xl67 style='height:15.6pt;border-top:none'>writebacks</td>
  <td class=xl68 style='border-top:none;border-left:none'>5973<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>5965<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>6017<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>6030<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl69 style='border-top:none;border-left:none'>6047<span
  style='mso-spacerun:yes'> </span></td>
 </tr>
 <tr height=21 style='height:15.6pt'>
  <td height=21 class=xl67 style='height:15.6pt;border-top:none'>invalidations</td>
  <td class=xl68 style='border-top:none;border-left:none'>0<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>0<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>0<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>0<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl69 style='border-top:none;border-left:none'>0<span
  style='mso-spacerun:yes'> </span></td>
 </tr>
 <tr height=21 style='height:15.6pt'>
  <td height=21 class=xl67 style='height:15.6pt;border-top:none'>miss_rate</td>
  <td class=xl68 style='border-top:none;border-left:none'>0.0405<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>0.0402<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>0.0405<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>0.0406<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl69 style='border-top:none;border-left:none'>0.0407<span
  style='mso-spacerun:yes'> </span></td>
 </tr>
 <tr height=21 style='height:15.6pt'>
  <td height=21 class=xl67 style='height:15.6pt;border-top:none'>repl_rate</td>
  <td class=xl68 style='border-top:none;border-left:none'>0.0347<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>0.0345<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>0.0348<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>0.0349<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl69 style='border-top:none;border-left:none'>0.0350<span
  style='mso-spacerun:yes'> </span></td>
 </tr>
 <tr height=21 style='height:15.6pt'>
  <td height=21 class=xl67 style='height:15.6pt;border-top:none'>wb_rate</td>
  <td class=xl68 style='border-top:none;border-left:none'>0.0333<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>0.0333<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>0.0336<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>0.0336<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl69 style='border-top:none;border-left:none'>0.0337<span
  style='mso-spacerun:yes'> </span></td>
 </tr>
 <tr height=21 style='height:15.6pt'>
  <td height=21 class=xl67 style='height:15.6pt;border-top:none'>inv_rate</td>
  <td class=xl68 style='border-top:none;border-left:none'>0.0000<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>0.0000<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>0.0000<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>0.0000<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>0.0000<span
  style='mso-spacerun:yes'> </span></td>
 </tr>
</table>
<br>

>&emsp;&emsp;选定不同的Cache相联度对vortex测试数据集进行测试所得数据对比如图38所示。
<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src="https://img-blog.csdnimg.cn/20200704150651213.png">
    <br>
    <div style="color:orange; border-bottom: 1px solid #d9d9d9;
    display: inline-block;
    color: #999;
    padding: 2px;">图 38 选定不同的Cache相联度对vortex测试数据集进行测试所得数据对比</div>
</center>
<br>

>&emsp;&emsp;选定不同的Cache块大小对vortex测试数据集进行测试所得数据如表12所示。
<table border='0' cellpadding='0' cellspacing='0' width='495' style='border-collapse: 
 collapse;table-layout:fixed;width:371pt'>
 <col width='175' style='mso-width-source:userset;width:131.25pt'>
 <caption>表 12 选定不同的Cache块大小对vortex测试数据集进行测试所得数据</caption>
 <col width='64' span='5' style='width:48pt'>
 <tr height='48' style='mso-height-source:userset;height:36pt' id='r0'>
<td height='46' class='x21' width='175' style='height:34.5pt;width:131.25pt;'><font class="font2"><div align=right>Cache 块大小</div><span style='mso-spacerun:yes;'>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </span></font><font class="font3"><br><div align=left>指标</div><span style='mso-spacerun:yes;white-space:nowrap;'>&nbsp; </span></font></td>
<td class=xl66 width=136 style='border-left:none;width:102pt'>⨉2</td>
  <td class=xl66 width=114 style='border-left:none;width:86pt'>⨉4</td>
  <td class=xl66 width=101 style='border-left:none;width:76pt'>⨉8</td>
  <td class=xl66 width=133 style='border-left:none;width:100pt'>⨉64</td>
 </tr>
 <tr height=21 style='height:15.6pt'>
  <td height=21 class=xl67 style='height:15.6pt;border-top:none'>accesses</td>
  <td class=xl68 style='border-top:none;border-left:none'>179276<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>179276<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>179276<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>179276<span
  style='mso-spacerun:yes'> </span></td>
 </tr>
 <tr height=21 style='height:15.6pt'>
  <td height=21 class=xl67 style='height:15.6pt;border-top:none'>hits</td>
  <td class=xl68 style='border-top:none;border-left:none'>151381<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>165145<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>172023<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>175493<span
  style='mso-spacerun:yes'> </span></td>
 </tr>
 <tr height=21 style='height:15.6pt'>
  <td height=21 class=xl67 style='height:15.6pt;border-top:none'>misses</td>
  <td class=xl68 style='border-top:none;border-left:none'>27895<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>14131<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>7253<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>3783<span
  style='mso-spacerun:yes'> </span></td>
 </tr>
 <tr height=21 style='height:15.6pt'>
  <td height=21 class=xl67 style='height:15.6pt;border-top:none'>replacements</td>
  <td class=xl68 style='border-top:none;border-left:none'>23799<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>12083<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>6229<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>3271<span
  style='mso-spacerun:yes'> </span></td>
 </tr>
 <tr height=21 style='height:15.6pt'>
  <td height=21 class=xl67 style='height:15.6pt;border-top:none'>writebacks</td>
  <td class=xl68 style='border-top:none;border-left:none'>23036<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>11665<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>5973<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>3110<span
  style='mso-spacerun:yes'> </span></td>
 </tr>
 <tr height=21 style='height:15.6pt'>
  <td height=21 class=xl67 style='height:15.6pt;border-top:none'>invalidations</td>
  <td class=xl68 style='border-top:none;border-left:none'>0<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>0<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>0<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>0<span
  style='mso-spacerun:yes'> </span></td>
 </tr>
 <tr height=21 style='height:15.6pt'>
  <td height=21 class=xl67 style='height:15.6pt;border-top:none'>miss_rate</td>
  <td class=xl68 style='border-top:none;border-left:none'>0.1556<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>0.0788<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>0.0405<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>0.0211<span
  style='mso-spacerun:yes'> </span></td>
 </tr>
 <tr height=21 style='height:15.6pt'>
  <td height=21 class=xl67 style='height:15.6pt;border-top:none'>repl_rate</td>
  <td class=xl69 style='border-top:none;border-left:none'>0.1328</td>
  <td class=xl68 style='border-top:none;border-left:none'>0.0674<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>0.0347<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>0.0182<span
  style='mso-spacerun:yes'> </span></td>
 </tr>
 <tr height=21 style='height:15.6pt'>
  <td height=21 class=xl67 style='height:15.6pt;border-top:none'>wb_rate</td>
  <td class=xl68 style='border-top:none;border-left:none'>0.1285<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>0.0651<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>0.0333<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>0.0173<span
  style='mso-spacerun:yes'> </span></td>
 </tr>
 <tr height=21 style='height:15.6pt'>
  <td height=21 class=xl67 style='height:15.6pt;border-top:none'>inv_rate</td>
  <td class=xl68 style='border-top:none;border-left:none'>0.0000<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>0.0000<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>0.0000<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>0.0000<span
  style='mso-spacerun:yes'> </span></td>
 </tr>
</table>
<br>

>选定不同的Cache块大小对vortex测试数据集进行测试所得数据对比如图39所示。
<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src="https://img-blog.csdnimg.cn/20200704151059696.png">
    <br>
    <div style="color:orange; border-bottom: 1px solid #d9d9d9;
    display: inline-block;
    color: #999;
    padding: 2px;">图 39 选定不同的Cache块大小对vortex测试数据集进行测试所得数据对比</div>
</center>
<br>

>选定不同的Cache容量对vortex测试数据集进行测试所得数据如表13所示。
<table border='0' cellpadding='0' cellspacing='0' width='495' style='border-collapse: 
 collapse;table-layout:fixed;width:371pt'>
 <col width='175' style='mso-width-source:userset;width:131.25pt'>
 <caption>表 13 选定不同的Cache容量对vortex测试数据集进行测试所得数据</caption>
 <col width='64' span='5' style='width:48pt'>
 <tr height='48' style='mso-height-source:userset;height:36pt' id='r0'>
<td height='46' class='x21' width='175' style='height:34.5pt;width:131.25pt;'><font class="font2"><div align=right>Cache 容量</div><span style='mso-spacerun:yes;'>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </span></font><font class="font3"><br><div align=left>指标</div><span style='mso-spacerun:yes;white-space:nowrap;'>&nbsp; </span></font></td>
<td class=xl66 width=95 style='border-left:none;width:71pt'>⨉2</td>
  <td class=xl66 width=104 style='border-left:none;width:78pt'>⨉4</td>
  <td class=xl66 width=94 style='border-left:none;width:70pt'>⨉8</td>
  <td class=xl66 width=64 style='border-left:none;width:48pt'>⨉64</td>
 </tr>
 <tr height=21 style='height:15.6pt'>
  <td height=21 class=xl67 style='height:15.6pt;border-top:none'>accesses</td>
  <td class=xl68 style='border-top:none;border-left:none'>179276<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>179276<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>179276<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>179276<span
  style='mso-spacerun:yes'> </span></td>
 </tr>
 <tr height=21 style='height:15.6pt'>
  <td height=21 class=xl67 style='height:15.6pt;border-top:none'>hits</td>
  <td class=xl68 style='border-top:none;border-left:none'>169301<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>170926<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>171530<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>172144<span
  style='mso-spacerun:yes'> </span></td>
 </tr>
 <tr height=21 style='height:15.6pt'>
  <td height=21 class=xl67 style='height:15.6pt;border-top:none'>misses</td>
  <td class=xl68 style='border-top:none;border-left:none'>9975<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>8350<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>7746<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>7132<span
  style='mso-spacerun:yes'> </span></td>
 </tr>
 <tr height=21 style='height:15.6pt'>
  <td height=21 class=xl67 style='height:15.6pt;border-top:none'>replacements</td>
  <td class=xl68 style='border-top:none;border-left:none'>9911<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>8222<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>7490<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>5084<span
  style='mso-spacerun:yes'> </span></td>
 </tr>
 <tr height=21 style='height:15.6pt'>
  <td height=21 class=xl67 style='height:15.6pt;border-top:none'>writebacks</td>
  <td class=xl68 style='border-top:none;border-left:none'>7927<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>7362<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>6998<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>4869<span
  style='mso-spacerun:yes'> </span></td>
 </tr>
 <tr height=21 style='height:15.6pt'>
  <td height=21 class=xl67 style='height:15.6pt;border-top:none'>invalidations</td>
  <td class=xl68 style='border-top:none;border-left:none'>0<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>0<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>0<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>0<span
  style='mso-spacerun:yes'> </span></td>
 </tr>
 <tr height=21 style='height:15.6pt'>
  <td height=21 class=xl67 style='height:15.6pt;border-top:none'>miss_rate</td>
  <td class=xl68 style='border-top:none;border-left:none'>0.0556<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>0.0466<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>0.0432<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>0.0398<span
  style='mso-spacerun:yes'> </span></td>
 </tr>
 <tr height=21 style='height:15.6pt'>
  <td height=21 class=xl67 style='height:15.6pt;border-top:none'>repl_rate</td>
  <td class=xl69 style='border-top:none;border-left:none'>0.0553</td>
  <td class=xl68 style='border-top:none;border-left:none'>0.0459<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>0.0418<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>0.0284<span
  style='mso-spacerun:yes'> </span></td>
 </tr>
 <tr height=21 style='height:15.6pt'>
  <td height=21 class=xl67 style='height:15.6pt;border-top:none'>wb_rate</td>
  <td class=xl68 style='border-top:none;border-left:none'>0.0442<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>0.0411<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>0.0390<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>0.0272<span
  style='mso-spacerun:yes'> </span></td>
 </tr>
 <tr height=21 style='height:15.6pt'>
  <td height=21 class=xl67 style='height:15.6pt;border-top:none'>inv_rate</td>
  <td class=xl68 style='border-top:none;border-left:none'>0.0000<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>0.0000<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>0.0000<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>0.0000<span
  style='mso-spacerun:yes'> </span></td>
 </tr>
</table>
<br>

>&emsp;&emsp;选定不同的Cache容量对vortex测试数据集进行测试所得数据对比如图40所示。
<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src="https://img-blog.csdnimg.cn/20200704151450920.png">
    <br>
    <div style="color:orange; border-bottom: 1px solid #d9d9d9;
    display: inline-block;
    color: #999;
    padding: 2px;">图 40 选定不同的Cache容量对vortex测试数据集进行测试所得数据对比</div>
</center>
<br>

>&emsp;&emsp;选定不同的Cache相联度对vpr测试数据集进行测试所得数据如表14所示。
<table border='0' cellpadding='0' cellspacing='0' width='495' style='border-collapse: 
 collapse;table-layout:fixed;width:371pt'>
 <col width='175' style='mso-width-source:userset;width:131.25pt'>
 <caption>表 14 选定不同的Cache相联度对vpr测试数据集进行测试所得数据</caption>
 <col width='64' span='5' style='width:48pt'>
 <tr height='48' style='mso-height-source:userset;height:36pt' id='r0'>
<td height='46' class='x21' width='175' style='height:34.5pt;width:131.25pt;'><font class="font2"><div align=right>Cache 相联度</div><span style='mso-spacerun:yes;'>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </span></font><font class="font3"><br><div align=left>指标</div><span style='mso-spacerun:yes;white-space:nowrap;'>&nbsp; </span></font></td>
<td class=xl66 width=131 style='border-left:none;width:98pt'>⨉2</td>
  <td class=xl66 width=89 style='border-left:none;width:67pt'>⨉4</td>
  <td class=xl66 width=119 style='border-left:none;width:89pt'>⨉8</td>
  <td class=xl66 width=143 style='border-left:none;width:107pt'>⨉16</td>
  <td class=xl66 width=95 style='border-left:none;width:71pt'>⨉64</td>
 </tr>
 <tr height=21 style='height:15.6pt'>
  <td height=21 class=xl67 style='height:15.6pt;border-top:none'>accesses</td>
  <td class=xl68 style='border-top:none;border-left:none'>10789<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>10789<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>10789<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>10789<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl69 style='border-top:none;border-left:none'>10789<span
  style='mso-spacerun:yes'> </span></td>
 </tr>
 <tr height=21 style='height:15.6pt'>
  <td height=21 class=xl67 style='height:15.6pt;border-top:none'>hits</td>
  <td class=xl68 style='border-top:none;border-left:none'>10261<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>10261<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>10261<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>10261<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl69 style='border-top:none;border-left:none'>10261<span
  style='mso-spacerun:yes'> </span></td>
 </tr>
 <tr height=21 style='height:15.6pt'>
  <td height=21 class=xl67 style='height:15.6pt;border-top:none'>misses</td>
  <td class=xl68 style='border-top:none;border-left:none'>528<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>528<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>528<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>528<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl69 style='border-top:none;border-left:none'>528<span
  style='mso-spacerun:yes'> </span></td>
 </tr>
 <tr height=21 style='height:15.6pt'>
  <td height=21 class=xl67 style='height:15.6pt;border-top:none'>replacements</td>
  <td class=xl68 style='border-top:none;border-left:none'>1</td>
  <td class=xl68 style='border-top:none;border-left:none'>0<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>0<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>0<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>0<span
  style='mso-spacerun:yes'> </span></td>
 </tr>
 <tr height=21 style='height:15.6pt'>
  <td height=21 class=xl67 style='height:15.6pt;border-top:none'>writebacks</td>
  <td class=xl68 style='border-top:none;border-left:none'>0<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>0<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>0<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>0<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl69 style='border-top:none;border-left:none'>0<span
  style='mso-spacerun:yes'> </span></td>
 </tr>
 <tr height=21 style='height:15.6pt'>
  <td height=21 class=xl67 style='height:15.6pt;border-top:none'>invalidations</td>
  <td class=xl68 style='border-top:none;border-left:none'>0<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>0<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>0<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>0<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl69 style='border-top:none;border-left:none'>0<span
  style='mso-spacerun:yes'> </span></td>
 </tr>
 <tr height=21 style='height:15.6pt'>
  <td height=21 class=xl67 style='height:15.6pt;border-top:none'>miss_rate</td>
  <td class=xl68 style='border-top:none;border-left:none'>0.0489<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>0.0489<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>0.0489<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>0.0489<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl69 style='border-top:none;border-left:none'>0.0489<span
  style='mso-spacerun:yes'> </span></td>
 </tr>
 <tr height=21 style='height:15.6pt'>
  <td height=21 class=xl67 style='height:15.6pt;border-top:none'>repl_rate</td>
  <td class=xl68 style='border-top:none;border-left:none'>0.0001<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>0.0000<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>0.0000<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>0.0000<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl69 style='border-top:none;border-left:none'>0.0000<span
  style='mso-spacerun:yes'> </span></td>
 </tr>
 <tr height=21 style='height:15.6pt'>
  <td height=21 class=xl67 style='height:15.6pt;border-top:none'>wb_rate</td>
  <td class=xl68 style='border-top:none;border-left:none'>0.0000<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>0.0000<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>0.0000<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>0.0000<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl69 style='border-top:none;border-left:none'>0.0000<span
  style='mso-spacerun:yes'> </span></td>
 </tr>
 <tr height=21 style='height:15.6pt'>
  <td height=21 class=xl67 style='height:15.6pt;border-top:none'>inv_rate</td>
  <td class=xl68 style='border-top:none;border-left:none'>0.0000<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>0.0000<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>0.0000<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>0.0000<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>0.0000<span
  style='mso-spacerun:yes'> </span></td>
 </tr>
</table>
<br>

>&emsp;&emsp;选定不同的Cache相联度对vpr测试数据集进行测试所得数据对比如图41所示。
<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src="https://img-blog.csdnimg.cn/2020070415184283.png">
    <br>
    <div style="color:orange; border-bottom: 1px solid #d9d9d9;
    display: inline-block;
    color: #999;
    padding: 2px;">图 41 选定不同的Cache相联度对vpr测试数据集进行测试所得数据对比</div>
</center>
<br>

>&emsp;&emsp;使用vpr测试数据集设置Cache块大小进行测试的示例如图42所示。
<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src="https://img-blog.csdnimg.cn/2020070415205034.png">
    <br>
    <div style="color:orange; border-bottom: 1px solid #d9d9d9;
    display: inline-block;
    color: #999;
    padding: 2px;">图 42 使用vpr测试数据集设置Cache块大小进行测试示例</div>
</center>
<br>

>&emsp;&emsp;选定不同的Cache块大小对vpr测试数据集进行测试所得数据如表15所示。
<table border='0' cellpadding='0' cellspacing='0' width='495' style='border-collapse: 
 collapse;table-layout:fixed;width:371pt'>
 <col width='175' style='mso-width-source:userset;width:131.25pt'>
 <caption>表 15 选定不同的Cache块大小对vpr测试数据集进行测试所得数据</caption>
 <col width='64' span='5' style='width:48pt'>
 <tr height='48' style='mso-height-source:userset;height:36pt' id='r0'>
<td height='46' class='x21' width='175' style='height:34.5pt;width:131.25pt;'><font class="font2"><div align=right>Cache 块大小</div><span style='mso-spacerun:yes;'>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </span></font><font class="font3"><br><div align=left>指标</div><span style='mso-spacerun:yes;white-space:nowrap;'>&nbsp; </span></font></td>
<td class=xl67 width=136 style='border-left:none;width:102pt'>⨉2</td>
  <td class=xl67 width=114 style='border-left:none;width:86pt'>⨉4</td>
  <td class=xl67 width=101 style='border-left:none;width:76pt'>⨉8</td>
  <td class=xl67 width=133 style='border-left:none;width:100pt'>⨉64</td>
 </tr>
 <tr height=21 style='height:15.6pt'>
  <td height=21 class=xl68 style='height:15.6pt;border-top:none'>accesses</td>
  <td class=xl69 style='border-top:none;border-left:none'>10789<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl69 style='border-top:none;border-left:none'>10789<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl69 style='border-top:none;border-left:none'>10789<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl69 style='border-top:none;border-left:none'>10789<span
  style='mso-spacerun:yes'> </span></td>
 </tr>
 <tr height=21 style='height:15.6pt'>
  <td height=21 class=xl68 style='height:15.6pt;border-top:none'>hits</td>
  <td class=xl69 style='border-top:none;border-left:none'>8877<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl69 style='border-top:none;border-left:none'>9800<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl69 style='border-top:none;border-left:none'>10261</td>
  <td class=xl69 style='border-top:none;border-left:none'>10497<span
  style='mso-spacerun:yes'> </span></td>
 </tr>
 <tr height=21 style='height:15.6pt'>
  <td height=21 class=xl68 style='height:15.6pt;border-top:none'>misses</td>
  <td class=xl69 style='border-top:none;border-left:none'>1912<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl69 style='border-top:none;border-left:none'>989<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl69 style='border-top:none;border-left:none'>528</td>
  <td class=xl69 style='border-top:none;border-left:none'>292<span
  style='mso-spacerun:yes'> </span></td>
 </tr>
 <tr height=21 style='height:15.6pt'>
  <td height=21 class=xl68 style='height:15.6pt;border-top:none'>replacements</td>
  <td class=xl70 style='border-top:none;border-left:none'>1</td>
  <td class=xl69 style='border-top:none;border-left:none'>1<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl69 style='border-top:none;border-left:none'>1<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl69 style='border-top:none;border-left:none'>1<span
  style='mso-spacerun:yes'> </span></td>
 </tr>
 <tr height=21 style='height:15.6pt'>
  <td height=21 class=xl68 style='height:15.6pt;border-top:none'>writebacks</td>
  <td class=xl69 style='border-top:none;border-left:none'>0<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl69 style='border-top:none;border-left:none'>0<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl69 style='border-top:none;border-left:none'>0<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl69 style='border-top:none;border-left:none'>0<span
  style='mso-spacerun:yes'> </span></td>
 </tr>
 <tr height=21 style='height:15.6pt'>
  <td height=21 class=xl68 style='height:15.6pt;border-top:none'>invalidations</td>
  <td class=xl69 style='border-top:none;border-left:none'>0<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl69 style='border-top:none;border-left:none'>0<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl69 style='border-top:none;border-left:none'>0<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl69 style='border-top:none;border-left:none'>0<span
  style='mso-spacerun:yes'> </span></td>
 </tr>
 <tr height=21 style='height:15.6pt'>
  <td height=21 class=xl68 style='height:15.6pt;border-top:none'>miss_rate</td>
  <td class=xl69 style='border-top:none;border-left:none'>0.1772<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl69 style='border-top:none;border-left:none'>0.0917<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl69 style='border-top:none;border-left:none'>0.0489</td>
  <td class=xl69 style='border-top:none;border-left:none'>0.0271<span
  style='mso-spacerun:yes'> </span></td>
 </tr>
 <tr height=21 style='height:15.6pt'>
  <td height=21 class=xl68 style='height:15.6pt;border-top:none'>repl_rate</td>
  <td class=xl69 style='border-top:none;border-left:none'>0.0001<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl69 style='border-top:none;border-left:none'>0.0001<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl69 style='border-top:none;border-left:none'>0.0001</td>
  <td class=xl69 style='border-top:none;border-left:none'>0.0001<span
  style='mso-spacerun:yes'> </span></td>
 </tr>
 <tr height=21 style='height:15.6pt'>
  <td height=21 class=xl68 style='height:15.6pt;border-top:none'>wb_rate</td>
  <td class=xl69 style='border-top:none;border-left:none'>0.0000<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl69 style='border-top:none;border-left:none'>0.0000<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl69 style='border-top:none;border-left:none'>0.0000<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl69 style='border-top:none;border-left:none'>0.0000<span
  style='mso-spacerun:yes'> </span></td>
 </tr>
 <tr height=21 style='height:15.6pt'>
  <td height=21 class=xl68 style='height:15.6pt;border-top:none'>inv_rate</td>
  <td class=xl69 style='border-top:none;border-left:none'>0.0000<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl69 style='border-top:none;border-left:none'>0.0000<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl69 style='border-top:none;border-left:none'>0.0000<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl69 style='border-top:none;border-left:none'>0.0000<span
  style='mso-spacerun:yes'> </span></td>
 </tr>
 <tr height=21 style='height:15.6pt'>
  <td height=21 style='height:15.6pt'></td>
  <td class=xl65></td>
  <td colspan=3 style='mso-ignore:colspan'></td>
 </tr>
</table>
<br>

>&emsp;&emsp;选定不同的Cache块大小对vpr测试数据集进行测试所得数据对比图如图43所示。
<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src="https://img-blog.csdnimg.cn/20200704152523210.png">
    <br>
    <div style="color:orange; border-bottom: 1px solid #d9d9d9;
    display: inline-block;
    color: #999;
    padding: 2px;">图 43 选定不同的Cache块大小对vpr测试数据集进行测试所得数据对比</div>
</center>
<br>

>&emsp;&emsp;选定不同的Cache容量对vpr测试数据集进行测试所得数据如表16所示。
<table border='0' cellpadding='0' cellspacing='0' width='495' style='border-collapse: 
 collapse;table-layout:fixed;width:371pt'>
 <col width='175' style='mso-width-source:userset;width:131.25pt'>
 <caption>表 16 选定不同的Cache容量对vpr测试数据集进行测试所得数据</caption>
 <col width='64' span='5' style='width:48pt'>
 <tr height='48' style='mso-height-source:userset;height:36pt' id='r0'>
<td height='46' class='x21' width='175' style='height:34.5pt;width:131.25pt;'><font class="font2"><div align=right>Cache 容量</div><span style='mso-spacerun:yes;'>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </span></font><font class="font3"><br><div align=left>指标</div><span style='mso-spacerun:yes;white-space:nowrap;'>&nbsp; </span></font></td>
<td class=xl66 width=95 style='border-left:none;width:71pt'>⨉2</td>
  <td class=xl66 width=104 style='border-left:none;width:78pt'>⨉4</td>
  <td class=xl66 width=94 style='border-left:none;width:70pt'>⨉8</td>
  <td class=xl66 width=64 style='border-left:none;width:48pt'>⨉64</td>
 </tr>
 <tr height=21 style='height:15.6pt'>
  <td height=21 class=xl67 style='height:15.6pt;border-top:none'>accesses</td>
  <td class=xl68 style='border-top:none;border-left:none'>10789<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>10789<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>10789<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>10789<span
  style='mso-spacerun:yes'> </span></td>
 </tr>
 <tr height=21 style='height:15.6pt'>
  <td height=21 class=xl67 style='height:15.6pt;border-top:none'>hits</td>
  <td class=xl68 style='border-top:none;border-left:none'>10139<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>10207<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>10216<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>10261<span
  style='mso-spacerun:yes'> </span></td>
 </tr>
 <tr height=21 style='height:15.6pt'>
  <td height=21 class=xl67 style='height:15.6pt;border-top:none'>misses</td>
  <td class=xl68 style='border-top:none;border-left:none'>650<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>582<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>573<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>528<span
  style='mso-spacerun:yes'> </span></td>
 </tr>
 <tr height=21 style='height:15.6pt'>
  <td height=21 class=xl67 style='height:15.6pt;border-top:none'>replacements</td>
  <td class=xl68 style='border-top:none;border-left:none'>586<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>454<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>317<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>0<span
  style='mso-spacerun:yes'> </span></td>
 </tr>
 <tr height=21 style='height:15.6pt'>
  <td height=21 class=xl67 style='height:15.6pt;border-top:none'>writebacks</td>
  <td class=xl68 style='border-top:none;border-left:none'>508<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>414<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>292<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>0<span
  style='mso-spacerun:yes'> </span></td>
 </tr>
 <tr height=21 style='height:15.6pt'>
  <td height=21 class=xl67 style='height:15.6pt;border-top:none'>invalidations</td>
  <td class=xl68 style='border-top:none;border-left:none'>0<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>0<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>0<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>0<span
  style='mso-spacerun:yes'> </span></td>
 </tr>
 <tr height=21 style='height:15.6pt'>
  <td height=21 class=xl67 style='height:15.6pt;border-top:none'>miss_rate</td>
  <td class=xl68 style='border-top:none;border-left:none'>0.0602<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>0.0539<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>0.0531<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>0.0489<span
  style='mso-spacerun:yes'> </span></td>
 </tr>
 <tr height=21 style='height:15.6pt'>
  <td height=21 class=xl67 style='height:15.6pt;border-top:none'>repl_rate</td>
  <td class=xl69 style='border-top:none;border-left:none'>0.0543</td>
  <td class=xl68 style='border-top:none;border-left:none'>0.0421<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>0.0294<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>0.0000<span
  style='mso-spacerun:yes'> </span></td>
 </tr>
 <tr height=21 style='height:15.6pt'>
  <td height=21 class=xl67 style='height:15.6pt;border-top:none'>wb_rate</td>
  <td class=xl68 style='border-top:none;border-left:none'>0.0471<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>0.0384<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>0.0271<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>0.0000<span
  style='mso-spacerun:yes'> </span></td>
 </tr>
 <tr height=21 style='height:15.6pt'>
  <td height=21 class=xl67 style='height:15.6pt;border-top:none'>inv_rate</td>
  <td class=xl68 style='border-top:none;border-left:none'>0.0000<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>0.0000<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>0.0000<span
  style='mso-spacerun:yes'> </span></td>
  <td class=xl68 style='border-top:none;border-left:none'>0.0000<span
  style='mso-spacerun:yes'> </span></td>
 </tr>
</table>
<br>

>&emsp;&emsp;选定不同的Cache容量对vpr测试数据集进行测试所得数据对比如图44所示。
<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src="https://img-blog.csdnimg.cn/20200704152904562.png">
    <br>
    <div style="color:orange; border-bottom: 1px solid #d9d9d9;
    display: inline-block;
    color: #999;
    padding: 2px;">图 44 选定不同的Cache容量对vpr测试数据集进行测试所得数据对比</div>
</center>
<br>

>&emsp;&emsp;**实验结论：**<br>
&emsp;&emsp;从以上的各数据对比图可得出以下结论<br>
&emsp;&emsp;**``cache容量：``**<br>
&emsp;&emsp;**``随着cache容量的不断增大，其失效次数和失效率在⼀定程度上有所减小，原因是增⼤了cache容量后，会减少了容量失效。但当容量增⼤到⼀定值后，失效率不再减⼩。``**<br>
&emsp;&emsp;**``Cache相联度：``**<br>
&emsp;&emsp;**``随着cache相联度的增⼤，各程序中cache失效率均⼤体呈下降趋势。因为随着相联度的提升，冲突失效会减⼩，却也会增⼤容量失效。``**<br>
&emsp;&emsp;**``Cache块大小：``**<br>
&emsp;&emsp;**``在⼀定范围内，增⼤cache块⼤⼩的确能够有效降低失效率，因为增加块大小会减少强制性失效，但当块大小增大到⼀定值时，失效率将增⼤。出现这种现象的原因是在增大块大小的同时，块的数量在随之减少，所以会增加冲突失效。``**

<br>
<br>
<br>

## 4 关键程序代码
>&emsp;&emsp;本次实验所用命令如下所示。

```bash
#例如:-cache:d11 dl1:2048:64:4:r，表示对一级数据cache进行配置，2048表示有2048组，64表示cache块大小为64 byte，4表示相联度为4，r表示替换策略为RANDOM。
#在此配置下，一级数据cache的容量为2048*64*4=512 KB。


#vpr capacity 2
sim-cache -cache:dl1 dl1:32:32:2:l -cache:dl2 none -cache:il2 none -max:inst 2000000000 ./vpr.ss ./arch.in ./net.in ./place.in
#vpr capacity 4
sim-cache -cache:dl1 dl1:64:32:2:l -cache:dl2 none -cache:il2 none -max:inst 2000000000 ./vpr.ss ./arch.in ./net.in ./place.in
#vpr capacity 8
sim-cache -cache:dl1 dl1:128:32:2:l -cache:dl2 none -cache:il2 none -max:inst 2000000000 ./vpr.ss ./arch.in ./net.in ./place.in
#vpr capacity 64
sim-cache -cache:dl1 dl1:1024:32:2:l -cache:dl2 none -cache:il2 none -max:inst 2000000000 ./vpr.ss ./arch.in ./net.in ./place.in

#vpr association 2
sim-cache -cache:dl1 dl1:512:32:2:l -cache:dl2 none -cache:il2 none -max:inst 2000000000 ./vpr.ss ./arch.in ./net.in ./place.in
#vpr association 4
sim-cache -cache:dl1 dl1:256:32:4:l -cache:dl2 none -cache:il2 none -max:inst 2000000000 ./vpr.ss ./arch.in ./net.in ./place.in
#vpr association 8
sim-cache -cache:dl1 dl1:128:32:8:l -cache:dl2 none -cache:il2 none -max:inst 2000000000 ./vpr.ss ./arch.in ./net.in ./place.in
#vpr association 16
sim-cache -cache:dl1 dl1:64:32:16:l -cache:dl2 none -cache:il2 none -max:inst 2000000000 ./vpr.ss ./arch.in ./net.in ./place.in
#vpr association 64
sim-cache -cache:dl1 dl1:16:32:64:l -cache:dl2 none -cache:il2 none -max:inst 2000000000 ./vpr.ss ./arch.in ./net.in ./place.in

#vpr Block Size 2
sim-cache -cache:dl1 dl1:2048:8:2:l -cache:dl2 none -cache:il2 none -max:inst 2000000000 ./vpr.ss ./arch.in ./net.in ./place.in
#vpr Block Size 4
sim-cache -cache:dl1 dl1:1024:16:2:l -cache:dl2 none -cache:il2 none -max:inst 2000000000 ./vpr.ss ./arch.in ./net.in ./place.in
#vpr Block Size 8
sim-cache -cache:dl1 dl1:512:32:2:l -cache:dl2 none -cache:il2 none -max:inst 2000000000 ./vpr.ss ./arch.in ./net.in ./place.in
#vpr Block Size 64
sim-cache -cache:dl1 dl1:256:64:2:l -cache:dl2 none -cache:il2 none -max:inst 2000000000 ./vpr.ss ./arch.in ./net.in ./place.in


#####################################################################################
#vortex capacity 2
sim-cache -cache:dl1 dl1:32:32:2:l -cache:dl2 none -cache:il2 none -max:inst 2000000000 ./vortex.ss bendian.raw ./bendian.rnv ./bendian.wnv ./lendian.raw ./lendian.rnv ./lendian.wnv ./persons.1k
#vortex capacity 4
sim-cache -cache:dl1 dl1:64:32:2:l -cache:dl2 none -cache:il2 none -max:inst 2000000000 ./vortex.ss bendian.raw ./bendian.rnv ./bendian.wnv ./lendian.raw ./lendian.rnv ./lendian.wnv ./persons.1k
#vortex capacity 8
sim-cache -cache:dl1 dl1:128:32:2:l -cache:dl2 none -cache:il2 none -max:inst 2000000000 ./vortex.ss bendian.raw ./bendian.rnv ./bendian.wnv ./lendian.raw ./lendian.rnv ./lendian.wnv ./persons.1k
#vortex capacity 64
sim-cache -cache:dl1 dl1:1024:32:2:l -cache:dl2 none -cache:il2 none -max:inst 2000000000 ./vortex.ss bendian.raw ./bendian.rnv ./bendian.wnv ./lendian.raw ./lendian.rnv ./lendian.wnv ./persons.1k

#vortex association 2
sim-cache -cache:dl1 dl1:512:32:2:l -cache:dl2 none -cache:il2 none -max:inst 2000000000 ./vortex.ss bendian.raw ./bendian.rnv ./bendian.wnv ./lendian.raw ./lendian.rnv ./lendian.wnv ./persons.1k
#vortex association 4
sim-cache -cache:dl1 dl1:256:32:4:l -cache:dl2 none -cache:il2 none -max:inst 2000000000 ./vortex.ss bendian.raw ./bendian.rnv ./bendian.wnv ./lendian.raw ./lendian.rnv ./lendian.wnv ./persons.1k
#vortex association 8
sim-cache -cache:dl1 dl1:128:32:8:l -cache:dl2 none -cache:il2 none -max:inst 2000000000 ./vortex.ss bendian.raw ./bendian.rnv ./bendian.wnv ./lendian.raw ./lendian.rnv ./lendian.wnv ./persons.1k
#vortex association 16
sim-cache -cache:dl1 dl1:64:32:16:l -cache:dl2 none -cache:il2 none -max:inst 2000000000 ./vortex.ss bendian.raw ./bendian.rnv ./bendian.wnv ./lendian.raw ./lendian.rnv ./lendian.wnv ./persons.1k
#vortex association 64
sim-cache -cache:dl1 dl1:16:32:64:l -cache:dl2 none -cache:il2 none -max:inst 2000000000 ./vortex.ss bendian.raw ./bendian.rnv ./bendian.wnv ./lendian.raw ./lendian.rnv ./lendian.wnv ./persons.1k

#vortex Block Size 2
sim-cache -cache:dl1 dl1:2048:8:2:l -cache:dl2 none -cache:il2 none -max:inst 2000000000 ./vortex.ss bendian.raw ./bendian.rnv ./bendian.wnv ./lendian.raw ./lendian.rnv ./lendian.wnv ./persons.1k
#vortex Block Size 4
sim-cache -cache:dl1 dl1:1024:16:2:l -cache:dl2 none -cache:il2 none -max:inst 2000000000 ./vortex.ss bendian.raw ./bendian.rnv ./bendian.wnv ./lendian.raw ./lendian.rnv ./lendian.wnv ./persons.1k
#vortex Block Size 8
sim-cache -cache:dl1 dl1:512:32:2:l -cache:dl2 none -cache:il2 none -max:inst 2000000000 ./vortex.ss bendian.raw ./bendian.rnv ./bendian.wnv ./lendian.raw ./lendian.rnv ./lendian.wnv ./persons.1k
#vortex Block Size 64
sim-cache -cache:dl1 dl1:256:64:2:l -cache:dl2 none -cache:il2 none -max:inst 2000000000 ./vortex.ss bendian.raw ./bendian.rnv ./bendian.wnv ./lendian.raw ./lendian.rnv ./lendian.wnv ./persons.1k


#####################################################################################
#mcf capacity 2
sim-cache -cache:dl1 dl1:32:32:2:l -cache:dl2 none -cache:il2 none -max:inst 2000000000 ./mcf.ss ./inp.in
#mcf capacity 4
sim-cache -cache:dl1 dl1:64:32:2:l -cache:dl2 none -cache:il2 none -max:inst 2000000000 ./mcf.ss ./inp.in
#mcf capacity 8
sim-cache -cache:dl1 dl1:128:32:2:l -cache:dl2 none -cache:il2 none -max:inst 2000000000 ./mcf.ss ./inp.in
#mcf capacity 64
sim-cache -cache:dl1 dl1:1024:32:2:l -cache:dl2 none -cache:il2 none -max:inst 2000000000 ./mcf.ss ./inp.in

#mcf association 2
sim-cache -cache:dl1 dl1:512:32:2:l -cache:dl2 none -cache:il2 none -max:inst 2000000000 ./mcf.ss ./inp.in
#mcf association 4
sim-cache -cache:dl1 dl1:256:32:4:l -cache:dl2 none -cache:il2 none -max:inst 2000000000 ./mcf.ss ./inp.in
#mcf association 8
sim-cache -cache:dl1 dl1:128:32:8:l -cache:dl2 none -cache:il2 none -max:inst 2000000000 ./mcf.ss ./inp.in
#mcf association 16
sim-cache -cache:dl1 dl1:64:32:16:l -cache:dl2 none -cache:il2 none -max:inst 2000000000 ./mcf.ss ./inp.in
#mcf association 64
sim-cache -cache:dl1 dl1:16:32:64:l -cache:dl2 none -cache:il2 none -max:inst 2000000000 ./mcf.ss ./inp.in

#mcf Block Size 2
sim-cache -cache:dl1 dl1:2048:8:2:l -cache:dl2 none -cache:il2 none -max:inst 2000000000 ./mcf.ss ./inp.in
#mcf Block Size 4
sim-cache -cache:dl1 dl1:1024:16:2:l -cache:dl2 none -cache:il2 none -max:inst 2000000000 ./mcf.ss ./inp.in
#mcf Block Size 8
sim-cache -cache:dl1 dl1:512:32:2:l -cache:dl2 none -cache:il2 none -max:inst 2000000000 ./mcf.ss ./inp.in
#mcf Block Size 64
sim-cache -cache:dl1 dl1:256:64:2:l -cache:dl2 none -cache:il2 none -max:inst 2000000000 ./mcf.ss ./inp.in


#####################################################################################
#bzip2 capacity 2
sim-cache -cache:dl1 dl1:32:32:2:l -cache:dl2 none -cache:il2 none -max:inst 2000000000 ./bzip2.ss ./control ./input.random
#bzip2 capacity 4
sim-cache -cache:dl1 dl1:64:32:2:l -cache:dl2 none -cache:il2 none -max:inst 2000000000 ./bzip2.ss ./control ./input.random
#bzip2 capacity  8
sim-cache -cache:dl1 dl1:128:32:2:l -cache:dl2 none -cache:il2 none -max:inst 2000000000 ./bzip2.ss ./control ./input.random
#bzip2 capacity 64
sim-cache -cache:dl1 dl1:1024:32:2:l -cache:dl2 none -cache:il2 none -max:inst 2000000000 ./bzip2.ss ./control ./input.random

#bzip2 association 2
sim-cache -cache:dl1 dl1:512:32:2:l -cache:dl2 none -cache:il2 none -max:inst 2000000000 ./bzip2.ss ./control ./input.random
#bzip2 association 4
sim-cache -cache:dl1 dl1:256:32:4:l -cache:dl2 none -cache:il2 none -max:inst 2000000000 ./bzip2.ss ./control ./input.random
#bzip2 association 8
sim-cache -cache:dl1 dl1:128:32:8:l -cache:dl2 none -cache:il2 none -max:inst 2000000000 ./bzip2.ss ./control ./input.random
#bzip2 association 16
sim-cache -cache:dl1 dl1:64:32:16:l -cache:dl2 none -cache:il2 none -max:inst 2000000000 ./bzip2.ss ./control ./input.random
#bzip2 association 64
sim-cache -cache:dl1 dl1:16:32:64:l -cache:dl2 none -cache:il2 none -max:inst 2000000000 ./bzip2.ss ./control ./input.random

#bzip2 Block Size 2
sim-cache -cache:dl1 dl1:2048:8:2:l -cache:dl2 none -cache:il2 none -max:inst 2000000000 ./bzip2.ss ./control ./input.random
#bzip2 Block Size 4
sim-cache -cache:dl1 dl1:1024:16:2:l -cache:dl2 none -cache:il2 none -max:inst 2000000000 ./bzip2.ss ./control ./input.random
#bzip2 Block Size 8
sim-cache -cache:dl1 dl1:512:32:2:l -cache:dl2 none -cache:il2 none -max:inst 2000000000 ./bzip2.ss ./control ./input.random
#bzip2 Block Size 64
sim-cache -cache:dl1 dl1:256:64:2:l -cache:dl2 none -cache:il2 none -max:inst 2000000000 ./bzip2.ss ./control ./input.random
```
<br>
<br>
<br>

## 5 实验心得
>&emsp;&emsp;本次实验使用SimpleScalar模拟器通过本次实验，我加深了对Cache的基本概念、基本组织结构以及基本工作原理的理解，了解了Cache的容量、相联度、块大小对Cache性能的影响，掌握了降低Cache失效率的各种方法，以及这些方法对Cache性能提高的好处，同时也理解了Cache失效的产生原因以及Cache的三种失效，对cache这⼀结构的理解更加深入。

# 参考资料
&emsp;&emsp;[链接1](https://github.com/gchopra/SimpleScalarSimulations)<br>
&emsp;&emsp;[链接2](https://github.com/sdenel/How-to-install-SimpleScalar-on-Ubuntu)

# MATLAB绘图代码
&emsp;&emsp;代码的第一行都是文件名，看名字应该都能猜到是画哪个图了。<br>
&emsp;&emsp;实验2：<br>
```matlab
%gcc_Branch_Predictor.m
y=[14035938	16910752	5136299	4473381	4029194	4029194];
b=bar(y);
grid on;
ch = get(b,'children');
set(gca,'XTickLabel',{'taken', 'Not-taken', 'bimod(512)','Bimod(1024)','2-level-1024','2-level-64'}, 'FontSize', 16)

legend('Misses', 'FontSize', 16);
xlabel('Predictive method', 'FontSize', 16);
ylabel('Total misses', 'FontSize', 16);
title('The relevance between branch prediction failure efficiency and predictive method (based on gcc dataset)', 'FontSize', 16);
```
<br>

```matlab
%mcf_Branch_Predictor.m
y=[16943797	15400844	6221643	6186787	6186481	6186481];
b=bar(y);
grid on;
ch = get(b,'children');
set(gca,'XTickLabel',{'taken', 'Not-taken', 'bimod(512)','Bimod(1024)','2-level-1024','2-level-64'}, 'FontSize', 16)

legend('Misses', 'FontSize', 16);
xlabel('Predictive method', 'FontSize', 16);
ylabel('Total misses', 'FontSize', 16);
title('The relevance between branch prediction failure efficiency and predictive method (based on mcf dataset)', 'FontSize', 16);
```
<br>

```matlab
%vortex_Branch_Predictor.m
y=[26610	49310	6723	6155	5710	5710];
b=bar(y);
grid on;
ch = get(b,'children');
set(gca,'XTickLabel',{'taken', 'Not-taken', 'bimod(512)','Bimod(1024)','2-level-1024','2-level-64'}, 'FontSize', 16)

legend('Misses', 'FontSize', 16);
xlabel('Predictive method', 'FontSize', 16);
ylabel('Total misses', 'FontSize', 16);
title('The relevance between branch prediction failure efficiency and predictive method (based on vortex dataset)', 'FontSize', 16);
```
<br>

```matlab
%vpr_Branch_Predictor.m
y=[1925	2492	576	517	480	480];
b=bar(y);
grid on;
ch = get(b,'children');
set(gca,'XTickLabel',{'taken', 'Not-taken', 'bimod(512)','Bimod(1024)','2-level-1024','2-level-64'}, 'FontSize', 16)

legend('Misses', 'FontSize', 16);
xlabel('Predictive method', 'FontSize', 16);
ylabel('Total misses', 'FontSize', 16);
title('The relevance between branch prediction failure efficiency and predictive method (based on vpr dataset)', 'FontSize', 16);
```

<br>
&emsp;&emsp;实验3<br>

```matlab
%bzip2_association.m
y=[0.0658 ;	0.0667 ;	0.0699; 	0.0746; 	0.0746;];
b=bar(y);
grid on;
ch = get(b,'children');
set(gca,'XTickLabel',{'2-way','4-way','8-way','16-way', '64-way'}, 'FontSize', 16)

legend('Miss rate', 'FontSize', 16);
xlabel('Number of way', 'FontSize', 16);
ylabel('Miss rate', 'FontSize', 16);
title('The relevance between L2 cache failure efficiency and Cache coherence (based on bzip2 dataset)', 'FontSize', 16);
```

<br>

```matlab
%bzip2_Block_size.m
y=[0.2551 ;	0.1290 	;0.0658 ;0.0337;];
b=bar(y);
grid on;
ch = get(b,'children');
set(gca,'XTickLabel',{'*2','*4','*8','*64'}, 'FontSize', 16)

legend('Miss rate', 'FontSize', 16);
xlabel('Size of Cache block', 'FontSize', 16);
ylabel('Miss rate', 'FontSize', 16);
title('The relevance between L2 cache failure efficiency and the size of Cache block (based on bzip2 dataset)', 'FontSize', 16);
```

<br>

```matlab
%bzip2_capacity.m
y=[0.0845;	0.0836	;0.0831	;0.0590];
b=bar(y);
grid on;
ch = get(b,'children');
set(gca,'XTickLabel',{'*2','*4','*8','*64'}, 'FontSize', 16)

legend('Miss rate', 'FontSize', 16);
xlabel('Capacity of Cache', 'FontSize', 16);
ylabel('Miss rate', 'FontSize', 16);
title('The relevance between L2 cache failure efficiency and Cache Capacity (based on bzip2 dataset)', 'FontSize', 16);
```

<br>

```matlab
%mcf_association.m
y=[0.0911 	0.0842 	0.0835 	0.0830 	0.0838];
b=bar(y);
grid on;
ch = get(b,'children');
set(gca,'XTickLabel',{'2-way','4-way','8-way','16-way', '64-way'}, 'FontSize', 16)

legend('Miss rate', 'FontSize', 16);
xlabel('Number of way', 'FontSize', 16);
ylabel('Miss rate', 'FontSize', 16);
title('The relevance between L2 cache failure efficiency and Cache coherence (based on mcf dataset)', 'FontSize', 16);
```

<br>

```matlab
%mcf_Block_Size.m
y=[0.2213 	0.1443 	0.0911 	0.0772 ];
b=bar(y);
grid on;
ch = get(b,'children');
set(gca,'XTickLabel',{'*2','*4','*8','*64'}, 'FontSize', 16)

legend('Miss rate', 'FontSize', 16);
xlabel('Size of Cache block', 'FontSize', 16);
ylabel('Miss rate', 'FontSize', 16);
title('The relevance between L2 cache failure efficiency and the size of Cache block (based on mcf dataset)', 'FontSize', 16);
```

<br>

```matlab
%mcf_capacity.m
y=[0.1542	0.1361	0.1218	0.0720];
b=bar(y);
grid on;
ch = get(b,'children');
set(gca,'XTickLabel',{'*2','*4','*8','*64'}, 'FontSize', 16)

legend('Miss rate', 'FontSize', 16);
xlabel('Capacity of Cache', 'FontSize', 16);
ylabel('Miss rate', 'FontSize', 16);
title('The relevance between L2 cache failure efficiency and Cache Capacity (based on mcf dataset)', 'FontSize', 16);
```

<br>

```matlab
%vortex_association.m
y=[0.0405 	0.0402 	0.0405 	0.0406 	0.0407 ];
b=bar(y);
grid on;
ch = get(b,'children');
set(gca,'XTickLabel',{'2-way','4-way','8-way','16-way', '64-way'}, 'FontSize', 16)

legend('Miss rate', 'FontSize', 16);
xlabel('Number of way', 'FontSize', 16);
ylabel('Miss rate', 'FontSize', 16);
title('The relevance between L2 cache failure efficiency and Cache coherence (based on vortex dataset)', 'FontSize', 16);
```

<br>

```matlab
%vortex_Block_size.m
y=[0.1556 	0.0788 	0.0405 	0.0211];
b=bar(y);
grid on;
ch = get(b,'children');
set(gca,'XTickLabel',{'*2','*4','*8','*64'}, 'FontSize', 16)

legend('Miss rate', 'FontSize', 16);
xlabel('Size of Cache block', 'FontSize', 16);
ylabel('Miss rate', 'FontSize', 16);
title('The relevance between L2 cache failure efficiency and the size of Cache block (based on vortex dataset)', 'FontSize', 16);
```

<br>

```matlab
%vortex_capacity.m
y=[0.0556 	0.0466 	0.0432 	0.0398 ];
b=bar(y);
grid on;
ch = get(b,'children');
set(gca,'XTickLabel',{'*2','*4','*8','*64'}, 'FontSize', 16)

legend('Miss rate', 'FontSize', 16);
xlabel('Capacity of Cache', 'FontSize', 16);
ylabel('Miss rate', 'FontSize', 16);
title('The relevance between L2 cache failure efficiency and Cache Capacity (based on vortex dataset)', 'FontSize', 16);
```

<br>

```matlab
%vpr_association.m
y=[0.0489 	0.0489 	0.0489 	0.0489 	0.0489 ];
b=bar(y);
grid on;
ch = get(b,'children');
set(gca,'XTickLabel',{'2-way','4-way','8-way','16-way', '64-way'}, 'FontSize', 16)

legend('Miss rate', 'FontSize', 16);
xlabel('Number of way', 'FontSize', 16);
ylabel('Miss rate', 'FontSize', 16);
title('The relevance between L2 cache failure efficiency and Cache coherence (based on vpr dataset)', 'FontSize', 16);
```

<br>

```matlab
%vpr_Block_size.m
y=[0.1772 	0.0917 	0.0489	0.0271 ];
b=bar(y);
grid on;
ch = get(b,'children');
set(gca,'XTickLabel',{'*2','*4','*8','*64'}, 'FontSize', 16)

legend('Miss rate', 'FontSize', 16);
xlabel('Size of Cache block', 'FontSize', 16);
ylabel('Miss rate', 'FontSize', 16);
title('The relevance between L2 cache failure efficiency and the size of Cache block (based on vpr dataset)', 'FontSize', 16);
```

<br>

```matlab
%vpr_capacity.m
y=[0.0602 	0.0539 	0.0531 	0.0489 ];
b=bar(y);
grid on;
ch = get(b,'children');
set(gca,'XTickLabel',{'*2','*4','*8','*64'}, 'FontSize', 16)

legend('Miss rate', 'FontSize', 16);
xlabel('Capacity of Cache', 'FontSize', 16);
ylabel('Miss rate', 'FontSize', 16);
title('The relevance between L2 cache failure efficiency and Cache Capacity (based on vpr dataset)', 'FontSize', 16);
```