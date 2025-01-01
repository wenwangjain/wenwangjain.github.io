---
title: 2. 收集数据
weight: 2
#next: /step1
#prev: /docs
editURL: "https://example.com/edit/this/page"
toc: true
math: true
---

<br>

## 1、数据来源：


1. ***数据文件：*** 这是存储数据的常见形式，例如 CSV（逗号分隔值）文件、Excel 文件、JSON 文件、XML 文件等。数据文件通常以结构化或半结构化的方式组织数据，可以通过读取文件的方式将数据导入到应用程序或分析工具中。
  
2. ***数据库：*** 是专门用于存储和管理数据的系统，如关系型数据库（如 MySQL、Oracle、SQL Server 等）和非关系型数据库（如 MongoDB、Cassandra 等）。数据库提供了高效的数据存储、检索、更新和管理功能，并支持复杂的查询和事务处理。

3. ......



<br><br><br>


## 2、选择数据：

选择将要使用的所有可用数据的子集。需要考虑实际需要哪些数据来解决您正在处理的问题或难题。对所需的数据进行一些假设，并小心记录这些假设，以便以后可以在需要时对其进行测试。

> ***以下是一些问题，可帮助您思考整个过程：*** 
> - 您拥有的数据范围有多大？例如，通过时间，数据库表，连接的系统。确保您对可以使用的所有内容都有清晰的了解。
> - 哪些数据不可用，而您希望您有这些数据？例如，未记录或无法记录的数据。您可以派生或模拟此数据。
> - 您不需要哪些数据来解决问题？排除数据几乎总是比包含数据更容易。记下您排除了哪些数据及其原因。
> - **只有在小问题中，例如竞赛或玩具数据集，数据已经为您选择了。**
> - 您选择的数据可能格式不适合使用。数据可能位于关系数据库中，您希望它位于平面文件中，或者数据可能采用专有文件格式。



<br><br><br>



## 3、工作空间：

{{< callout >}}
  工作空间可以理解为数据科学项目的目录结构\项目模板。
  - [Jupyter Notebook 上数据科学项目的 5 个免费模板](https://www.kdnuggets.com/5-free-templates-for-data-science-projects-on-jupyter-notebook)
  - 《Approaching(Almost) AnyMachineLearningProblem》 Abhishek Thakur
{{< /callout >}}



### 3.1、Abhishek Thakur

{{% details title="<font color=Gray face=Georgia size=3>1. Python *创建工作空间案例 1*</font>" closed="true" %}}
  ```python {linenos=table, linenostart=1, filename="example 1"}
  import os 
  object_name = 'Kaggle_001_Object-name'
      if object_name not in os.listdir():
          os.mkdir(object_name)
          os.mkdir(object_name+'/input')
          os.mkdir(object_name+'/src')
          os.mkdir(object_name+'/models')
          os.mkdir(object_name+'/notebooks')
          open(object_name+'/README.md','w')
          open(object_name+'/LICENSE','w')
      else:
          print(object_name + ' is OK!')
  ```
{{% /details %}}


{{% details title="<font color=Gray face=Georgia  size=3>2. Python *创建工作空间案例 2*</font>" closed="true" %}}
  ```python {linenos=table, linenostart=1, filename="example 2"}
  import os
  
  project_name = 'Kaggle_002_class-name'
  folder_name  = ['input', 'src', 'models', 'notebooks']
  file_name    = ['README.md', 'LICENSE']
  file_list    = os.listdir()
  
  if project_name not in file_list:
    
      # （1）、如果该空间不存在则创建工作空间
      # ----------------------------------------------------------------------
      os.mkdir(project_name)
    
      # （2）、创建文件夹：'input', 'src', 'models', 'notebooks'
      # ----------------------------------------------------------------------
      for i in folder_name:
          path_folder = os.path.join(project_name, i)
          os.mkdir(path_folder)
        
      # （3）、创建文件：'README.md', 'LICENSE'
      # ----------------------------------------------------------------------
      for j in file_name:
          path_file = os.path.join(project_name, j)
          open(path_file, 'w', encoding='utf-8')
    
      print(project_name + ' is OK!')
      
  else:
      print(project_name + ' is OK!')
  ```
{{% /details %}}


{{% details title="<font color=Gray face=Georgia size=3>3. Python *创建 .ipynb 文件*</font>" closed="true" %}}
  ```python {linenos=table, linenostart=1, filename="创建 .ipynb 文件"}
  import json
  
  data = {
      "cells": [
          {
            "cell_type": "code",
            "execution_count": None,
            "metadata": {},
            "outputs": [],
            "source": []
          }
      ],
      "metadata": {},
      "nbformat": 4,
      "nbformat_minor": 4,
  }
  
  with open('new_notebook.ipynb', 'w') as f:
      json.dump(data, f)
  ```
{{% /details %}}


{{< cards >}}
  {{< card link="/guide/python/python_modules" title="Python os Module" icon="back" >}}
{{< /cards >}}

<br>





<br><br><br>



## 4、显示设置\库版本：

### 4.1、查看库版本


{{% details title="<font color=Gray face=Georgia size=3>1. %load_ext watermark</font>" closed="true" %}}
```python {linenos=table, linenostart=1}
# numpy,pandas,matplotlib,sklearn,seaborn version
%load_ext watermark
%watermark -a "Sebastian Raschka" -u -d -v -p numpy,pandas,matplotlib,sklearn,seaborn
```
{{% /details %}}


{{% details title="<font color=Gray face=Georgia size=3>2. xxx.\_\_version\_\_</font>" closed="true" %}}
```python {linenos=table, linenostart=1}
# pandas version
import pandas
print('pandas: {}'.format(pandas.__version__))
```
{{% /details %}}


{{% details title="<font color=Gray face=Georgia size=3>3. !python --version</font>" closed="true" %}}
```python {linenos=table, linenostart=1}
# jupyterlab Python version：
!python --version
```
{{% /details %}}


<br><br>


### 4.2、Python 显示设置

{{% details title="<font color=Gray face=Georgia size=3>1. pandas，numpy，matplotlib *显示设置*</font>" closed="true" %}}
```python {linenos=table, linenostart=1, filename="create_markdown"}
import warnings
warnings.filterwarnings("ignore") # 禁止显示不需要的警告


pd.set_option('display.float_format','${:,.2f}'.format)  # 显示格式 $0.67
pd.set_option('display.unicode.east_asian_width', False) # 设置输出右对齐，此代码写入脚本中
 
pd.set_option('display.max_info_columns',200) # info()变量最多显示200个
pd.set_option('display.max_info_rows',200)    # info()缺失值个数上限
pd.set_option('display.max_rows',5)           # 数据框行数       
pd.set_option('display.max_columns',100)      # 数据框列数 
pd.set_option('display.max_colwidth',200)     # 数据框列宽       
pd.set_option('display.chop_threshold',0.5)   # 绝对值小于 0.5 显示 0
pd.set_option('display.precision',4)          # 保留4位小数
pd.set_option('precision', 3)                 # 保留3位小数
pd.options.display.max_colwidth = 80
pd.options.display.max_columns = 20 
pd.options.display.max_rows = 20
pd.set_option('display.colheader_justify', 'left') # 确保列名不换行


plt.rcParams['font.sans-serif']=['FangSong']  # 替换sans-serif字体，正常显示中文(黑体)\'SimHei'\'FangSong' 
plt.rcParams["font.weight"] = "bold"          # 字体加粗
plt.rcParams['axes.unicode_minus'] = False    # 坐标显示负号
plt.rcParams['savefig.dpi'] = 1000            # 图片像素
plt.rcParams['figure.dpi'] = 100              # 分辨率（不常用）
plt.style.use('classic')
plt.style.use('ggplot')  
matplotlib.rcdefaults() # Set default theme


np.set_printoptions(precision=3, suppress=True) # precision：保留几位小数，后面不会补0，supress=True：对很大/小的数不使用科学计数法
np.set_printoptions(formatter={'float': '{: 0.3f}'.format}) # formatter：强制格式化，后面会补0 
```
{{% /details %}}



<br><br><br>



## 5、导入数据：

### 5.1、Sklearn 创建数据

{{% details title="<font color=Gray face=Georgia size=3>1. sklearn.datasets.make_regression() *—— 回归*</font>" closed="true" %}}
```python {linenos=table, linenostart=1, filename="sklearn.datasets.make_regression()"}
# Load library
from sklearn.datasets import make_regression

# Generate features matrix, target vector, and the true coefficients
features, target, coefficients = make_regression(
	 n_samples = 100    # 指定生成的样本数量为 100 个。
	,n_features = 3     # 指定数据集的特征数量为 3 个。
	,n_informative = 3  # 指定具有实际信息（对预测目标有贡献）的特征数量为 3 个。      
	,n_targets = 1      # 指定目标变量的数量为 1 个。
	,noise = 0.0        # 设置噪声水平为 0，即生成的数据集没有噪声。较小的值（如 0.1、0.5 等）用于模拟适度的噪声，较大的值（如 1.0 及以上）则表示较强的噪声干扰。
	,coef = True        # 表示返回生成数据的真实系数。
	,random_state = 1   # 设置随机数生成器的种子，以确保结果的可重复性。
	)
	
# features      ：特征数据 
# target        ：目标数据
# coefficients  ：真实的系数
```
{{% /details %}}





{{% details title="<font color=Gray face=Georgia size=3>2. sklearn.datasets.make_classification() *—— 分类* </font>" closed="true" %}}
> 生成具有特定分类特征和复杂分布的数据集
```python {linenos=table, linenostart=1, filename="sklearn.datasets.make_classification()"}
# Load library
from sklearn.datasets import make_classification

# Generate features matrix and target vector
features, target = make_classification(
     n_samples = 100        # 生成 100 个样本。
    ,n_features = 3         # 每个样本有 3 个特征。
    ,n_informative = 3      # 有 3 个具有信息量的特征，即对区分类别有帮助的特征。
    ,n_redundant = 0        # 没有冗余特征。
    ,n_classes = 2          # 生成 2 个类别。
    ,weights = [.25, .75]   # 指定两个类别的样本比例，这里第一个类别的样本占比 25%，第二个类别的样本占比 75%。
    ,random_state = 1       # 设置随机数种子，以确保结果的可重复性。
    )

```

***n_informative 和 n_redundant 的主要区别在于它们对生成特征的作用和影响不同：***
- ***n_informative*** ：指定了具有实际区分能力、对确定样本类别有帮助的特征数量。这些特征携带了用于准确分类样本的关键信息。
- ***n_redundant*** ：表示冗余特征的数量。冗余特征是由其他具有信息量的特征通过线性组合生成的。也就是说，冗余特征可以通过具有信息量的特征计算得出，它们并没有为分类提供新的、独立的信息。
> 例如，如果 n_informative = 3 且 n_redundant = 0 ，那么生成的特征中会有 3 个是真正对区分样本类别起关键作用的独立特征，并且不存在可以通过这 3 个关键特征计算得出的冗余特征。<br>

> 如果 n_informative = 3 且 n_redundant = 1 ，那么除了 3 个关键特征外，还会有 1 个特征可以通过这 3 个关键特征的某种线性组合得到。

{{% /details %}}






{{% details title="<font color=Gray face=Georgia size=3>3. sklearn.datasets.make_blobs() *—— 聚类*</font>" closed="true" %}}
> 生成简单的聚类型数据集
```python {linenos=table, linenostart=1, filename="sklearn.datasets.make_blobs()"}
# Load library
from sklearn.datasets import make_blobs

# Generate features matrix and target vector
features, target = make_blobs(
	     n_samples = 100    # 生成 100 个样本
	    ,n_features = 2     # 每个样本有 3 个特征
	    ,centers = 3        # 指定生成数据的类别数为 3，即会生成围绕 3 个中心点的数据簇；也可以指定具体中心店：centers = [[-2, 2], [2, 2], [0, 4]]
	    ,cluster_std = 0.5  # 每个数据簇的标准差为 0.5，决定了数据的分散程度；可以指定不同标准差：cluster_std=[1.0,3.0]
	    ,shuffle = True		# 在生成数据后，对数据进行随机打乱。
	    ,random_state = 1   # 置随机数生成器的种子，以保证结果的可重复性。
	    )
```
{{% /details %}}





- [sklearn.datasets.make_regression — scikit-learn 1.3.2 文档](https://scikit-learn.org/stable/modules/generated/sklearn.datasets.make_regression.html)
- [sklearn.datasets.make_classification — scikit-learn 1.3.2 documentation](https://scikit-learn.org/stable/modules/generated/sklearn.datasets.make_classification.html)
- [sklearn.datasets.make_blobs — scikit-learn 1.3.2 documentation](https://scikit-learn.org/stable/modules/generated/sklearn.datasets.make_blobs.html)



<br><br>



### 5.2、Sklearn.datasets

<div style="font-size: 14px; border-left=0; border-right=0">
  <table>

| ***数据集*** | ***数据集描述*** |
| :-: | :-: |
|load_iris          |鸢尾花数据集（分类）。|
|load_diabetes      |糖尿病数据集（回归）。|
|load_digits        |数字数据集（分类）。|
|load_linnerud      |体力锻炼 Linnerud 数据集。|
|load_wine          |葡萄酒数据集（分类）。|
|load_breast_cancer |威斯康星州乳腺癌数据集（分类）。|
  </table>
</div>

{{% details title="<font color=Gray face=Georgia size=3>1. sklearn.datasets.load_digits()</font>" closed="true" %}}
```python {linenos=table, linenostart=1, filename="sklearn.datasets.make_blobs()"}
# Load scikit-learn's datasets
from sklearn import datasets

# Load digits dataset
digits = datasets.load_digits()

# Create features matrix
features = digits.data

# Create target vector
target = digits.target

# Print the attribute
print(digits.DESCR)

print(digits.keys())
```
{{% /details %}}


- [7.1. Toy datasets — scikit-learn 1.4.0 documentation](https://scikit-learn.org/stable/datasets/toy_dataset.html)



<br><br>



### 5.3、Dictionary OR Array

{{% details title="<font color=Gray face=Georgia size=3>1. pd.DataFrame(Dictionary)</font>" closed="true" %}}
```python {linenos=table, linenostart=1, filename="pd.DataFrame(Dictionary)"}
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

<div style="font-size: 14px; border-left=0; border-right=0">
  <table>

|	A|	B|	C|	D|	E|	F|
|-|-|-|-|-|-|
|0	|1.0	|2013-01-02	|1.0	|3	|test	|foo|
|1	|1.0	|2013-01-02	|1.0	|3	|train  |foo|
|2	|1.0	|2013-01-02	|1.0	|3	|test	|foo|
|3	|1.0	|2013-01-02	|1.0	|3	|train  |foo|

  </table>
</div>

{{% /details %}}


{{% details title="<font color=Gray face=Georgia size=3>2. pd.DataFrame(Array, index, ,columns)</font>" closed="true" %}}
```python {linenos=table, linenostart=1, filename="sklearn.datasets.make_blobs()"}
import numpy as np
import pandas as pd

dates = pd.date_range("20130101", periods=6)

df = pd.DataFrame(
    np.random.randn(6, 4) 
    ,index=dates           
    ,columns=list("ABCD")  
    )

df

df3 = df.copy()
df3["E"] = ["one", "one", "two", "three", "four", "three"]
df3
```
<div style="font-size: 14px; border-left=0; border-right=0">
  <table>

|A|	B|	C|	D|	E|
|-|-|-|-|-|
|2013-01-01 |	0.654804	 | 0.089649	  |-0.162848	|  0.668634	  |one  | 
|2013-01-02 |	-0.969746	|  -1.615553 |	0.281458	|  0.899988	  |one  | 
|2013-01-03 |	-0.572867 |	0.651239	  |0.098376	 | 0.263776	    |two  | 
|2013-01-04 |	-0.436956 |	0.469009	  |-0.054018	|  -0.103285	|three| 
|2013-01-05	|  -0.865556| 	-0.818567	|  1.058492|	  -1.623429	|four | 
|2013-01-06 |	-0.172757 |	-1.730109	 | 0.898024	|  -0.339679	  |three| 
  </table>
</div>

{{% /details %}}


<br><br>


### 5.4、.csv

{{% details title="<font color=Gray face=Georgia size=3>1. pd.read_csv()</font>" closed="true" %}}
```python {linenos=table, linenostart=1, filename="pd.read_csv()"}
import pandas as pd

df = pd.read_csv(
    file='dir/data.csv'         # 文件名称
        ,sep=';'
        ,na_values=[':', ' ']   # 不可用字符/标记为缺失值的字符
        ,usecols=['', '', '']   # 需要的列
        ,delim_whitespace=True  # 默认 False 是否指定空格(" "或"\t")为分隔符使用，等效于设定sep='\s+'。
    )
```
{{% /details %}}



{{% details title="<font color=Gray face=Georgia size=3>2. open() + csv.reader()</font>" closed="true" %}}
```python {linenos=table, linenostart=1, filename="open() + csv.reader()"}
import numpy as np
import csv
import os
 
data_filename = os.path.join('datasets', "iris_no_col.csv")
 
# 用 csv 模块来导入数据集文件，并创建 csv 阅读器对象
with open(data_filename, 'r') as input_file:
    reader = csv.reader(input_file)
    iris_data =  list(reader)
 
iris_data[0:5]
```
{{% /details %}}



{{% details title="<font color=Gray face=Georgia size=3>3. open() + np.loadtxt()</font>" closed="true" %}}
> ***此函数假定没有标题行，并且所有数据都具有相同的格式***
```python {linenos=table, linenostart=1, filename="open() + np.loadtxt()"}
import numpy as np
import os

data_filename = os.path.join('datasets', "wine.data")

raw_data = open(data_filename, 'rb')

data = np.loadtxt(raw_data, delimiter=",")
data[0:5]
```
{{% /details %}}



<br><br><br>



## 6、数据合并：

### 6.1、纵向合并

{{% details title="<font color=Gray face=Georgia size=3>1. pd.concat([df1, df2], axis=0)</font>" closed="true" %}}
```python {linenos=table, linenostart=1, filename="pd.concat([df1, df2], axis=0)"}
import pandas as pd

# 创建两个示例 DataFrame
df1 = pd.DataFrame({'A': [1, 2, 3], 'B': ['a', 'b', 'c']})
df2 = pd.DataFrame({'A': [4, 5, 6], 'B': ['d', 'e', 'f']})

# 沿行方向连接
result = pd.concat([df1, df2], axis=0)

# 重新设置索引
result.reset_index(drop=True, inplace=True)

# 增加一列标记数据所属的原始 DataFrame
result['Source'] = ['df1'] * len(df1) + ['df2'] * len(df2)

print(result)
```
{{% /details %}}


{{% details title="<font color=Gray face=Georgia size=3>2. np.vstack((a, b))</font>" closed="true" %}}
```python {linenos=table, linenostart=1, filename="np.vstack((a, b))"}
import numpy as np

a = np.array([[1, 2], [3, 4]])
b = np.array([[5, 6], [7, 8]])

result = np.vstack((a, b))
print(result)
```
{{% /details %}}


<br><br>


### 6.2、横向合并

{{% details title="<font color=Gray face=Georgia size=3>1. pd.concat([df1, df2], axis=1)</font>" closed="true" %}}
```python {linenos=table, linenostart=1, filename="pd.concat([df1, df2], axis=1)"}
import pandas as pd

# 创建示例 DataFrame
df1 = pd.DataFrame({'A': [1, 2, 3], 'B': ['a', 'b', 'c']})
df2 = pd.DataFrame({'C': [4, 5, 6], 'D': ['d', 'e', 'f']})

# 沿列方向连接
result = pd.concat([df1, df2], axis=1)

result
```
{{% /details %}}



{{% details title="<font color=Gray face=Georgia size=3>2. np.hstack((a, b))</font>" closed="true" %}}
```python {linenos=table, linenostart=1, filename="np.hstack((a, b))"}
import numpy as np

a = np.array([[1, 2], [3, 4]])
b = np.array([[5, 6], [7, 8]])

result = np.hstack((a, b))
result
```
{{% /details %}}



<br><br><br>



## 7、数据抽样：

{{< callout >}}
  可用的选定数据可能比您需要使用的要多得多。更多的数据可能导致算法的运行时间更长，计算和内存要求更高。在考虑整个数据集之前，您可以对所选数据进行较小的代表性示例，这些样本对于探索和原型设计解决方案可能要快得多。 在数据上使用的机器学习工具很可能会影响您需要执行的预处理。您可能会重新访问此步骤。
{{< /callout >}}


### 7.1、随机抽样

{{% details title="<font color=Gray face=Georgia size=3>1. df.sample(100)</font>" closed="true" %}}
```python {linenos=table, linenostart=1, filename="df.sample(100)"}
df.sample(100, random_state=42)        # 随机抽取100个样本
```
{{% /details %}}


{{% details title="<font color=Gray face=Georgia size=3>2. df.sample(frac=0.1)</font>" closed="true" %}}
```python {linenos=table, linenostart=1, filename="df.sample(frac=0.1)"}
df.sample(frac=0.1, random_state=42)   # 随机抽取 10% 样本
```
{{% /details %}}



<br><br>



### 7.2、放回随机抽样

{{% details title="<font color=Gray face=Georgia size=3>1. sklearn.utils.resample()</font>" closed="true" %}}
```python {linenos=table, linenostart=1, filename="sklearn.utils.resample()"}
from sklearn.utils import resample

train = resample(df, replace=True, n_samples=4, random_state=42)
```
{{% /details %}}


{{% details title="<font color=Gray face=Georgia size=3>2. df.sample(n=3, replace=True)</font>" closed="true" %}}
```python {linenos=table, linenostart=1, filename="sklearn.utils.resample()"}
import pandas as pd

# 创建一个示例 DataFrame
data = {'A': [1, 2, 3, 4, 5]}
df = pd.DataFrame(data)

# 进行放回随机抽样，抽取 3 个样本
sampled_df = df.sample(n=3, replace=True, random_state=42)

print(sampled_df)
```
{{% /details %}}



{{% details title="<font color=Gray face=Georgia size=3>3. df.sample(frac=0.8, replace=True)</font>" closed="true" %}}
```python {linenos=table, linenostart=1, filename="sklearn.utils.resample()"}
import pandas as pd

# 创建一个示例 DataFrame
data = {'A': [1, 2, 3, 4, 5]}
df = pd.DataFrame(data)

# 进行放回随机抽样，抽取 3 个样本
sampled_df = df.sample(frac=0.8, replace=True, random_state=42)

print(sampled_df)
```
{{% /details %}}



<br><br>



### 7.3、分层随机抽样

{{% details title="<font color=Gray face=Georgia size=3>1. df.groupby('layer').sample(frac=0.5)</font>" closed="true" %}}
```python {linenos=table, linenostart=1, filename="df.groupby('layer').sample(frac=0.5)"}
import pandas as pd

# 假设有一个数据集 df，包含分层的列 'layer' 和其他数据列
data = {'layer': ['A', 'A', 'A', 'B', 'B', 'B'],
        'value': [10, 20, 30, 40, 50, 60]}
df = pd.DataFrame(data)

# 按 'layer' 列进行分层随机抽样，每个层抽取 50% 的样本
sampled_df = df.groupby('layer').sample(frac=0.5, random_state=42)

print(sampled_df)
```
{{% /details %}}



<br><br><br>



## 8、数据拆分\训练\测试：

{{% details title="<font color=Gray face=Georgia size=3>1. sklearn.model_selection.train_test_split</font>" closed="true" %}}
```python {linenos=table, linenostart=1, filename="sklearn.model_selection.train_test_split"}
from sklearn.model_selection import train_test_split

# Create training and test sets
features_train, features_test, target_train, target_test = train_test_split(
    features, target, test_size=0.1, stratify=y, random_state=1)

# stratify = y 
# shuffle = True # 打乱排序
```
{{% /details %}}



{{% details title="<font color=Gray face=Georgia size=3>2. df.sample(frac=0.5)</font>" closed="true" %}}
```python {linenos=table, linenostart=1, filename="df.sample(frac=)"}
import pandas as pd

# 创建示例数据
data = {'col1': [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]}
df = pd.DataFrame(data)

# 计算抽样比例（例如 50%）
sample_ratio = 0.5

# 随机抽样得到第一部分数据
part1 = df.sample(frac=sample_ratio)

# 第二部分数据为原始数据中除去第一部分的数据
part2 = df.drop(part1.index)

print("第一部分数据：")
print(part1)
print("第二部分数据：")
print(part2)
```
{{% /details %}}



{{% details title="<font color=Gray face=Georgia size=3>3. df.sample(frac=0.5) *—分层*</font>" closed="true" %}}
```python {linenos=table, linenostart=1, filename="df.sample(frac=0.5)"}
import pandas as pd
import numpy as np

# 创建示例数据，假设根据 'col1' 的值分层
data = {'col1': [1, 1, 2, 2, 2, 3, 3, 3, 3, 4],
        'col2': [10, 20, 30, 40, 50, 60, 70, 80, 90, 100]}
df = pd.DataFrame(data)

# 定义分层列
stratify_column = 'col1'

# 获取分层列的唯一值
strata = df[stratify_column].unique()

# 计算抽样比例（例如 50%）
sample_ratio = 0.5

# 存储抽样后的两部分数据
part1 = pd.DataFrame()
part2 = pd.DataFrame()

# 对每个分层进行抽样
for stratum in strata:
    stratum_df = df[df[stratify_column] == stratum]
    stratum_sample = stratum_df.sample(frac=sample_ratio)
    part1 = pd.concat([part1, stratum_sample])
    part2 = pd.concat([part2, stratum_df.drop(stratum_sample.index)])

print("第一部分数据：")
print(part1)
print("第二部分数据：")
print(part2)
```
{{% /details %}}



<br><br><br>










