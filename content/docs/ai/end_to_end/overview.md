---
title: 2.1. AI 概述
weight: 101
#next: /step1
#prev: /docs
editURL: "https://example.com/edit/this/page"
toc: true
math: true
---


## <font face=Georgia>1、了解人工智能</font>

### <font face=Georgia>1.1、相关概念</font>



***<font color=DarkCyan face=Georgia  align=center>1. 人工智能</font>***，是指可以像人类一样学习、理解、思考的计算机程序。<br>
***<font color=DarkCyan face=Georgia  align=center>2. 机器学习</font>***，是人工智能的一个子集。使用数据训练模型，这些模型可以根据在数据中找到的关系进行预测。<br>
***<font color=DarkCyan face=Georgia  align=center>3. 深度学习</font>***，是机器学习的一个分支。
> - 使用特殊分层结构的机器学习方法（这些分层依次堆叠），形成了一个像堆叠的煎饼一样的“深度”结构。
> - 深度学习算法受到大脑结构的启发，可以很好地处理图像、视频或文本等非结构化数据。
<br>

***<font color=DarkCyan face=Georgia  align=center>4. 深度学习框架</font>***，是一个拼凑了层和函数等组件的库。具体来说，它是一种具有求导功能的编程语言（有人也成“可微分编程语言”）。<br>
***<font color=DarkCyan face=Georgia  align=center>5. 强化学习</font>***，这是一种让AI系统通过与环境的交互学习和提升的方法。（用于训练AI玩视频游戏或控制机器人等）。<br>
***<font color=DarkCyan face=Georgia  align=center>6. 自然语言</font>***，这技术使机器理解并回应人类语言成为可能。（聊天机器人，语音助手，自动翻译系统等）<br>
***<font color=DarkCyan face=Georgia  align=center>7. 计算机视觉</font>***，通过相机、视频和图像直观地解释世界的 AI 功能。（如自动驾驶）<br>
***<font color=DarkCyan face=Georgia  align=center>8. 生成式人工智能</font>***，是一种机器学习模型，它可以生成以前从未见过的新内容，如音乐，文本，图像等。对比预测性质的模型，生成性模型可以创造全新的输出。

<br>

> - [Training | Microsoft Learn —— 基本 AI 概念](https://learn.microsoft.com/zh-cn/training/modules/get-started-ai-fundamentals/)
> - [《Python深度学习》- 第2版 - 弗朗索瓦·肖莱](https://weread.qq.com/web/reader/33f32c90813ab71c6g018fffkd3d322001ad3d9446802347?)



<br><br><br>



### <font face=Georgia>1.2、人工智能简史</font>

***<font color=DarkCyan face=Georgia  align=center>19 世纪 30~40 年代</font>*** —— 
***<font face=Georgia  align=center>查尔斯 • 巴贝奇 —— 分析机（Analytical Engine）</font>***<br>
第一台通用的机械式计算机。它的用途仅仅是利用机械操作将数学分析领域的某些计算自动化，因此得名“分析机”

***<font color=DarkCyan face=Georgia  align=center>20 世纪 50 年代</font>*** —— 
***<font face=Georgia  align=center>符号主义人工智能（symbolic AI）</font>***<br>
精心编写足够多的明确规则来处理知识，就可以实现与人类水平相当的人工智能。<br>
人工智能先驱阿兰 • 图灵在其 1950年发表的具有里程碑意义的论文“计算机器和智能”。

***<font color=DarkCyan face=Georgia  align=center>20 世纪 60~70年代初</font>*** —— 
***<font face=Georgia  align=center>第一次冬天</font>***<br>
由于过高的期望未能实现，研究人员和政府资金均转向其他领域。

***<font color=DarkCyan face=Georgia  align=center>20 世纪 80 年代</font>*** —— 
***<font face=Georgia  align=center>专家系统（expert system）</font>***<br>
符号主义人工智能热度达到了顶峰。

***<font color=DarkCyan face=Georgia  align=center>20 世纪 90 年代初</font>*** —— 
***<font face=Georgia  align=center>第二次冬天</font>***<br>
专家系统维护费用变得很高，难于扩展，并且使用范围有限，人们逐渐对其失去兴趣。

***<font color=DarkCyan face=Georgia  align=center>20 世纪 90 年代</font>*** —— 
***<font face=Georgia  align=center>机器学习</font>***<br>
专家系统难于给出明确的规则来解决更加复杂、模糊的问题，比如图像分类、语音识别、和语言翻译。<br>
于是20世纪90年代出现了机器学习来替代符号人工智能。<br>
机器学习是训练出来的，而不是明确规地用程序编写出来的。

***<font color=DarkCyan face=Georgia  align=center>21 世纪 20 年代</font>*** —— 
***<font face=Georgia  align=center>生成式人工智能</font>***<br>
OpenAI 在2020年6月发布了 GPT-3，这是一个非常大且复杂的模型，拥有1750亿个参数。<br>
GPT-3 在生成文本和其他语言任务方面的表现令人瞩目，并且激发了大量关于 AI 的讨论。

<br>

> - [《Python深度学习》- 第2版 - 弗朗索瓦·肖莱](https://weread.qq.com/web/reader/33f32c90813ab71c6g018fffkd3d322001ad3d9446802347?)



<br><br><br>




## <font face=Georgia>2、机器学习分类</font>

### <font face=Georgia>2.1、基本分类</font>
 
#### ***<font color=Coral face=Georgia  align=center>2.1.1、监督学习</font>***

***<font color=DarkCyan face=Georgia  align=center>1. 从有标注（标签\标记）的数据中学习预测模型的机器学习问题；</font>***<br>

***<font color=DarkCyan face=Georgia  align=center>2. 监督学习主要任务 —— 分类、回归；</font>***
> - ***分类任务：*** 将实例数据划分到预设的某些类别中，是一种离散型预测。如，判断一封电子邮件是不是垃圾邮件；<br>
> - ***回归任务：*** 用于预测连续值。比如预测房价，股票价格等；<br>

<br>

{{< callout emoji="🎨" type="info" link="docs">}}
***生成模型 \ 判别模型：*** 监督学习的任务就是学习一个模型，应用这个模型，对给定的输入预测相应的输出。<br>
   这个模型的一般形式为决策函数（***判别模型*** ）：
   $$Y = f(X)$$ 
   或者条件概率分布（***生成模型***）：
   $$Y = P(Y|X)$$
- ***判别模型***：在已知输入的情况下，预测出输出，常见的判别模型有逻辑回归、支持向量机和深度学习神经网络等。<br>
- ***生成模型***：尝试捕捉数据中的潜在分布，常见的生成模型有高斯混合模型和朴素贝叶斯分类器等。
- ***<font color=Coral face=Georgia  align=center>《统计学习方法》 第2版 - 李航</font>***
{{< /callout >}}



<br><br>



#### ***<font color=Coral face=Georgia  align=center>2.1.2、无监督学习</font>***

***<font color=DarkCyan face=Georgia  align=center>1. 从无标注（标签\标记）的、或结构未知的数据中学习预测模型的机器学习问题；</font>***<br>
> - 这种学习方式的目标通常是为了探索数据，找出其中的结构或者模式；

***<font color=DarkCyan face=Georgia  align=center>2. 无监督学习主要任务 —— 聚类、降维、异常检测、关联规则；</font>***
> - ***聚类：目标是发现并识别数据中的自然分组。是构造信息和从数据中导出有意义关系的一种有用的技术；*** <br>
>> 例如，将客户分为几个群体进行市场细分；为分析过程中出现的每个群定义一组对象，<br>
它们之间都具有一定程度的相似性，但与其他群中对象的差异性更大；<br>

<br>

> - ***降维：特征预处理中数据去噪的一种常用方法，这个过程叫作特征提取。目标是在不丢失太多信息的前提下简化数据；*** <br>
>> 将多个相关特征合并为一个。降低了某些算法对预测性能的要求，<br>
并在保留大部分相关信息的同时将数据压缩到较小维数的子空间上。<br>
案例：汽车的里程与其使用年限存在很大的相关性，所以降维算法会将它们合并成一个代表汽车磨损的特征。<br>
这个过程叫作特征提取。

<br>

> - ***异常检测：异常检测的目标是检测出不符合其他正常数据行为的数据点；*** <br>
>> 比如，检测信用卡交易中的欺诈行为；<br>

<br>

> - ***关联规则：挖掘大量数据，发现属性之间的有趣联系；*** <br>
>> 比如，在超市销售日志上运行关联规则之后发现买烧烤酱和薯片的人也倾向于购买牛排。那么，可以将这几样商品摆放得更近一些；<br>

<br>

> - ***<font color=Coral face=Georgia  align=center>《机器学习实战：基于 Scikit-Learn、Keras 和 TensorFlow》 第2版</font>***




<br><br><br>




#### ***<font color=Coral face=Georgia  align=center>2.1.3、半监督学习</font>***

***<font color=DarkCyan face=Georgia  align=center>1. 使用标注数据和未标注数据学习预测模型的机器学习问题；通常是大量未标记数据和少量的标记数据；</font>***
> - 半监督学习旨在通过利用大量的未标注数据，帮助提高利用少量标注数据进行监督学习的性能；<br>
> - 大多数半监督式学习算法是无监督式和监督式算法的结合；例如深度信念网络（DBN），它基于一种互相堆叠的无监督式组件，这个组件叫作受限玻尔兹曼机（RBM）。受限玻尔兹曼机以无监督的方式进行训练，然后使用监督式学习对整个系统进行微调。

<br>

{{< callout emoji="🎨" type="info" link="docs">}}
- ***主动学习：*** 在训练过程中为模型提供部分数据标签；模型可以选择它认为最需要标签的数据进行标记，从而提高学习效率。<br>
> 1. 算法可以主动地选择它想学习的样本，而不是用全部数据进行训练的算法。<br>
> 主要思想是，如果允许学习系统选择它自己的训练集，可能会提高学习的效率和效果。<br>
> 它通常用于样本标签成本高、标签难以获得，而未标注样本充足的场景。主动学习可以有效地选择最具信息量、对当前模型最有帮助的样本进行标注，从而减少标注的代价。

{{< /callout >}}



<br><br><br>




#### ***<font color=Coral face=Georgia  align=center>2.1.4、强化学习</font>***

***<font color=DarkCyan face=Georgia  align=center>1. 智能系统在与环境的连续互动中学习最有行为策略的机器学习问题；</font>***
> - 它的学习系统（在其语境中称为智能体）能够观察环境，做出选择，执行操作，并获得回报（reward），或者是以负面回报的形式获得惩罚；<br>
> - 它必须自行学习什么是最好的策略（policy），从而随着时间推移获得最大的回报。策略代表智能体在特定情况下应该选择的操作。；<br>
> - 例如，许多机器人通过强化学习算法来学习如何行走；




<br><br><br>












