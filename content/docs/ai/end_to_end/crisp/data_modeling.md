---
title: 【5】数据建模
weight: 5
#next: /step1
#prev: /docs
editURL: "https://example.com/edit/this/page"
toc: true
math: true
---

<br>

## 1、模型评估

<br>

### 1.1、评估方法

|*评估方法*|*优点*|*缺点*|*适用情况*|
|:-:|:-:|:-:|:-:|
|***留出法***|简单、直观<br>计算开销小|评估结果可能不稳定<br>受划分数据随机性影响较大|数据量足够大时适用|
|***交叉验证***|充分利用数据<br>评估结果相对稳定|计算开销较大|数据量适中\较小时适用<br>需要更可靠评估的情况|
|***留一法***|利用了几乎所有数据、偏差小<br>交叉验证的特殊情况|计算开销极大|数据量较小时适用|
|***自助法***|能在数据量较小的情况下<br>产生不同的训练/测试集|改变了初始数据集的分布<br>引入估计偏差|数据量较小时适用<br>难以有效划分训练/测试集|

#### (1). 留出法


<br><br>


#### (2). 交叉验证


<br><br>


#### (3). 留一法


<br><br>


#### (4). 自助法


<br><br>


### 1.2、评估指标

#### (1). 分类

|*方法*|*优点*|*缺点*|*适用情况*|
|:-:|:-|:-|:-|
|***准确率***|1.直观易懂；<br>2.综合考虑了所有类别的分类情况；|1.类别不平衡时可能会产生误导；<br>2.不能描述不同类别的表现情况；|适用类别平衡，<br>错误分类的代价相差不多；<br>模型初步探索和比较；|
|||||
|||||
|||||
|||||


<br><br>


{{% details title="<font color=Gray size=3>1. ***准确率***：`sklearn.metrics.accuracy_score()` ***参数***</font>" closed="true" %}}
|*参数*|*解释*|*取值\取值类型*|*默认值*|*是否关联*|*参数类型*|
|:-:|:-:|:-:|:-:|:-:|:-:|
|***`y_true`***|真实的标签值|||||
|***`y_pred`***|预测的标签值|||||
|`normalize`|设置输出正确比例、样本数|布尔值<br>True：返回比例；False：返回样本数|`True`||***可选***|
|`sample_weight`|设置样本的权重|根据具体的业务需求和数据特点来设置取值|||***可选***|
{{% /details %}}

{{% details title="<font color=Gray size=3>2. ***准确率***：`sklearn.metrics.accuracy_score()` ***案例***</font>" closed="true" %}}
```python
from sklearn.metrics import accuracy_score

y_true = [0, 1, 2, 0, 1, 2]
y_pred = [0, 1, 1, 0, 0, 2]

print(accuracy_score(y_true, y_pred))
print(accuracy_score(y_true, y_pred, normalize=True))
print(accuracy_score(y_true, y_pred, normalize=False))

sample_weight = [0.5, 1, 0.8, 0.6, 0.9, 0.7]
print(accuracy_score(y_true, y_pred, sample_weight=sample_weight))

"""
0.6666666666666666
0.6666666666666666
4.0
0.6222222222222222
"""
```
{{% /details %}}




<br><br>


<br><br>


#### (2). 回归


<br><br>


#### (3). 聚类


<br><br><br>



## 2、模型选择

### 2.1、通过自动机器学习选择



<br><br>



### 2.2、通过网格搜索选择



<br><br><br>



## 3、模型堆叠\融合



<br><br><br>



## 4、模型解释



<br><br><br>



## 5、模型保存



<br><br><br>
