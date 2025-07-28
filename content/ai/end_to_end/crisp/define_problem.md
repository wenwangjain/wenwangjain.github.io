---
title: 1️⃣ 业务/研究理解
weight: 1141
prev: /end_to_end
type: "docs" 
toc: true
math: true
---


## 1、定义问题

1. 问题是什么？
2. 为什么需要解决问题？
3. 探索如何解决问题？

<br>

### 1.1、问题是什么？

1. 简单描述问题;
2. 定义问题目标; (主要目标，次要目标)
3. 解决问题方案; (假设列表，算法列表; 评价指标; 展示方案，……)
4. 查看相似项目;

> 例如，展示方案如下：
> - 编写分析报告展示你的结果；
> - 使用 Streamlit 开发一个 demo 展示模型；
> - 部署模型，并托管，监控……
> - 部署到移动设备，或其他电子元实现智能化

<br>

### 1.2、为什么需要解决问题？

1. 练习；不需要使用最合适的算法，而是想探索不熟悉的算法，学习新技能；
2. 工作；解决工作中的数据分析问题；
3. 竞赛；获取良好的排名，提升知名度，获取奖金。


<br>

### 1.3、探索如何解决问题？

1. 现有：逐步列出您将收集哪些数据？<br>
   —> 现有数据范围有多大（存储地址\数据量）？<br>
   —> 都是什么样的（数据质量）？<br>
   —> 能不能解决我们的问题？<br>
   
3. 期望：希望拥有哪些数据？能否获取到这些数据？
4. 尝试：使用已经收集的数据解决现有问题，验证假设列表；

<br>

{{< callout emoji=📝 type='default' >}}
参考网址\书籍：
1. https://machinelearningmastery.com/how-to-define-your-machine-learning-problem/
{{< /callout >}}








#### 2.1.5、导入数据

{{< tabs items="1️⃣ 字典, 2️⃣ 列表, 3️⃣ sklearn, 4️⃣ .csv, 5️⃣ .xlsx, 6️⃣ 数据库" >}}
  {{< tab >}}
通过 `pd.DataFrame()` 函数将字典转换为数据框格式。

```python
import numpy as np
import pandas as pd

directory = {
    "A": 1.0,
    "B": pd.Timestamp("20130102"),
    "C": pd.Series(1, index=list(range(4)), dtype="float32"),
    "D": np.array([3] * 4, dtype="int32"),
    "E": pd.Categorical(["test", "train", "test", "train"]),
    "F": "foo",
}

df2 = pd.DataFrame(directory)
df2
```

| A      | B           | C      | D | E     | F   |
|--------|-------------|--------|---|-------|-----|
| $1.00  | 2013-01-02  | $1.00  | 3 | test  | foo |
| $1.00  | 2013-01-02  | $1.00  | 3 | train | foo |
| $1.00  | 2013-01-02  | $1.00  | 3 | test  | foo |
| $1.00  | 2013-01-02  | $1.00  | 3 | train | foo |
  {{< /tab >}}



  {{< tab >}}
通过 `pd.DataFrame()` 函数将列表转换为数据框格式。

```python
import numpy as np
import pandas as pd

dates = pd.date_range("20130101", periods=6)

df = pd.DataFrame(
    np.random.randn(6, 4) 
    ,index=dates           
    ,columns=list("ABCD")  
    )

df.head(3)
```
|             | A       | B       | C       | D       |
|-------------|---------|---------|---------|---------|
| 2013-01-01  | $-0.29  | $0.23   | $0.01   | $1.61  |
| 2013-01-02  | $-0.04  | $0.03   | $-0.63  | $0.51  |
| 2013-01-03  | $0.22   | $-0.90  | $-0.15  | $0.71  |
  {{< /tab >}}



  {{< tab >}}
Sklearn 库自带数据如下表

| **数据集** | **数据集描述**|
| :-: | :-: |
|load_iris         |鸢尾花数据集（分类）|
|load_diabetes     |糖尿病数据集（回归）|
|load_digits       |数字数据集（分类）|
|load_linnerud     |体力锻炼 Linnerud 数据集|
|load_wine         |葡萄酒数据集（分类）|
|load_breast_cancer|威斯康星州乳腺癌数据集（分类）|

<br>

案例：查看鸢尾花分类数据集

```python
# 导入 sklearn.datasets 数据集
from sklearn import datasets

# 导入鸢尾花分类数据集
iris = datasets.load_iris()

# 打印数据描述
#print(iris.DESCR)

# 打印数据字典中的关键字
print('---------- iris.keys() ----------')
print(iris.keys(), '\n')

# 特征值
features = iris.data
print('---------- features[0:10] ----------')
print(features[0:10], '\n')

# 标签值
target = iris.target
print('---------- target[0:10] ----------')
print(target[0:10], '\n')

# 特征名称
feature_names = iris.feature_names
print('---------- feature_names ----------')
print(feature_names, '\n')

# 标签名称
target_names = iris.target_names
print('---------- target_names ----------')
print(target_names, '\n')
```

```
---------- iris.keys() ----------
dict_keys(['data', 'target', 'frame', 'target_names', 'DESCR', 'feature_names', 'filename', 'data_module']) 

---------- features[0:10] ----------
[[ 5.100  3.500  1.400  0.200]
 [ 4.900  3.000  1.400  0.200]
 [ 4.700  3.200  1.300  0.200]
 [ 4.600  3.100  1.500  0.200]
 [ 5.000  3.600  1.400  0.200]
 [ 5.400  3.900  1.700  0.400]
 [ 4.600  3.400  1.400  0.300]
 [ 5.000  3.400  1.500  0.200]
 [ 4.400  2.900  1.400  0.200]
 [ 4.900  3.100  1.500  0.100]] 

---------- target[0:10] ----------
[0 0 0 0 0 0 0 0 0 0] 

---------- feature_names ----------
['sepal length (cm)', 'sepal width (cm)', 'petal length (cm)', 'petal width (cm)'] 

---------- target_names ----------
['setosa' 'versicolor' 'virginica'] 
```
  {{< /tab >}}


  {{< tab >}}
**（1）pandas.read_csv**
```python
import pandas as pd

df = pd.read_csv(
    'PATH/file_name'        # 文件名称
    ,header=0               # 设置第一行为列名称
    ,names=['','','',...]   # header=None 时，设置列名
    ,sep=','                # 设置分隔符
    ,na_values=[':', ' ']   # 不可用字符/标记为缺失值的字符
    ,usecols=['', '', '']   # 需要的列
    ,delim_whitespace=True  # 默认 False 是否指定空格(" "或"\t")为分隔符使用，等效于设定sep='\s+'。
    )
```

> 读取 kaggle 泰坦尼克号数据集

```python
import pandas as pd

df = pd.read_csv(
    'datasets/titanic/train.csv' # 文件名称
    ,header=0                   # 设置第一行为列名称
    )

# 产看前 3 行，前 4 列
df.iloc[:3,0:4]
```

<br>

**（2）open()+csv.read()**

```python
import numpy as np
import pandas as pd
import csv
import os

# 数据集文件的路径，'datasets/titanic'是文件夹名，"train.csv"是文件名
data_filename = os.path.join(
    'datasets'
    , 'titanic'
    , 'train.csv'
    )

# 用 csv 模块来导入数据集文件，并创建 csv 阅读器对象
with open(data_filename, 'r') as input_file:
    # 创建一个 CSV 读取器对象，用于读取数据文件
    reader = csv.reader(input_file)
    # 将读取到的 CSV 数据转换为列表形式并存储在 iris_data 变量中
    data = list(reader)

# 查看前 3 行，前 4 列
pd.DataFrame(data).iloc[:3,0:4]
```
  {{< /tab >}}



  {{< tab >}}
**（1）pandas.read_excel()**

```python
import pandas as pd

df = pd.read_excel(
    'datasets/titanic/train.xlsx' # 文件名称
    ,sheet_name='train' 
    ,header=0   # 设置第一行为列名称
    )

# 查看前 3 行，前 4 列
df.iloc[:3,0:4]
```
  {{< /tab >}}


  {{< tab >}}

**（1）MySql -> DataFrame**

使用 pymysql 链接数据库，并使用 pd.read_sql 读取数据。

```python
# 禁止显示不需要的警告
import warnings
warnings.filterwarnings("ignore") 

sql_student = "SELECT * FROM student"
sql_score = "SELECT * FROM score"
sql_teacher = "SELECT * FROM teacher"
sql_course = "SELECT * FROM course"

# 导入库
import pymysql
import pandas as pd

conn = pymysql.connect(
     host='localhost'
    ,user='root'
    ,password = "000000"
    ,db='test'
)

df_student = pd.read_sql(
     sql_student # 
    ,conn
    )

df_student.head()
```

  {{< /tab >}}
{{< /tabs >}}


<br>


#### 2.1.6、创建数据

通过 Sklearn.datasets 模块的函数可以创建指定类型数据集：
1. `make_classification` 函数：生成具有特定分类特征和复杂分布的数据集。
2. `make_regression` 函数：生成连续目标特征的数据集。
3. `make_blobs` 函数：生成简单的聚类型数据集。
4. `make_moons` 函数：创建两个交错的半圆数据。
5. `make_circles` 函数：在 2d 中画一个大圆，里面包含一个小圆。一个简单的玩具数据集，用于可视化聚类和分类算法。

<br>

{{< tabs items="1️⃣ make_classification, 2️⃣ make_regression, 3️⃣ make_blobs, 4️⃣ make_moons, 5️⃣ make_circles" >}}
  {{< tab >}}
生成具有特定分类特征和复杂分布的数据集。***注***：`make_classification` 函数较多，这里简单列举了几个常用的。 

```python
from sklearn.datasets import make_classification

features, target = make_classification(
     n_samples = 100        # 生成 100 个样本。
    ,n_features = 3         # 每个样本有 3 个特征。
    ,n_informative = 3      # 有 3 个具有信息量的特征，即对区分类别有帮助的特征。
    ,n_redundant = 0        # 没有冗余特征。
    ,n_classes = 2          # 生成 2 个类别。
    ,weights = [.25, .75]   # 指定两个类别的样本比例，这里第一个类别的样本占比 25%，第二个类别的样本占比 75%。
    ,random_state = 1       # 设置随机数种子，以确保结果的可重复性。
    )

print(features[0:5],'\n')
print(target[0:5])
```
  {{< /tab >}}



  {{< tab >}}
生成连续目标特征的数据集。

```python
from sklearn.datasets import make_regression

features, target, coefficients = make_regression(
	 n_samples = 100    # 指定生成的样本数量为 100 个。
	,n_features = 3     # 指定数据集的特征数量为 3 个。
	,n_informative = 3  # 指定具有实际信息（对预测目标有贡献）的特征数量为 3 个。      
	,n_targets = 1      # 指定目标变量的数量为 1 个。
	,noise = 0.0        # 设置噪声水平为 0，即生成的数据集没有噪声。
	,coef = True        # 表示返回生成数据的真实系数。
	,random_state = 1   # 设置随机数生成器的种子，以确保结果的可重复性。
	)

"""
参数 noise：
较小的值（如 0.1、0.5 等）用于模拟适度的噪声，
较大的值（如 1.0 及以上）则表示较强的噪声干扰。
"""

# features      ：特征数据 
# target        ：目标数据
# coefficients  ：真实的系数

print(features[0:5],'\n')
print(target[0:5],'\n')
print(coefficients)
```
  {{< /tab >}}



  {{< tab >}}
生成简单的聚类型数据集。

```python
from sklearn.datasets import make_blobs

features, target = make_blobs(
	 n_samples = 100    # 生成 100 个样本
	,n_features = 2     # 每个样本有 2 个特征
	,centers = 3        # 指定生成数据的类别数为 3，即会生成围绕 3 个中心点的数据簇；也可以指定具体中心店：centers = [[-2, 2], [2, 2], [0, 4]]
	,cluster_std = 0.5  # 每个数据簇的标准差为 0.5，决定了数据的分散程度；可以指定不同标准差：cluster_std=[1.0,3.0]
	,shuffle = True		# 在生成数据后，对数据进行随机打乱。
	,random_state = 1   # 置随机数生成器的种子，以保证结果的可重复性。
	)

print(features[0:5],'\n')
print(target[0:5],'\n')
```

<br>

绘制创建数据集的散点图：

```python
import matplotlib.pyplot as plt

fig, ax = plt.subplots(figsize=(3, 3))

ax.scatter(
      features[:, 0]
    , features[:, 1]
    , c=target
    , cmap='viridis'
    )

plt.show()
```
  {{< /tab >}}



  {{< tab >}}
创建两个交错的半圆数据。

```python
from sklearn.datasets import make_moons

features, target = make_moons(
	n_samples=500    # 指定生成的样本总数。
	, noise=0.2      # 添加的噪声标准差。
    , shuffle=True   # 如果为True，则打乱样本顺序。
	, random_state=0 # 设置随机种子为 0 以确保可重复性
	)

print(features[0:5],'\n')
print(target[0:5],'\n')
```


<br>

绘制创建数据集的散点图：

```python
import matplotlib.pyplot as plt

fig, ax = plt.subplots(figsize=(3, 3))

ax.scatter(
      features[:, 0]
    , features[:, 1]
    , c=target
    , cmap='viridis'
    )

plt.show()
```
  {{< /tab >}}

  {{< tab >}}
在 2d 中画一个大圆，里面包含一个小圆。一个简单的玩具数据集，用于可视化聚类和分类算法。

```python
from sklearn.datasets import make_circles

features, target = make_circles(
	n_samples=500    # 指定生成的样本总数。
	, noise=0.2      # 添加的噪声标准差。可以使生成的同心圆形状不那么规则，更接近真实世界的数据情况。
    , shuffle=True   # 如果为True，则打乱样本顺序。随机打乱生成的数据集的顺序。
	, random_state=0 # 设置随机种子为 0 以确保可重复性
    , factor=0.4     # 内圆与外圆之间的比例因子。控制两个同心圆之间的距离大小。
	)

print(features[0:5],'\n')
print(target[0:5],'\n')
```


<br>

绘制创建数据集的散点图：

```python
import matplotlib.pyplot as plt

fig, ax = plt.subplots(figsize=(3, 3))

ax.scatter(
      features[:, 0]
    , features[:, 1]
    , c=target
    , cmap='viridis'
    )

plt.show()
```
  {{< /tab >}}
{{< /tabs >}}



<br>



#### 2.1.7、导出数据


{{< tabs items="1️⃣ 数据库" >}}
  {{< tab >}}

 **（1）将 `Pandas` 数据框导入 `MySQL`**

 使用 python pandas 生成一个数据框。

```python
import pandas as pd
import numpy as np
import random

cities = ['北京', '上海', '广州', '深圳', '成都']
address_samples = ['中山路{}号'.format(i) for i in range(1000)]

data = {
    'id': range(1, 101),
    'city': [random.choice(cities) for _ in range(100)],
    'address': [random.choice(address_samples) for _ in range(100)],
    'price': np.random.randint(1000000, 10000000, 100)
}

df = pd.DataFrame(data)

df.head()
```


<BR>


使用 python sqlalchemy 库将生成的数据直接写入 MySQL。

```python
from sqlalchemy import create_engine
import sqlalchemy

engine = create_engine('mysql+pymysql://root:123456@localhost:3306/test')

df.to_sql( 'housing_price' # 数据库表名
    , con=engine
    , index=False 
    , if_exists='replace' # 如果表已经存在，它会被替换
    , dtype={ 
        'id': sqlalchemy.types.INT
        ,'city':  sqlalchemy.types.NVARCHAR(length=10)
        ,'address': sqlalchemy.types.NVARCHAR(length=40)
        ,'price': sqlalchemy.types.DECIMAL(15, 3)
    }
)
```
  
  {{< /tab >}}
{{< /tabs >}}


<br>





|             | A       | B       | C       | D       |
|-------------|---------|---------|---------|---------|
| 2013-01-01  | $-0.29  | $0.23   | $0.01   | $1.61  |
| 2013-01-02  | $-0.04  | $0.03   | $-0.63  | $0.51  |
| 2013-01-03  | $0.22   | $-0.90  | $-0.15  | $0.71  |



<style>
  /* 自定义表格字体 */
  .markdown-body table {
    font-family: "Georgia", "Times New Roman", serif; /* 设置字体 */
    font-size: 9px;                                /* 字体大小 */
    color: #333;                                    /* 字体颜色 */
  }
</style>

|             | A       | B       | C       | D       |
|-------------|---------|---------|---------|---------|
| 2013-01-01  | $-0.29  | $0.23   | $0.01   | $1.61  |
| 2013-01-02  | $-0.04  | $0.03   | $-0.63  | $0.51  |
| 2013-01-03  | $0.22   | $-0.90  | $-0.15  | $0.71  |














































































