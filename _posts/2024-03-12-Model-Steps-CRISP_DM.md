---
layout: post
title: CRISP-DM
subtitle: Modeling steps in machine learning.
categories: AI
tags: [Steps]
---
<br>

## ***1. 定义问题***

* [如何定义机器学习问题 - MachineLearningMastery.com](https://machinelearningmastery.com/how-to-define-your-machine-learning-problem/)
<br>

### ***1.1. 问题是什么?***

1. 简单描述问题;
2. 定义问题目标; (***主要目标，次要目标***)
3. 解决问题方案; (***假设列表，算法列表; 评价指标; 展示方案，等***)
5. 查看相似项目；
<br>

> ***例如，展示方案如下：***
> - 编写分析报告展示你的结果；
> - 使用 Streamlit 开发一个 demo 展示模型；
> - 部署模型，并托管，监控……
<br>

### ***1.2. 为什么需要解决问题？***

* 练习；不需要使用最合适的算法，而是想探索不熟悉的算法，学习新技能；
* 工作；解决工作中的数据分析问题；
* 竞赛；获取良好的排名，提升知名度，获取奖金。
<br>

### ***1.3. 探索如何解决问题？***

* 逐步列出您将收集哪些数据？
* 现有数据范围有多大？都是什么样的？能不能解决我们的问题？
* 希望拥有哪些数据？能否获取到这些数据？
* 收集您遇到的所有这些详细信息，并更新问题定义的内容。
<br>

## ***2. 收集数据***

- [《Approaching(Almost) Any Machine Learning Problem》](https://ytzfhqs.github.io/AAAMLP-CN/)
- 《Python数据分析与数据化运营（第2版）》 宋天龙 (著)
- 《Machine.Learning.with.Python.Cookbook》2nd.Edition
- 《Machine Learning Mastery With Python》
<br>

### ***2.1. 工作空间***


| Folder| Describe|
|------------------|-----------|
| ***input/***     | 所有输入文件、数据文件；<br />NLP 项目，可以将嵌入保留在此处；<br />图像项目，则所有图像都将转到该文件夹中的子文件夹中; |
| ***src/***       | 所有 python 脚本；                                                                                              |
| ***models/***    | 所有经过训练的模型；                                                                                             |
| ***notebooks/*** | 所有jupyter笔记本（即任何*.ipynb文件）都存储在笔记本文件夹中；                                                     |
| ***README.md***  | 这是一个讲解文件，您可以在其中描述您的项目;如编写关于如何训练模型或在生产环境中提供模型的说明；                         |
| ***LICENSE***    | 这是一个简单的文本文件，包含项目的许可证，如MIT、Apache等。详细了解许可证超出了本书的范围；                           |

<br>

#### **01）python：os 模块**

> （1）python os 模块主要函数有四个：如下

```python
import os
os.getcwd()        # 获取当前工作空间/目录
os.mkdir("/PASH")  # 新建目录
os.chdir("/PATH")  # 切换新都工作空间
os.listdir()       # 列出当前工作空间文件/文件夹
```
<br>

>  （2）通过 python os 模块创建工作空间，案例 1 如下，使用循环；可以新建一个 notebook 然后在执行如下代码，可以在现有空间下面创建一个有关该项目的新的工作空间。

```python
import os

project_name = 'Kaggle_004_Object-name'
folder_name  = ['input', 'src', 'models', 'notebooks']
file_name    = ['README.md', 'LICENSE']

if project_name not in os.listdir():
    os.mkdir(project_name)

	# 创建文件夹：'input', 'src', 'models', 'notebooks'
    for i in folder_name:
        os.mkdir(os.path.join(project_name, i))

	# 创建文件：'README.md', 'LICENSE'
    for j in file_name:
        open(os.path.join(project_name, j), 'w')
    print(project_name + ' is Mkdired!')
else:
    print(project_name + ' is OK!')
```
<br>

> （3）使用 python os 模块创建工作空间，案例 2 如下：不适用循环

```python
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
<br>


### ***2.2. 数据来源***

1. 数据文件
2. 数据库
3. API
4. 流式数据
<br>

### ***2.3. 数据导入***

#### **01). CSV File**

##### **pd.read_csv()**

> **pd.read_csv()**

- [(62条消息)pandas.read_csv参数超级详解，好多栗子！_python read csv_BigBai小白的博客-CSDN](https://blog.csdn.net/sinat_35562946/article/details/81058221)
<br>

```python
# Load library
import pandas as pd

df = pd.read_csv(
    file='dir/Data.csv'    # 文件名称
    ,sep=';'
    ,na_values=[':' ,’ ’]  # 不可用字符/标记为缺失值的字符
    ,usecols=['', '', '']  # 需要的列
    ,delim_whitespace=True # 默认False是否指定空格(" "或"\t")为分隔符使用，等效于设定sep='\s+'。
    )
```
<br>


##### **open()+csv.reader()**

> **open()+csv.reader()**

```python
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
<br>


```python
import numpy as np
import csv
import os

# 用Data文件夹路径、数据集所在的文件夹名称和数据集名称组合成数据集文件的完整路径
data_filename = os.path.join('datasets', "ionosphere", "ionosphere.data")
X = np.zeros((351, 34), dtype='float')
y = np.zeros((351,), dtype='bool')

# 用 csv 模块来导入数据集文件，并创建 csv 阅读器对象
with open(data_filename, 'r') as input_file:
    reader = csv.reader(input_file)
    # 遍历文件中的每一行数据
    for i, row in enumerate(reader):
        # 获取每一个个体的前34个值，将其强制转化为浮点型，保存到 X 中
        data = [float(datum) for datum in row[:-1]]
        X[i] = data
        # 获取每个个体最后一个表示类别的值，把字母转化为数字，如果类别为“g”，值为1，否则值为0。
        y[i] = row[-1] == 'g'

X[0:2], y[0:2]
```
<br>

##### **open()+np.loadtxt()**
> 此函数假定没有标题行，并且所有数据都具有相同的格式

```python
import numpy as np
import os

data_filename = os.path.join('datasets', "wine.data")

raw_data = open(data_filename, 'rb')

data = np.loadtxt(raw_data, delimiter=",")
data[0:5]
```
<br>


#### **02). Excel File**


### ***2.4. 数据合并***

- https://pandas.pydata.org/pandas-docs/stable/user_guide/merging.html#

#### **01). 纵向合并**

##### **pd.concat([],axis=0)**

> **pd.concat([],axis=0)**

```python
# Load library
import pandas as pd

# Create DataFrame_a
data_a = {
     'id': ['1', '2', '3']
    ,'first': ['Alex', 'Amy', 'Allen']
    ,'last': ['Anderson', 'Ackerman', 'Ali']
    }

dataframe_a = pd.DataFrame(data_a, columns = ['id', 'first', 'last'])

# Create DataFrame_b
data_b = {
     'id': ['4', '5', '6']
    ,'first': ['Billy', 'Brian', 'Bran']
    ,'last': ['Bonder', 'Black', 'Balwner']
    }

dataframe_b = pd.DataFrame(data_b, columns = ['id', 'first', 'last'])


# Concatenate DataFrames by rows
pd.concat([dataframe_a, dataframe_b], axis=0)
```

|  | id | first | last |
|---|---|---|---|
| 0 | 1 | Alex | Anderson |
| 1 | 2 | Amy | Ackerman |
| 2 | 3 | Allen | Ali |
| 0 | 4 | Billy | Bonder |
| 1 | 5 | Brian | Black |
| 2 | 6 | Bran | Balwner |
<br>

#### **02). 横向合并**

##### **pd.concat([],axis=1)**

> **pd.concat([],axis=1)**

```python
import pandas as pd

from sklearn.datasets import load_iris
data = load_iris()
X, y = data.data, data.target

df_data = pd.concat([
     pd.DataFrame(X, columns=data.feature_names)
    ,pd.DataFrame(y, columns=['class'])],axis=1
    )

df_data.head()
```

|sepal length (cm)|sepal width (cm)|petal length (cm)|petal width (cm)|class|
|-----------------|----------------|-----------------|----------------|-----|
|0 	|5.1 	|3.5 	|1.4 	|0.2 	|0|
|1 	|4.9 	|3.0 	|1.4 	|0.2 	|0|
|2 	|4.7 	|3.2 	|1.3 	|0.2 	|0|
|3 	|4.6 	|3.1 	|1.5 	|0.2 	|0|
|4 	|5.0 	|3.6 	|1.4 	|0.2 	|0|
<br>

##### **pd.concat([],axis=1,join='inner')** 

> **pd.concat([],axis=1,join='inner')**

![image](https://github.com/wenwangjain/wenwangjain.github.io/assets/106724523/4cd5c042-6337-45f0-ac59-53bed4a9185b)
<br>



## ***3. 数据探索（EDA）***

> ***可以使用可视化、统计方法来了解数据中的结构和关系，主要内容如下：***

> ***(1)、初步了解数据集***

1. 通过描述统计分析，初步了解数据集的分布，数据类型，特征值等信息
<br>

> ***（2）、探索分类变量***

1. **众数**：数据集中出现次数最多的类别或值
2. **列联表**：一种对两个或两个以上分类变量做计数的表格
3. **条形图**：在绘图中，以条形表示每个类别出现的频数或占比情况
4. **饼图**：在绘图中，圆饼中的一个扇形部分表示每个类别出现的频数或占比情况。
<br>

> ***（3）、探索数值变量***

1. 百分位数、箱线图；
2. 频数表；
3. 直方图、密度图；
4. 期望值：如果类别可以与一个数值相关联，可以根据类别的出现概率计算一个平均值。
<br>

> ***（4）、探索变量间的相关性***

1. 百分位数、箱线图；
2. 频数表；
3. 直方图、密度图；
4. 期望值：如果类别可以与一个数值相关联，可以根据类别的出现概率计算一个平均值。
<br>

> ***（5）、尝试不同的属性组合***

1. 通过不同属性间的关系，重新创建新特征。
<br>



### ***3.0. 副本，显示设置***


- [Python pandas库(21) 设置数字格式，小数位数、百分号、千位分隔符 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/30955381)
- [pandas round方法保留两位小数的设置 (zhihu.com)](https://www.zhihu.com/tardis/zm/art/155504224?source_id=1005)
- [pandas 列保留2位小数 - CSDN文库](https://wenku.csdn.net/answer/zefigui2hi#:~:text=pandas%E4%BF%9D%E7%95%99%E4%B8%A4%E4%BD%8D%E5%B0%8F%E6%95%B0%201%20%E9%A6%96%E5%85%88%EF%BC%8C%E4%BD%A0%E9%9C%80%E8%A6%81%E5%AF%BC%E5%85%A5pandas%E5%BA%93%E5%B9%B6%E8%AF%BB%E5%8F%96%E4%BD%A0%E7%9A%84%E6%95%B0%E6%8D%AE%E6%96%87%E4%BB%B6%E3%80%82%20%E4%BD%A0%E5%8F%AF%E4%BB%A5%E4%BD%BF%E7%94%A8%E4%BB%A5%E4%B8%8B%E4%BB%A3%E7%A0%81%E5%AE%9E%E7%8E%B0%EF%BC%9A%20import%20pandas%20as%20pd,%E4%BD%A0%E5%8F%AF%E4%BB%A5%E4%BD%BF%E7%94%A8%E4%BB%A5%E4%B8%8B%E4%BB%A3%E7%A0%81%E5%AE%9E%E7%8E%B0%EF%BC%9A%20df%5B%27your_column%27%5D%20%3D%20df%5B%27your_column%27%5D.apply%28lambda%20x%3A%20round%28x%2C%202%29%29%20%E8%BF%99%E5%B0%86%E5%AF%B9%E4%BD%A0%E7%9A%84%E5%88%97%E8%BF%9B%E8%A1%8C%E5%9B%9B%E8%88%8D%E4%BA%94%E5%85%A5%EF%BC%8C%E5%B9%B6%E4%BF%9D%E7%95%99%E4%B8%A4%E4%BD%8D%E5%B0%8F%E6%95%B0%E3%80%82)
<br>

#### **1). DF.copy()**

```python
train_copy = train.copy()
```
<br>

#### **2). Library Display Settings**


```python
# pandas 显示设置
# ------------------------------------------------------------------------------------------
pd.set_option('display.float_format','${:,.2f}'.format)  # 显示格式 $0.67
pd.set_option('display.unicode.east_asian_width', False) # 设置输出右对齐，此代码写入脚本中
pd.set_option('display.max_info_columns',200) # info()变量最多显示200个 
pd.set_option('display.max_info_rows',200) # info()缺失值个数上限 

pd.set_option('display.chop_threshold',0.5) # 绝对值小于 0.5 显示 0 
pd.set_option('display.precision',4) # 保留4位小数 
pd.set_option('precision', 3) # 保留3位小数

pd.set_option('display.max_rows',5) # 数据框行数 
pd.set_option('display.max_columns',100) # 数据框列数 
pd.set_option('display.max_colwidth',200) # 数据框列宽 

pd.options.display.max_colwidth = 80 
pd.options.display.max_columns = 20 
pd.options.display.max_rows = 20

# matplotlib 显示设置
# ------------------------------------------------------------------------------------------
plt.rcParams['font.sans-serif']=['FangSong'] # 替换sans-serif字体，正常显示中文(体)\'SimHei'\'FangSong' 
plt.rcParams["font.weight"] = "bold" # 字体加粗 
plt.rcParams['axes.unicode_minus'] = False # 坐标显示负号 
plt.rcParams['savefig.dpi'] = 1000 # 图片像素 
plt.rcParams['figure.dpi'] = 100 # 分辨率（不常用） 
plt.style.use('classic') 
plt.style.use('ggplot') 
matplotlib.rcdefaults() # 恢复默认风格

# numpy 显示设置
# ------------------------------------------------------------------------------------------
np.set_printoptions(precision=3, suppress=True) # precision：保留几位小数，后面不会补0，supress=True：对很大/小的数不使用科学计数法 
np.set_printoptions(formatter={'float': '{: 0.3f}'.format}) # formatter：强制格式化，后面会补0
```
<br>


#### **3). round(), format()**

```python
import pandas as pd

# 假设我们有一个 DataFrame df
df = pd.DataFrame({
     'value1': [1.123456, 2.654321, 3.141592]
    ,'value2': [1123456 , 2654321 , 3141592]
    })

# 【1】使用 .round() 函数将 'values' 列的数值四舍五入到两位小数
df['value3'] = df['value1'].round(decimals=3)

# 【2】使用 .roung() 函数将 'value4','value5'保留两位、一位小数
df['value4'] = df['value1']
df['value5'] = df['value1']
df = df.round({'value4':2, 'value5':1})

# 【3】对整个df进行四舍五入到两位小数
# df = df.round(decimals=3)

# 【4】我们可以使用 .round() 函数将 'values' 列的数值四舍五入到两位小数
df['value6'] = df['value1'].map(lambda x:round(x, 2))

# 【5】处理后数据从float格式转换成了带2位小数和百分号的对象（object） 
df['value7'] = df['value1'].map(lambda x:format(x, '0.2%'))

# 【6】# 设置千位分隔符，转换后，这些已经不再是数字了，而是数字和逗号组成的字符串。 
df['value8'] = df['value2'].map(lambda x:format(x, ','))

# 打印结果
df.head()
```
<br>

| id  | value1   | value2  | value3 | value4 | value5 | value6 | value7  | value8    |
| --- | -------- | ------- | ------ | ------ | ------ | ------ | ------- | --------- |
| 0   | 1.123456 | 1123456 | 1.123  | 1.12   | 1.1    | 1.12   | 112.35% | 1,123,456 |
| 1   | 2.654321 | 2654321 | 2.654  | 2.65   | 2.7    | 2.65   | 265.43% | 2,654,321 |
| 2   | 3.141592 | 3141592 | 3.142  | 3.14   | 3.1    | 3.14   | 314.16% | 3,141,592 |

<br>




### ***3.1. 初步了解数据集***

#### **1). 常用函数，统计/排序**

| 序号  | 函数名称                                                      | 解释             |
| --- | --------------------------------------------------------- | -------------- |
| 1   | ***df.head()***                                           | # 前5行          |
| 2   | ***df.tail(3)***                                          | # 后3行          |
| 3   | ***df.shape***                                            | # 行数+列数        |
| 4   | ***df.sample(10)***                                       | # 随机 10 行      |
| .   |                                                           |                |
| 5   | ***df.index***                                            | # 查看行索引        |
| 6   | ***df.index.tolist()***                                   |                |
| .   |                                                           |                |
| 7   | ***df.columns***                                          | # 列名称          |
| 8   | ***list(df.columns)***                                    |                |
| 9   | ***df.columns.tolist()***                                 |                |
| 10  | ***df.columns.values.tolist()***                          |                |
| .   |                                                           |                |
| 11  | ***df.dtypes***                                           | # 数据类型         |
| 12  | ***df.dtypes.to_dict()***                                 |                |
| 13  | ***df.dtypes.to_list()***                                 |                |
| .   |                                                           |                |
| 14  | ***df.info()***                                           | # 特征类型\非缺失计数   |
| 15  | ***df.count()***                                          | # 非缺失计数        |
| 16  | ***df.describe()***                                       | # 数值变量摘要       |
| 17  | ***df.describe(include='object').T***                     | # 分类变量摘要       |
| 18  | ***df.describe(include=['O']).T***                        |                |
| .   |                                                           |                |
| 19  | ***df['Age'].skew()***                                    | # 偏态系数         |
| 20  | ***df['Age'].kurt()***                                    | # 峰态系数         |
| 21  | ***df.sum()***                                            | ***df.min()*** |
| 22  | ***df.mean()***                                           | ***df.max()*** |
| 23  | ***df.median()***                                         | # 中位数          |
| 24  | ***df.mode()***                                           | # 众数           |
| 25  | ***df.var()***                                            | # 无偏方差         |
| 26  | ***df.std()***                                            | # 无偏标准差        |
| 27  | ***df.['col_name'].quantile([0.1, 0.9])***                | # 分位数          |
| 28  | ***df.quantile(q=0.25)***                                 |                |
| 29  | ***df.prod()***                                           | # 乘积           |
| .   |                                                           |                |
| 30  | ***df.sort_values(by="column")***                         | # 列升序（默认）      |
| 31  | ***df.sort_values(by="column", ascending=False)***        | # 列降序          |
| 32  | ***df.sort_index(axis=0, ascending=False,inplace=True)*** | # 轴降序          |

<br>

#### **2). 常用探索库**

##### **(1). Sweetviz：生成 EDA 报告**

- [使用sweetviz库，1行代码生成美观清晰的数据分析报告 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/206597487)
<br>


> ***1、sweetviz.analyze() 查看所有变量概况***

```python
import warnings
warnings.filterwarnings("ignore")

import pandas as pd
import os 

file = os.path.join('datasets', 'train.csv')

train = pd.read_csv(file, header=0)
train.head()
```

| id  | PassengerId | Survived | Pclass | Name                                              | Sex    | Age  | SibSp | Parch | Ticket    | Fare    | Cabin | Embarked |
| --- | ----------- | -------- | ------ | ------------------------------------------------- | ------ | ---- | ----- | ----- | --------- | ------- | ----- | -------- |
| 0   | 1           | 0        | 3      | Braund, Mr. Owen Harris                           | male   | 22.0 | 1     | 0     | A/5 21171 | 7.2500  | NaN   | S        |
| 1   | 2           | 1        | 1      | Cumings, Mrs. John Bradley (Florence Briggs Th... | female | 38.0 | 1     | 0     | PC 17599  | 71.2833 | C85   | C        |


<br>

```python
import sweetviz as sv

my_report = sv.analyze(
     train
    ,target_feat ='Survived' # 目标变量
    )

my_report.show_html("Report_analyze.html") # .show_notebook()
```
<br>

> ***2、sweetviz.compare_intra() 查看所有变量关于目标变量不同取值的分布***

```python
# 目标变量取不同值时，其他变量的分布情况对比
my_report = sv.compare_intra(
     train
    ,train['Survived'] == 0
    ,['Survived_0','Survived_1']
    ,target_feat ='Survived' # 目标变量
)
my_report.show_html("Report_compare_intra.html") # .show_notebook()
```
<br>

> ***3、sweetviz.compare() 查看所有变量关于分类变量不同取值的分布***

```python
A = train.loc[train['Survived'] == 0,:]
B = train.loc[train['Survived'] != 0,:]

sv.compare([A, 'train_no'], [B, 'train_yes']).show_html( 'Report_compare.html') #.show_notebook()
```
<br>

##### **(2). pandas_profiling：生成 EDA 报告**

- [太香了，墙裂推荐3个Python数据分析EDA神器！ - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/285240381)
<br>

> ***1、安装 pandas_profiling 库***

```python
# 安装Jupyter扩展widget 
jupyter nbextension enable --py widgetsnbextension

# 或者通过conda安装
conda env create -n pandas-profiling
conda activate pandas-profiling
conda install -c conda-forge pandas-profiling

# 或者直接从源地址安装
pip install https://github.com/pandas-profiling/pandas-profiling/archive/master.zip
```

<br>

> ***2、pandas_profiling 生成 EDA 报告***

```python
from pandas_profiling import ProfileReport

profile = ProfileReport(
     train
    ,title='MPG Pandas Profiling Report'
    ,explorative = True)
# profile # 直接在 notebook 上展示
profile.to_file("data_profiling.html")
```

<br>


##### **(3). 【pygwalker】：类似 Tableau 可视化**

- [登上GitHub热榜的Python可视化工具：PyGWalker - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/609129220)
<br>

```python
import pygwalker as pyg 
gwalker = pyg.walk(train)
```

<br>

##### **(4). 【pivottablejs】：透视表\图**

- [数据透视表JS ·皮皮 (pypi.org)](https://pypi.org/project/pivottablejs/)
<br>

```python
from pivottablejs import pivot_ui 
pivot_ui(train)
```

<br>

##### **(5). pandasGUI：拖放 EDA 图\表**

- [太香了，墙裂推荐3个Python数据分析EDA神器！ - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/285240381)
<br>

```python
# pip安装
pip install pandasgui

# 或者通过源下载
pip install git+https://github.com/adamerose/pandasgui.git
```

<br>

```python
from pandasgui import show 
# 部署GUI的数据集 
gui = show(mpg)
```

<br>

#### **3). 分组表\图，唯一值\图**

##### **(1). 表：df\['clo'\].value_counts()**

```python
df["clome_name"].value_counts() 
df["clome_name"].value_counts().sort_values(ascending=False)
```
<br>

##### **(2). 图：df\['col'\].value_counts().plot.bar()**

```python
df['col_name'].value_counts().plot.bar()
```
<br>

```python
class EDA:
    def group_bar(df, col):
        figsize = (5, 2.5)
        legend_font = {"family" : "Times New Roman", 'weight':'bold', 'size':9}
        
        import matplotlib.pyplot as plt
        
        fig, ax = plt.subplots(figsize = figsize)
        
        # -----------------------------------------------------------------------------------
        for i in ['left', 'bottom']:
            ax.spines[i].set_linewidth(0.4) #设置底部坐标轴的粗细
            ax.spines[i].set_position(("outward", 5)) # 设置坐标轴位置，向外移动
        
        for j in ['right', 'top']:
            ax.spines[j].set_color('none') # 设置坐标轴无色
            
        # -----------------------------------------------------------------------------------
        plt.yticks(fontproperties = 'FangSong', size = 10) 
        plt.xticks(fontproperties = 'FangSong', size = 10, rotation=0)
        
        # -------------------------------------------------------------------------------------
        df[col].value_counts().plot.bar(alpha=0.8
                                 , width=0.9 # 条形图宽度
                                 , facecolor="DimGray" # lightcoral coral\DimGray
                                 #, edgecolor="white" # 条形图边款色  
                                )
        
        # -----------------------------------------------------------------------------------
        plt.xlabel(None)
        plt.title(col, fontproperties = 'FangSong', size = 13, loc='center') # 'left','center','right'
        plt.show()
```
<br>

```python
EDA.group_bar(train, 'Survived')
```
<br>

##### **(3). 图：sns.countplot(x=col, data=df)**

```python
import seaborn as sns

col = 'Survived'
df = train.copy()

b = sns.countplot(x=col, data=df , facecolor="coral") # lightcoral coral\DimGray)
b.set_xlabel(x, fontsize=13)
b.set_ylabel("count", fontsize=13)
```
<br>

##### **(4). 表：df['col'].unique()，.nunique()**

```python
# Select unique values
df['Sex'].unique() # 输出：array(['female', 'male'], dtype=object)

# Show number of unique values
df['Sex'].nunique() # 输出：4
```
<br>

##### **(5). 表：np.unique(y)，np.bincount(y)**

```python
df.values
np.unique(y)   # 
np.bincount(y) # 调用NumPy的bincount函数来对阵列中的每个值进行统计
```
<br>

#### **4). 【自定义函数】**

```
class EDA:
    def title(test):
        print('\n')
        from rich.console import Console
        console=Console()
        console.print('  .:. ', test , ' .:.','\n' , "="*60 , style="bold green")    #打印红色字体
        #console.print(,style="bold green")    #打印红色字体
    
    def des_table(df, cols=None):
        import warnings
        warnings.filterwarnings('ignore')
        from pandas import DataFrame
        import pandas as pd
        import numpy as np
        
        pd.set_option('display.max_colwidth',200)                    # 数据框列宽
        pd.set_option('display.precision',2) # 保留4位小数
        
        
        
        df01 = DataFrame(df.dtypes ,columns=['Dtypes']).reset_index()
        #df01['Sample_size'] =  df.shape[0]
        df01['Feature_Chinese'] = cols
        df01.rename(columns={'index':'---Feature_Nname---'},inplace=True) 
        
        df03  = DataFrame(df.count(),columns=['Count'])
        des2  = pd.merge(df01,df03,left_on="---Feature_Nname---",right_index=True,how="outer")
        
        df04  = DataFrame(df.isnull().sum(),columns=["Null_c"])
        des3  = pd.merge(des2,df04,left_on="---Feature_Nname---",right_index=True,how="outer")
        des3["Null%"] = des3["Null_c"]/df.shape[0] #des3["Sample_size"]
        df_dtr = df.copy()
        for i in df_dtr.columns.tolist():
            df_dtr[i] = df_dtr[i].astype('str')
        df_dtr_des = df_dtr.describe(include='object').T
        df_dtr_des['Top_1%'] = df_dtr_des['freq']/df.shape[0]
        df_dtr1 = df_dtr_des[['unique','freq','Top_1%']]
        df_dtr2 = pd.merge(des3,df_dtr1,left_on="---Feature_Nname---",right_index=True,how="left")
        
        
        
        df05  = DataFrame(df.describe().T)
        des4  = pd.merge(df_dtr2,df05,left_on="---Feature_Nname---",right_index=True,how="left")
        des4.drop('count', axis=1, inplace=True)
        des4['Inclination'] = 3*(des4["mean"] - des4["50%"])/des4["std"]
        
        
        df06  = DataFrame(df.dtypes,columns=['Dtypes'])
        df07  = df06.loc[df06['Dtypes'] != "object",:]
        
        df_ = df.copy()
        name01 = []
        for i in df07.index.tolist():
            df_[str(i)+"_IQR"] = df_[i].quantile(q=0.75) - df_[i].quantile(q=0.25)
            df_[str(i)+"_1"] = np.where((df_[i] < (df_[i].quantile(q=0.25) - 1.5 * df_[str(i)+"_IQR"])) | 
                                   (df_[i] > (df_[i].quantile(q=0.75) + 1.5 * df_[str(i)+"_IQR"])),1,0)
            name01.append(str(i)+"_1")
        
        df08 = df_[name01]
        df09 = DataFrame(df08.sum(),columns=["IQR_Outlier"])
        df09.reset_index(inplace=True)
        df09["index"] = df09["index"].str.replace("_1","")
    
        des5 = pd.merge(des4,df09,left_on="---Feature_Nname---",right_on="index",how="left")
        des5["IQR_Outlier%"] = des5["IQR_Outlier"]/df.shape[0] #des5["Sample_size"]
        
        des5.drop('index', axis=1, inplace=True)
        
        des5.rename(columns={ 'Count':'--Count--'
                             ,'Null_c':'-Null_c-'
                             ,'Null%':'Null%'
                             ,'Top_1%':'Top_1_c%'
                             ,'mean':'-Mean-'
                             ,'std':'--Std--'
                             ,'min':'--Min--'
                             ,'25%':'--25%--'
                             ,'50%':'--50%--'
                             ,'75%':'--75%--'
                             ,'max':'--Max--'
                             ,'unique':'Unique'
                             ,'freq':'Top_1_c'
                            }
                    ,inplace=True)
        name02 = list(des5.columns)[3:]  
        describe =(des5.style.format({ name02[2]:"{:.1%}"
                                      ,name02[3]:"{:.0f}",name02[4]:"{:.0f}",name02[5]:"{:.1%}",name02[6]:"{:.2f}",name02[7]:"{:.2f}"
                                      ,name02[8]:"{:.2f}",name02[9]:"{:.2f}",name02[10]:"{:.2f}",name02[11]:"{:.2f}"
                                      ,name02[12]:"{:.2f}",name02[13]:"{:.2f}",name02[14]:"{:.0f}",name02[15]:"{:.2%}"
                                     }
                                    ).bar( color='Coral' #'lightcoral'
                                           , subset=name02
                                           , align='zero'
                                           , height=80
                                           , width=70
                                         )
                  )
        
        return describe

    def des_chart(df):
        import numpy as np
        import matplotlib.pyplot as plt
        import seaborn as sns
        import scipy.stats as stats
        import math
        from statsmodels.distributions.empirical_distribution import ECDF
        import matplotlib
        
        plt.rcParams['font.sans-serif'] = ['FangSong'] # 设置中文黑体 SimHei
        plt.rcParams['axes.unicode_minus'] = False     # 设置显示负号
        
        
        #sns.set(style="white")
        matplotlib.rcdefaults()
        #plt.style.use('ggplot') # classic
        #sns.set(style="white")
        plt.rcParams['figure.dpi'] = 115 #分辨率
         
        df = df.fillna(value=0)
        dict_columns = df.dtypes.to_dict()
        
        font1 = {'fontproperties':'FangSong', 'fontweight': 'bold', 'size': 10, 'c':'k'} # 
        
        for i in df.columns:
            if str(dict_columns[i]) != 'object':
                fig = plt.figure(figsize=(16, 0.9))
          
                len_plot = 1/(16/1.5)
                typeface = 'FangSong'
                bins = 12
          
                left_1, width_1 = 0, len_plot*1.3  # left:左边、width:宽度
                left_2, width_2 = width_1+0.03, len_plot*1.6
                left_3, width_3 = left_2+width_2+0.03, len_plot*0.8
                left_4, width_4 = left_3+width_3+0.03, len_plot*0.8
                left_5, width_5 = left_4+width_4+0.03, len_plot*0.8
          
                bottom, height = 0, 0.6 # bottom:底部、height:高度
          
                rect_hist1 = [left_1, bottom, width_1, height+0.2]
                rect_hist2 = [left_2, bottom, width_2, height+0.2]
                rect_hist3 = [left_3, bottom, width_3, height+0.6]
                rect_hist4 = [left_4, bottom, width_4, height+0.6]
                rect_hist5 = [left_5, bottom, width_5, height+0.6]
        
                # --------------------------------------------------------------------------------
                ax_hist1 = plt.axes(rect_hist1)
                # --------------------------------------------------------------------------------
                plt.hist( df[i]
                          , bins=bins
                          #, density=1 #设置此项目可以使纵坐标显示频率
                          , facecolor="Coral" # 'lightcoral'/'coral'/'lightblue'/'cornflowerblue'
                          , edgecolor="white" # 条形边框颜色，不设置显示白色/white/indianred
                          )
                ax=plt.gca()
                ax.spines['left'].set_linewidth(0.47) #设置坐标轴的粗细
                ax.spines['right'].set_color('none')
                ax.spines['top'].set_color('none')
                ax.spines['left'].set_color('none')
                ax.spines['bottom'].set_linewidth(0.47)
                #ax.spines["left"].set_position(("outward", 5)) # 设置坐标轴位置
                ax.spines["bottom"].set_position(("outward", 5))
                plt.yticks(fontproperties = typeface, size = 8)
                plt.xticks(fontproperties = typeface, size = 8) 
                #plt.title(i, font1) # , x=0.45, y=height+0.4 
                plt.title(i, size = 9
                       , fontproperties = 'FangSong'
                       , color = '#525252'
                       , fontweight='bold' 
                       , fontfamily='serif'
                      ) # fontproperties = 'FangSong',                      
                # --------------------------------------------------------------------------------
                ax_hist2 = plt.axes(rect_hist2)
                # --------------------------------------------------------------------------------
                g1 = sns.kdeplot(df[i],linewidth = 1 ,c='DimGray') # DimGray\cornflowerblue
                #sns.despine() #可以自动隐藏上部（top）、右部（right）轴 #sns.despine( top=True, right=True)  #,bottom=True,left=True
                g1.set(xlabel=None)
                g1.set(ylabel=None)
                #g1.set(xticklabels=[]) 隐藏坐标轴标签 g1.set(yticklabels=[]) 
                plt.hist(df[i]
                          , bins=bins
                          , density=1 #设置此项目可以使纵坐标显示频率
                          , facecolor="Coral" # 'lightcoral'/'coral'/'lightblue'
                          , edgecolor="white" # 条形边框颜色，不设置显示白色/white/indianred
                          ) 
                ax=plt.gca()
                ax.spines['left'].set_linewidth(0.47) #设置坐标轴的粗细
                ax.spines['right'].set_color('none')
                ax.spines['top'].set_color('none')
                ax.spines['left'].set_color('none')
                ax.spines['bottom'].set_linewidth(0.47); 
                #ax.spines["left"].set_position(("outward", 5)) # 设置坐标轴位置
                ax.spines["bottom"].set_position(("outward", 5)) 
                plt.yticks(fontproperties = typeface, size = 8)
                plt.xticks(fontproperties = typeface, size = 8) 
                
                # --------------------------------------------------------------------------------
                ax_hist3 = plt.axes(rect_hist3)
                # --------------------------------------------------------------------------------
                data = df[i].values
                ecdf = ECDF(data)
                cdf = ecdf(data)
                data.sort()
                cdf.sort()
                plt.scatter(data,cdf,c='DimGray',s=5) # cornflowerblue
                plt.plot(data,cdf,c='Coral',lw=1)
          
                ax=plt.gca()
                ax.spines['left'].set_linewidth(0.47) #设置坐标轴的粗细
                ax.spines['right'].set_linewidth(0.47) #设置坐标轴的粗细
                ax.spines['top'].set_linewidth(0.47)
                ax.spines['bottom'].set_linewidth(0.47)
                # ax.spines['right'].set_color('none')
                #ax.spines["left"].set_position(("outward", 5)) # 设置坐标轴位置
                #ax.spines["bottom"].set_position(("outward", 5)) 
                #ax.spines["right"].set_position(("outward", 5))
                #ax.spines["top"].set_position(("outward", 5)) 
                plt.yticks(fontproperties = typeface, size = 8)
                plt.xticks(fontproperties = typeface, size = 8)
                plt.ylim(0,1)#X轴范围
                #data = churn["Account Length"]
                #if math.ceil(data.max()) < 0:
                #    good = - math.ceil(data.max())
                #else:
                #    good = math.ceil(data.max())
                #                         
                #hist, bin_edges = np.histogram(data, bins=good, density=True)# 计算随机数的频数分布
                #cdf = np.cumsum(hist * np.diff(bin_edges))# 计算随机数的累积分布函数
                #plt.plot(cdf, linewidth = 0.9)
                
                # --------------------------------------------------------------------------------
                ax_hist4 = plt.axes(rect_hist4)
                # --------------------------------------------------------------------------------
                data = df[i]
          
                mu, sigma = 0, 1
                np.random.seed(12345)
                x = np.random.normal(mu,sigma,size=len(data))
                x.sort()
                plt.scatter(x,data,c='DimGray',s=5) # cornflowerblue
                z = np.polyfit(x, data, 1)
                f = np.poly1d(z)
          
                # 绘制拟合线
                plt.plot(x,f(x),c='Coral', linewidth =1)
                ax=plt.gca()
                ax.spines['left'].set_linewidth(0.47) #设置坐标轴的粗细
                ax.spines['right'].set_linewidth(0.47) #设置坐标轴的粗细
                ax.spines['top'].set_linewidth(0.47)
                ax.spines['bottom'].set_linewidth(0.47)
                # ax.spines['right'].set_color('none')
                #ax.spines["left"].set_position(("outward", 5)) # 设置坐标轴位置
                #ax.spines["bottom"].set_position(("outward", 5)) 
                #ax.spines["right"].set_position(("outward", 5))
                #ax.spines["top"].set_position(("outward", 5)) 
                plt.yticks(fontproperties = typeface, size = 8)
                plt.xticks(fontproperties = typeface, size = 8)
                plt.xlabel('')
                plt.ylabel('')
                plt.title('')
                #stats.probplot(churn["Account Length"], plot=plt,)
                # --------------------------------------------------------------------------------
                ax_hist5 = plt.axes(rect_hist5)
                # --------------------------------------------------------------------------------
                ax=plt.gca()
                #ax.spines['left'].set_linewidth(0.47) #设置坐标轴的粗细
                #ax.spines['right'].set_linewidth(0.47) #设置坐标轴的粗细
                #ax.spines['top'].set_linewidth(0.47)
                ax.spines['bottom'].set_linewidth(0.47)
                for i in ['left', 'right', 'top', 'bottom']:
                    ax.spines[i].set_color('none')
                # ax.spines['right'].set_color('none')
                ax.spines["left"].set_position(("outward", 5)) # 设置坐标轴位置
                ax.spines["bottom"].set_position(("outward", 5)) 
                ax.spines["right"].set_position(("outward", 5))
                ax.spines["top"].set_position(("outward", 5)) 
                plt.yticks([], fontproperties = typeface, size = 8)
                plt.xticks([], fontproperties = typeface, size = 8)
                plt.xlabel('')
                plt.ylabel('')
                plt.title('')
        
                
                
            else:
                data1 = df[i].value_counts()[0:20]
                data2 = df[i].value_counts().cumsum()[0:20]/df.shape[0]
                x = [str(k) for k in data1.index]
                y =  data2.values
                z =  data1.values
                
                hight = 1.2
                width = 5 #len(data1)*(10/20)
                
                
                from matplotlib import font_manager
                my_font=font_manager.FontProperties(fname="C:\Windows\Fonts\SIMYOU.TTF")
                
                plt.rcParams['axes.unicode_minus'] = False     # 设置显示负号
                
                fig, ax = plt.subplots(figsize=(width,hight))
                p1 = plt.bar(  x
                        , z
                        , facecolor="DimGray" # lightcoral\coral\cornflowerblue\lightblue
                        #, alpha=0.2
                        , width = 0.9
                       )
                
                plt.bar_label(p1, label_type='edge', fontproperties = my_font, size = 9, fontweight='bold')
                
                ax=plt.gca() 
                ax.spines['left'].set_color('none')
                ax.spines['right'].set_color('none')
                ax.spines['top'].set_color('none')
                ax.spines['bottom'].set_linewidth(0.47); #设置底部坐标轴的粗细
                ax.spines["bottom"].set_position(("outward", 5)) 
                plt.xticks(fontproperties = my_font, size = 8, rotation=60)
                plt.yticks([]) #fontproperties = 'Times New Roman', size = 8)
                #plt.title(i, size = 9)  
                
                
                ax_ = ax.twinx()
                plt.scatter(x,y,c='Coral',s=6)
                plt.plot(x,y,c='Coral',lw=0.8)
                
                ax_=plt.gca() 
                ax_.spines['left'].set_color('none')
                ax_.spines['right'].set_color('none')
                ax_.spines['top'].set_color('none')
                ax_.spines['bottom'].set_linewidth(0.47); #设置底部坐标轴的粗细
                ax_.spines["bottom"].set_position(("outward", 5))
                
                ax_.set_ylim((0,1.1))
                
                plt.yticks(fontproperties = 'Times New Roman', size = 8)
                plt.xticks(fontproperties = my_font, size = 8, rotation=60)
                #plt.title(i, size = 9)    
                
                #plt.title(i, font1, x=0.08, y=hight+0.05)
                plt.title(i, size = 9
                       , fontproperties = 'FangSong'
                       , color = '#525252'
                       , fontweight='bold' 
                       , fontfamily='serif'
                      ) # fontproperties = 'FangSong',   
                plt.show()
```
<br>






















































