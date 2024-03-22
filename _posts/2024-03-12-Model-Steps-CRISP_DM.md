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

#### **1). 常用函数**

| 序号  | 函数名称                | 解释                         |
| --- | ------------------- | -------------------------- |
| 1   | ***df.head()***     | # 查看前5行，可以自定义函数，如：head(10) |
| 2   | ***df.tail(3)***    | # 查看后三行                    |
| 3   | ***df.sample(10)*** | # 随机 10 行                  |
| 4   | ***df.shape***      | # 行数+列数                    |
| 5   | ******              |                            |
| 6   | ******              |                            |
| 7   | ******              |                            |
| 8   | ******              |                            |
| 9   | ******              |                            |
| 10  | ******              |                            |
| 11  | ******              |                            |
| 12  | ******              |                            |





































































