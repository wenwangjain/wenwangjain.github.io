---
title: 人工智能
weight: 1
#next: /step1
#prev: /docs
editURL: "https://example.com/edit/this/page"
toc: true
---


## 学习路径图

```mermaid
flowchart LR
    A(人工智能<br>学习路线):::someclassA --> B(基础内容):::someclassA 
        classDef someclassA fill:#58C9B9
        classDef someclassB fill:#9DC8C8
        classDef someclassC fill:#f100
        classDef someclassD fill:#a3c9c7
    A -- 阶段 1 --> C(端到端的机器学习):::someclassA
    A -- 阶段 2 --> D(掌握机器学习):::someclassA
    A -- 阶段 3 --> E(生成式人工智能):::someclassA
    A -- 阶段 4 --> F(相关领域专业知识):::someclassA

    B --> B1(pyhon) --> B2(微积分<br>线性代数):::someclassC --> B3(概率论<br>数理统计):::someclassC 

    C --> C1(人工智能<br>概述) --> C2(机器学习<br>常用算法) --> C3(建模工具<br>sklearn) --> C4(步骤\过程<br>CRISP-DM) --> C5(练习<br>UCI 数据) 
          C5 --> Z
    C --> C11(自动<br>机器学习):::someclassC  --> C12(处理大型<br>数据集):::someclassC

    D --> D1(先进的<br>机器学习):::someclassB
          D1 --> D11(集成学习<br>XGBoost) --> D111(深度学习<br>迁移学习) --> D112(建模工具<br>keras<br>PyTorch<br>tensorflow)
                 D112 --> D1121(计算机视觉<br>CV)
                 D112 --> D1122(自然语言处理<br>NLP)
                 D1121 --> Z
                 D1122 --> Z
          D1 --> D12(机器学习<br>Code 实现<br>python):::someclassC --> D121(sklearn<br>源码):::someclassC --> D122(深度学习<br>Code 实现<br>DeZero):::someclassC --> D123(PyTorch<br>tensorflow<br>源码):::someclassC

    D --> D2(模型部署<br>MLOps):::someclassB
          D2 --> D211(工程基础<br>git\github\Linux<br>容器\云<br>HF Spaces\<br>Streamlit Sharing) --> D212(MLOps 概述<br>部署方式<br>核心概念<br>......) --> D213(主要内容<br>自动化管道<br>监控<br>生命周期管理<br>治理) --> D214(管理工具<br>MLFlow<br>DVC<br>Polyaxon<br>Metaflow<br>Kubeflow) 

    E --> E10(深度学习) --> E1(生成模型)
          E1 --> E11(自然语言处理<br>NLP) --> E111(大语言模型<br>LLM)
                 E111 --> E2
          E1 --> E12(计算机视觉<br>CV)
                 E12 --> E2
         
          E2(模型部署) --> Z
  

    Z(竞赛<br>kaggle<br>阿里天池):::someclassA
```




```markdown
%%{ init: { 'flowchart': { 'curve': 'bumpX', 'styles': {
   'stroke-width': '1px'
} } } }%%
```




<br><br><br><br><br><br><br><br>



## 学习路径图

```mermaid

flowchart LR

    classDef someclassA fill:#58C9B9
    classDef someclassB fill:#9DC8C8
    classDef someclassC fill:#f100,stroke-width:1px
    classDef someclassD fill:#a3c9c7
    classDef someclassE fill:#fff,stroke:#fff,color:#fff
    classDef someclassF fill:#ff9900

    A(人工智能):::someclassA 
    
    A -- 基础知识 --> B1(Python\ R):::someclassC -.-> B2(线性代数<br>微积分):::someclassC -.-> B3(概率论<br>数理统计):::someclassC -.-> B4(贝叶斯统计):::someclassC

    A -- 阶段1：入门 --> C(端到端的<br>机器学习):::someclassA --> C12(机器学习<br>概述) --> C13(机器学习<br>常用算法) --> C14(建模工具<br>Sklearn) --> C15(建模步骤<br>CRISP-DM) --> Y

    A -- 阶段2：进阶 --> D(深度学习):::someclassA --> D11(深度学习<br>概述) --> D12(深度学习<br>算法) --> D13(建模工具<br>keras<br>PyTorch<br>Tensorflow<br>FastAI) 
        D13 --> D141(自然语言<br>NLP) --> Y
        D13 --> D142(计算机视觉<br>CV) --> Y

    A -- 算法解析 --> E21(深度解析<br>算法):::someclassF  -.- E22(自制框架<br>DeZero):::someclassC

    A -- 阶段3：先进 --> F(生成式<br>人工智能):::someclassA --> F1(提示工程)
        F3(从头构建<br>生成模型) --> F4(最新趋势<br>\研究\论文) --> Y
        F1 --> F21(NLP -> LLM) --> F3
        F1 --> F22(CV -> VLM) --> F3

    A -- 补充知识 --> G1(自动 ML<br>AutoML):::someclassB --> G2(集成学习):::someclassB -.- G3(时间序列):::someclassB -.- G4(迁移学习):::someclassB 

    Y(练习<br>UCI 数据集<br><br>竞赛<br>kaggle<br>阿里天池<br>...):::someclassA --> Z

    Z(模型部署<br>MLOps):::someclassF
    Z1(版本控制\协作:<br>Git\Github) -.-> Z12(操作系统:Linux<br>容器化\云:Docker) -.->  Z13(ML应用平台：<br>HF Spaces\<br>Streamlit Sharing) -.-> Z2(《MLOps 概述》<br>部署方式<br>核心概念<br>......) --> Z3(《主要内容》<br>自动化管道<br>监控<br>生命周期管理<br>治理) --> Z4(《管理工具》<br>MLFlow<br>DVC<br>Polyaxon<br>Metaflow<br>Kubeflow)
    Z4 --> Z

```


A -- AutoML<br>自动机器学习 --> Z



<br><br><br><br><br><br><br><br><br>



## 基础知识

{{< cards >}}
  {{< card link="/guide/math_linear_algebra" title="*线性代数*"  subtitle="<br>" icon="matrix" >}}
  {{< card link="/guide/math_calculus" title="微积分"  subtitle="" icon="calculus" >}}
  {{< card link="/guide/math_probability_theory" title="概率论"  subtitle="" icon="probability" >}}
  {{< card link="/guide/math_mathematical_statistics" title="数理统计" subtitle="" icon="statistics" >}}
  {{< card link="/guide/python/python" title="Python" subtitle="" icon="python" >}}
  {{< card link="/guide/python/python_modules" title="Python Modules" subtitle="" icon="python" >}}
{{< /cards >}}



<br><br><br>



## 阶段一：入门训练

### > 端到端的机器学习：

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
6. 将模型打包或序列化后的结果部署为 **`Flask API`** 或 **`Streamlit\Gradio`** 应用；

<font color=DarkCyan face=Georgia align=right>***推荐阅读：***</font>

- 《深度学习：从基础到实践》 （上、下册）- [美] Andrew Glassner



<br><br><br>



## 阶段 4：持续学习

<font color=DarkCyan face=Georgia align=right>***持续学习，主要内容参考如下：***</font>

1. [机器学习的最新进展带代码的论文](https://paperswithcode.com/)






<br><br><br><br><br><br><br><br><br><br><br><br>

    C --> C2(集成学习):::someclassA --> C22(集成学习<br>概述) --> C23(集成学习<br>算法) --> C24(集成学习<br>工具) -.- C25(>):::someclassE
    C25 -.-> Y
    
    C --> C3(ML 算法深度解析):::someclassA --> C31(ML 算法<br>Code 实现):::someclassB --> C32(Sklearn<br>源码):::someclassC










<br><br><br>

### 2、集成学习：
<font color=DarkCyan face=Georgia align=right>***学习集成学习，主要内容参考如下：***</font>

1. 了解集成学习相关概念；
2. 学习集成学习常用算法及集成学习方法体系（`Bagging`，`Boosting`，`Stacking`，`Blending`，等）；
3. 学习集成学习 Python 库（`Scikit-learn`，`XGBoost`，`LightGBM`，`CatBoost`）；
4. 练习\实践。如，小数据集 [`UCI ML`](https://archive.ics.uci.edu/) 或 `kaggle` 等；
5. 通过 **`Flask API`** 或 **`Streamlit\Gradio`** 部署应用；

<font color=DarkCyan face=Georgia align=right>***推荐阅读：***</font>

- 《集成学习：基础与算法》 - 周志华，李楠

<br><br><br>

### 3、ML 算法深度解析

{{< callout >}}
  机器学习算法深度解析，需要一定数学基础（线性代数，微积分，概率论与数理统计）。
  从头开始理解机器学习算法将帮助您为任务选择正确的算法，解释结果，解决高级问题，将算法扩展到新应用程序，并提高现有算法的性能。
{{< /callout >}}

<font color=DarkCyan face=Georgia align=right>***推荐阅读：***</font>

- 《achine Learning Algorithms in Depth》 - VADIM SMOLYAKOV





<br><br><br>



## 阶段 2：进阶

{{% steps %}}

### 1、时间序列：

<br><br><br>

### 2、深度学习：

<br><br><br>

### 3、NLP：

<br><br><br>

### 4、CV：

<br><br><br>

### 5、DL 算法深度解析

{{% /steps %}}



<br><br><br>



## 阶段三：高深

{{% steps %}}

### 1、NLP：

<br><br><br>

### 2、CV：

{{% /steps %}}



<br><br><br>







<br><br><br><br><br><br><br><br>

{{% steps %}}




### 阶段二：掌握机器学习



<font color=DarkCyan face=Georgia align=right>***掌握先进的机器学习技术：***</font>

1. 学习线性代数，微积分，深入研究机器学习算法；
2. 从集成学习开始，然后转向深度学习（神经网络及流行框架），迁移学习；
3. 深入研究深度学习，关注自然语言处理 (NLP) 和计算机视觉 (CV)；
4. 通过参竞赛（Kaggle，阿里天池），练习使用机器学习方法解决现实世界的问题；

<br>

<font color=DarkCyan face=Georgia align=right>***MLOps，机器学习的部署和生命周期管理：***</font>

1. 基础知识：`git`\ `github`\ `Linux`\容器化\云，`HF Spaces`\ `Streamlit Sharing`；
2. 部署方式：在线部署：批处理，实时（数据库触发器、发布/订阅、Web 服务、应用内）；离线部署（在本地开发环境、测试环境或内部离线环境中部署批处理，实时处理）；
3. 主要内容：自动化管道，监控，生命周期管理，治理；
4. 核心概念：持续集成与持续部署（CI/CD），版本控制，模型监控；
5. 管理工具：`MLFlow`，`Polyaxon`，`Metaflow`，`Kubeflow`；
  
<br>

<font color=DarkCyan face=Georgia align=right>***推荐书籍：***</font>

- 《统计学习方法》 (第2版) - 李航
- 《机器学习》（西瓜书）- 周志华





<br><br><br>



### 阶段三：高级人工智能

{{< callout >}}
  完成第二步的学习，可称为机器学习工程师，能建模，也能部署实践。***需要学习先进的人工智能技术，生成式人工智能***。
{{< /callout >}}

<font color=DarkCyan face=Georgia align=right>***深入研究高级人工智能主题，关注生成模型：***</font>

1. 开始使用，[coze](https://www.coze.com)；
2. NLP 生成模型，LLM（大语言模型）；
3. CV 生成模型；



<br><br><br>



### 阶段四：相关领域专业知识

{{< callout >}}
  ***作为数据科学家，需要具备解决相关领域的问题，需要理解相关领域的专业知识***。
{{< /callout >}}

<font color=DarkCyan face=Georgia align=right>***领域专业知识：***</font>

1. 学习不同领域专业知识，如保险，信贷，物流，电商等；
2. 通过研究竞赛平台多领域数据科学问题，获得 ***多样化的经验*** 培养 ***解决问题的技能***；
3. 可以通过收集的行业知识\信息，分析案例，创建行业知识库；



{{% /steps %}}

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
3. [从数据收集到模型部署：数据科学项目的 6 个阶段 - KDnuggets](https://www.kdnuggets.com/2023/01/data-collection-model-deployment-6-stages-data-science-project.html)
4. [全面的 MLOps 学习路径：2024 年版](https://www.analyticsvidhya.com/blog/2023/12/a-comprehensive-mlops-learning-path/)
5. [2024 年学习生成式人工智能的最佳路线图](https://www.analyticsvidhya.com/blog/2023/05/from-novice-to-pro-the-epic-journey-of-mastering-generative-ai/)
6. [MLOps 概述](https://www.kdnuggets.com/2021/03/overview-mlops.html)






