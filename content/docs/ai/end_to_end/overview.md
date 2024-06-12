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



1. ***人工智能***，是指可以像人类一样学习、理解、思考的计算机程序。
2. ***机器学习***，是人工智能的一个子集。使用数据训练模型，这些模型可以根据在数据中找到的关系进行预测。
- --
3. ***深度学习***，是机器学习的一个分支。
   - 使用特殊分层结构的机器学习方法（这些分层依次堆叠），形成了一个像堆叠的煎饼一样的“深度”结构。
   - 深度学习算法受到大脑结构的启发，可以很好地处理图像、视频或文本等非结构化数据。
- --
4. ***深度学习框架***，是一个拼凑了层和函数等组件的库。具体来说，它是一种具有求导功能的编程语言（有人也成“可微分编程语言”）。
- --
5. ***强化学习***，这是一种让AI系统通过与环境的交互学习和提升的方法。（用于训练AI玩视频游戏或控制机器人等）。
- --
6. ***自然语言***，这技术使机器理解并回应人类语言成为可能。（聊天机器人，语音助手，自动翻译系统等）
7. ***计算机视觉***，通过相机、视频和图像直观地解释世界的 AI 功能。（如自动驾驶）
- --
8. ***生成式人工智能***，是一种机器学习模型，它可以生成以前从未见过的新内容，如音乐，文本，图像等。对比预测性质的模型，生成性模型可以创造全新的输出。



<br><br><br>



### <font face=Georgia>1.2、人工智能简史</font>

***<font color=Coral face=Georgia  align=center>19 世纪 30~40 年代</font>*** —— 
***<font face=Georgia  align=center>查尔斯 • 巴贝奇 —— 分析机（Analytical Engine）</font>***<br>
第一台通用的机械式计算机。它的用途仅仅是利用机械操作将数学分析领域的某些计算自动化，因此得名“分析机”

***<font color=Coral face=Georgia  align=center>20 世纪 50 年代</font>*** —— 
***<font face=Georgia  align=center>符号主义人工智能（symbolic AI）</font>***<br>
精心编写足够多的明确规则来处理知识，就可以实现与人类水平相当的人工智能。<br>
人工智能先驱阿兰 • 图灵在其 1950年发表的具有里程碑意义的论文“计算机器和智能”。

***<font color=Coral face=Georgia  align=center>20 世纪 60~70年代初</font>*** —— 
***<font face=Georgia  align=center>第一次冬天</font>***<br>
由于过高的期望未能实现，研究人员和政府资金均转向其他领域。

***<font color=Coral face=Georgia  align=center>20 世纪 80 年代</font>*** —— 
***<font face=Georgia  align=center>专家系统（expert system）</font>***<br>
符号主义人工智能热度达到了顶峰。

***<font color=Coral face=Georgia  align=center>20 世纪 90 年代初</font>*** —— 
***<font face=Georgia  align=center>第二次冬天</font>***<br>
专家系统维护费用变得很高，难于扩展，并且使用范围有限，人们逐渐对其失去兴趣。

***<font color=Coral face=Georgia  align=center>20 世纪 90 年代</font>*** —— 
***<font face=Georgia  align=center>机器学习</font>***<br>
专家系统难于给出明确的规则来解决更加复杂、模糊的问题，比如图像分类、语音识别、和语言翻译。<br>
于是20世纪90年代出现了机器学习来替代符号人工智能。<br>
机器学习是训练出来的，而不是明确规地用程序编写出来的。

***<font color=Coral face=Georgia  align=center>21 世纪 20 年代</font>*** —— 
***<font face=Georgia  align=center>生成式人工智能</font>***<br>
OpenAI 在2020年6月发布了 GPT-3，这是一个非常大且复杂的模型，拥有1750亿个参数。<br>
GPT-3 在生成文本和其他语言任务方面的表现令人瞩目，并且激发了大量关于 AI 的讨论。



<br><br><br>



## <font face=Georgia>2、机器学习分类</font>

### <font face=Georgia>2.1、基本分类</font>

***<font color=Coral face=Georgia  align=center>监督学习（supervised learning）</font>*** —— 
***<font face=Georgia  align=center>从有标注（标签\标记）的数据中学习预测模型的机器学习问题。</font>***<br>
- ***分类任务：*** 预测变量为分类（离散）变量，如：是否流失；
- ***回归任务：*** 预测变量为数值（连续）变量，如：营业收入；<br><br>

- --

<br>

>  ***生成模型 \ 判别模型：*** 监督学习的任务就是学习一个模型，应用这个模型，对给定的输入预测相应的输出。<br>
   这个模型的一般形式为决策函数（***判别模型*** ）：
   $$Y = f(X)$$ 
   或者条件概率分布（***生成模型***）：
   $$Y = P(Y|X)$$
- ***判别模型***：在已知输入的情况下，预测出输出，常见的判别模型有逻辑回归、支持向量机和深度学习神经网络等。<br>
- ***生成模型***：尝试捕捉数据中的潜在分布，常见的生成模型有高斯混合模型和朴素贝叶斯分类器等。


<br><br>
  
***<font color=Coral face=Georgia  align=center>监督学习（supervised learning）</font>*** —— 
***<font face=Georgia  align=center>从有标注（标签\标记）的数据中学习预测模型的机器学习问题。</font>***<br>
- ***分类任务：*** 预测变量为分类（离散）变量，如：是否流失；
- ***回归任务：*** 预测变量为数值（连续）变量，如：营业收入；






