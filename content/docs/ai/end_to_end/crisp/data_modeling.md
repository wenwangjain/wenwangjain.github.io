---
title: 5. 数据建模
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


### 1.1、评估指标

#### (1). 分类

<div style="font-size: 14px; border-left=0; border-right=0">
  <table>

|*方法*|*优点*|*缺点*|*适用情况*|
|:-:|:-|:-|:-|
|***混淆矩阵***|1.直观易懂；<br>2.提供了各个类别上的详细分类情况；|1.多分类会变得复杂庞大；<br>2.不能给出一个综合评估指标；|1.需要查看每个类别上的分类表现时；<br>2.洞察模型的行为和改进方向；<br>3.需要不平衡数据中少数类别的分类效果|
|***准确率***|1.直观易懂；<br>2.综合考虑了所有类别的分类情况；|1.类别不平衡时可能会产生误导；<br>2.不能描述不同类别的表现情况；|适用类别平衡，<br>错误分类的代价相差不多；<br>模型初步探索和比较；|
|||||
|||||
|||||
|||||

  </table>
</div>


<br>

{{< cards >}}
  {{< card link="/docs/ai/end_to_end/crisp/custom_modules" title="Model.metrics_con_matrix()" icon="back" >}}
{{< /cards >}}

<br>

{{% details title="<font color=Coral size=3>1. ***混淆矩阵***：`sklearn.metrics.confusion_matrix()` ***参数 + 案例***</font>" closed="true" %}}

<div style="font-size: 14px; color: Gray; border-left=0; border-right=0">
  <table>

|*参数*|*解释*|*取值\取值类型*|*默认值*|*是否关联*|*参数类型*|
|:-:|:-:|:-:|:-:|:-:|:-:|
|***`y_true`***|真实的标签值|一维数组||||
|***`y_pred`***|预测的标签值|一维数组||||
|`labels`|指定要包含在混淆矩阵<br>中的类别标签列表。|列表（标签列表）|||***可选***|
|`sample_weight`|设置样本的权重|一维数组|||***可选***|
|`normalize`|控制混淆矩阵是否<br>进行归一化|`None`：不进行归一化，返回原始的计数值<br>`'true'`：按真实值进行归一化<br>`'pred'`：按预测值进行归一化<br>`'all'`：按所有的值进行归一化<br>|`None`||***可选***|

  </table>
</div>

{{% details title="<font color=Gray size=3>`sklearn.metrics.confusion_matrix(y_true, y_pred)`</font>" closed="true" %}}
```python 
from sklearn.metrics import confusion_matrix
import numpy as np

y_true = np.array([2, 0, 2, 2, 0, 1])
y_pred = np.array([0, 0, 2, 2, 0, 2])

# Do not set labels
print(confusion_matrix(y_true, y_pred), '\n') 
"""
[[2 0 0]
 [0 0 1]
 [1 0 2]] 
"""
```
{{% /details %}}


{{% details title="<font color=Gray size=3>`sklearn.metrics.confusion_matrix(y_true, y_pred, labels=labels)`</font>" closed="true" %}}
```python
from sklearn.metrics import confusion_matrix
import numpy as np

y_true = np.array([2, 0, 2, 2, 0, 1])
y_pred = np.array([0, 0, 2, 2, 0, 2])

# Set labels is [0, 2]
labels = [0, 2]
print(confusion_matrix(y_true, y_pred, labels=labels), '\n')

"""
[[2 0]
 [1 2]] 
"""
```
{{% /details %}}


{{% details title="<font color=Gray size=3>`sklearn.metrics.confusion_matrix(y_true, y_pred, sample_weight=sample_weight)`</font>" closed="true" %}}
```python
from sklearn.metrics import confusion_matrix
import numpy as np

y_true = np.array([2, 0, 2, 2, 0, 1])
y_pred = np.array([0, 0, 2, 2, 0, 2])

# Set sample_weight is [0.5, 1, 0.8, 0.6, 0.7, 0.9]
sample_weight = np.array([0.5, 1, 0.8, 0.6, 0.7, 0.9])
print(confusion_matrix(y_true, y_pred, sample_weight=sample_weight), '\n')

"""
[[1.7 0.  0. ]
 [0.  0.  0.9]
 [0.5 0.  1.4]] 
"""
```
{{% /details %}}


{{% details title="<font color=Gray size=3>`sklearn.metrics.confusion_matrix(y_true, y_pred, normalize=None)`</font>" closed="true" %}}
```python
from sklearn.metrics import confusion_matrix
import numpy as np

y_true = np.array([2, 0, 2, 2, 0, 1])
y_pred = np.array([0, 0, 2, 2, 0, 2])

# Set normalize
print(confusion_matrix(y_true, y_pred, normalize=None), '\n')

"""
[[2 0 0]
 [0 0 1]
 [1 0 2]] 
"""
```
{{% /details %}}


{{% details title="<font color=Gray size=3>`sklearn.metrics.confusion_matrix(y_true, y_pred, normalize='true')`</font>" closed="true" %}}
```python
from sklearn.metrics import confusion_matrix
import numpy as np

y_true = np.array([2, 0, 2, 2, 0, 1])
y_pred = np.array([0, 0, 2, 2, 0, 2])

print(confusion_matrix(y_true, y_pred, normalize='true'), '\n')

"""
[[1.         0.         0.        ]
 [0.         0.         1.        ]
 [0.33333333 0.         0.66666667]] 
"""
```
{{% /details %}}


{{% details title="<font color=Gray size=3>`sklearn.metrics.confusion_matrix(y_true, y_pred, normalize='pred')`</font>" closed="true" %}}
```python
from sklearn.metrics import confusion_matrix
import numpy as np

y_true = np.array([2, 0, 2, 2, 0, 1])
y_pred = np.array([0, 0, 2, 2, 0, 2])

print(confusion_matrix(y_true, y_pred, normalize='pred'), '\n')

"""
[[0.66666667 0.         0.        ]
 [0.         0.         0.33333333]
 [0.33333333 0.         0.66666667]] 
"""
```
{{% /details %}}


{{% details title="<font color=Gray size=3>`sklearn.metrics.confusion_matrix(y_true, y_pred, normalize='all')`</font>" closed="true" %}}
```python
from sklearn.metrics import confusion_matrix
import numpy as np

y_true = np.array([2, 0, 2, 2, 0, 1])
y_pred = np.array([0, 0, 2, 2, 0, 2])

print(confusion_matrix(y_true, y_pred, normalize='all'), '\n')

"""
[[0.33333333 0.         0.        ]
 [0.         0.         0.16666667]
 [0.16666667 0.         0.33333333]] 
"""
```
{{% /details %}}


{{% details title="<font color=DarkCyan size=3>`mypackage.Model.metrics_con_matrix()`</font>" closed="true" %}}
```python {filename="mypackage.Model.metrics_con_matrix()"}
import warnings
warnings.filterwarnings("ignore") # Prohibit displaying unnecessary warnings

from sklearn import datasets
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LogisticRegression

# Load digits dataset
iris = datasets.load_iris()
X, y = iris.data, iris.target

# Create training and test sets
X_train, X_test, y_train, y_test = train_test_split(
    X, y, test_size=0.3, stratify = y, random_state=1)

model = LogisticRegression()
model.fit(X_train , y_train)

y_train_pre = model.predict(X_train)
y_test_pre  = model.predict(X_test)


# confusion matrix
from mypackage import Model

Model.metrics_con_matrix(y_train, y_train_pre, size=0)

"""
Estimate_confusion_matrix(
      y_train
    , y_train_pre
    , size=0
    , serif='FangSong'
    , cmap_color = ['#FFFFFF', 'DimGrey']
    , rgb_color = (237/255, 243/255, 238/255)
    )
"""
```
{{% /details %}}

{{% /details %}}





{{% details title="<font color=Coral size=3>2. ***准确率***：`sklearn.metrics.accuracy_score()` ***参数 + 案例***</font>" closed="true" %}}
|*参数*|*解释*|*取值\取值类型*|*默认值*|*是否关联*|*参数类型*|
|:-:|:-:|:-:|:-:|:-:|:-:|
|***`y_true`***|真实的标签值|||||
|***`y_pred`***|预测的标签值|||||
|`normalize`|设置输出正确比例、样本数|布尔值<br>`True`：返回比例；<br>`False`：返回样本数；|`True`||***可选***|
|`sample_weight`|设置样本的权重|根据具体的业务需求和数据特点来设置取值|||***可选***|


{{% details title="<font color=Gray size=3>`sklearn.metrics.accuracy_score(y_true, y_pred)`</font>" closed="true" %}}
```python
from sklearn.metrics import accuracy_score

y_true = [0, 1, 2, 0, 1, 2]
y_pred = [0, 1, 1, 0, 0, 2]

print(accuracy_score(y_true, y_pred))
print(accuracy_score(y_true, y_pred, normalize=True))
"""
0.6666666666666666
0.6666666666666666
"""
```
{{% /details %}}


{{% details title="<font color=Gray size=3>`sklearn.metrics.accuracy_score(y_true, y_pred, normalize=False)`</font>" closed="true" %}}
```python
from sklearn.metrics import accuracy_score

y_true = [0, 1, 2, 0, 1, 2]
y_pred = [0, 1, 1, 0, 0, 2]

# Set normalize is False
print(accuracy_score(y_true, y_pred, normalize=False))

"""
4.0
"""
```
{{% /details %}}


{{% details title="<font color=Gray size=3>`sklearn.metrics.accuracy_score(y_true, y_pred, sample_weight=sample_weight)`</font>" closed="true" %}}
```python
from sklearn.metrics import accuracy_score

y_true = [0, 1, 2, 0, 1, 2]
y_pred = [0, 1, 1, 0, 0, 2]

# Set sample_weight is [0.5, 1, 0.8, 0.6, 0.9, 0.7]
sample_weight = [0.5, 1, 0.8, 0.6, 0.9, 0.7]
print(accuracy_score(y_true, y_pred, sample_weight=sample_weight))

"""
0.6222222222222222
"""
```
{{% /details %}}

{{% /details %}}














<br><br>









#### (2). 回归


<br><br>


#### (3). 聚类



<br><br><br>



### 1.2、评估方法

<div style="font-size: 14px; border-left=0; border-right=0">
  <table>

|评估方法|简述|优点|缺点|适用情况|
|:-:|:-|:-|:-|:-|
|**留出法**|1. 拆分为训练集\测试集<br>2. 使用测试集评估模型性能<br>3. 需要调参，可拆分验证集|1. 简单、直观<br>2. 计算开销小|1. 评估结果可能不稳定<br>2. 受划分数据随机性影响较大|数据量足够大时适用|
|**交叉验证**|随机平均分成 K 份<br>选择其中 1 份为测试集<br>其余 K-1 份为训练集<br>重复 K 次得到 K 个评估结果|1. 充分利用数据<br>2. 评估结果相对稳定|计算开销较大|1. 数据量适中\较小时适用<br>2. 需要更可靠评估的情况|
|**留一法**|1. 交叉验证的特殊情况<br>2. 每次取一个样本作为测试集|1. 充分利用数据<br>2. 无偏估计|1. 计算成本高<br>2. 不一定反映真实性能|数据量较小时适用|
|**自助法**||能在数据量较小的情况下<br>产生不同的训练/测试集|改变了初始数据集的分布<br>引入估计偏差|数据量较小时适用<br>难以有效划分训练/测试集|

  </table>
</div>

<br>

#### (1). *留出法*

{{% details title="<font color=DarkCyan face=Georgia size=3>`sklearn.sklearn.model_selection.train_test_split()` —— *分层拆分训练集\测试集*</font>" closed="true" %}}
```python {linenos=table, linenostart=1}
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



{{% details title="<font color=Gray face=Georgia size=3>`df.groupby(column).sample(frac=0.7, random_state=42)` —— *分层拆分训练集\测试集*</font>" closed="true" %}}
```python {linenos=table, linenostart=1}
# Load libraries
import pandas as pd
from sklearn import datasets

# Load iris dataset
iris = datasets.load_iris()
X, y = iris.data, iris.target

df = pd.concat([pd.DataFrame(X, columns=iris.feature_names), pd.DataFrame(y, columns=['class'])]
    , axis=1)

#df.head()

# 定义分层列
stratify_column = 'class'

# 计算抽样比例（例如 50%）
sample_ratio = 0.7



part1 = df.groupby(stratify_column).sample(frac=0.7, random_state=42)
part2 = df.drop(part1.index)

print("第一部分数据：", part1.shape)
print("第二部分数据：", part2.shape, '\n')

print("第一部分数据：", part1[stratify_column].value_counts(), '\n')
print("第二部分数据：", part2[stratify_column].value_counts())

"""
第一部分数据： (105, 5)
第二部分数据： (45, 5) 

第一部分数据： class
0    35
1    35
2    35
Name: count, dtype: int64 

第二部分数据： class
0    15
1    15
2    15
Name: count, dtype: int64
"""
```

{{% /details %}}



{{% details title="<font color=Gray face=Georgia size=3>`df.sample(frac=0.7, random_state=42)` + `df[column].unique()` —— *分层拆分训练集\测试集*</font>" closed="true" %}}
```python {linenos=table, linenostart=1}
# Load libraries
import pandas as pd
from sklearn import datasets

# Load iris dataset
iris = datasets.load_iris()
X, y = iris.data, iris.target

df = pd.concat([pd.DataFrame(X, columns=iris.feature_names), pd.DataFrame(y, columns=['class'])]
    , axis=1)

#df.head()

# 定义分层列
stratify_column = 'class'

# 计算抽样比例（例如 50%）
sample_ratio = 0.7



part1 = df.groupby(stratify_column).sample(frac=0.7, random_state=42)
part2 = stratum_df.drop(part1.index)

print("第一部分数据：", part1.shape)
print("第二部分数据：", part2.shape, '\n')

print("第一部分数据：", part1[stratify_column].value_counts(), '\n')
print("第二部分数据：", part2[stratify_column].value_counts())

"""
第一部分数据： (105, 5)
第二部分数据： (45, 5) 

第一部分数据： class
0    35
1    35
2    35
Name: count, dtype: int64 

第二部分数据： class
0    15
1    15
2    15
Name: count, dtype: int64
"""
```

{{% /details %}}



{{% details title="<font color=DarkCyan face=Georgia size=3>`sklearn.sklearn.model_selection.train_test_split()` + `sklearn.pipeline.Pipeline()` </font>" closed="true" %}}
```python {linenos=table, linenostart=1}
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

{{% details title="<font color=Gray face=Georgia size=3>`sklearn.model_selection.KFold()` —— *K 折交叉验证*</font>" closed="true" %}}
```python {linenos=table, linenostart=1}
# Load libraries
from sklearn import datasets
from sklearn.model_selection import KFold
from sklearn.linear_model import LogisticRegression
from sklearn.metrics import accuracy_score

# Load iris dataset
iris = datasets.load_iris()
X, y = iris.data, iris.target

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



{{% details title="<font color=Gray face=Georgia size=3>`sklearn.model_selection.cross_val_score()` —— *K 折交叉验证*</font>" closed="true" %}}
```python {linenos=table, linenostart=1}
# Load libraries
from sklearn import datasets
from sklearn.linear_model import LogisticRegression
from sklearn.model_selection import cross_val_score

# Load iris dataset
iris = datasets.load_iris()
X, y = iris.data, iris.target

model = LogisticRegression(max_iter=1000)

print(cross_val_score(model, X, y, cv=5, scoring="accuracy"))

'''
[0.92222222 0.87222222 0.94150418 0.93871866 0.89693593]
'''
```
{{% /details %}}



{{% details title="<font color=DarkCyan face=Georgia size=3>cross_val_score  VS  KFold </font>" closed="true" %}}

<div style="font-size: 14px; color: Gray; border-left=0; border-right=0">
  <table>

|*函数*|*简述*|*适用情况*|
|:-:|:-:|:-|
|***`KFold`***|它主要用于手动控制交叉验证的分割过程，<br>你可以根据 KFold 的分割结果，<br>自行实现模型的训练和评估逻辑。|1. 当你需要对交叉验证的分割过程有更精细的控制；<br>2. 结合其他复杂的流程或算法，需要灵活处理交叉验证的各个折；|
|***`cross_val_score`***|一个方便的函数，它接受一个模型、数据集<br>和交叉验证策略（如 KFold ），自动完成<br>交叉验证的过程，并返回每个折的评估分数|1. 快速进行交叉验证评估，无需手动编写复杂的循环和评估逻辑；<br>2. 只想获取交叉验证的评估分数，而不需要深入控制每个折的具体操作|

  </table>
</div>

> - 总的来说，***`cross_val_score`*** 和 ***`KFold`*** 都能进行交叉验证，前者提供了更快捷的方式，后者则提供了更高的灵活性。可以根据实际的需求选择使用哪一个。
{{% /details %}}


{{% details title="<font color=DarkCyan face=Georgia size=3>**`sklearn.model_selection.KFold()`** + **`.cross_val_score()`** —— *K 折交叉验证*</font>" closed="true" %}}
```python {linenos=table, linenostart=1}
# Load libraries
from sklearn import datasets

from sklearn.pipeline import make_pipeline
from sklearn.preprocessing import StandardScaler
from sklearn.model_selection import KFold, cross_val_score
from sklearn.linear_model import LogisticRegression


# Load iris dataset
iris = datasets.load_iris()
X, y = iris.data, iris.target

# Create a pipeline that standardizes, then runs logistic regression
pipeline = make_pipeline(
      StandardScaler()
    , LogisticRegression()
    )

# Create k-fold cross-validation
kf = KFold(
      n_splits=5
    , shuffle=True # 数据是独立且相同分布的,分配到褶皱时，打乱观测结果
    , random_state=0
    )

# Conduct k-fold cross-validation
cv_results = cross_val_score(
      pipeline  # Pipeline
    , X         # Feature matrix
    , y         # Target vector
    , cv=kf 
    , scoring="accuracy"    # Performance metric
    , n_jobs=-1             # Use all available CPU cores for parallel computing
    ) 

# Calculate mean
print(cv_results.mean())
# View score for all 5 folds
print(cv_results)



# 使用整个数据集进行训练
pipeline.fit(X, y)

# 进行预测
target_pre = pipeline.predict(X)

'''
0.9677329000309502
[0.96111111 0.95833333 0.97771588 0.96935933 0.97214485]
'''
```
{{% /details %}}


{{% details title="<font color=DarkCyan face=Georgia size=3>**`sklearn.model_selection.StratifiedKFold()`** —— *分层 K 折交叉验证*</font>" closed="true" %}}
```python {linenos=table, linenostart=1}
from sklearn.model_selection import StratifiedKFold
from sklearn.datasets import make_classification
from sklearn.linear_model import LogisticRegression
from sklearn.metrics import accuracy_score

# 生成一个二分类数据集
X, y = make_classification(
    n_samples=100, n_features=20, n_informative=2, n_redundant=10, random_state=42)

# 实例化分层 k-fold 对象
skf = StratifiedKFold(n_splits=10)

accuracies = []

# 使用分层k-fold
for train_index, test_index in skf.split(X, y):
    X_train, X_test = X[train_index], X[test_index]
    y_train, y_test = y[train_index], y[test_index]

    # 拟合逻辑回归模型
    model = LogisticRegression(random_state=42)
    model.fit(X_train, y_train)

    # 预测测试集
    y_pred = model.predict(X_test)

    # 计算准确率并添加到列表
    accuracy = accuracy_score(y_test, y_pred)
    accuracies.append(accuracy)

# 计算平均准确率
average_accuracy = sum(accuracies) / len(accuracies)
print(f'平均准确率：{average_accuracy}')

"""
平均准确率：0.9800000000000001
"""
```

> 以上代码，设置了按照目标变量 `y` 取值进行分层，然后拆分 10 折进行交叉验证，每一折的分层都与 `y` 一致，可以修改分层变量 `category_column`，如下：

```python {linenos=table, linenostart=1}
for train_index, test_index in skf.split(X, category_column):
    X_train, X_test = X[train_index], X[test_index]
    y_train, y_test = y[train_index], y[test_index]
```
{{% /details %}}


{{% details title="<font color=DarkCyan face=Georgia size=3>**`sklearn.model_selection.GroupKFold()`** —— *分组交叉验证*</font>" closed="true" %}}
```python {linenos=table, linenostart=1}
from sklearn.model_selection import GroupKFold

X = ... # 输入特征
y = ... # 目标变量
groups = ... # 数据的组标签

gkf = GroupKFold(n_splits=5)

for train_index, test_index in gkf.split(X, y, groups=groups):
    X_train, X_test = X[train_index], X[test_index]
    y_train, y_test = y[train_index], y[test_index]
    # 其余的模型训练和评估步骤与常规交叉验证相同
```

```python {linenos=table, linenostart=1}
from sklearn import datasets
from sklearn.model_selection import GroupKFold
from sklearn.linear_model import LogisticRegression
from sklearn.metrics import accuracy_score
import numpy as np
import random

# 设置随机种子
np.random.seed(42)
random.seed(42)

# 加载鸢尾花数据集
iris = datasets.load_iris()
X, y = iris.data, iris.target

# 假设我们用一个随机生成的整数序列作为分组标签，实际应用中应根据具体情况设置合理的分组标签
groups = np.random.randint(0, 3, size=len(y))

# 创建逻辑回归模型
model = LogisticRegression(max_iter=1000)

# 创建分组 K 折交叉验证对象
gkf = GroupKFold(n_splits=len(np.unique(y)))

# 进行交叉验证
for train_index, test_index in gkf.split(X, y, groups=groups):
    X_train, X_test = X[train_index], X[test_index]
    y_train, y_test = y[train_index], y[test_index]

    model.fit(X_train, y_train)
    predictions = model.predict(X_test)
    accuracy = accuracy_score(y_test, predictions)
    print(f"Fold accuracy: {accuracy}")

"""
Fold accuracy: 0.9464285714285714
Fold accuracy: 0.9583333333333334
Fold accuracy: 1.0
"""
```

> 这里使用 ```GroupKFold``` 按照目标变量 `y` 进行分组交叉验证。修改一下代码，可以设置使用需要的分类特征进行分组验证：

```python {linenos=table, linenostart=1}
# 假设我们用一个随机生成的整数序列作为分组标签，实际应用中应根据具体情况设置合理的分组标签
groups = np.random.randint(0, 3, size=len(y))

# 创建分组 K 折交叉验证对象
gkf = GroupKFold(n_splits=len(np.unique(y)))
```

{{% /details %}}






<br><br>


#### (3). 留一法

{{< callout >}}
  ***留一法***（Leave-One-Out，LOO）是一种特殊的交叉验证方法。
{{< /callout >}}

{{% details title="<font color=Gray face=Georgia size=3>`sklearn.model_selection.LeaveOneOut()` + `cross_val_score()` —— *留一法*</font>" closed="true" %}}
```python {linenos=table, linenostart=1}

# Load libraries
from sklearn import datasets
from sklearn.model_selection import LeaveOneOut
from sklearn.model_selection import cross_val_score
from sklearn.linear_model import LogisticRegression

# Load iris dataset
iris = datasets.load_iris()
X, y = iris.data, iris.target

loocv = LeaveOneOut()
model = LogisticRegression(max_iter=1000)
results = cross_val_score(model, X, y, cv=loocv) 

print(("Accuracy: %.3f%% (%.3f%%)") % (results.mean()*100.0, results.std()*100.0))
"""
Accuracy: 96.667% (17.951%)
"""
```
{{% /details %}}



<br><br>



#### (4). 自助法



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
