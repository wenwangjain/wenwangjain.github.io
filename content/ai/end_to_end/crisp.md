---
title: 4️⃣ 步骤
weight: 114
prev: /end_to_end
type: "docs" 
toc: true
math: true
---

## 1、定义问题

1. 问题是什么？
2. 为什么需要解决问题？
3. 探索如何解决问题？

{{< callout emoji=📝 type='default' >}}
参考网址\书籍：
1. https://machinelearningmastery.com/how-to-define-your-machine-learning-problem/
{{< /callout >}}

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



<br><br>



## 2、收集数据

### 2.1、数据来源

1. ***数据文件***： 这是存储数据的常见形式，例如 CSV（逗号分隔值）文件、Excel 文件、JSON 文件、XML 文件等。数据文件通常以结构化或半结构化的方式组织数据，可以通过读取文件的方式将数据导入到应用程序或分析工具中。
2. ***数据库***： 是专门用于存储和管理数据的系统，如关系型数据库（如 MySQL、Oracle、SQL Server 等）和非关系型数据库（如 MongoDB、Cassandra 等）。数据库提供了高效的数据存储、检索、更新和管理功能，并支持复杂的查询和事务处理。
3. ……

<br>

### 2.2、选择数据

选择将要使用的所有可用数据的子集。需要考虑实际需要哪些数据来解决您正在处理的问题或难题。对所需的数据进行一些假设，并小心记录这些假设，以便以后可以在需要时对其进行测试。

> 以下是一些问题，可帮助您思考整个过程：
 - 您拥有的数据范围有多大？例如，申请使用通过时间，数据库表数量，连接的系统。确保您对可以使用的所有内容都有清晰的了解。
 - 哪些数据不可用，而您希望您有这些数据？例如，未记录或无法记录的数据。您可以派生或模拟此数据。
 - 您不需要哪些数据来解决问题？排除数据几乎总是比包含数据更容易。记下您排除了哪些数据及其原因。
 - 只有在小问题中，例如竞赛或玩具数据集，数据已经为您选择了。
 - 您选择的数据可能格式不适合使用。数据可能位于关系数据库中，您希望它位于平面文件中，或者数据可能采用专有文件格式。

<br>

### 2.3、工作空间

工作空间可以理解为数据科学项目的目录结构\项目模板。

{{< callout emoji=📝 type='default' >}}
参考网址\书籍：
1. 《Approaching (Almost)  Any Machine Learning Problem》 Abhishek Thakur
{{< /callout >}}

{{< tabs items="1️⃣ 创建工作空间案例1, 2️⃣ 创建工作空间案例2" >}}
{{< tab >}}
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
{{< /tab >}}

{{< tab >}}
```python
import os

project_name = 'Kaggle_002_class-name'
folder_name  = ['input', 'src', 'models', 'notebooks']
file_name    = ['README.md', 'LICENSE']
file_list    = os.listdir()

if project_name not in file_list:
  
    # （1）、如果该空间不存在则创建工作空间
    os.mkdir(project_name)
  
    # （2）、创建文件夹：'input', 'src', 'models', 'notebooks'
    for i in folder_name:
        path_folder = os.path.join(project_name, i)
        os.mkdir(path_folder)
      
    # （3）、创建文件：'README.md', 'LICENSE'
    for j in file_name:
        path_file = os.path.join(project_name, j)
        open(path_file, 'w', encoding='utf-8')
  
    print(project_name + ' is OK!')
    
else:
    print(project_name + ' is OK!')
```
{{< /tab >}}
{{< /tabs >}}


<br>


### 2.4、显示设置\库版本


{{< tabs items="1️⃣ 查看库版本, 2️⃣ 显示设置, 3️⃣ 显示设置案例" >}}
{{< tab >}}

***（1）`%load_ext watermark` 查看库版本：***

```python
# 在 jupyter lab 执行以下代码查看库版本
# 需要先安装 watermark 库
# numpy,pandas,matplotlib,sklearn,seaborn version
%load_ext watermark
%watermark -a "Sebastian Raschka" -u -d -v -p\
    numpy,pandas,matplotlib,sklearn,seaborn
```

```
Author: Sebastian Raschka<br>
<br>
Last updated: 2025-07-25<br>
<br>
Python implementation: CPython<br>
Python version       : 3.12.7<br>
IPython version      : 8.27.0<br>
<br>
numpy     : 1.26.4<br>
pandas    : 2.2.2<br>
matplotlib: 3.9.2<br>
sklearn   : 1.5.1<br>
seaborn   : 0.13.2<br>
```

<br>

***（2）`xxx.\_\_version\_\_` 查看库版本：***

```python
# 在 jupyter lab 执行以下代码查看 pandas 版本
import pandas
print('pandas: {}'.format(pandas.__version__))
```
pandas: 2.2.2

<br>

***（3）`!python --version` 查看 python 版本：***

```python
# 在 jupyter lab 执行以下代码查看 python 版本
!python --version
```
Python 3.12.7

{{< /tab >}}


{{< tab >}}

这里介绍的显示设置主要是关于 pandas 数据框，numpy 数组，matplotlib 的一些常规显示设置 。如，小数位数，matplotlib 主题等，主要是在 jupyter lab 中展示时需要设置。

```python
# （1）禁止显示不需要的警告
# -------------------------
import warnings
warnings.filterwarnings("ignore") 


# （2）pandas 设置
# -------------------------

pd.set_option('display.max_info_columns',200) # info()变量最多显示200个
pd.set_option('display.max_info_rows',200)    # info()缺失值个数上限

pd.set_option('display.float_format','${:,.2f}'.format)  # 显示格式 $0.67
pd.set_option('display.unicode.east_asian_width', False) # 设置输出右对齐，此代码写入脚本中
pd.set_option('display.precision',4)          # 保留4位小数
pd.set_option('precision', 3)                 # 保留3位小数
pd.set_option('display.chop_threshold',0.5)   # 绝对值小于 0.5 显示 0

pd.set_option('display.max_rows',5)           # 设置显示数据框行数       
pd.set_option('display.max_columns',100)      # 设置显示数据框列数 
pd.set_option('display.max_colwidth',200)     # 设置显示数据框列宽       
pd.options.display.max_colwidth = 80          # 设置显示数据框列宽  
pd.options.display.max_columns = 20           # 设置显示数据框列数 
pd.options.display.max_rows = 20              # 设置显示数据框行数

pd.set_option('display.colheader_justify', 'left') # 确保列名不换行


# （3）matplotlib 设置
# -------------------------
plt.rcParams['font.sans-serif']=['FangSong']  # 替换sans-serif字体，正常显示中文(黑体)\'SimHei'\'FangSong' 
plt.rcParams["font.weight"] = "bold"          # 字体加粗
plt.rcParams['axes.unicode_minus'] = False    # 坐标显示负号
plt.rcParams['savefig.dpi'] = 1000            # 图片像素
plt.rcParams['figure.dpi'] = 100              # 分辨率（不常用）

plt.style.use('classic')                      # 设置绘图风格'ggplot'\'classic' 
matplotlib.rcdefaults()                       # 使用默认绘图风格


# （4）numpy 设置
# -------------------------
np.set_printoptions(precision=3, suppress=True) # precision：保留几位小数，后面不会补0，supress=True：对很大/小的数不使用科学计数法
np.set_printoptions(formatter={'float': '{: 0.3f}'.format}) # formatter：强制格式化，后面会补0 
```

{{< /tab >}}


<br>


{{< tab >}}


```python
import numpy as np

# 创建三个随机小数
random_floats = np.random.rand(3)
print(random_floats)
```
[0.28369287 0.16186594 0.76617009]

<br>


```python
# formatter：强制格式化，后面会补0 
np.set_printoptions(
    formatter={'float': '{: 0.3f}'.format}
    )
 
print(random_floats)
```
[ 0.284  0.162  0.766]

<br>


```python
import pandas as pd
# 将列表转换为数据框
pd.DataFrame(random_floats)
```
	
||	0|
|-|-|
|0	|0.283693|
|1	|0.161866|
|2	|0.766170|



<br>

```python
import pandas as pd

# 保留3位小数
pd.set_option('display.precision',3)          
pd.DataFrame(random_floats)
```

||	0|
|-|-|
|0	|0.284|
|1	|0.162|
|2	|0.766|


<br>

```python
import pandas as pd

# 显示格式 $0.67
pd.set_option('display.float_format','${:,.2f}'.format)     
pd.DataFrame(random_floats)
```

||	0|
|-|-|
|0|	$0.28|
|1|	$0.16|
|2|	$0.77|

{{< /tab >}}

{{< /tabs >}}


<br>


### 2.5、导入数据


{{< tabs items="1️⃣ 字典, 2️⃣ 列表, 3️⃣ Sklearn, 4️⃣ .csv, 5️⃣ .xlsx, 6️⃣ 数据库" >}}
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


<br>


### 2.6、导出数据


{{< tabs items="1️⃣ 数据库" >}}
  {{< tab >}}

 ***（1）将 Pandas 数据框导入 MySQL*** 

 > 使用 python pandas 生成一个数据框。

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


> 使用 python sqlalchemy 库将生成的数据直接写入 MySQL。

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






















































































