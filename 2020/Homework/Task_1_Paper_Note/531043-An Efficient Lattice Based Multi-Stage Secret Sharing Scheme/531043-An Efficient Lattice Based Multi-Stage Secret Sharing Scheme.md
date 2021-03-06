# 论文阅读笔记

**论文阅读笔记**

论文题目：An Efficient Lattice Based Multi-Stage Secret Sharing Scheme. 

论文作者：Pilaram，Hossein，Eghlidos， Taraneh

论文出处：IEEE Transactions on Dependable & Secure Computing

原文链接：https://ieeexplore.ieee.org/document/7110574

笔记作者：林越 2017141531043

[toc]

## 论文概要

​	本文根据 Ajtai 的单向函数构造，构造了一种基于格的多级密钥共享(MSSS)方案。 在本方案中，被授权的密钥共享者可以在每个阶段恢复部分密钥子集，并保持其他密钥不公开。 在本文中，每个密钥都是来自 t 维格的一个向量，每个格的基都是私有的。 一个t子组的n个参与者可以使用他们被分配到的份额来恢复密钥。 为了保障在部分秘密暴露之后未恢复密钥的计算安全性，这里使用了基于晶格的单向函数。即为了共享一组新的密钥，更新一些公共信息就足够了，因此不再需要新的共享分发。 此外，该方案是可验证的，参与者可以利用公开信息进行验证。

## 主要内容

### 研究背景

​	密钥共享方案在许多密码协议中被用作工具，包括电子投票、云计算和传感器网络中的密钥管理等。 密钥共享方案允许一个人在一组人之间分享一个密钥，每一个参与者被分配不同的部分，称为共享，并且只有他们授权的子集才能使用这些共享信息恢复密钥。参与者的授权子集的集合称为访问结构，由r表示。在SSS中，我们打算t中的任何子集都可以重建密钥，而r中的子集不能恢复任何关于密钥的信息。 

​	一个(t，n)阈值秘密共享方案是由 Blakley 和 Shamir 于 1979 年独立引入的，在这个方案中，访问结构由P的所有子集组成，其中至少包括t个参与者。 此后还提出了许多其他密钥共享方案。然而，这些 计划只适用于一个单一的密钥，一旦密钥被改变为一个新的密钥，系统必须更新密钥的分配和重新发送新的部分密钥给参与者。 

​	但当密钥被重新组装时，会为攻击者提供了获取完整密钥的可乘之机，留下不小的安全隐患。

### 方案描述

#### 算法

​	文章提出了一种基于晶格的(t，n)阈值 MSSS 方案，其中 t 参与者需要恢复每个密钥。该方案使参与者能够独立地恢复任何份额的密钥，并且在计算上很难使用这些信息来获取其他部分密钥。

​	在该方案中，<img src="C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20200421000714381.png" style="zoom:50%;" />其中 q 是素数，t 是阈值。 

​	分配商随机选择一个最后条目等于1的向量<img src="C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20200421001247102.png" alt="image-20200421001247102" style="zoom:50%;" /> 进行发布，然后对于每一个密钥，都能找到一个私有格基B满足下式

<img src="C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20200421001522530.png" alt="image-20200421001522530" style="zoom:50%;" /> 

​	对于求解该式，本文提出的方案。首先，dealer选择一个具有线性独立的列和集的随机矩阵，解出s，然后求解以下方程组，得到矩阵A的集合

<img src="C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20200421003344362.png" alt="image-20200421003344362" style="zoom:67%;" />

dealer从A的集合中按照一定规律随机抽取计算A

​	当dealer准备完所有先决条件后，核实份额。他将选择一个随机矩阵，并将其与份额的散列向量一起公布。

#### 安全分析

​	分析得出该方案有效、可靠、可验证，并适用于参与者不需要复杂操作的程序。

## 创新点

​	本文考虑了一种多级密钥共享方案。这种方案所期望的安全性水平是计算安全性。 在本方案中，秘密可以在不同阶段恢复。 参与者使用从其原始份额中衍生出来的伪密钥份额来收回这些秘密。并验证得到新方案是多阶段、多渠道、可验证的，并提供了基于晶格问题最坏情况下硬度的计算安全性，使其对量子计算机具有安全性。 此外，该计划在参与 者中效率很高，即使参与者的处理能力有限，也是合适的。

## 不足

​	在本文证明安全的模型下，攻击者在攻击开始前已经声明了攻击对象。但基于完全安全模型的方案就不需要攻击者预先声明自己的攻击对象。因此，完全安全的密码体制比选择安全的密码体制安全性要强一些。但该方案并不能够在完全安全模型下证明其安全性。