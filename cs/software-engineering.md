# 软件工程

[toc]

## 课程介绍

软件工程是计算机科学与技术大三上半年的课程，我们将全面介绍软件工程所涉及的各方面知识，包括软件过程、软件需求、结构化分析和设计方法、面向对象分析和设计方法、敏捷开发方法、软件测试、软件项目管理、软件开发工具和环境。让大家初步了解软件开发和维护的方法学，为进一步深入学习各专题打下基础。

+ 考试时间：2h
+ 考试方式：闭卷考试



## 推荐课程

### MIT 6.031: Software Construction

#### 课程简介

- 所属大学：MIT
- 先修要求：掌握至少一门编程语言
- 编程语言：Java
- 课程难度：🌟🌟🌟🌟
- 预计学时：100 小时

这门课的目标就是让学生学会如何写出高质量的代码，所谓高质量，则是满足下面三个目标（课程设计者原话复制，以防自己翻译曲解本意）：

> Safe from bugs. Correctness (correct behavior right now) and defensiveness (correct behavior in the future) are required in any software we build.
>
> Easy to understand. The code has to communicate to future programmers who need to understand it and make changes in it (fixing bugs or adding new features). That future programmer might be you, months or years from now. You’ll be surprised how much you forget if you don’t write it down, and how much it helps your own future self to have a good design.
>
> Ready for change. Software always changes. Some designs make it easy to make changes; others require throwing away and rewriting a lot of code.

为此，这门课的设计者们精心编写了一本书来阐释诸多软件构建的核心原则与前人总结下来的宝贵经验，内容细节到如何编写注释和函数 Specification，如何设计抽象数据结构以及诸多并行编程的内容，并且会让你在精心设计的 Java 编程项目里体验和练习这些编程模式。

2016年春季学期这门课开源了其所有编程作业的代码框架，而最新的课程教材可以在其最新的教学网站上找到，具体链接参见下方。



#### 课程资源

- 课程网站：[2021spring](http://web.mit.edu/6.031/www/sp21/), [2016spring](https://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-005-software-construction-spring-2016/)
- 课程视频：无
- 课程教材：参见课程网站的课程 notes
- 课程作业：4 个编程作业 + 1 个 Project

> B站上面机翻课程https://www.bilibili.com/video/BV1Tp4y197XX?spm_id_from=333.999.0.0&vd_source=2aa1b484303c30fb1e5d65c91d790f2d



#### 资源汇总

我在学习这门课中用到的所有资源和作业实现都汇总在 [PKUFlyingPig/MIT6.031-software-construction - GitHub](https://github.com/PKUFlyingPig/MIT6.031-software-construction) 中。





## 软件计划周期

软件生存期可分为三个大的阶段： 计划阶段，开发阶段，维护阶段。

计划阶段包括三部分：问题定义、可行性研究、需求分析。



### 七个阶段

软件开发主要分为以下几个阶段

> 使用的visio绘图、建设模型（三种模型）

1. 问题定义
   1. 确定好要解决的问题是什么（what），通过对客户的访问调查，系统分析员扼要的写出关于问题性质、工程目标和工程规模的书面报告，经过讨论和必要的修改之后这份报告应该得到客户的确认。

2. 可行性研究
   1. 技术可行性（能否做出来）
   2. 经济可行性（能否赚钱）
   3. 市场可行性（是否违法）

3. 需求分析
   1. 深入具体的了解用户的需求，在所开发的系统要做什么这个问题上和用户想法完全一致。明确目标系统必须做什么，确定目标系统必须具备哪些功能。通常用数据流图、数据字典和简要的算法表示系统的逻辑模型。用《规格说明书》记录对目标系统的需求。

4. 概要设计（总体设计）
   1. 概括的说，应该怎样实现目标系统，设计出实现目标系统的几种可能方案，设计程序的体系结构，也就是确定程序由哪些模块组成以及模块之间的关系。

5. 详细设计
   1. 实现系统的具体工作，编写详细规格说明，程序员可以根据它们写出实际的程序代码。详细设计也称模块设计，在这个阶段将详细的设计每个模块，确定实现模块功能所需的算法和数据结构。

6. 编码和单元测试（编码占全部开发工作量的10%-20%）

7. 综合测试（测试占全部开发工作量的40%-50%）
   1. 分为集成测试和验收测试。

8. 软件维护
   1. 通过各种必要的维护活动使系统持久的满足用户的需求。主要分为 改正性维护、适应性维护、完善性维护、预防性维护。



### 可行性研究报告

1、什么是可行性研究报告

> 可行性研究报告是从事一种经济活动（投资）之前，双方要从经济、技术、生产、供销直到社会各种环境、法律等各种因素进行具体调查、研究、分析，确定有利和不利的因素、项目是否可行，估计成功率大小、经济效益和社会效果程度，为决策者和主管机关审批的上报文件。

2、可行性研究报告的任务

> 在最短的时间内将问题找出来，确定问题，而不是解决问题！

3、可行性研究报告是给谁看的呢

> 可行性研究报告是给项目经理的，比如拿大米时代（公司）和（廊坊师范学院）来举个例子，廊坊师范学院要求大米时代给它做机房收费系统，但是在开始之前必须拟定可行性研究报告，这个可行性研究报告是给开发公司的项目经理的，于是这个报告就交到了大米时代的项目经理手中，由他确定是否执行！



### 项目开发计划

1、什么是项目开发计划 ？

> 项目开发计划是软件开发工作的第一步，是一个软件项目进入系统实施的启动阶段，主要进行的工作包括：确定详细的项目实施范围、定义递交的工作成果、评价实施过程中主要的风险、制定项目实施的的时间计划、成本和预算计划、人力资源计划等……体现了准备做什么，什么时候做，由谁去做以及如何做的未来行动方案。

2、项目开发计划的任务是什么?

> 软件项目计划包括两个任务：研究和估算。即通过研究确定该软件项目的主要功能、想能和系统界面，以便根据本计划开展和检查本项目的开发工作，从而保证项目能够在合理的时间内，用尽可能低的成本，完成尽可能高的质量。

3、项目开发计划是由谁负责的，写给谁看的呢

> 项目开发计划是由项目经理负责，写给软件开发人员与系统分析员的，



## 软件生命周期模型

目前来讲，主要的软件[生命周期](https://so.csdn.net/so/search?q=生命周期&spm=1001.2101.3001.7020)模型有如下几种。

- Big-Bang：大爆炸模型。
- Waterfall：瀑布模型。（适用中小型系统，以文档为驱动）
- Spiral：[螺旋模型](https://so.csdn.net/so/search?q=螺旋模型&spm=1001.2101.3001.7020)。 （适用大型，特大型，以风险为驱动）
- Code and Fix：边做边改模型。（以原型为驱动）

| **开发流程分类** | **优  点**                   | **缺  点**                                           |
| ---------------- | ---------------------------- | ---------------------------------------------------- |
| 大爆炸模型       | 简单，不用学习就会           | 拍脑门的想法，产品质量无法保证。尽量避免使用         |
| 边做边改模型     | 快速得到可运行的版本         | 计划有些缺乏，导致版本前后变化较大。可选择的模型之一 |
| 瀑布模型         | 计划周密，专业，按部就班实现 | 相对难于做到快速开发，以抢占市场。可选择的模型之一   |
| 螺旋模型         | 计划变化同时考虑             | 可选择的模型之一                                     |



## 数据库的设计

**数据库的设计是一个非常严谨的过程，在设计数据库的过程需要满足三范式？**

>  关系模式CTHRSG，依赖关系为{C→T,HR→C,CS→G,HS→R,HT→R}，求候选码？
>
> + 左L（一定满足）：H、S
> + 右R（一定不满足）: G
> + 左右LR（可能满足）：C、T、R
> + 无N（一定满足）：
>
> **闭包：**
>
> HS –> HSRCTG  : 可以得到所有属性（候选码）



### 数据库范式

**求候选码的目的是为了解决范式**

+ 1NF：列不可再分

| 成绩 |      |
| ---- | ---- |
| 数学 | 物理 |

+ 2FN：若某关系R属于第一范式，且每一个非主属性完全函数依赖于任何一个候选码，则关系R属于第二范式。

  + 2FN是消除了部分依赖

  

+ 3FN： 非主属性既不传递依赖于码，也不部分依赖于码。

  + 3FN是设计数据库一个合格的标准，消除了传递依赖

> 有关系模式R(S,T,C,D,G)，
> 根据语义有如下函数依赖集：
> F={(S,C) →T,C→D,(S,C)→G,T→C}。
> 关系模式R的规范化程序最高达到（A）。
> A）1NF 
> B）2NF 
> C）3NF 
> D）BCNF
>
> <img src="https://sm.nsddd.top//typora/image-20220831111052945.png?mail:3293172751@qq.com" alt="image-20220831111052945" style="zoom: 25%;" />



> 有关系模式P(C,S,T,R)，
> 根据语义有如下函数依赖集：
> F={C→T,ST→R,TR→C}。 
> 关系模式P的规范化程度最高达到（  ）。
> A）1NF   
> B）2NF    
> C）3NF   
> D）BCNF![image-20220831112822615](https://sm.nsddd.top//typora/image-20220831112822615.png?mail:3293172751@qq.com)
>
> 





### 无损连接

> 有关系模式R（A，B，C，D，E），根据语义有如下函数依赖集：F={A→C，BC→D，CD→A，AB→E}。
> 现将关系模式R分解为两个关系模式R1（A，C，D），R2（A，B，E)
>
> 那么这个分解（）。
> A）不具有无损连接性且不保持函数依赖 
> B）具有无损连接性且不保持函数依赖 
> C）不具有无损连接性且保持函数依赖 
> D）具有无损连接性且保持函数依赖
>
> <img src="https://sm.nsddd.top//typora/image-20220831114236094.png?mail:3293172751@qq.com" alt="image-20220831114236094" style="zoom:25%;" />

> R1∩R2=A, A+=AC，没有包含R1或R2的所有属性，所以是有损
>
> A→C保持在R1,BC→D没有被保持，所以不保持函数依赖   选A