---
title: 【4】数据准备
weight: 4
#next: /step1
#prev: /docs
editURL: "https://example.com/edit/this/page"
toc: true
math: true
---

<br>

## 1、主要内容：

***1. 预处理***：大部分原始数据未被处理，是不完整且含有噪声的。预处理步骤是将所选数据转换为可以处理的表单。
> ***以下是一些数据常见问题：***
> - 过时和坈余字；
> - 缺失值；
> - 异常值/离群值；
> - 其形式不适合数据挖掘模型的数据；
> - 与策略或常识不一致的值。 

> ***两个常见的数据预处理内容是：*** 
> - ***数据清理*** ：删除或修复缺失（重复\异常\不一致\不规范等）的数据。此外，某些属性中可能存在敏感信息，这些属性可能需要匿名化或从数据中完全删除。
> - ***数据转换***： 通过使用缩放、属性分解和属性聚合工程，转换准备好用于学习的预处理数据。

<br>

***2. 特征工程***：选择或重塑对分析问题有用的特征，可以提高分析准确率。
> - ***特征提取***：转换特征集，得到一个新的特征集，仍然保留了大部分信息。生成的新特征将无法被人类解释。
> - ***特征选择***：删除不重要的特征，但保留了其他特征的当前状态。在分析过程中可以完全被人类解释。

<br><br><br>


## 2、预处理

### 2.1、初步整理：

{{% details title="<font color=Gray size=3>1. ***重新设置行索引***：`df.set_index(dataframe['Name'])`</font>" closed="true" %}}
```python {linenos=table, linenostart=1}
import numpy as np
import pandas as pd

data = {
    'ID': [1,2,3,4,5,6]
    ,'Name': ['Alice', 'Bob', 'Charlie', 'Wu', 'Zhang', 'Wang']
    ,'City': ['New York', 'London', 'Paris', 'new york', 'PAR', 'China']
    ,'Age': [25, 30, 35, 25, 30, 35]
    ,'Income': [50000, 60000, 70000, 40000, 30000, 90000]
}

df = pd.DataFrame(data)
df
```

|    |   ID | Name    | City     |   Age |   Income |
|---:|-----:|:--------|:---------|------:|---------:|
|  0 |    1 | Alice   | New York |    25 |    50000 |
|  1 |    2 | Bob     | London   |    30 |    60000 |
|  2 |    3 | Charlie | Paris    |    35 |    70000 |
|  3 |    4 | Wu      | new york |    25 |    40000 |
|  4 |    5 | Zhang   | PAR      |    30 |    30000 |
|  5 |    6 | Wang    | China    |    35 |    90000 |

```python {linenos=table, linenostart=1}
df = df.set_index(df['ID'])
df = df.drop('ID', axis=1)
df
```

|   ID | Name    | City     |   Age |   Income |
|-----:|:--------|:---------|------:|---------:|
|    1 | Alice   | New York |    25 |    50000 |
|    2 | Bob     | London   |    30 |    60000 |
|    3 | Charlie | Paris    |    35 |    70000 |
|    4 | Wu      | new york |    25 |    40000 |
|    5 | Zhang   | PAR      |    30 |    30000 |
|    6 | Wang    | China    |    35 |    90000 |
{{% /details %}}

<br>

{{% details title="<font color=Gray size=3>2. ***通过索引修改值***：`df.iloc[0,0]='new_value'`</font>" closed="true" %}}
```python {linenos=table, linenostart=1}
# 通过索引修改值
df.iloc[0,0]='《China》'
df
```

|   ID | Name      | City     |   Age |   Income |
|-----:|:----------|:---------|------:|---------:|
|    1 | 《China》 | New York |    25 |    50000 |
|    2 | Bob       | London   |    30 |    60000 |
|    3 | Charlie   | Paris    |    35 |    70000 |
|    4 | Wu        | new york |    25 |    40000 |
|    5 | Zhang     | PAR      |    30 |    30000 |
|    6 | Wang      | China    |    35 |    90000 |
{{% /details %}}



{{% details title="<font color=Gray size=3>3. ***通过标签修改值***：`df.loc[2,'Column_Name']='new_value'`</font>" closed="true" %}}
```python {linenos=table, linenostart=1}
# 通过标签修改值
df.loc[2,'Name']='《Bob》'
df
```

|   ID | Name      | City     |   Age |   Income |
|-----:|:----------|:---------|------:|---------:|
|    1 | 《China》 | New York |    25 |    50000 |
|    2 | 《Bob》   | London   |    30 |    60000 |
|    3 | Charlie   | Paris    |    35 |    70000 |
|    4 | Wu        | new york |    25 |    40000 |
|    5 | Zhang     | PAR      |    30 |    30000 |
|    6 | Wang      | China    |    35 |    90000 |
{{% /details %}}



{{% details title="<font color=Gray size=3>4. ***通过替换修改值***：`df\df[].replace(replace_value, replace_to, inplace=True)`</font>" closed="true" %}}
```python {linenos=table, linenostart=1}
# 单个列，单个值，替换
def replace_value_one_to_one(df, column, replace_value, replace_to):
    df[column].replace(replace_value, replace_to, inplace=True)
    return df

# 单个列，多个值，替换
def replace_value_more_to_one(df, column, replace_value_array, replace_to):
    for i in replace_value_array:
        df[column].replace(i, replace_to, inplace=True)
    return df

# 全部列，单个值/多个值，替换
def replace_value_df(df, replace_value_array, replace_to):
    for i in replace_value_array:
        df.replace(i, replace_to, inplace=True)
    return df


df = replace_value_one_to_one(df, 'Name', 'Charlie', '《Zuo》')
df
```

|   ID | Name      | City     |   Age |   Income |
|-----:|:----------|:---------|------:|---------:|
|    1 | 《China》 | New York |    25 |    50000 |
|    2 | 《Bob》   | London   |    30 |    60000 |
|    3 | 《Zuo》   | Paris    |    35 |    70000 |
|    4 | Wu        | new york |    25 |    40000 |
|    5 | Zhang     | PAR      |    30 |    30000 |
|    6 | Wang      | China    |    35 |    90000 |

{{% /details %}}

<br>

{{% details title="<font color=Gray size=3>5. ***修改多个列名称***：`df.rename(columns={'col1':'new_name1', 'col2':'new_name2'}, inplace=True)`</font>" closed="true" %}}
```python {linenos=table, linenostart=1}
df.rename(columns={'Name':'name', 'City':'city'}, inplace=True)
```

|   ID | 《name》   | 《city》   |   Age |   Income |
|-----:|:-----------|:-----------|------:|---------:|
|    1 | 《China》  | New York   |    25 |    50000 |
|    2 | 《Bob》    | London     |    30 |    60000 |
|    3 | 《Zuo》    | Paris      |    35 |    70000 |
|    4 | Wu         | new york   |    25 |    40000 |
|    5 | Zhang      | PAR        |    30 |    30000 |
|    6 | Wang       | China      |    35 |    90000 |
{{% /details %}}



{{% details title="<font color=Gray size=3>6. ***修改全部列名称***：`df.columns = ['', '',...]`</font>" closed="true" %}}
```python {linenos=table, linenostart=1}
name = ['name', 'city', 'age', 'income']
df.columns = name
df
```

|   ID | name      | city     |   age |   income |
|-----:|:----------|:---------|------:|---------:|
|    1 | 《China》 | New York |    25 |    50000 |
|    2 | 《Bob》   | London   |    30 |    60000 |
|    3 | 《Zuo》   | Paris    |    35 |    70000 |
|    4 | Wu        | new york |    25 |    40000 |
|    5 | Zhang     | PAR      |    30 |    30000 |
|    6 | Wang      | China    |    35 |    90000 |
{{% /details %}}

<br>

{{% details title="<font color=Gray size=3>7. ***修改列数据类型***：`df1['age'].astype('object')`、`df.astype({'col1':'int32'})`</font>" closed="true" %}}
```python {linenos=table, linenostart=1}
df1 = df.copy()

df1['age'] = df1['age'].astype('object')
# 修改多列数据类型
# df.astype({'col1':'int32'}) # 指定字段转指定类型

df['age'].info(), df1['age'].info()
```

```small
<class 'pandas.core.series.Series'>
Index: 6 entries, 1 to 6
Series name: age
Non-Null Count  Dtype
--------------  -----
6 non-null      int64
dtypes: int64(1)
memory usage: 268.0 bytes

<class 'pandas.core.series.Series'>
Index: 6 entries, 1 to 6
Series name: age
Non-Null Count  Dtype 
--------------  ----- 
6 non-null      object
dtypes: object(1)
memory usage: 268.0+ bytes
```
{{% /details %}}

<br>

{{% details title="<font size=3>8. ***Pandas 管道整理***：`df.pipe().pipe()...`</font>" closed="true" %}}
```python {linenos=table, linenostart=1}
# DataFrame column value replacement
# ------------------------------------------------------------

# 单个列，单个值，替换
def replace_value_one_to_one(df, column, replace_value, replace_to):
    df[column].replace(replace_value, replace_to, inplace=True)
    return df

# 单个列，多个值，替换
def replace_value_more_to_one(df, column, replace_value_array, replace_to):
    for i in replace_value_array:
        df[column].replace(i, replace_to, inplace=True)
    return df

# 全部列，单个值/多个值，替换
def replace_value_df(df, replace_value_array, replace_to):
    for i in replace_value_array:
        df.replace(i, replace_to, inplace=True)
    return df

# DataFrame modifies the feature name
# ------------------------------------------------------------

# 修改特征名称
def replace_column(df, columns):
    #df.rename(columns={'col_name1':'new_name1','col_name2':'new_name2'},inplace=True)
    df.rename(columns = columns, inplace=True) #
    return df

```

```python {linenos=table, linenostart=1}
df_result = (
    df.pipe(replace_value_more_to_one, 'City', ['New York','new york'], 'NY')
      .pipe(replace_value_df, ['China'], 'Good')  
      .pipe(replace_column, {'Name':'姓名','City':'城市'})
    )
df_result
```
{{% /details %}}



<br><br><br>



### 2.2、数据清理：

#### (1). 重复值：

|*方法*|*优点*|*确点*|
|:-:|:-:|:-:|
|***标记***|1. 保留了数据的完整性，您可以直观地看到哪些行是重复的，同时保留了所有原始数据以便进行进一步的分析或比较。<br><br>2. 有助于理解数据的分布和重复模式，可能会发现一些潜在的规律或问题。|1. 数据量较大时，增加了数据的复杂性和存储空间。<br><br>2. 如果后续的分析或处理不需要关注重复值的标记，那么这些标记可能会造成干扰。|
|***删除***|1. 可以减少数据量，提高数据处理和分析的效率，特别是在处理大规模数据时。<br><br>2. 使数据更加简洁和清晰，避免重复值可能带来的混淆和错误。|1. 可能会丢失一些信息，尤其是在不确定重复值的含义和重要性时。<br><br>2. 如果删除操作有误，可能无法恢复原始的完整数据。|

<br>

{{% details title="<font color=Gray size=3>1. *标记重复值：* `df.duplicated()`</font>" closed="true" %}}
```python {linenos=table, linenostart=1}
import pandas as pd

# 假设我们有一个 DataFrame
data = {'A': [1, 2, 2, 3, 3, 3],
        'B': ['a', 'b', 'b', 'c', 'c', 'c']}
df = pd.DataFrame(data)

# 使用 duplicated 方法标记重复值
df['is_duplicated'] = df.duplicated()

df
```
{{% /details %}}



{{% details title="<font color=Gray size=3>2. *删除重复值：* `df.drop_duplicates()`</font>" closed="true" %}}
```python {linenos=table, linenostart=1}
# Drop duplicates
dataframe.drop_duplicates()
dataframe.drop_duplicates(keep='first')  # 保留首次出现的重复行，默认值
dataframe.drop_duplicates(keep='last')  # 保留最后一次出现的重复行

dataframe.drop_duplicates(subset=['Sex'])
dataframe.drop_duplicates(subset=['Sex'], keep='last')
```
{{% /details %}}



<br><br>



#### (2). 缺失值：

|方法|	优点|	缺点|	适用情况|
|:-----:|:-:|:-:|:-:|
|***删除***|简单直接，不需要进行复杂的处理|可能会丢失大量有价值的信息，减少了样本量，可能影响模型的准确性和稳定性|缺失值的比例较小，且数据量较大，缺失值的分布是随机的，且与其他变量没有明显的关联|
|***填充***|保留了更多的数据，避免了因删除数据而导致的信息丢失|填充的值可能不准确，引入一定的偏差，填充方法的选择可能会对结果产生影响|缺失值的比例适中，且数据的特征对模型较为重要，可以根据数据的分布和特征选择合适的填充方法|
|***预测***|利用已有数据的模式和关系来推测缺失值，可能更准确|计算成本较高，需要建立预测模型，预测模型可能存在过拟合或欠拟合的风险|缺失值与其他变量存在较强的相关性，可以建立有效的预测模型，对数据的准确性要求较高，且有足够的计算资源和数据来训练预测模型|
|***标记***|保留了原始数据的完整性，同时明确标识了缺失值|可能需要对模型进行特殊处理，以适应标记后的缺失值|希望在后续的分析中明确考虑缺失值的存在及其影响，数据的缺失具有特殊的意义或模式，需要单独分析|

<br>

{{% details title="<font color=Gray size=3>1. *查看*：`df.isnull().sum()\.any()\.all()`</font>" closed="true" %}}
```python {linenos=table, linenostart=1}
import pandas as pd

df = pd.read_csv('datasets/titanic/train.csv')

# --------------------------------------------------------------------------------
df.isnull()
df.isnull().sum()
df.isnull().sum().sum()
df.isnull().any()
df.isnull().all()
```
{{% /details %}}



{{% details title="<font color=Gray size=3>2. *可视化*：`missingno.bar(df)`，`missingno.matrix(df)`</font>" closed="true" %}}
- https://github.com/ResidentMario/missingno
```python {linenos=table, linenostart=1}
import pandas as pd

train = pd.read_csv('datasets/titanic/train.csv')
df = train.copy()
df.head()

# --------------------------------------------------------------------------------
import missingno as msno
import matplotlib.pyplot as plt

plt.rcParams['font.sans-serif']=['FangSong']  # 替换sans-serif字体，正常显示中文(黑体)\'SimHei'\'FangSong' 

# 绘制非缺失值条形图
msno.bar(df)

fig = plt.gcf() # 获取当前图形
fig.set_dpi(60) # 降低分辨率，例如设置为 60

plt.show()
```

```python {linenos=table, linenostart=1}
import missingno as msno
import matplotlib.pyplot as plt

plt.rcParams['font.sans-serif']=['FangSong']  # 替换sans-serif字体，正常显示中文(黑体)\'SimHei'\'FangSong' 

# 矩阵可视化,解缺失的数据是如何通过数据分布的,即它们是局部的还是均匀分布的，
# 或者是否存在任何模式和许多此类问题。
msno.matrix(df)

fig = plt.gcf() # 获取当前图形
fig.set_dpi(60) # 降低分辨率，例如设置为 60

# 或者直接保存图形时设置分辨率和大小
plt.savefig('missingno_matrix.png')  # 保存为 PNG 格式，调整分辨率和裁剪空白
plt.show()
```
{{% /details %}}



{{% details title="<font color=Gray size=3>3. *删除*：`df.dropna()`，`df.drop([''], axis=1)`</font>" closed="true" %}}
```python {linenos=table, linenostart=1}
df.dropna()

df.drop([''], axis=1)
```
{{% /details %}}



{{% details title="<font color=Gray size=3>4. *填充*：`df.fillna()`</font>" closed="true" %}}
```python {linenos=table, linenostart=1}
# 用特定值填充
data_fill_constant = data.fillna(0)  

# 用均值填充
data_fill_mean = data.fillna(data.mean())  

# 用前一个非缺失值填充
data_fill_forward = data.fillna(method='ffill')  

# 用后一个非缺失值填充
data_fill_backward = data.fillna(method='bfill')  
```
{{% /details %}}



{{% details title="<font color=Gray size=3>5. *填充*：`sklearn.impute.SimpleImputer()`</font>" closed="true" %}}
```python {linenos=table, linenostart=1}
from sklearn.impute import SimpleImputer
import pandas as pd
import numpy as np

# 示例数据
data = {'NumericColumn': [1, 2, np.nan, 4, 5],
        'CategoricalColumn': ['A', np.nan, 'A', 'B', 'B']}
df = pd.DataFrame(data)

# 数值变量的均值填充
num_imputer = SimpleImputer(strategy='mean')
df['NumericColumn'] = num_imputer.fit_transform(df[['NumericColumn']]).ravel()  # 使用 ravel 函数将二维数组转换为一维

# 分类变量的众数填充
cat_imputer = SimpleImputer(strategy='most_frequent')
df['CategoricalColumn'] = cat_imputer.fit_transform(df[['CategoricalColumn']]).ravel()  # 使用 ravel 函数将二维数组转换为一维

df
```
{{% /details %}}



{{% details title="<font color=Gray size=3>6. *标记*：`data['A_is_missing'] = data['A'].isnull()`</font>" closed="true" %}}
```python {linenos=table, linenostart=1}
data['A_is_missing'] = data['A'].isnull()
```
{{% /details %}}



<br><br>



#### (3). 异常值：



<br><br><br>



### 2.3、数据转换：

#### (1). 标准化：


<br><br>


#### (2). 非线性变换：


<br><br>



#### (3). 离散化：


<br><br>



<br><br><br>



## 3、特征工程

### 3.1、特征选择

|*特征选择方法*|*优点*|*缺点*|
|:--:|:--|:--|
|*过滤方法（Filter）*|1. 算效率高，因为它独立于后续的学习算法，不需要多次运行学习算法来评估特征子集。<br><br>2. 可以快速处理高维数据，对大型数据集较为适用。<br><br>3. 基于数据的一般特征（如相关性、方差等）进行选择，具有较好的通用性。|1. 没有考虑特征之间的相互关系，可能会忽略一些对模型有协同作用的特征组合。<br><br>2. 所选特征子集可能不是针对特定学习算法的最优选择，因为没有直接基于模型的性能来评估特征。|
|*包装方法（Wrapper）*|1. 直接基于特定学习算法的性能来选择特征，通常能找到对给定模型性能最优的特征子集。<br><br>2. 考虑了特征之间的相互作用。|1. 计算成本高，因为需要多次训练学习算法来评估不同的特征子集。<br><br>2. 容易过拟合，可能会选择出过于针对特定训练集的特征子集，导致在新数据上的泛化能力不佳。<br><br>3. 对于高维数据，搜索空间过大，计算复杂度难以承受。|
|*嵌入方法（Embedded）*|1. 在学习模型的过程中同时进行特征选择，效率相对较高。<br><br>2. 考虑了特征与模型的相关性，能够选择出对模型有重要影响的特征。<br><br>3. 可以处理高维数据，并且在一定程度上避免了过拟合。|1. 特征选择的过程可能不够直观，难以解释。<br><br>2. 对于某些复杂的嵌入方法，可能需要较多的计算资源和调参工作。|


<br><br>


#### (1). 过滤方法(Filter)


<br><br>


#### (2). 包装方法(Wrapper)


<br><br>


#### (3). 嵌入方法(Embedded)


<br><br>


### 3.2、特征提取



<br><br><br>



## 4、流水线

### 4.1、自定义删除列

{{% details title="<font color=Gray size=3>1. *导入数据：*</font>" closed="true" %}}
```python {linenos=table, linenostart=1}
import numpy as np
import pandas as pd

train = pd.read_csv('datasets/titanic/train.csv')
data = train.loc[:,['PassengerId', 'Survived', 'Pclass', 'Sex', 'Age', 'Fare', 'Embarked']]
data.head()
```
{{% /details %}}

{{% details title="<font color=Gray size=3>2. *拆分训练集\测试集：*</font>" closed="true" %}}
```python {linenos=table, linenostart=1}
df = data.copy()
X = df.drop('Survived', axis=1)
y = df['Survived']

from sklearn.model_selection import train_test_split

X_train, X_test, y_train, y_test = train_test_split(
    X, y, test_size=0.3, random_state=12, stratify=y)
```
{{% /details %}}

{{% details title="<font color=Gray size=3>3. *通过 Sklearn 自定义类，删除变量：*</font>" closed="true" %}}
```python {linenos=table, linenostart=1}
from sklearn.base import BaseEstimator, TransformerMixin

class DropSpecifiedColumns(BaseEstimator, TransformerMixin):
    def __init__(self, columns_to_drop):
        self.columns_to_drop = columns_to_drop

    def fit(self, X, y=None):
        return self

    def transform(self, X):
        return X.drop(columns=self.columns_to_drop)
```
{{% /details %}}

{{% details title="<font color=Gray size=3>4. *直接使用 Sklearn 自定义的删除变量类：*</font>" closed="true" %}}
```python {linenos=table, linenostart=1}
columns_to_drop = ['PassengerId']

transformer = DropSpecifiedColumns(columns_to_drop)
transformer.fit(X_train)
X_train_pre = transformer.transform(X_train)
X_test_pre  = transformer.transform(X_test)
X_train_pre.head()
```
{{% /details %}}

{{% details title="<font color=Gray size=3>5. *将 Sklearn 自定义的删除变量类加入到 Sklearn 流水线 Pipeline 中：*</font>" closed="true" %}}
```python {linenos=table, linenostart=1}
columns_to_drop = ['PassengerId']


from sklearn.pipeline import Pipeline

# 创建流水线
pipe = Pipeline([
    ('DropSpecifiedColumns', DropSpecifiedColumns(columns_to_drop))
])

pipe.fit(X_train, y_train)

X_train_pre = pipe.transform(X_train)
X_test_pre  = pipe.transform(X_test)

X_test_pre.head()
```
{{% /details %}}

{{% details title="<font color=Gray size=3>6. *选择 Sklearn 流水线中的一个类：删除变量，单独执行并查看结果*</font>" closed="true" %}}
> 流水线里面有很多步骤，需要单独查看流水线的一部分执行结果，或是一个结果
```python {linenos=table, linenostart=1}
pipe_DropSpecifiedColumns = pipe['DropSpecifiedColumns']

#X_train_pre = pipe_DropSpecifiedColumns.fit_transform(X_train)

pipe_DropSpecifiedColumns.fit(X_train, y_train)
X_train_pre = pipe_DropSpecifiedColumns.transform(X_train)
X_test_pre  = pipe_DropSpecifiedColumns.transform(X_test)

X_test_pre.head()
```
{{% /details %}}


<br><br>


### 4.2、自定义删除缺失值的列

{{% details title="<font color=Gray size=3>1. *通过 Sklearn 自定义类，删除含有缺失值的变量：*</font>" closed="true" %}}
```python {linenos=table, linenostart=1}
import pandas as pd
from sklearn.base import BaseEstimator, TransformerMixin

class DropColumnsWithMissing(BaseEstimator, TransformerMixin):
    def __init__(self, threshold=0):
        self.threshold = threshold

    def fit(self, X, y=None):
        return self

    def transform(self, X):
        num_missing = X.isnull().sum()
        columns_to_drop = num_missing[num_missing > self.threshold].index
        return X.drop(columns=columns_to_drop)
```
{{% /details %}}



<br><br>



### 4.3、自定义填充缺失值

{{% details title="<font color=Gray size=3>1. *通过 Sklearn 自定义类，填充缺失值：*</font>" closed="true" %}}
```python {linenos=table, linenostart=1}
from sklearn.impute import SimpleImputer
from sklearn.base import BaseEstimator, TransformerMixin
import pandas as pd

class MissingValueFiller(BaseEstimator, TransformerMixin):
    def fit(self, X, y=None):
        return self

    def transform(self, X):
        num_columns = X.select_dtypes(include=['number']).columns
        cat_columns = X.select_dtypes(include=['object']).columns

        # 数值列使用均值填充
        for col in num_columns:
            X[col].fillna(X[col].mean(), inplace=True)

        # 分类列使用众数填充
        for col in cat_columns:
            X[col].fillna(X[col].mode()[0], inplace=True)

        return X
```
{{% /details %}}

{{% details title="<font color=Gray size=3>2. *将 Sklearn 自定义的填充缺失值类加入到 Sklearn 流水线 Pipeline 中：*</font>" closed="true" %}}
```python {linenos=table, linenostart=1}
columns_to_drop = ['PassengerId']

from sklearn.pipeline import Pipeline

# 创建流水线
preprocessing_pipeline = Pipeline([
     ('DropSpecifiedColumns', DropSpecifiedColumns(columns_to_drop))
    ,('MissingValueFiller', MissingValueFiller())
])

preprocessing_pipeline.fit(X_train, y_train)

X_train_pre = preprocessing_pipeline.transform(X_train)
X_test_pre  = preprocessing_pipeline.transform(X_test)

X_test_pre.head()
```

```python {linenos=table, linenostart=1}
X_train_pre.isnull().sum(), X_test_pre.isnull().sum()
```
{{% /details %}}



<br><br>





















