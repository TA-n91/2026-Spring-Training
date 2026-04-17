# Preparation

## 引言

Pwn 的学习曲线比较陡峭。入门需要理解很多东西，并耗费一些时间

但是学习到的是底层比较有用的知识。也比较贴合实际。学会了可以真的去入侵并操控计算机

## 基础

c语言（看题），汇编指令（理解程序逻辑和利用漏洞），linux系统和（执行脚本输入）简单反汇编工具（看题）的使用。python(攻击/利用脚本)

## 工具

- IDA pro 反汇编工具（反汇编工具有很多，大家都用并且一般都用的就是这个）
- VMware虚拟机  搭建一个环境。并且在里面配置好python库和环境（起码把pwntools库安装了）。编译器我一般是拿记事本。（你要觉得不方便或者体验感不好再在虚拟机里面再装vscode那些也行）

ps：虚拟机环境的配置对新手来说有点复杂、费时间，请大家耐心进行配置。

复杂费时间是里面有一些细节上的东西你要自己去研究琢磨解决。因为别人帮你也是要先找到你的问题。然后再帮你解决。你自己大致知道问题，解决起来也就容易

推荐教程：

> 1. https://blog.csdn.net/j284886202/article/details/134931709
> 2. 【2024最新pwn环境配置与基础讲解】https://www.bilibili.com/video/BV1ssxgeoEmc?vd_source=8d7bccf8603b4f98319f2c2d2ca1d60c
> 3. https://www.cnblogs.com/seyedog/p/18432103

## 途径，做题方法

pwn的学习来源于一篇篇文章的积累，刚开始你可以搜一下一个最基础的pwn题是怎么解决的，跟着流程了解做题的步骤。然后，wp是学习的一个很好的途径，刚开始的你一定不清楚一个攻击脚本到底该怎么写，但可以搜索别人的解题wp进行模仿学习，一些模板都是固定不变的（但是要有准备，也不是死套模板。后面有一些细节需要仔细处理）

下面简单描述一下一道pwn题的解决思路：（只有使用IDA是在本机操作，其他攻击过程均在虚拟机）

1. 下载附件，下载后也要复制到虚拟机
2. 在虚拟机的终端进行checksec查看文件的保护机制，以及文件是32/64位
3. 将附件拖入对应位数的IDA反汇编，查看题目逻辑。思考漏洞解题
4. 编写攻击脚本，python3执行
5. 打通拿到了shell，ls查看文件目录，cat flag拿到flag。打不通继续在虚拟机里去调试。然后再去试

## 一些练习平台

1. **[NSSCTF](https://www.nssctf.cn/)**  提供题库、比赛和 Writeup 资源，国内很多比赛的题目可以在这里复现，非常适合系统练习和社区交流。
2. **[BUUCTF](https://buuoj.cn/)** 包含大量CTF比赛题目的聚合平台，适合题海战术式练习和复现经典题目。
3. **[Hello CTF](https://hello-ctf.com/)** Hello CTF是免费开源的CTF入门教程，拥有全面的知识点锦集、配套的题目靶场和完善的工具系统。
4. **[青少年CTF练习平台](https://www.qsnctf.com)** 提供题库、比赛和 Writeup 资源

# 本周任务

## 基础知识

![img](https://hnusec-star.feishu.cn/space/api/box/stream/download/asynccode/?code=Y2VhMGE4Mjc3MWM4YzBkMGNmYjc0YmUwNzNlN2Q3YjVfMmRpbVE2b0hHQWowbnJGNURlanRWaFF3M0lieG0xTWFfVG9rZW46SFAyeWIxeUwzb1dGT0d4QzNxQmN3U2VybndxXzE3NzU3MzI4NzI6MTc3NTczNjQ3Ml9WNA)

1. 了解Linux基本指令，学会使用pwn的一些基本工具，如IDA、pwntools的使用、checksec、gdb、ROPgadget。
   1. 推荐文章[深入解析:pwn知识点——命令篇 - tlnshuju - 博客园](https://www.cnblogs.com/tlnshuju/p/19094173)  
   2. [pwn从入门到放弃第二章——ida的基本使用教程](https://ch4r1l3.github.io/2018/06/21/pwn从入门到放弃第二章——ida的基本使用教程/)
   3. pwntools的使用，这是写攻击脚本必备的

（网上文章很多，大家可以搜索然后按个人喜好选择学习）



## 题1

1. 即使你现在不会任何工具的使用，只要搭建好pwn的环境，就可以做出入门后的第一道题目。（了解Linux中nc、ls、cat指令）nc后去cat flag吧

​     题目1：https://buuoj.cn/challenges#test_your_nc

## 题2、3

1. 现在的你应该会使用IDA反汇编了吧，检验代码审计能力，快去看看怎么执行到system("/bin/sh")
   1.    newstarCTF注册：https://newstar.games/login?redirect=/profile
   2.    newstarCTF平台：https://ma tch.ichunqiu.com/2025newstargk
   3.  *ps:打远程或者本地都可以*

题目2：newstarCTF2025 【pwn1】pwns‘door

题目3：newstarCTF2025 【pwn1】INTbug（整数溢出）



## 题4、5

可以先简单的看一下栈溢出。然后这里这两道题也不着急套模板直接做出来贴上去，可以先稍微理解一下逻辑和它的数据结构。

比较经典了：

ctf-show pwn37,pwn38

知识：

[第一个PWN：栈溢出原理以及EXP的编写 - FreeBuf网络安全行业门户](https://www.freebuf.com/articles/system/253225.html)

[初探Pwn之栈溢出入门 - M0urn - 博客园](https://www.cnblogs.com/M0urn/articles/17761215.html)

[pwn栈溢出详解 - ret2z - 博客园](https://www.cnblogs.com/ret2z/p/18870794)

# 作业提交

**完成多少交多少，不要不交，先交上后面也可以继续补充**

除了4，5其它的写一下题解，4，5选做一梭子

学习笔记也要写。然后要交的话就交到这个文件夹pwn第一周下面。用md格式直接交上来

命名就按照 年级-名称-第x周



# 快进行学习吧！！！
