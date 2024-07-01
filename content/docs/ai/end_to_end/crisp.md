---
title: 2.3. CRISP-DM
weight: 103
#next: /step1
#prev: /docs
editURL: "https://example.com/edit/this/page"
toc: true
math: true
---


## ***<font face=Georgia>1、定义问题</font>***

- [如何定义机器学习问题 - MachineLearningMastery.com](https://machinelearningmastery.com/how-to-define-your-machine-learning-problem/)

### **<font face=Georgia>1.1、问题是什么？</font>**

- 简单描述问题;
- 定义问题目标; (***主要目标，次要目标***)
- 解决问题方案; (***假设列表，算法列表; 评价指标; 展示方案，……***)
- 查看相似项目；
  
> ***例如，展示方案如下：***
> 
> 1. 编写分析报告展示你的结果；
> 2. 使用 Streamlit 开发一个 demo 展示模型； 
> 3. 部署模型，并托管，监控……
> 4. 部署到移动设备，或其他电子元实现智能化

<br><br>

### **<font face=Georgia>1.2、为什么需要解决问题？</font>**

- 练习；不需要使用最合适的算法，而是想探索不熟悉的算法，学习新技能；
- 工作；解决工作中的数据分析问题；
- 竞赛；获取良好的排名，提升知名度，获取奖金。
  
<br><br>

### **<font face=Georgia>1.3、探索如何解决问题？</font>**

- 现有：逐步列出您将收集哪些数据？—> 现有数据范围有多大（存储地址\数据量）？—> 都是什么样的（数据质量）？—> 能不能解决我们的问题？
- 期望：希望拥有哪些数据？能否获取到这些数据？
- 收集您遇到的所有这些详细信息，并更新问题定义的内容。




<br><br><br>




## ***<font face=Georgia>2、收集数据</font>***

### **<font face=Georgia>2.1、工作空间：</font>**



{{% details title="<font color=Coral face=Georgia size=3>2.1.1、*Python os 模块常用函数*</font>" closed="true" %}}
  ```python {linenos=table, linenostart=1}
  import os
  os.getcwd()                         # 获取当前工作空间/目录
  os.mkdir("PASH")                    # 新建目录
  os.chdir("PATH")                    # 切换新都工作空间
  os.listdir()                        # 列出当前工作空间文件/文件夹
  os.path.splitext("PATH")            # 分离文件名和扩展名
  os.path.join('PATH1', 'PATH1', ...) # 拼接多个目录
  ```
{{% /details %}}



{{% details title="<font color=Gray face=Georgia size=3>（1）、*os.path.splitext( ) —— 拆分文件名，后缀名*</font>" closed="true" %}}
  ```python {linenos=table, linenostart=1}
  # os.path.splitext()是 Python 的 os 模块中的一个函数，它用来分离文件名和扩展名。
  os.path.splitext(path_file)

  # 输出：
  # ('input\11595\train.csv', '.zip')
  ```
  ```python {linenos=table, linenostart=1, filename="_, "}
  _, file_type = os.path.splitext(path_file)
  # 其中的 _ 是一个常规的 Python 变量，并且它被用来存储分离的文件名部分。
  # 由于文件名部分在这个语句中并不需要，所以采用了 _ 作为变量名，以表示这个值会被忽略。
  file_type
  
  # 输出：
  # '.zip'
  ```
{{% /details %}}



{{% details title="<font color=Gray face=Georgia size=3>（2）、*os.listdir( ) —— 查看文件夹下的内容*</font>" closed="true" %}}
  ```python {linenos=table, linenostart=1, filename="example 1"}
  import os 

  path = os.getcwd() # 查看当前工作空间
  path_join = os.path.join(path, 'input', '11595')

  os.listdir(path_join)
  ```
{{% /details %}}



{{% details title="<font color=Gray face=Georgia size=3>（3）、*os.walk( ) —— 查看文件夹下的内容*</font>" closed="true" %}}
  ```python {linenos=table, linenostart=1, filename="example 2"}
  import os
    
  path_join = os.path.join('input', '11595')
    
  for dirname, _, filenames in os.walk(path_join):
      for filename in filenames:
          print(os.path.join(dirname, filename))
  ```
{{% /details %}}

<br>

{{% details title="<font color=Coral face=Georgia size=3>2.1.2、*工作空间案例 —— 《Approaching(Almost) Any Machine Learning Problem》*</font>" closed="true" %}}
  - ***<font color=DarkCyan face=Georgia  >input/</font>***：所有输入文件、数据文件； NLP 项目，可以将嵌入保留在此处；图像项目，则所有图像都将转到该文件夹中的子文件夹中;
  - ***<font color=DarkCyan face=Georgia  >src/</font>***：所有 python 脚本；
  - ***<font color=DarkCyan face=Georgia  >models/</font>***：所有经过训练的模型；
  - ***<font color=DarkCyan face=Georgia  >notebooks/</font>***：所有jupyter笔记本（即任何*.ipynb文件）都存储在笔记本文件夹中；
  - ***<font color=DarkCyan face=Georgia  >README.md</font>***：这是一个讲解文件，您可以在其中描述您的项目；如编写关于如何训练模型或在生产环境中提供模型的说明；
  - ***<font color=DarkCyan face=Georgia  >LICENSE</font>***：这是一个简单的文本文件，包含项目的许可证，如MIT、Apache等。
{{% /details %}}



{{% details title="<font color=DarkCyan face=Georgia size=3>（1）、*Python os 模块创建案例 1*</font>" closed="true" %}}
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



{{% details title="<font color=DarkCyan face=Georgia size=3>（2）、*Python os 模块创建案例 2*</font>" closed="true" %}}
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



{{% details title="<font color=Gray face=Georgia size=3>（3）、*Python os 模块创建 .ipynb 文件案例*</font>" closed="true" %}}
  ```python {linenos=table, linenostart=1}
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












<br><br><br>



### **<font face=Georgia>2.2、数据来源：</font>**

1. 数据文件
2. 数据库
3. API
4. 流式数据



<br><br><br>



### **<font face=Georgia>2.3、显示设置\库版本：</font>**

***<font color=Coral face=Georgia >2.3.1、查看库版本</font>***

{{% details title="<font color=Gray face=Georgia size=3>（1）、*%load_ext watermark*</font>" closed="true" %}}
```python {linenos=table, linenostart=1}
# numpy,pandas,matplotlib,sklearn,seaborn version
%load_ext watermark
%watermark -a "Sebastian Raschka" -u -d -v -p numpy,pandas,matplotlib,sklearn,seaborn
```
{{% /details %}}



{{% details title="<font color=Gray face=Georgia size=3>（2）、*xxx.\_\_version\_\_*</font>" closed="true" %}}
```python {linenos=table, linenostart=1}
# pandas version
import pandas
print('pandas: {}'.format(pandas.__version__))
```
{{% /details %}}



{{% details title="<font color=Gray face=Georgia size=3>（3）、*!python --version*</font>" closed="true" %}}
```python {linenos=table, linenostart=1}
# jupyterlab Python version：
!python --version
```
{{% /details %}}

<br>

***<font color=Coral face=Georgia >2.3.2、Python 显示设置</font>***

{{% details title="<font color=Gray face=Georgia size=3>（1）、*pandas，numpy，matplotlib 显示设置*</font>" closed="true" %}}
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



### **<font face=Georgia>2.4、数据导入：</font>**

#### ***<font face=Georgia >2.4.1、创建数据</font>***

{{% details title="<font color=Gray face=Georgia size=3>（1）、*sklearn*</font>" closed="true" %}}

{{% /details %}}






<br><br><br>





## ***<font face=Georgia>5、数据建模</font>***

- <font color=Coral face=Georgia  >《Machine Learning with Python Cookbook》</font>

<br>

### ***<font face=Georgia>5.1、模型评估：</font>***

#### <font face=Georgia >5.1.1、*留出法：训练\测试*</font>

{{% details title="<font color=Gray face=Georgia size=3>（1）、*sklearn.model_selection.train_test_split()*</font>" closed="true" %}}
```python {linenos=table, linenostart=1}
# Load libraries
from sklearn import datasets

from sklearn.model_selection import train_test_split
from sklearn.preprocessing import StandardScaler
from sklearn.linear_model import LogisticRegression

# Load digits dataset
digits = datasets.load_digits()
features, target = digits.data, digits.target


# Create training and test sets
features_train, features_test, target_train, target_test = train_test_split(
    features, target, test_size=0.1, random_state=1)

# stratify = y 
# shuffle = True # 打乱排序

# Create standardizer
standardizer = StandardScaler()

# Fit standardizer to training set
standardizer.fit(features_train)

# Apply to both training and test sets which can then be used to trainmodels
features_train_std = standardizer.transform(features_train)
features_test_std = standardizer.transform(features_test)

model = LogisticRegression()
model.fit(features_train_std , target_train)
result = model.score(features_test_std , target_test )
print(("Accuracy: %.3f%%") % (result*100.0))
```
> Accuracy: 97.778%
{{% /details %}}



<br>



#### ***<font  face=Georgia >5.1.2、交叉验证</font>***

{{% details title="<font color=Gray face=Georgia   size=3>（1）、*sklearn.model_selection.KFold() —— K 折交叉验证*</font>" closed="true" %}}
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
```
> 0.9277777777777778<br>
> 0.875<br>
> 0.9415041782729805<br>
> 0.9387186629526463<br>
> 0.9080779944289693<br>
{{% /details %}}



{{% details title="<font color=Gray face=Georgia   size=3>（2）、*sklearn.model_selection.cross_val_score() —— K 折交叉验证*</font>" closed="true" %}}
```python {linenos=table, linenostart=1}
from sklearn import datasets, linear_model
from sklearn.model_selection import cross_val_score
diabetes = datasets.load_diabetes()
X = diabetes.data[:150]
y = diabetes.target[:150]
lasso = linear_model.Lasso()
print(cross_val_score(lasso, X, y, cv=3))
```
> 1. cross_val_score(): 这是一个非常方便的函数，允许你只需一行代码就能实现交叉验证的过程。它自动处理数据的分割、模型的训练以及对模型进行评估的过程。cross_val_score()函数接受一个估计器对象（例如，你的模型）、所有的数据和目标标签，然后返回一个得分列表，列表中的每个得分对应于一次迭代的结果。
> 2. KFold(): 这是一个更为灵活的工具，允许你更精细地控制交叉验证的过程。KFold()通过接受一个整数n，然后生成一个迭代器，这个迭代器会将你的数据集分割成n个连续的折叠。在每次迭代中，它会返回训练集和测试集的索引，然后你可以使用这些索引来划分数据并训练模型。使用KFold()可以让你有机会在每次迭代中手动处理数据和模型，提供了更高的灵活性。
> - 总的来说，cross_val_score()和KFold()都能进行交叉验证，但前者提供了更快捷的方式，后者则提供了更高的灵活性。你可以根据实际的需求选择使用哪一个。
{{% /details %}}





{{% details title="<font color=Gray face=Georgia   size=3>（3）、*sklearn.model_selection.KFold(), cross_val_score() —— K 折交叉验证*</font>" closed="true" %}}
```python {linenos=table, linenostart=1}
# Load libraries
from sklearn import datasets

from sklearn.pipeline import make_pipeline
from sklearn.preprocessing import StandardScaler
from sklearn.model_selection import KFold, cross_val_score
from sklearn.linear_model import LogisticRegression
from sklearn import metrics

# Load digits dataset
digits = datasets.load_digits()
features, target = digits.data, digits.target

standardizer = StandardScaler() # Create standardizer
logit = LogisticRegression() # Create logistic regression object

# Create a pipeline that standardizes, then runs logistic regression
pipeline = make_pipeline(
      standardizer
    , logit
    )

# Create k-fold cross-validation
kf = KFold(
      n_splits=5
    , shuffle=True # 数据是独立且相同分布的,分配到褶皱时，打乱观测结果
    , random_state=0
    )

# Conduct k-fold cross-validation
cv_results = cross_val_score(
      pipeline # Pipeline
    , features # Feature matrix
    , target # Target vector
    , cv=kf # Performance metric
    , scoring="accuracy" # Loss function
    , n_jobs=-1
    ) # Use all CPU cores

# Calculate mean
print(cv_results.mean())

# View score for all 5 folds
print(cv_results)
```
> 0.969958217270195<br>
> [0.96111111 0.96388889 0.98050139 0.97214485 0.97214485]
<br>

> 当我们使用验证集或交叉验证时，重要的是基于训练集对数据进行预处理，然后将这些转换应用于训练集和测试集。 Scikit-learn 的 pipeline 包使这一点在使用交叉验证技术时变得容易。我们首先创建一个对数据进行预处理的管道（例如，标准化器），然后训练一个模型（逻辑回归， logit）：
```python {linenos=table, linenostart=1}
# Create a pipeline
pipeline = make_pipeline(standardizer, logit)
```
> 然后，我们使用该管道运行KFCV，sklearn 为我们完成所有工作：
```python {linenos=table, linenostart=1}
# Conduct k-fold cross-validation
cv_results = cross_val_score(
    pipeline # Pipeline
    , features # Feature matrix
    , target # Target vector
    , cv=kf # Performance metric
    , scoring="accuracy" # Loss function
    , n_jobs=-1
    ) # Use all CPU cores
```
{{% /details %}}




{{% details title="<font color=Gray face=Georgia size=3>（4）、*sklearn.model_selection.LeaveOneOut(), cross_val_score() —— 留一交叉验证（留一法）*</font>" closed="true" %}}
```python {linenos=table, linenostart=1}
from sklearn.model_selection import LeaveOneOut
from sklearn.model_selection import cross_val_score
from sklearn.linear_model import LogisticRegression


from sklearn import datasets

# Load digits dataset
digits = datasets.load_digits()
X, Y = digits.data, digits.target

loocv = LeaveOneOut()
model = LogisticRegression(max_iter=1000)
results = cross_val_score(model, X, Y, cv=loocv)
print("Accuracy: %.3f%% (%.3f%%)") % (results.mean()*100.0, results.std()*100.0)
```
{{% /details %}}





{{% details title="<font color=Gray face=Georgia size=3>（5）、*sklearn.model_selection.GroupKFold() —— 分组 K 折交叉验证*</font>" closed="true" %}}
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
{{% /details %}}



{{% details title="<font color=Gray face=Georgia size=3>（6）、*sklearn.model_selection.StratifiedKFold() —— 分层 K 折交叉验证*</font>" closed="true" %}}
```python {linenos=table, linenostart=1}
from sklearn.model_selection import StratifiedKFold
from sklearn.datasets import make_classification
from sklearn.linear_model import LogisticRegression
from sklearn.metrics import accuracy_score

# 生成一个二分类数据集
X, y = make_classification(n_samples=100, n_features=20, n_informative=2, n_redundant=10, random_state=42)

# 实例化分层k-fold对象
skf = StratifiedKFold(n_splits=5)

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
```
{{% /details %}}

<br>

> ***<font color=DarkCyan face=Georgia  >将交叉验证的结果存储下来，或是新建一列存储交叉验证的折数；</font>***


{{% details title="<font color=Gray face=Georgia size=3>（1）、*sklearn.model_selection.KFold() —— K 折交叉验证*</font>" closed="true" %}}
- 我们可以使用来自scikit learn的KFold将任何数据拆分为k等分。当使用k倍交叉验证时，每个样本被分配一个从0到k-1的值。
```python {linenos=table, linenostart=1}
import pandas as pd
from sklearn import model_selection

if __name__ == "__main__":
    # Training data is in a CSV file called train.csv
    df = pd.read_csv('datasets/wine/train.csv')
  
    # we create a new column called kfold and fill it with -1
    df["kfold"] = -1

    # use sample with frac=1 to shuffle the dataframe
    # the next step is to randomize the rows of the data
    df = df.sample(frac=1, random_state=2).reset_index(drop=True)
  
    # initiate the kfold class from model_selection module
    kf = model_selection.KFold(n_splits=5) 
    # shuffle=True # 打乱观测结果
    # random_state=0
  
    # fill the new kfold column
    for fold, (trn_, val_) in enumerate(kf.split(X=df)):
        df.loc[val_, 'kfold'] = fold
      
    # save the new csv with kfold column
    df.to_csv("train_folds.csv", index=False)
```
```python {linenos=table, linenostart=1}
for fold, (trn_, val_) in enumerate(kf.split(X=df)):
    print(fold, (trn_, val_))
```
{{% /details %}}



{{% details title="<font color=Gray face=Georgia size=3>（2）、*sklearn.model_selection.StratifiedKFold() —— 分层 K 折交叉验证*</font>" closed="true" %}}
```python {linenos=table, linenostart=1}
# import pandas and model_selection module of scikit-learn
import pandas as pd
from sklearn import model_selection

if __name__ == "__main__":
    # Training data is in a csv file called train.csv
    df = pd.read_csv("datasets/wine/train.csv")
  
    # we create a new column called kfold and fill it with -1
    df["kfold"] = -1
  
    # the next step is to randomize the rows of the data
    df = df.sample(frac=1).reset_index(drop=True)
  
    # fetch targets
    #y = df.target.values
    y = df.iloc[:, -1].values
  
    # initiate the kfold class from model_selection module
    kf = model_selection.StratifiedKFold(n_splits=5)
  
    # fill the new kfold column
    for f, (t_, v_) in enumerate(kf.split(X=df, y=y)):
        df.loc[v_, 'kfold'] = f
      
    # save the new csv with kfold column
    df.to_csv("train_folds.csv", index=False)
```
{{% /details %}}



{{% details title="<font color=Gray face=Georgia size=3>（3）、*sklearn.model_selection.StratifiedKFold() —— 回归分层 K 折交叉验证*</font>" closed="true" %}}
```python {linenos=table, linenostart=1}
# 回归分层交叉验证

import numpy as np
import pandas as pd
from sklearn import datasets
from sklearn import model_selection

def create_folds(data):
    # we create a new column called kfold and fill it with -1
    data["kfold"] = -1
  
    # the next step is to randomize the rows of the data
    data = data.sample(frac=1).reset_index(drop=True)
  
    # calculate the number of bins by Sturge's rule
    # I take the floor of the value, you can also
    # just round it
    num_bins = int(np.floor(1 + np.log2(len(data))))
  
    # bin targets
    data.loc[:, "bins"] = pd.cut(
        data["target"], bins=num_bins, labels=False
    )
    # initiate the kfold class from model_selection module
    kf = model_selection.StratifiedKFold(n_splits=5)
  
    # fill the new kfold column
    # note that, instead of targets, we use bins!
    for f, (t_, v_) in enumerate(kf.split(X=data, y=data.bins.values)):
        data.loc[v_, 'kfold'] = f
      
    # drop the bins column
    data = data.drop("bins", axis=1)
    # return dataframe with folds
    return data

if __name__ == "__main__":
    # we create a sample dataset with 15000 samples
    # and 100 features and 1 target
    X, y = datasets.make_regression(
        n_samples=15000, n_features=100, n_targets=1
    )
    # create a dataframe out of our numpy arrays
    df = pd.DataFrame(
        X,columns=[f"f_{i}" for i in range(X.shape[1])]
    )
    df.loc[:, "target"] = y
    # create folds
    df = create_folds(df)
```
{{% /details %}}



{{% details title="<font color=Gray face=Georgia size=3>（4）、*sklearn.model_selection.StratifiedKFold()，GroupKFold() —— 分层分组 K 折交叉验证*</font>" closed="true" %}}
```python {linenos=table, linenostart=1}
import numpy as np
from sklearn.model_selection import StratifiedKFold, GroupKFold

class GroupedStratifiedKFold():

    def __init__(self, n_splits=5):
        self.n_splits = n_splits

    def split(self, X, y=None, groups=None):
        kfold = StratifiedKFold(self.n_splits)

        unique_groups = np.unique(groups)
        group_kfold = GroupKFold(self.n_splits)

        for train_groups, test_groups in group_kfold.split(X, y, groups=unique_groups):
            train_indices = np.isin(groups, unique_groups[train_groups]).astype(int)
            test_indices = np.isin(groups, unique_groups[test_groups]).astype(int)

            for train_idx, test_idx in kfold.split(X[train_indices == 1], y[train_indices == 1]):
                yield (train_idx, test_idx)

# 使用方式
grouped_stratkfold = GroupedStratifiedKFold(n_splits=5)
for train_idx, test_idx in grouped_stratkfold.split(X, y, groups):
    X_train, y_train = X.iloc[train_idx], y.iloc[train_idx]
    X_test, y_test = X.iloc[test_idx], y.iloc[test_idx]
```
{{% /details %}}


<br>



#### ***<font  face=Georgia >5.1.3、自助法</font>***

{{% details title="<font color=Gray face=Georgia   size=3>（1）、*sklearn.model_selection.ShuffleSplit() —— 重复随机拆分\抽样*</font>" closed="true" %}}
```python {linenos=table, linenostart=1}
import warnings
warnings.filterwarnings("ignore")

from sklearn.model_selection import ShuffleSplit
from sklearn.model_selection import cross_val_score
from sklearn.linear_model import LogisticRegression

kfold = ShuffleSplit(n_splits=10, test_size=0.33, random_state=42)
model = LogisticRegression()
results = cross_val_score(model, X, y, cv=kfold)
print(("Accuracy: %.3f%% (%.3f%%)") % (results.mean()*100.0, results.std()*100.0))
```
{{% /details %}}




{{% details title="<font color=Gray face=Georgia   size=3>（2）、*sklearn.utils.resample() —— 放回随机抽样*</font>" closed="true" %}}
```python {linenos=table, linenostart=1}
# 放回随机抽取4个样本
from sklearn.utils import resample

train = resample(df, replace=True, n_samples=4, random_state=42)
```
{{% /details %}}




<br><br><br>




### ***<font face=Georgia>5.2、评估指标：</font>***


<br>

#### <font face=Georgia >5.2.1、*分类*</font>

***<font color=Coral face=Georgia   size=3>1、Accuracy (A) 准确性\准确率：</font>***

{{% details title="<font color=Gray face=Georgia   size=3>（1）、*Python code writing*</font>" closed="true" %}}
```python {linenos=table, linenostart=1}
def accuracy(y_true, y_pred):
    """
    Function to calculate accuracy
    :param y_true: list of true values
    :param y_pred: list of predicted values
    :return: accuracy score
    """
  
    # initialize a simple counter for correct predictions
    correct_counter = 0
  
    # loop over all elements of y_true
    # and y_pred "together"
    for yt, yp in zip(y_true, y_pred):
        if yt == yp:
        # if prediction is equal to truth, increase the counter
            correct_counter += 1
        
    # return accuracy
    # which is correct predictions over the number of samples
    return correct_counter / len(y_true)

if __name__ == "__main__":
    l1 = [0,1,1,1,0,0,0,1]
    l2 = [0,1,0,1,0,1,0,0]
    print(accuracy(l1, l2))
```
{{% /details %}}



{{% details title="<font color=Gray face=Georgia   size=3>（2）、*Sklearn.metrics.accuracy_score()*</font>" closed="true" %}}
```python {linenos=table, linenostart=1}
from sklearn.metrics import accuracy_score
l1 = [0,1,1,1,0,0,0,1]
l2 = [0,1,0,1,0,1,0,0]

accuracy_score(l1, l2)
```
```python {linenos=table, linenostart=1}
# Load libraries
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LogisticRegression
from sklearn.metrics import accuracy_score
from sklearn.datasets import make_classification

# Generate features matrix and target vector
X, y = make_classification(
     n_samples = 10000
    ,n_features = 3
    ,n_informative = 3
    ,n_redundant = 0
    ,n_classes = 2 # 3 Multiclass
    ,random_state = 1
    )

# Create training and test split
X_train, X_test, y_train, y_test = train_test_split(X,y,test_size=0.1,random_state=1)

# Create logistic regression
logit = LogisticRegression()

# Predict values for training target vector
y_hat = logit.fit(X_train, y_train).predict(X_test)

# Calculate accuracy
accuracy_score(y_test, y_hat)
```
{{% /details %}}



{{% details title="<font color=Gray face=Georgia   size=3>（3）、*Sklearn.model_selection.cross_val_score(model, X, y, scoring='accuracy')*</font>" closed="true" %}}
```python {linenos=table, linenostart=1}
import numpy as np
np.set_printoptions(formatter={'float': '{: 0.3f}'.format})


# Load libraries
from sklearn.model_selection import cross_val_score
from sklearn.linear_model import LogisticRegression
from sklearn.datasets import make_classification

# Generate features matrix and target vector
X, y = make_classification(
     n_samples = 10000
    ,n_features = 3
    ,n_informative = 3
    ,n_redundant = 0
    ,n_classes = 2
    ,random_state = 1
    )

# Create logistic regression
logit = LogisticRegression()

# Cross-validate model using accuracy
cross_val_score(logit, X, y, scoring="accuracy")
```
{{% /details %}}



{{% details title="<font color=Gray face=Georgia   size=3>（4）、*Sklearn.model_selection.cross_val_score(model, X, Y, cv=kfold, scoring=scoring)*</font>" closed="true" %}}
```python {linenos=table, linenostart=1}
# Cross Validation Classification Accuracy
from pandas import read_csv
from sklearn.model_selection import KFold
from sklearn.model_selection import cross_val_score
from sklearn.linear_model import LogisticRegression

filename = 'datasets/pima-indians-diabetes.data.csv'
names = ['preg', 'plas', 'pres', 'skin', 'test', 'mass', 'pedi', 'age', 'class']
dataframe = read_csv(filename, names=names)


array = dataframe.values
X = array[:,0:8]
Y = array[:,8]

kfold = KFold(n_splits=10, random_state=7, shuffle=True)
model = LogisticRegression(max_iter=10000)

results = cross_val_score(model, X, Y, cv=kfold, scoring="accuracy")
print(("Accuracy: %.3f (%.3f)") % (results.mean(), results.std()))
results
```
{{% /details %}}



<br>


***<font color=Coral face=Georgia   size=3>2、Precision (P) 精确率\查准率：</font>***

{{% details title="<font color=Gray face=Georgia   size=3>（1）、*Sklearn.model_selection.cross_val_score(model, X, y, scoring='precision')*</font>" closed="true" %}}
```python {linenos=table, linenostart=1}
# Cross-validate model using precision
cross_val_score(logit, X, y, scoring="precision")
```
{{% /details %}}



<br>


***<font color=Coral face=Georgia   size=3>3、Recall (R) 召回率\查全率：</font>***

{{% details title="<font color=Gray face=Georgia   size=3>（1）、*Sklearn.model_selection.cross_val_score(model, X, y, scoring='recall')*</font>" closed="true" %}}
```python {linenos=table, linenostart=1}
# Cross-validate model using recall
cross_val_score(logit, X, y, scoring="recall")
```
{{% /details %}}



<br>


***<font color=Coral face=Georgia   size=3>4、P-R曲线（Precision Recall Curve）：</font>***

{{% details title="<font color=Gray face=Georgia   size=3>（1）、*Sklearn.metrics.precision_recall_curve()*</font>" closed="true" %}}
```python {linenos=table, linenostart=1}
from sklearn.metrics import precision_recall_curve
import matplotlib.pyplot as plt
from sklearn.svm import SVC
from sklearn.datasets import make_classification

# 创建一个简单的二分类数据集
X, y = make_classification(n_samples=1000, n_classes=2, random_state=1)

# 使用支持向量机分类器
classifier = SVC(random_state=1, kernel='linear', probability=True)
classifier.fit(X, y)

# 获取预测的概率
probs_y = classifier.predict_proba(X)

# 计算Precision-Recall值
precision, recall, _ = precision_recall_curve(y, probs_y[:, 1])

# 绘制Precision-Recall曲线
plt.plot(recall, precision)
plt.xlabel('Recall')
plt.ylabel('Precision')
plt.title('Precision-Recall Curve')
plt.show()
```
{{% /details %}}



<br>


***<font color=Coral face=Georgia   size=3>5、F1-Score（F1 分数）：精确率（Precision）和召回率（Recall）的调和平均数</font>***

{{% details title="<font color=Gray face=Georgia   size=3>（1）、*sklearn.model_selection.cross_val_score(model, X, y, scoring='f1')*</font>" closed="true" %}}
```python {linenos=table, linenostart=1}
# Cross-validate model using F1
cross_val_score(logit, X, y, scoring="f1")
```
{{% /details %}}



<br>


***<font color=Coral face=Georgia   size=3>6、ROC曲线：真正例率（TPR）\敏感度或召回率为纵轴，假正例率（FPR）\（1-特异度）为横轴</font>***

{{% details title="<font color=Gray face=Georgia   size=3>（1）、*sklearn.metrics.roc_curve(), auc()*</font>" closed="true" %}}
```python {linenos=table, linenostart=1}
from sklearn.metrics import roc_curve, auc
from sklearn.model_selection import train_test_split
from sklearn.datasets import load_breast_cancer
from sklearn.linear_model import LogisticRegression
import matplotlib.pyplot as plt

# 读取数据
data = load_breast_cancer()
X = data.data
y = data.target

# 划分数据集
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.3, random_state=0)

# 训练模型
model = LogisticRegression()
model.fit(X_train, y_train)

# 预测，并计算ROC曲线的值
y_score = model.predict_proba(X_test)[:, 1]
fpr, tpr, _ = roc_curve(y_test, y_score)
roc_auc = auc(fpr, tpr)

# 绘制ROC曲线
plt.figure()
lw = 2
plt.plot(fpr, tpr, color='darkorange',
         lw=lw, label='ROC curve (area = %0.2f)' % roc_auc)
plt.plot([0, 1], [0, 1], color='navy', lw=lw, linestyle='--')
plt.xlim([0.0, 1.0])
plt.ylim([0.0, 1.05])
plt.xlabel('False Positive Rate')
plt.ylabel('True Positive Rate')
plt.title('Receiver Operating Characteristic Example')
plt.legend(loc="lower right")
plt.show()
```
{{% /details %}}



<br><br>


#### <font face=Georgia >5.2.2、*回归*</font>



***<font color=Coral face=Georgia   size=3>1、Mean absolute error (MAE) 平均绝对误差</font>***

{{% details title="<font color=Gray face=Georgia   size=3>（1）、*cross_val_score(model, X, y, scoring='neg_mean_absolute_error')*</font>" closed="true" %}}
```python {linenos=table, linenostart=1}
# Load libraries
from sklearn.datasets import make_regression
from sklearn.model_selection import cross_val_score
from sklearn.linear_model import LinearRegression

# Generate features matrix, target vector
features, target = make_regression(
     n_samples = 100
    ,n_features = 3
    ,n_informative = 3
    ,n_targets = 1
    ,noise = 50
    ,coef = False
    ,random_state = 1
    )

# Create a linear regression object
ols = LinearRegression()

# Cross-validate the linear regression using (negative) MSE
cross_val_score(ols, features, target, scoring='neg_mean_absolute_error')
```
{{% /details %}}



<br>



***<font color=Coral face=Georgia   size=3>2、Mean squared error (MSE) 均方误差</font>***

{{% details title="<font color=Gray face=Georgia   size=3>（1）、*cross_val_score(model, X, y, scoring='neg_mean_squared_error')*</font>" closed="true" %}}
```python {linenos=table, linenostart=1}
# Cross-validate the linear regression using (negative) MSE
cross_val_score(ols, features, target, scoring='neg_mean_squared_error')
```
{{% /details %}}



<br>



***<font color=Coral face=Georgia   size=3>3、Root mean squared error (RMSE) 均方根误差</font>***

{{% details title="<font color=Gray face=Georgia   size=3>（1）、*cross_val_score(model, X, y, scoring='neg_mean_squared_error')，np.sqrt()*</font>" closed="true" %}}
```python {linenos=table, linenostart=1}
from sklearn.model_selection import cross_val_score
from sklearn.linear_model import LinearRegression
import numpy as np

# 假设 X 是特征数据，y 是目标数据
# 初始化你的模型，比如线性回归模型
model = LinearRegression()

# 使用负均方误差进行交叉验证
mse_scores = cross_val_score(model, X, y, scoring='neg_mean_squared_error', cv=5)

# inversed negative MSE to positive
mse_scores_positive = -mse_scores

# 计算每次迭代的RMSE，然后取平均值
rmse_scores = np.sqrt(mse_scores_positive)
avg_rmse = np.mean(rmse_scores)

print("RMSE Scores: ", rmse_scores)
print("Average RMSE: ", avg_rmse)
```
{{% /details %}}



<br>



***<font color=Coral face=Georgia   size=3>4、Root mean squared logarithmic error (RMSLE) 均方根对数误差</font>***

{{% details title="<font color=Gray face=Georgia   size=3>（1）、*cross_val_score(model, X, y, scoring='neg_mean_squared_log_error')，np.sqrt()*</font>" closed="true" %}}
```python {linenos=table, linenostart=1}
from sklearn.model_selection import cross_val_score
from sklearn.linear_model import LinearRegression
import numpy as np

# 假设 X 是特征数据，y 是目标数据
# 初始化你的模型，比如线性回归模型
model = LinearRegression()

# 使用负均方对数误差进行交叉验证
msle_scores = cross_val_score(model, X, y, scoring='neg_mean_squared_log_error', cv=5)

# 转换为正的均方对数误差（MSLE）
msle_scores_positive = -msle_scores

# 计算每次迭代的 RMSLE，并取平均值
rmsle_scores = np.sqrt(msle_scores_positive)
avg_rmsle = np.mean(rmsle_scores)

print("RMSLE Scores: ", rmsle_scores)
print("Average RMSLE: ", avg_rmsle)
```
{{% /details %}}




<br>



***<font color=Coral face=Georgia   size=3>5、Mean percentage error (MPE) 平均百分比误差</font>***

{{% details title="<font color=Gray face=Georgia   size=3>（1）、*make_scorer(自定义评价函数)*</font>" closed="true" %}}
```python {linenos=table, linenostart=1}
from sklearn.model_selection import cross_val_score
from sklearn.metrics import make_scorer
from sklearn.linear_model import LinearRegression
import numpy as np

# 假设 X 是特征数据，y 是目标数据
# 初始化你的模型，比如线性回归模型
model = LinearRegression()

# 定义MPE计算函数
def mean_percentage_error(y_true, y_pred): 
    return np.mean((y_true - y_pred) / y_true) * 100

# 创建MPE评估器
mpe = make_scorer(mean_percentage_error, greater_is_better=False)

# 使用MPE进行交叉验证
mpe_scores = cross_val_score(model, X, y, scoring=mpe, cv=5)

print("MPE Scores: ", mpe_scores)
print("Average MPE: ", np.mean(mpe_scores))
```
{{% /details %}}




<br>



***<font color=Coral face=Georgia   size=3>6、Mean absolute percentage error (MAPE) 平均绝对百分比误差</font>***

{{% details title="<font color=Gray face=Georgia   size=3>（1）、*make_scorer(自定义评价函数)*</font>" closed="true" %}}
```python {linenos=table, linenostart=1}
from sklearn.model_selection import cross_val_score
from sklearn.metrics import make_scorer
from sklearn.linear_model import LinearRegression
import numpy as np

# 假设 X 是特征数据，y 是目标数据
# 初始化你的模型，比如线性回归模型
model = LinearRegression()

# 定义 MAPE 计算函数
def mean_absolute_percentage_error(y_true, y_pred):
    return np.mean(np.abs((y_true - y_pred) / y_true)) * 100

# 创建 MAPE 评估器
mape = make_scorer(mean_absolute_percentage_error, greater_is_better=False)

# 使用 MAPE 进行交叉验证
mape_scores = cross_val_score(model, X, y, scoring=mape, cv=5)

print("MAPE Scores: ", mape_scores)
print("Average MAPE: ", np.mean(mape_scores))
```
{{% /details %}}




<br>



***<font color=Coral face=Georgia   size=3>7、$R^2$</font>***

{{% details title="<font color=Gray face=Georgia   size=3>（1）、*cross_val_score(model, X, y, scoring='r2')*</font>" closed="true" %}}
```python {linenos=table, linenostart=1}
```
{{% /details %}}




<br><br><br>




### ***<font face=Georgia>5.3、模型选择：</font>***




<br><br><br>




### ***<font face=Georgia>5.4、模型解释：</font>***





<br><br><br>






### ***<font face=Georgia>5.5、模型部署：</font>***

















