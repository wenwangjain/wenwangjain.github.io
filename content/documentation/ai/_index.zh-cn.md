---
title: 人工智能
weight: 1
#next: /step1
prev: /documentation
editURL: "https://example.com/edit/this/page"
type: "docs"
toc: true
math: true
---


{{< cards >}}
{{< card link="/documentation/ai/end_to_end" title="端到端的机器学习"  subtitle="简单易用，功能强大丰富。" icon="route" >}}
{{< card link="/documentation/ai/deep_learning" title="深度学习" subtitle="简单易用，功能强大丰富。" icon="neuron" >}}
{{< card link="/documentation/ai/gai" title="生成式人工智能" subtitle="大模型" icon="natural_language" >}}
{{< card link="/documentation/ai/mlops" title="模型部署 MLOps" subtitle="简单易用，功能强大丰富。" icon="automated_reporte" >}}
{{< card link="/documentation/ai/distributed" title="分布式训练" subtitle="简单易用，功能强大丰富。" icon="algorithm" >}}
{{< /cards >}}

<br><br>

## 学习路径


```mermaid

flowchart LR

    classDef someclassA fill:#58C9B9
    classDef someclassB fill:#9DC8C8
    classDef someclassC fill:#f100,stroke-width:1px
    classDef someclassD fill:#a3c9c7
    classDef someclassE fill:#fff,stroke:#fff,color:#fff
    classDef someclassF fill:#ff9900

    A(人工智能):::someclassA 
    
    A -- 阶段0：基础 --> B(基础知识):::someclassB --> B1(Python\ R):::someclassC -.-> B2(线性代数<br>微积分):::someclassC -.-> B3(概率论<br>数理统计<br>贝叶斯统计):::someclassC

    A -- 阶段1：入门 --> C(端到端的<br>机器学习):::someclassA --> C12(机器学习概述) --> C13(机器学习算法) --> C14(建模工具<br>Sklearn) --> C15(建模步骤<br>CRISP-DM) --> Y
        C -.-> C21(自动机器学习<br>Auto ML):::someclassC -.-> C22(大数据集处理):::someclassC

    A -- 阶段2：进阶 --> D(深度学习):::someclassA --> D11(深度学习概述) --> D12(深度学习算法) --> D13(建模工具<br>keras<br>PyTorch<br>Tensorflow<br>FastAI)
        D -.-> D21(深度解析算法):::someclassC -.-> D22(自制框架<br>DeZero):::someclassC -.-> D23(工具源码):::someclassC
        D13 --> D141(自然语言<br>NLP) --> Y
        D13 --> D142(计算机视觉<br>CV) --> Y

    A -- 阶段3：先进 --> F(生成式<br>人工智能):::someclassA --> F1(提示工程)
        F3(从头构建<br>生成模型) --> F4(最新趋势<br>\研究\论文) --> Y
        F1 --> F21(NLP -> LLM) --> F3
        F1 --> F22(CV -> VLM) --> F3

    Y(练习<br>UCI 数据集<br><br>竞赛<br>kaggle<br>阿里天池<br>...):::someclassA --> Z

    A -- 阶段4：部署 --> Z1
    Z(模型部署<br>MLOps):::someclassF
    Z1(版本控制\协作:<br>Git\Github) -.-> Z12(操作系统:Linux<br>容器化\云:Docker) -.->  Z13(ML应用平台：<br>HF Spaces\<br>Streamlit Sharing) -.-> Z2(《MLOps 概述》<br>部署方式<br>核心概念<br>......) --> Z3(《主要内容》<br>自动化管道<br>监控<br>生命周期管理<br>治理) --> Z4(《管理工具》<br>MLFlow<br>DVC<br>Polyaxon<br>Metaflow<br>Kubeflow)
    Z4 --> Z


    A -- 补充知识 --> G1(集成学习):::someclassB -.- G2(时间序列):::someclassB -.- G3(迁移学习):::someclassB -.- G4(强化学习):::someclassB -.- G5(专业知识):::someclassB

```

<br><br>

## 阶段 0：基础知识

{{< cards >}}
  {{< card link="/guide/math_calculus" title="微积分"  subtitle="是研究变化\微分与累积\积分的数学分支，用于解决运动、曲线、面积等动态问题。" icon="calculus" tag= "AI 基础">}}
  {{< card link="/guide/math_linear_algebra" title="线性代数"  subtitle="是研究向量、矩阵和线性变换的数学分支，核心用来解方程、处理空间变换和数据分析。" icon="matrix" tag= "AI 基础">}}
  {{< card link="/guide/math_probability_theory" title="概率论"  subtitle="是研究随机现象规律性的数学分支，用概率量化不确定性。" icon="probability" tag= "AI 基础">}}
  {{< card link="/guide/math_mathematical_statistics" title="数理统计" subtitle="是用数学工具（尤其是概率论）从数据中预测未知的学科，核心是抽样、估计和假设检验。" icon="statistics" tag= "AI 基础">}}
  {{< card link="/guide/program_python" title="Python" subtitle="一种广泛使用的解释型、高级和通用的编程语言。" icon="python" tag= "AI 基础">}}
{{< /cards >}}



<br><br>




## 阶段 1：端到端的机器学习


{{< callout >}}
  以学习完整的建模过程为主要目标，以了解常用机器算法（优缺点，原理，步骤，应用）和学习建模工具（`Sklearn`\ `scikit-learn`）为次要目标，
  快速熟悉端到端的建模过程。
{{< /callout >}}

<font color=DarkCyan face=Georgia align=right>***实践多个案例，熟悉端到端的建模过程，主要内容参考如下：***</font>

1. 了解人工智能，机器学习，深度学习，统计机器学习等相关概念；
2. 学习常用算法原理。了解算法优缺点，原理，步骤，应用即可，不必过多关注数学公式；
3. 学习建模分步过程。如：[**`CRISP-DM`**](https://www.ibm.com/docs/zh/spss-modeler/saas?topic=dm-crisp-help-overview)；
4. 学习建模工具。如：[**`scikit-learn`**](https://scikit-learn.org/stable/user_guide.html)；
5. 在小数据集上练习。如： [the UC Irvine Machine Learning Repository](https://archive.ics.uci.edu/)；
6. 将模型打包或序列化后的结果部署为 `Flask API` 或 `Streamlit\Gradio` 应用；

<font color=DarkCyan face=Georgia align=right>***补充内容：***</font>

1. 了解自动化机器学习工具。
2. 了解处理大数据集的 python 库。

<font color=DarkCyan face=Georgia align=right>***推荐阅读：***</font>

- 《深度学习：从基础到实践》 （上册）- [美] Andrew Glassner
- 《Machine Learning with Python Cookbook》 Chris Albon
- 《machine-learning-mastery-with-python》 Jason Brownlee 
- 《菜菜的机器学习sklearn课堂》
- 《机器学习实战：基于Scikit-Learn和TensorFlow》 （法）奥雷利安·杰龙
- 《Python机器学习》 （美）塞巴斯蒂安·拉施卡（Sebastian Raschka） （美）瓦希德·米尔贾利利（Vahid Mirjalili）

<br>

{{< cards >}}
  {{< card link="/guide/python_numpy" title="Numpy" subtitle="Python 科学计算的基本包；强大的 N 维数组；数值计算工具。" icon="numpy" tag= "数据分析">}}
  {{< card link="/guide/python_pandas" title="Pandas" subtitle="一个快速、强大、灵活且易于使用的开源数据分析和操作工具。" icon="pandas" tag= "数据分析">}}
  {{< card link="/guide/python_sklearn" title="Sklearn" subtitle="Python 中的机器学习；简单有效的预测数据分析工具。" icon="sklearn" tag= "机器学习">}}
{{< /cards >}}



<br><br><br>


## 阶段 2：深度学习

<font color=DarkCyan face=Georgia align=right>***深度学习，主要内容参考如下：***</font>

1. 了解深度学习相关概念；
2. 学习深度学习常用算法及深度学习方法体系（`CNN`，`RNN`，`LSTM`，`Transformer`，等）；
3. 学习深度学习框架\工具（`keras`，`PyTorch`，`Tensorflow`，`FastAI`）；
4. 学习自然语言处理，计算机视觉；
5. 在 KAggle，阿里天池上练习；


<font color=DarkCyan face=Georgia align=right>***补充内容：***</font>

{{< callout >}}
  机器学习算法深度解析，需要一定数学基础（线性代数，微积分，概率论与数理统计）。
  从头开始理解机器学习算法将帮助您为任务选择正确的算法，解释结果，解决高级问题，将算法扩展到新应用程序，并提高现有算法的性能。
{{< /callout >}}

1. 深度解析机器学习算法；
2. 学习深度学习自制框架：DeZero；
3. 学习框架\工具源码；


<font color=DarkCyan face=Georgia align=right>***推荐阅读：***</font>

- 《深度学习：从基础到实践》 （下册）- [美] Andrew Glassner
- 《深度学习入门基于Python的理论与实现》 - [日] 斋藤康毅
- 《深度学习入门2自制框架》 - [日] 斋藤康毅
- 《深度学习进阶：自然语言处理》 - [日] 斋藤康毅
- 《深度学习入门4：强化学习》 - [日] 斋藤康毅
- --
- 《achine Learning Algorithms in Depth》 - VADIM SMOLYAKOV
- 《统计学习方法》 (第2版) - 李航
- 《机器学习》（西瓜书）- 周志华


<br><br><br>



## 阶段 3：生成式人工智能

<font color=DarkCyan face=Georgia align=right>***深入研究高级人工智能主题，关注生成模型：***</font>

1. 学习提示工程（专注于创建和改进提示）。如：[coze](https://www.coze.com)；
2. NLP 的生成模型，LLM（大语言模型）；
3. 计算机视觉的生成模型；
4. 了解如何从头开始构建这些生成模型；
5. 了解生成人工智能的最新趋势和研究；


<font color=DarkCyan face=Georgia align=right>***推荐阅读：***</font>

- [2024 年学习生成式人工智能的最佳路线图](https://www.analyticsvidhya.com/blog/2023/05/from-novice-to-pro-the-epic-journey-of-mastering-generative-ai/)
- [机器学习的最新进展带代码的论文](https://paperswithcode.com/)
- [10 个学习法学硕士的免费资源](https://www.kdnuggets.com/10-free-resources-to-learn-llms)



<br><br><br>



## 阶段 4：模型部署

<font color=DarkCyan face=Georgia align=right>***MLOps，机器学习的部署和生命周期管理：***</font>

1. 基础知识：`git`\ `github`\ `Linux`\容器化\云，`HF Spaces`\ `Streamlit Sharing`；
2. 部署方式：在线部署：批处理，实时（数据库触发器、发布/订阅、Web 服务、应用内）；离线部署（在本地开发环境、测试环境或内部离线环境中部署批处理，实时处理）；
3. 主要内容：自动化管道，监控，生命周期管理，治理；
4. 核心概念：持续集成与持续部署（CI/CD），版本控制，模型监控；
5. 管理工具：`MLFlow`，`Polyaxon`，`Metaflow`，`Kubeflow`；


<font color=DarkCyan face=Georgia align=right>***推荐阅读：***</font>

- [成为 MLOps 工程师所需的唯一免费课程：MLOps Zoomcamp](https://www.kdnuggets.com/the-only-free-course-you-need-to-become-a-mlops-engineer)
- [掌握 MLOps 的 10 个 GitHub 存储库](https://www.kdnuggets.com/10-github-repositories-to-master-mlops)



<br><br><br>



## 补充知识

### 1、集成学习

<font color=DarkCyan face=Georgia align=right>***主要内容参考如下：***</font>

1. 了解集成学习相关概念；
2. 学习集成学习常用算法及集成学习方法体系（`Bagging`，`Boosting`，`Stacking`，`Blending`，等）；
3. 学习集成学习 Python 库（`Scikit-learn`，`XGBoost`，`LightGBM`，`CatBoost`）；
4. 练习\实践。如，小数据集 [`UCI ML`](https://archive.ics.uci.edu/) 或 `kaggle` 等；
5. 通过 **`Flask API`** 或 **`Streamlit\Gradio`** 部署应用；

<font color=DarkCyan face=Georgia align=right>***推荐阅读：***</font>

- 《集成学习：基础与算法》 - 周志华，李楠



<br><br><br>



### 2、领域专业知识

{{< callout >}}
  ***作为数据科学家，需要具备解决相关领域的问题，需要理解相关领域的专业知识***。
{{< /callout >}}

<font color=DarkCyan face=Georgia align=right>***领域专业知识：***</font>

1. 学习不同领域专业知识，如保险，信贷，物流，电商等；
2. 通过研究竞赛平台多领域数据科学问题，获得 ***多样化的经验*** 培养 ***解决问题的技能***；
3. 可以通过收集的行业知识\信息，分析案例，创建行业知识库；



<br><br><br>



## 创建投资组合

<font color=DarkCyan face=Georgia align=right>***选择与众不同的新颖项目创建投资组合：***</font>

1. 以 [Kaggle](https://www.kaggle.com/) 和 [阿里天池](https://tianchi.aliyun.com/competition/activeList) 等竞赛网站为起点；
2. 将报告在微信公众号、知乎、掘金等平台展示结果；
3. 在 Github 上托管个人博客；
4. 考虑录制一段简短的视频，展示您的发现；



<br><br><br>



## 参考网址：

1. [应用机器学习获得报酬](https://machinelearningmastery.com/ladder-approach-to-becoming-a-machine-learning-consultant/)
2. [2024 年成为数据科学家的学习路径](https://www.analyticsvidhya.com/blog/2020/12/a-comprehensive-learning-path-to-become-a-data-scientist/)
3. [2024 年学习生成式人工智能的最佳路线图](https://www.analyticsvidhya.com/blog/2023/05/from-novice-to-pro-the-epic-journey-of-mastering-generative-ai/)
4. [从数据收集到模型部署：数据科学项目的 6 个阶段 - KDnuggets](https://www.kdnuggets.com/2023/01/data-collection-model-deployment-6-stages-data-science-project.html)
5. [全面的 MLOps 学习路径：2024 年版](https://www.analyticsvidhya.com/blog/2023/12/a-comprehensive-mlops-learning-path/)
6. [MLOps 概述](https://www.kdnuggets.com/2021/03/overview-mlops.html)

























