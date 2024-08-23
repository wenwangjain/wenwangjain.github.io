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

|*评估方法*|*简述*|*优点*|*缺点*|*适用情况*|
|:-:|:-:|:-:|:-:|:-:|
|***留出法***|拆分为训练集\测试集<br>使用测试集评估模型性能|简单、直观<br>计算开销小|评估结果可能不稳定<br>受划分数据随机性影响较大|数据量足够大时适用|
|***交叉验证***|随机平均分成 K 份<br>选择其中 1 份为测试集<br>其余 K-1 份为训练集<br>重复 K 次得到 K 个评估结果|充分利用数据<br>评估结果相对稳定|计算开销较大|数据量适中\较小时适用<br>需要更可靠评估的情况|
|***留一法***||利用了几乎所有数据、偏差小<br>交叉验证的特殊情况|计算开销极大|数据量较小时适用|
|***自助法***||能在数据量较小的情况下<br>产生不同的训练/测试集|改变了初始数据集的分布<br>引入估计偏差|数据量较小时适用<br>难以有效划分训练/测试集|

<br>

#### (1). *留出法*

{{% details title="<font color=Gray face=Georgia size=3>（1）、`sklearn.sklearn.model_selection.train_test_split()` —— *拆分训练集\测试集*</font>" closed="true" %}}
```python
# Load libraries
from sklearn import datasets
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LogisticRegression
from sklearn.metrics import accuracy_score


# Load iris dataset
iris = datasets.load_iris()
X, y = iris.data, iris.target


# Create training and test sets
X_train, X_test, y_train, y_test = train_test_split(
    X, y, test_size=0.3, stratify = y, random_state=3)
# stratify = y  # 设置分层
# shuffle = True # 打乱排序


model = LogisticRegression()
model.fit(X_train , y_train)

y_pred_test = model.predict(X_test)
result_test_Accuracy = accuracy_score(y_test, y_pred_test)

print(("result_test_Accuracy: %.3f%%") % (result_test_Accuracy*100.0))

"""
result_test_Accuracy: 93.333%
"""
```
{{% /details %}}

{{% details title="<font color=Gray face=Georgia size=3>（2）、`sklearn.sklearn.model_selection.train_test_split()` + `sklearn.pipeline.Pipeline()` </font>" closed="true" %}}
```python
# Load libraries
from sklearn import datasets
from sklearn.model_selection import train_test_split
from sklearn.pipeline import Pipeline
from sklearn.preprocessing import StandardScaler
from sklearn.linear_model import LogisticRegression
from sklearn.metrics import accuracy_score


# Load iris dataset
iris = datasets.load_iris()
X, y = iris.data, iris.target


# Create training and test sets
X_train, X_test, y_train, y_test = train_test_split(
    X, y, test_size=0.3, stratify = y, random_state=3)
# stratify = y  # 设置分层
# shuffle = True # 打乱排序


pipe = Pipeline([
     ('StandardScaler', StandardScaler())
    ,('LogisticRegression', LogisticRegression())
    ])

pipe.fit(X_train , y_train)

y_pred_test = pipe.predict(X_test)
result_test_Accuracy = accuracy_score(y_test, y_pred_test)

print(("result_test_Accuracy: %.3f%%") % (result_test_Accuracy*100.0))

'''
result_test_Accuracy: 91.111%
'''
```
{{% /details %}}



<br><br>



#### (2). *交叉验证*

{{% details title="<font color=Gray face=Georgia size=3>（1）、`sklearn.model_selection.KFold()` —— *K 折交叉验证*</font>" closed="true" %}}
```python {linenos=table, linenostart=1}
from sklearn.model_selection import KFold
from sklearn.linear_model import LogisticRegression
from sklearn.metrics import accuracy_score

from sklearn import datasets

# Load digits dataset
digits = datasets.load_digits()
X, y = digits.data, digits.target

kf = KFold(n_splits=5)
model = LogisticRegression(max_iter=1000)


for train_index, test_index in kf.split(X):
    X_train, X_test = X[train_index], X[test_index]
    y_train, y_test = y[train_index], y[test_index]
    
    model.fit(X_train, y_train)
    predictions = model.predict(X_test)
    print(accuracy_score(y_test, predictions))

'''
0.9277777777777778
0.875
0.9415041782729805
0.9387186629526463
0.9080779944289693
'''
```
{{% /details %}}

{{% details title="<font color=Gray face=Georgia size=3>（2）、`sklearn.model_selection.cross_val_score()` —— *K 折交叉验证*</font>" closed="true" %}}
```python {linenos=table, linenostart=1}
from sklearn import datasets
from sklearn.linear_model import LogisticRegression
from sklearn.model_selection import cross_val_score

diabetes = datasets.load_diabetes()
X, y = digits.data, digits.target

model = LogisticRegression(max_iter=1000)

print(cross_val_score(model, X, y, cv=5, scoring="accuracy"))

'''
[0.92222222 0.87222222 0.94150418 0.93871866 0.89693593]
'''
```
{{% /details %}}

{{% details title="<font color=DarkCyan face=Georgia size=3>（3）、***`KFold()`*** `VS` ***`cross_val_score()`***</font>" closed="true" %}}
|*函数*|*简述*|*适用情况*|
|:-:|:-:|:-|
|***`KFold`***|它主要用于手动控制交叉验证的分割过程，<br>你可以根据 KFold 的分割结果，<br>自行实现模型的训练和评估逻辑。|1. 当你需要对交叉验证的分割过程有更精细的控制；<br>2. 结合其他复杂的流程或算法，需要灵活处理交叉验证的各个折；|
|***`cross_val_score`***|一个方便的函数，它接受一个模型、数据集<br>和交叉验证策略（如 KFold ），自动完成<br>交叉验证的过程，并返回每个折的评估分数|1. 快速进行交叉验证评估，无需手动编写复杂的循环和评估逻辑；<br>2. 只想获取交叉验证的评估分数，而不需要深入控制每个折的具体操作|
> 总的来说，***`cross_val_score`*** 和 ***`KFold`*** 都能进行交叉验证，前者提供了更快捷的方式，后者则提供了更高的灵活性。可以根据实际的需求选择使用哪一个。
{{% /details %}}






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


<br>


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



## 参考网址

- <font color=Coral face=Georgia  >《Machine Learning with Python Cookbook》</font>
