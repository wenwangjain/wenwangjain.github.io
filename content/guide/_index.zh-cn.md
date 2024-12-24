---
title: "指南"
layout: hextra-home
---

<div style="display: flex; justify-content: center; width: 100%;">
  <div style="flex: 100%; padding: 10px; box-sizing: border-box; text-align: center;">

  {{< badge content="微积分" type="info" link="/guide/math_calculus">}}&nbsp;
  {{< badge content="线性代数" type="info" link="/guide/math_linear_algebra">}}&nbsp;
  {{< badge content="概率论" type="info" link="/guide/math_probability_theory">}}&nbsp;
  {{< badge content="数理统计" type="info" link="/guide/math_mathematical_statistics">}}&nbsp;

  {{< badge content="Python" type="warning" link="python/python">}}&nbsp;
  {{< badge content="java" type="warning" link="Java">}}&nbsp;

  {{< badge content="Numpy" type="error" link="python/python_numpy">}}&nbsp;
  {{< badge content="Pandas" type="error" link="python/python_pandas">}}&nbsp;
  {{< badge content="Statsmodels" type="error" link="python/python_statsmodels">}}&nbsp;
  {{< badge content="Sklearn" type="error" link="python/python_sklearn">}}&nbsp;
  {{< badge content="Sklearn 源码" type="" link="sc_sklearn">}}&nbsp;

  {{< badge content="Matplotlib" type="error" link="python/python_matplotlib">}}&nbsp;
  {{< badge content="Seaborn" type="error" link="python/python_seaborn">}}&nbsp;
  {{< badge content="Plotly" type="error" link="python/python_plotly">}}&nbsp;
  {{< badge content="Vega-Altair" type="error" link="python/python_vega-altair">}}&nbsp;

  {{< badge content="SHAP" type="" link="python/python_shap">}}&nbsp;
  {{< badge content="Streamlit" type="info" link="python/python_streamlit">}}&nbsp;
  {{< badge content="Flask" type="info" link="python/python_streamlit">}}&nbsp;
  {{< badge content="Airflow" type="info" link="bd_airflow">}}&nbsp;

  {{< badge content="GeoPandas" type="error" link="python/python_geopandas">}}&nbsp;
  {{< badge content="Folium" type="error" link="python/python_folium">}}&nbsp;

  {{< badge content="DeZero" type="info" link="dl_dezero">}}&nbsp;
  {{< badge content="Keras" type="info" link="dl_keras">}}&nbsp;
  {{< badge content="PyTorch" type="info" link="dl_pytorch">}}&nbsp;
  {{< badge content="TensorFlow" type="info" link="dl_tensorflow">}}&nbsp;
  {{< badge content="FastAI" type="info" link="dl_fastai">}}&nbsp;

  {{< badge content="PyTorch 源码" type="" link="sc_pytorch">}}&nbsp;
  {{< badge content="TensorFlow 源码" type="" link="sc_tensorflow">}}&nbsp;

  {{< badge content="Linux" type="warning" link="software_linux">}}&nbsp;
  {{< badge content="Git" type="warning" link="software_git">}}&nbsp;
  {{< badge content="Github" type="warning" link="software_github">}}&nbsp;
  {{< badge content="Docker" type="warning" link="software_docker">}}&nbsp;
  {{< badge content="Kubernetes" type="warning" link="software_kubernetes">}}&nbsp;

  {{< badge content="MySQL" type="info" link="database_mysql">}}&nbsp;
  {{< badge content="Datart" type="error" link="bi_datart">}}&nbsp;
  {{< badge content="PowerBI" type="error" link="bi_powerbi">}}&nbsp;
  {{< badge content="Tableau" type="error" link="bi_tableau">}}&nbsp;

  {{< badge content="Kafka" type="info" link="bd_kafka">}}&nbsp;
  {{< badge content="Flume" type="" link="bd_flume">}}&nbsp;
  {{< badge content="Flink CDC" type="info" link="bd_flink_cdc">}}&nbsp;
  {{< badge content="Flink" type="info" link="bd_flink">}}&nbsp;

  {{< badge content="Airflow" type="info" link="bd_airflow">}}&nbsp;
  {{< badge content="DolphinScheduler" type="info" link="bd_dolphinscheduler">}}&nbsp;
  {{< badge content="Datahub" type="info" link="bd_datahub">}}&nbsp;
  {{< badge content="OpenMetadata" type="info" link="bd_openmetadata">}}&nbsp;

  {{< badge content="Doris" type="info" link="bd_doris">}}&nbsp;
  {{< badge content="Druid" type="info" link="bd_druid">}}&nbsp;
  {{< badge content="Iceberg" type="info" link="bd_iceberg">}}&nbsp;
  {{< badge content="Zeppelin" type="error" link="bd_zeppelin">}}&nbsp;
  {{< badge content="StreamPark" type="error" link="bd_streampark">}}&nbsp;
  {{< badge content="Dinky" type="error" link="bd_dinky">}}&nbsp;

  {{< badge content="Hadoop" type="warning" link="bd_hadoop">}}&nbsp;
  {{< badge content="Hive" type="warning" link="bd_hive">}}&nbsp;
  {{< badge content="Spark" type="warning" link="bd_spark">}}&nbsp;
    </div>
</div>


<br>


## 1、数学基础

{{< cards >}}
  {{< card link="/guide/math_calculus" title="微积分"  subtitle="" icon="calculus" >}}
  {{< card link="/guide/math_linear_algebra" title="线性代数"  subtitle="" icon="matrix" >}}
  {{< card link="/guide/math_probability_theory" title="概率论"  subtitle="" icon="probability" >}}
  {{< card link="/guide/math_mathematical_statistics" title="数理统计" subtitle="" icon="statistics" >}}
{{< /cards >}}


<br>

## 2、编程语言

{{< cards >}}
  {{< card link="python/python" title="Python" subtitle="一种广泛使用的解释型、高级和通用的编程语言。" icon="python" >}}
  {{< card link="java" title="Java" subtitle="由 Sun 公司于 1995 年 5 月推出的高级程序设计语言。" icon="java" >}}
{{< /cards >}}

<br>




## 3、机器学习：Python

### 3.1、基础库

{{< cards >}}
  {{< card link="python/python_numpy" title="Numpy" subtitle="Python 科学计算的基本包；强大的 N 维数组；数值计算工具。" icon="numpy" >}}
  {{< card link="python/python_pandas" title="Pandas" subtitle="一个快速、强大、灵活且易于使用的开源数据分析和操作工具。" icon="pandas" >}}
  {{< card link="python/python_statsmodels" title="Statsmodels" subtitle="Python 统计建模库；用于进行统计测试和统计数据探索。" icon="package" >}}
  {{< card link="python/python_sklearn" title="Sklearn" subtitle="Python 中的机器学习；简单有效的预测数据分析工具。" icon="sklearn" >}}
  {{< card link="sc_sklearn" title="Sklearn 源码" subtitle="Sklearn 源码<br><br>" icon="sklearn" >}}
{{< /cards >}}

<br>

### 3.2、可视化

{{< cards >}}
  {{< card link="python/python_matplotlib" title="Matplotlib" subtitle="用 Python 创建静态、动画和交互式可视化。" icon="matploblib" >}}
  {{< card link="python/python_seaborn" title="Seaborn" subtitle="一个基于 matplotlib 的 Python 数据可视化库。" icon="seaborn" >}}
  {{< card link="python/python_plotly" title="Plotly" subtitle="Plotly 的 Python 图形库可制作交互式、出版质量的图形。" icon="plotly" >}}
  {{< card link="python/python_vega-altair" title="Vega-Altair" subtitle="一个基于 Vega 和 Vega-Lite 的 Python 声明式统计可视化库。" icon="vega" >}}
{{< /cards >}}

<br>

### 3.3、模型解释

{{< cards >}}
  {{< card link="python/python_shap" title="SHAP" subtitle="一种博弈论方法，用于解释任何机器学习模型的输出。" icon="package" >}}
{{< /cards >}}

<br>

### 3.4、模型部署

{{< cards >}}
  {{< card link="python/python_streamlit" title="Streamlit" subtitle="一个开源 Python 框架；快速构建和部署强大的数据应用程序。" icon="streamlit" >}}
  {{< card link="python/python_streamlit" title="Flask" subtitle="..." icon="flask" >}}
  {{< card link="bd_airflow" title="Airflow" subtitle="一个由社区创建的平台，用于以编程方式编写、安排和监控工作流程。" icon="airflow" >}}
{{< /cards >}}

<br>

### 3.5、空间数据

{{< cards >}}
  {{< card link="python/python_geopandas" title="GeoPandas" subtitle="旨在让使用 Python 处理地理空间数据变得更加容易。" icon="geopandas" >}}
  {{< card link="python/python_folium" title="Folium" subtitle="轻松地在交互式传单地图上可视化使用 Python 处理的数据。" icon="folium" >}}
{{< /cards >}}

<br>




## 4、深度学习

{{< cards >}}
  {{< card link="dl_dezero" title="DeZero" subtitle="使用 Python 从头开始实现深度神经网络。" icon="package" >}}
  {{< card link="dl_keras" title="Keras" subtitle="一个用 Python 编写的开源神经网络库。" icon="keras" >}}
  {{< card link="dl_pytorch" title="PyTorch" subtitle="一个基于 Python 的开源机器学习库。" icon="pytorch" >}}
  {{< card link="dl_tensorflow" title="TensorFlow" subtitle="Google Brain 团队开发的一个机器学习和深度学习的开源库。" icon="tensorflow" >}}
  {{< card link="dl_fastai" title="FastAI" subtitle="fastai 是一个深度学习库，易于使用且快速高效。" icon="package" >}}
  {{< card link="sc_pytorch" title="PyTorch 源码" subtitle="PyTorch 源码<br>......" icon="pytorch" >}}
  {{< card link="sc_tensorflow" title="TensorFlow 源码" subtitle="Tensorflow 源码" icon="tensorflow" >}}
{{< /cards >}}


<br>



## 5、软件工程

{{< cards >}}
  {{< card link="software_linux" title="Linux" subtitle="Linux 是一种自由和开放源码的类 UNIX 操作系统。" icon="linux" >}}
  {{< card link="software_git" title="Git" subtitle="Git 是一个免费的开源 分布式版本控制系统。" icon="git" >}}
  {{< card link="software_github" title="Github" subtitle="一个在线软件源代码托管服务平台，使用Git作为版本控制软件。" icon="github" >}}
  {{< card link="software_docker" title="Docker" subtitle="一个开源的应用容器引擎，基于 Go 语言。" icon="docker" >}}
  {{< card link="software_kubernetes" title="Kubernetes" subtitle="开源容器编排引擎，用于自动部署、扩展和管理容器化应用程序" icon="kubernetes" >}}
{{< /cards >}}

<br>


## 5、数据库

{{< cards >}}
  {{< card link="database_mysql" title="MySQL" subtitle="MySQL 是一个流行的关系型数据库管理系统。" icon="mysql" >}}
{{< /cards >}}

<br>


## 6、商业分析：BI

{{< cards >}}
  {{< card link="bi_datart" title="Datart" subtitle="Datart 是新一代数据可视化开放平台。" icon="package" >}}
  {{< card link="bi_powerbi" title="PowerBI" subtitle="Power BI 是由微软开发的商业分析工具集。" icon="powerbi" >}}
  {{< card link="bi_tableau" title="Tableau" subtitle="Tableau 是一款强大的数据可视化工具。" icon="tableau" >}}
{{< /cards >}}

<br>




## 7、大数据

{{< cards >}}
  {{< card link="bd_kafka" title="Kafka" subtitle="一个开源分布式事件流平台，实现高性能数据管道、流分析、数据集成和关键任务应用程序。" icon="kafka" >}}
  {{< card link="bd_flume" title="Flume" subtitle="一种分布式、可靠且可用的服务，用于高效收集、聚合和移动大量日志数据。" icon="apache" >}}
  {{< card link="bd_flink_cdc" title="Flink CDC" subtitle="一个基于流的数据集成工具，旨在为用户提供一套功能更加全面的编程接口（API）。" icon="flink" >}}
  {{< card link="bd_flink" title="Flink" subtitle="一个框架和分布式处理引擎，用于对无界和有界数据流进行有状态计算。" icon="flink" >}}
  
  {{< card link="bd_airflow" title="Airflow" subtitle="一个由社区创建的平台，用于以编程方式编写、安排和监控工作流程。" icon="airflow" >}}
  {{< card link="bd_dolphinscheduler" title="DolphinScheduler" subtitle="一个多元化、可扩展的开源工作流协调平台，具有强大的DAG可视化界面。" icon="apache" >}}
  {{< card link="bd_datahub" title="Datahub" subtitle="一个可扩展的数据目录，它支持数据发现、数据可观察性和联合治理，以帮助控制数据生态系统的复杂性。" icon="package" >}}
  {{< card link="bd_openmetadata" title="OpenMetadata" subtitle="一个统一的元数据平台，用于数据发现、数据可观测性和数据治理，由中央元数据存储库、深入的列级沿袭和无缝团队协作提供支持。" icon="package" >}}

  {{< card link="bd_doris" title="Doris" subtitle="一个用于实时分析的现代数据仓库。它可以对大规模实时数据进行闪电般快速的分析。" icon="apache" >}}
  {{< card link="bd_druid" title="Druid" subtitle="高性能实时分析数据库，可在大规模和负载下对流式和批量数据进行亚秒级查询。" icon="druid" >}}
  {{< card link="bd_iceberg" title="Iceberg" subtitle="一种用于大型分析表的高性能格式。" icon="iceberg" >}}

  {{< card link="bd_zeppelin" title="Zeppelin" subtitle="基于 Web 的笔记本，支持使用 SQL、Scala、Python、R 等进行 数据驱动、交互式数据分析和协作文档。" icon="zeppelin" >}}
  {{< card link="bd_streampark" title="StreamPark" subtitle="易于使用的流应用程序开发框架和运行平台，支持 Flink 和 Spark，为流处理应用程序提供完整的生命周期支持。" icon="apache" >}}
  {{< card link="bd_dinky" title="Dinky" subtitle="为 Flink 深度定制的新一代实时计算平台，提供敏捷的 Flink SQL, Flink Jar 作业开发、部署及监控能力，助力实时计算高效应用。" icon="package" >}}

{{< /cards >}}


<br>


{{< cards >}}
  {{< card link="bd_hadoop" title="Hadoop" subtitle="一个框架，允许使用简单的编程模型跨计算机集群分布式处理大型数据集。" icon="hadoop" >}}
  {{< card link="bd_hive" title="Hive" subtitle="Apache Hive 是一个分布式、容错数据仓库系统，可实现大规模分析。" icon="hive" >}}
  {{< card link="bd_spark" title="Spark" subtitle="一个多语言引擎，用于在单节点机器或集群上执行数据工程、数据科学和机器学习。" icon="spark" >}}
{{< /cards >}}


<br><br><br>







