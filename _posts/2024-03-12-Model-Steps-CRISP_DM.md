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

#### **01）CSV File**

##### **pd.read_csv()**

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



















