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
 - 使用特殊分层结构的机器学习方法（这些分层依次堆叠），形成了一个像堆叠的煎饼一样的“深度”结构。
 - 深度学习算法受到大脑结构的启发，可以很好地处理图像、视频或文本等非结构化数据。

***<font color=DarkCyan face=Georgia  align=center>4. 深度学习框架</font>***，是一个拼凑了层和函数等组件的库。具体来说，它是一种具有求导功能的编程语言（有人也成“可微分编程语言”）。<br>
***<font color=DarkCyan face=Georgia  align=center>5. 强化学习</font>***，这是一种让AI系统通过与环境的交互学习和提升的方法。（用于训练AI玩视频游戏或控制机器人等）。<br>
***<font color=DarkCyan face=Georgia  align=center>6. 自然语言</font>***，这技术使机器理解并回应人类语言成为可能。（聊天机器人，语音助手，自动翻译系统等）<br>
***<font color=DarkCyan face=Georgia  align=center>7. 计算机视觉</font>***，通过相机、视频和图像直观地解释世界的 AI 功能。（如自动驾驶）<br>
***<font color=DarkCyan face=Georgia  align=center>8. 生成式人工智能</font>***，它可以生成以前从未见过的新内容，如音乐，文本，图像等。对比预测性质的模型，生成性模型可以创造全新的输出。

 - [Training | Microsoft Learn —— 基本 AI 概念](https://learn.microsoft.com/zh-cn/training/modules/get-started-ai-fundamentals/)
 - [《Python深度学习》- 第2版 - 弗朗索瓦·肖莱](https://weread.qq.com/web/reader/33f32c90813ab71c6g018fffkd3d322001ad3d9446802347?)



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

 - [《Python深度学习》- 第2版 - 弗朗索瓦·肖莱](https://weread.qq.com/web/reader/33f32c90813ab71c6g018fffkd3d322001ad3d9446802347?)



<br><br><br>




## <font face=Georgia>2、机器学习分类</font>

### <font face=Georgia>2.1、基本分类</font>
 
#### ***<font color=Coral face=Georgia  align=center>2.1.1、监督学习</font>***

***<font color=DarkCyan face=Georgia  align=center>1. 从有标注（标签\标记）的数据中学习预测模型的机器学习问题；</font>***<br>

***<font color=DarkCyan face=Georgia  align=center>2. 监督学习主要任务 —— 分类、回归；</font>***
 - ***分类任务：*** 将实例数据划分到预设的某些类别中，是一种离散型预测。如，判断一封电子邮件是不是垃圾邮件；<br>
 - ***回归任务：*** 用于预测连续值。比如预测房价，股票价格等；<br>

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
 - 这种学习方式的目标通常是为了探索数据，找出其中的结构或者模式；

***<font color=DarkCyan face=Georgia  align=center>2. 无监督学习主要任务 —— 聚类、降维、异常检测、关联规则；</font>***
 - ***聚类：目标是发现并识别数据中的自然分组。是构造信息和从数据中导出有意义关系的一种有用的技术；*** <br>
> 例如，将客户分为几个群体进行市场细分；为分析过程中出现的每个群定义一组对象，<br>
它们之间都具有一定程度的相似性，但与其他群中对象的差异性更大；<br>

<br>

- ***降维：特征预处理中数据去噪的一种常用方法，这个过程叫作特征提取。目标是在不丢失太多信息的前提下简化数据；*** <br>
> 将多个相关特征合并为一个。降低了某些算法对预测性能的要求，<br>
并在保留大部分相关信息的同时将数据压缩到较小维数的子空间上。<br>
案例：汽车的里程与其使用年限存在很大的相关性，所以降维算法会将它们合并成一个代表汽车磨损的特征。<br>
这个过程叫作特征提取。

<br>

- ***异常检测：异常检测的目标是检测出不符合其他正常数据行为的数据点；*** <br>
> 比如，检测信用卡交易中的欺诈行为；<br>

<br>

- ***关联规则：挖掘大量数据，发现属性之间的有趣联系；*** <br>
> 比如，在超市销售日志上运行关联规则之后发现买烧烤酱和薯片的人也倾向于购买牛排。那么，可以将这几样商品摆放得更近一些；<br>

<br>

- ***<font color=Coral face=Georgia  align=center>《机器学习实战：基于 Scikit-Learn、Keras 和 TensorFlow》 第2版</font>***




<br><br><br>




#### ***<font color=Coral face=Georgia  align=center>2.1.3、半监督学习</font>***

***<font color=DarkCyan face=Georgia  align=center>1. 使用标注数据和未标注数据学习预测模型的机器学习问题；通常是大量未标记数据和少量的标记数据；</font>***
- 半监督学习旨在通过利用大量的未标注数据，帮助提高利用少量标注数据进行监督学习的性能；<br>
- 大多数半监督式学习算法是无监督式和监督式算法的结合；例如深度信念网络（DBN），它基于一种互相堆叠的无监督式组件，这个组件叫作受限玻尔兹曼机（RBM）。受限玻尔兹曼机以无监督的方式进行训练，然后使用监督式学习对整个系统进行微调。

<br>

{{< callout emoji="🎨" type="info" link="docs">}}
- ***主动学习：*** 在训练过程中为模型提供部分数据标签；模型可以选择它认为最需要标签的数据进行标记，从而提高学习效率。<br>
> - 算法可以主动地选择它想学习的样本，而不是用全部数据进行训练的算法。<br>
> - 主要思想是，如果允许学习系统选择它自己的训练集，可能会提高学习的效率和效果。它通常用于样本标签成本高、标签难以获得，而未标注样本充足的场景。主动学习可以有效地选择最具信息量、对当前模型最有帮助的样本进行标注，从而减少标注的代价。

- ***自学习（Self-training）：*** 自学习是一种简单但在一些场景下效果出奇好的半监督学习方法。
> - 这种方法的基本思想是先使用已有的标签数据训练出一个初步的模型，然后用这个模型预测未标签数据，把预测结果作为标签，再和原有标签数据一起重新训练模型。这个过程可以重复进行直到模型收敛。


- ***多视图学习（Multi-view learning）：*** 在多视图学习中我们假设数据是由多个视图或者说多个不同的特征集生成的，每个视图都可以进行学习和推断，不同视图之间的一致性被用作一种约束以引导学习过程。<br><br>

- ***生成模型（Generative models）：*** 生成模型是一类可以描述数据生成过程的模型，它可以同时学习标签数据和未标签数据的分布，并找出两者之间的关联。当有新的数据进来时，他们可以根据学习到的分布生成对应的标签。混合高斯模型和深度生成模型（例如变分自编码器和生成对抗网络）都是这个分类下的具体技术。

{{< /callout >}}



<br><br><br>




#### ***<font color=Coral face=Georgia  align=center>2.1.4、强化学习</font>***

***<font color=DarkCyan face=Georgia  align=center>1. 智能系统在与环境的连续互动中学习最有行为策略的机器学习问题；</font>***
- 它的学习系统（在其语境中称为智能体）能够观察环境，做出选择，执行操作，并获得回报（reward），或者是以负面回报的形式获得惩罚；<br>
- 它必须自行学习什么是最好的策略（policy），从而随着时间推移获得最大的回报。策略代表智能体在特定情况下应该选择的操作。；<br>
- 例如，许多机器人通过强化学习算法来学习如何行走；




<br><br><br>




### <font face=Georgia>2.2、线性\非线性</font>

***<font color=Coral face=Georgia  align=center>2.2.1. 线性模型；</font>***

线性模型是一种最简单也最重要的统计与机器学习模型。<br>
在线性模型中，输出是输入特征的线性组合。换句话说，假设特征和输出之间的关系是线性的，即满足一次方程。<br>
线性模型的一个主要优点是简单易理解、计算效率高，例如线性回归和逻辑回归。<br>
然而，现实生活中很多问题，特征和输出之间的关系复杂，非线性的。对于这类问题，线性模型的表达能力就显得不够。

<br>

***<font color=Coral face=Georgia  align=center>2.2.2. 非线性模型；</font>***

非线性模型则假设输入与输出之间是非线性关系。<br>
非线性关系的形式有很多，可能是二次、三次甚至更高次的多项式形式，也可能是指数、对数形式，等等。<br>
非线性模型的一个主要优点是可以拟合更复杂的关系，例如决策树、神经网络等。<br>
然而，非线性模型的主要挑战在于可能会过拟合数据（即模型对训练数据学习的过于复杂，不能很好地泛化到新的数据上）、和计算上的复杂性。





<br><br><br>




### <font face=Georgia>2.3、概率\非概率</font>

***<font color=Coral face=Georgia  align=center>2.3.1. 概率模型；</font>***

概率模型是一种基于概率理论的统计模型，它描述了随机变量之间的概率关系。<br>
在概率模型中，我们不仅预测某一结果，而且还给出了预测的不确定性（以概率的形式）。<br>
例如，朴素贝叶斯，高斯混合模型，隐马尔可夫模型，逻辑回归等都是概率模型。

概率模型的一个主要好处是给出了预测的不确定性，这在许多应用中是非常有用的，如天气预测、医疗诊断等。<br>
但是概率模型一般假定数据满足某种分布，这种假设在一些情况下可能过于严格，限制了模型的适应性。

<br>

***<font color=Coral face=Georgia  align=center>2.3.2. 非概率模型；</font>***

非概率模型不依赖于先验的可能性模型，而通常依赖于万丽最优化级星拉。<br>
非概率模型给出明确的预测，不提供预测的不确定性（即预测的概率）。<br>
例如，支持向量机，决策树，深度学习神经网络等都属于非概率模型。

非概率模型的优点是无需对数据分布做过多假设，这使得它们更具有适应性，能够处理各种复杂的数据情况。<br>
然而，非概率模型并不提供预测的不确定性，这在某些情况下可能是一个缺点。




<br><br><br>



### <font face=Georgia>2.4、参数\非参数</font>

***<font color=Coral face=Georgia  align=center>2.4.1. 参数模型；</font>***

参数模型是一种假设输入和输出之间的关系可以由一组参数完全确定，并且这组参数的数量是固定的。<br>
参数模型一般都有严格的假设，例如假设数据是正态分布的，或者输入和输出之间的关系是线性的等。<br>
常见的参数模型包括线性回归、逻辑回归、线性判别分析等。

参数模型的优点是理论清晰，计算相对简单。<br>
然而，缺点是对数据的假设可能过于严格，如果实际数据的分布或者结构与模型的假设不符，那么参数模型的表现可能会很差。

<br>

***<font color=Coral face=Georgia  align=center>2.4.2. 非参数模型；</font>***

非参数模型非常灵活，它不假设数据必须符合某一特定的分布，或者输入和输出间的关系必须是某一特定的形式。<br>
非参数模型的参数数量通常会随着数据量的增加而增加。<br>
常见的非参数模型包括决策树、随机森林、支持向量机等。

非参数模型的优点是非常灵活，可以处理各种复杂的数据情况。<br>
然而，非参数模型的缺点是计算上可能会比较复杂，而且由于模型过于灵活，如果数据量不足，可能会导致过度拟合。




<br><br><br>



### <font face=Georgia>2.5、基于实例\模型</font>

***<font color=Coral face=Georgia  align=center>2.5.1. 基于实例的学习；</font>***

系统先完全记住学习示例（example），然后通过某种相似度度量方式将其泛化到新的实例。<br>
基于实例的算法直接记住并使用训练实例进行预测，它们是一种惰性学习算法，因为它们仅在预测时进行计算。<br>
一个典型例子就是最近邻算法。

基于实例的学习的优点是可以适应复杂的问题，因为它们不需要进行任何明确的模拟。<br>
然而，存储和比较所有训练实例通常会造成大量的计算开销。

<br>

***<font color=Coral face=Georgia  align=center>2.5.2. 基于模型的学习；</font>***

在训练过程中会构建一个预测模型，然后使用该模型进行预测。这就是基于模型的学习。<br>
这种模型可以是线性的（例如线性回归），也可以是非线性的（例如神经网络），或者是更复杂的结构（例如决策树或随机森林）。<br>
构建模型的敏感过程（例如参数选择，模型选择）通常是自动进行的，并且侧重于提高预测的准确性。

基于模型的学习的一个主要优点是它们通常可以更有效地处理大量数据。<br>
然而，选择正确的模型并调整模型参数通常需要专门知识，并可能需要大量时间来得到满意的结果。




<br><br><br>



### <font face=Georgia>2.6、离线\在线学习</font>

***<font color=Coral face=Georgia  align=center>2.6.1. 离线学习；</font>***

离线学习，又称为批量学习，是最常见的学习方式。<br>
在离线学习中，我们先从一个固定的训练集中学习模型，然后将该模型应用于新的未知数据。

由于训练过程是从一个固定的数据集中进行的，因此可以对数据进行多次处理，也就是说可以重复训练。<br>
此外，训练过程通常需要大量的计算资源，因此通常在专用的机器上进行，并可能需要花费很长时间。

<br>

***<font color=Coral face=Georgia  align=center>2.6.1. 在线学习；</font>***

在线学习是一种连续的学习方式，可以适应新数据的出现。<br>
在在线学习中，模型以连续的方式接收数据并不断调整，因此能够实时适应新的信息。

这种学习方式非常适合那些需要不断适应新数据或数据量过大无法一次性处理的场景。<br>
然而，由于在线学习需要实时进行，因此其计算资源的需求通常比离线学习要更高。




<br><br><br>




