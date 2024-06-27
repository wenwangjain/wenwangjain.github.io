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

 - --

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

{{< tabs items="（1）Python 查看库版本>,（2）Python 显示设置>" >}}

{{< tab >}}
```python {linenos=table, linenostart=1, filename="example 1"}
# numpy,pandas,matplotlib,sklearn,seaborn version
%load_ext watermark
%watermark -a "Sebastian Raschka" -u -d -v -p numpy,pandas,matplotlib,sklearn,seaborn
```

```python {linenos=table, linenostart=1, filename="example 2"}
# pandas version
import pandas
print('pandas: {}'.format(pandas.__version__))
```

```python {linenos=table, linenostart=1, filename="example 3"}
# jupyterlab Python version：
!python --version
```
{{< /tab >}}


{{< tab >}}
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
{{< /tab >}}

{{< /tabs >}}



<br><br><br>



### **<font face=Georgia>2.4、数据导入：</font>**

{{< tabs items="（1）pd.DataFrame()>,（2）>" >}}

{{< tab >}}
{{< /tab >}}

{{< tab >}}
{{< /tab >}}

{{< tab >}}
{{< /tab >}}

{{< tab >}}
{{< /tab >}}

{{< tab >}}
{{< /tab >}}

{{< tab >}}
{{< /tab >}}

{{< tab >}}
{{< /tab >}}

{{< tab >}}
{{< /tab >}}

{{< /tabs >}}












<br><br><br>





## ***<font face=Georgia>5、数据建模</font>***

- <font color=Coral face=Georgia  >《Machine Learning with Python Cookbook》</font>

### ***<font face=Georgia>5.1、模型评估：</font>***

#### <font color=Coral face=Georgia>5.1.1、*留出法：训练\测试*</font>

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








#### ***<font color=Coral face=Georgia>5.1.2、交叉验证</font>***

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























