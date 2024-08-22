---
title: 【3】数据探索
weight: 3
#next: /step1
#prev: /docs
editURL: "https://example.com/edit/this/page"
toc: true
math: true
---

<br>


## 1、主要内容：

***使用可视化、统计方法来了解数据中的结构和关系，主要内容如下：*** 


***1. 初步了解数据集；***
> - 通过描述统计分析，初步了解数据集的分布，数据类型，特征值等信息。


***2. 分类变量分布；***
> - ***众数***：数据集中出现次数最多的类别或值。
> - ***列联表***：一种对两个或两个以上分类变量做计数的表格。
> - ***条形图***：在绘图中，以条形表示每个类别出现的频数或占比情况。
> - ***饼图***：在绘图中，圆饼中的一个扇形部分表示每个类别出现的频数或占比情况。


***3. 数值变量分布；***
> - ***均值（Mean）和标准差（Standard Deviation）***：描述数据集中趋势和离散程度的指标；标准差单位与数据单位相同，更便于理解和比较。
> - 百分位数、箱线图；
> - 直方图、密度图；


***4. 探索各组变量间的关系；***
> - ***相关系数***：一种用于测量数值变量间相关程度的度量，取值范围在 -1 到 +1 之间。相关矩阵，将变量在一个表格中按行和列显示，表格中每个单元格的值是对应变量间的相关性。
> - ***散点图***：在绘图中，x 轴显示一个变量的值，y 轴显示另一个变量的值。
> - ***分类条形图***
> - ***分类占比条形图***



<br><br><br>



## 2、初步了解数据集

### 2.1、常用函数：

|***函数***|***解释***|***函数***|***解释***|
|:-:|:-:|:-:|:-:|
|```df.copy()```         |复制         |```df.sum()```|求和|
|```df.head()```         |查看前 5 行  |```df.mean()```|均值|
|```df.tail(3)```        |查看后 3 行  |```df.median()```|中位数|
|```df.sample(10)```     |随机 10 行   |```df.min()```|最小值|
|```df.shape```          |行\列数      |```df.max()```|最大值|
|```df.columns```        |列名称       |```df.mode()```|众数|
|```df.index```          |行索引       |```df.var()```|无偏方差|
|```df.dtypes```         |数据类型     |```df.std()```|无偏标准差|
|```df.count()```        |非缺失计数    |```df.skew()```  |偏态系数|
|```df.info() ```        |概况         |```df.kurt()```  |峰态系数|
|```df.describe()```     |统计量       |```df['Sex'].unique()```|唯一值|
|```df.describe(include='object')```  ||```df['Sex'].nunique()```|唯一值计数|
|```df.describe(include=['O'])```     ||```np.unique(y)```||
|```df.quantile(q=0.25)```|分位数|```np.bincount(y)```||
|```df.quantile([0.1, 0.9])```||```df['Sex'].value_counts()```|分组计数|
|```df.sort_values(by="B", ascending=False)```|列降序|```df.reset_index()```|索引列|
|```df.sort_index(axis=0, ascending=False)```|轴降序|||





<br><br>



### 2.2、常用 EDA 库：

#### (1). Sweetviz 

> ***生成 EDA 报告***

{{% details title="<font color=Gray size=3>1. sweetviz.analyze()</font>" closed="true" %}}
```python {linenos=table, linenostart=1}
import warnings
warnings.filterwarnings("ignore")

import pandas as pd
train = pd.read_csv('datasets/titanic/train.csv')

import sweetviz as sv

my_report = sv.analyze(
    train
    , target_feat ='Survived' # 目标变量
    )
my_report.show_html()
train.head()
```
{{% /details %}}



{{% details title="<font color=Gray size=3>2. sweetviz.compare_intra()</font>" closed="true" %}}
```python {linenos=table, linenostart=1}
import warnings
warnings.filterwarnings("ignore")

import pandas as pd
train = pd.read_csv('datasets/titanic/train.csv')

# 设置需要分析的变量
my_report = sv.compare_intra(train
    ,train['Survived'] ==0
    ,['Survived_0','Survived_1']
    ,target_feat ='Survived'
)
my_report.show_html()
```
{{% /details %}}



{{% details title="<font color=Gray size=3>3. sweetviz.compare()</font>" closed="true" %}}
```python {linenos=table, linenostart=1}
import warnings
warnings.filterwarnings("ignore")

import pandas as pd
train = pd.read_csv('datasets/titanic/train.csv')

A = train.loc[train['Survived']==0,:]
B = train.loc[train['Survived']!=0,:]

sv.compare([A, 'train_no'], [B, 'train_yes']).show_html( 'sweet_report.html') #.show_notebook()
```
{{% /details %}}


<br><br>


#### (2). pandas_profiling  

> ***生成 EDA 报告***

{{% details title="<font color=Gray size=3>1. Install</font>" closed="true" %}}
```shell
# 安装Jupyter扩展widget 
jupyter nbextension enable --py widgetsnbextension

# 或者通过conda安装
conda env create -n pandas-profiling
conda activate pandas-profiling
conda install -c conda-forge pandas-profiling

# 或者直接从源地址安装
pip install https://github.com/pandas-profiling/pandas-profiling/archive/master.zip
```
{{% /details %}}



{{% details title="<font color=Gray size=3>2. pandas_profiling.ProfileReport()</font>" closed="true" %}}
```python {linenos=table, linenostart=1}
import warnings
warnings.filterwarnings("ignore")

import pandas as pd
train = pd.read_csv('datasets/titanic/train.csv')

from pandas_profiling import ProfileReport
profile = ProfileReport(train
    ,title='MPG Pandas Profiling Report'
    ,explorative = True)

profile
profile.to_file(outputfile="data_profiling.html")
```
{{% /details %}}



<br><br>



#### (3). pygwalker 

> ***类似 Tableau 可视化***

{{% details title="<font color=Gray size=3>1. pygwalker.pyg.walk(train)</font>" closed="true" %}}
```python {linenos=table, linenostart=1}
import warnings
warnings.filterwarnings("ignore")

import pandas as pd
train = pd.read_csv('datasets/titanic/train.csv')

import pygwalker as pyg 
gwalker = pyg.walk(train)
```
{{% /details %}}


<br><br>


#### (4). pivottablejs

> ***透视表\图（chart）***

- https://pypi.org/project/pivottablejs/

{{% details title="<font color=Gray size=3>1. pivottablejs.pivot_ui()</font>" closed="true" %}}
```python {linenos=table, linenostart=1}
import warnings
warnings.filterwarnings("ignore")

import pandas as pd
train = pd.read_csv('datasets/titanic/train.csv')

from pivottablejs import pivot_ui

pivot_ui(train)
```
{{% /details %}}


<br><br>


#### (5). pandasGUI

> ***拖放生成 EDA 图\表***

{{% details title="<font color=Gray size=3>1. install</font>" closed="true" %}}
```python {linenos=table, linenostart=1}
# pip安装
pip install pandasgui

# 或者通过源下载
pip install git+https://github.com/adamerose/pandasgui.git
```
{{% /details %}}


{{% details title="<font color=Gray size=3>2. pandasgui.show()</font>" closed="true" %}}
```python {linenos=table, linenostart=1}
import warnings
warnings.filterwarnings("ignore")

import pandas as pd
train = pd.read_csv('datasets/titanic/train.csv')

from pandasgui import show

# 部署GUI的数据集
gui = show(train)
```
{{% /details %}}


<br><br><br>



### 2.3、自定义函数：

{{< cards >}}
    {{< card link="/docs/ai/end_to_end/crisp/custom_modules" title="EDA.des_table()" icon="back" >}}
    {{< card link="/docs/ai/end_to_end/crisp/custom_modules" title="EDA.des_chart()" icon="back" >}}
{{< /cards >}}

#### (1). EDA.des_table()

```python
from mypackage import View, EDA

columns = ['ID', '姓氏', '性别', '性别', '年龄', ...]

View.title('Preliminary understanding of datasets')
EDA.des_table(train, columns)
```


<br><br>


#### (2). EDA.des_chart(train)

```python
View.title('Preliminary understanding of datasets')
EDA.des_chart(train)
```



<br><br><br>




## 3、探索分类变量：

### 3.1、单个变量

{{< cards >}}
  {{< card link="/docs/ai/end_to_end/crisp/custom_modules" title="EDA.class_bar()" icon="back" >}}
  {{< card link="/docs/ai/end_to_end/crisp/custom_modules" title="EDA.class_pie()" icon="back" >}}
{{< /cards >}}

<br>

{{% details title="<font color=Gray size=3>1. df[].value_counts()</font>" closed="true" %}}
```python {linenos=table, linenostart=1}
df = train.copy()
index = 'Survived'

df_table = pd.DataFrame(df[index].value_counts())
df_table['count_pro'] = df_table['count']/df_table['count'].sum()

View.df_border(df_table.reset_index())
```
{{% /details %}}




{{% details title="<font color=Gray size=3>2. pd.pivot_table()</font>" closed="true" %}}
```python {linenos=table, linenostart=1}
df = train.reset_index()

values = ["index"]
index  = ['Survived']


# ----------------------------------------------------------------------------------------------------
df_table = pd.pivot_table(
     df
    ,values = values
    ,index  = index     
    #,column = 
    #,margins=True
    ,aggfunc=len
    )
df_table.columns = ['count']

df_table["count_pro"] = df_table["count"]/df_table["count"].sum()

View.df_border(df_table.reset_index())

```
{{% /details %}}




{{% details title="<font color=Gray size=3>3. EDA.class_bar(category='barh')</font>" closed="true" %}}
```python {linenos=table, linenostart=1}
df_table_count = pd.DataFrame(df_table['count'])
EDA.class_bar(df_table_count, category='barh', alpha=1)
```
{{% /details %}}




{{% details title="<font color=Gray size=3>4. EDA.class_bar(category='bar', bar_width=10)</font>" closed="true" %}}
```python {linenos=table, linenostart=1}
df_table_count = pd.DataFrame(df_table['count'])
EDA.class_bar(df_table_count, category='bar', bar_width=10, alpha=1 )
```
{{% /details %}}





{{% details title="<font color=Gray size=3>5. EDA.class_pie()</font>" closed="true" %}}
```python {linenos=table, linenostart=1}
df_table_count = pd.DataFrame(df_table['count'])

EDA.class_pie(df_table_count)
```
{{% /details %}}





{{% details title="<font color=Gray size=3>6. sns.countplot()</font>" closed="true" %}}
```python {linenos=table, linenostart=1}
df = train.copy()

import seaborn as sns

sns.countplot(x=df['Survived'])
```
{{% /details %}}



<br><br>

### 3.2、多个变量

{{< cards >}}
  {{< card link="/docs/ai/end_to_end/crisp/custom_modules" title="EDA.class_table()" icon="back" >}}
  {{< card link="/docs/ai/end_to_end/crisp/custom_modules" title="EDA.class_bar()" icon="back" >}}
  {{< card link="/docs/ai/end_to_end/crisp/custom_modules" title="View.df_style()" icon="back" >}}
{{< /cards >}}

<br>

{{% details title="<font color=Gray size=3>1. df_table, df_table_count, df_table_propration = EDA.class_table()</font>" closed="true" %}}
```python {linenos=table, linenostart=1}
df = train.reset_index().copy()

values  = ["index"]
index   = ["Pclass", 'Sex']
columns = ["Survived"]

df_table, df_table_count, df_table_propration = EDA.class_table(df, values, index, columns)
```
{{% /details %}}




{{% details title="<font color=Gray size=3>2. EDA.class_bar(df_table_count, category='barh', bar_width=30, alpha=1, stacked=True)</font>" closed="true" %}}
```python {linenos=table, linenostart=1}
EDA.class_bar(df_table_count, category='barh', bar_width=30, alpha=1, stacked=True)
```
{{% /details %}}




{{% details title="<font color=Gray size=3>3. EDA.class_bar(df_table_propration, category='barh', bar_width=30, alpha=1, stacked=True)</font>" closed="true" %}}
```python {linenos=table, linenostart=1}
EDA.class_bar(df_table_propration, category='barh', bar_width=30, alpha=1, stacked=True)
```
{{% /details %}}




{{% details title="<font color=Gray size=3>4. View.df_style(df_table)</font>" closed="true" %}}
```python {linenos=table, linenostart=1}
View.df_style(df_table)
```
{{% /details %}}




<br><br><br>




## 4、探索连续变量：

### 4.1、单个变量

{{% details title="<font color=Gray size=3>1. ***直方图：*** df.hist(column=[], by=[]) </font>" closed="true" %}}
```python {linenos=table, linenostart=1}
df.hist(figsize=(5, 3), color='Coral', edgecolor='gray', alpha=1
    , bins=20
    , column = ['Age']
    #, by = ['Survived']
    )
plt.show()
```
{{% /details %}}





{{% details title="<font color=Gray size=3>2. ***累计直方图：*** df['Age'].plot.hist(cumulative=True) </font>" closed="true" %}}
```python {linenos=table, linenostart=1}
df['Age'].plot.hist(figsize=(5, 3), color='Coral', edgecolor='gray', alpha=1
    , bins=20
    , cumulative=True # 表示绘制累积直方图，即每个柱子的值是到该柱子为止（包含该柱子）的累计频率。
    #, orientation="horizontal" # 指定直方图的方向为水平方向，默认是垂直方向。
    )
```
{{% /details %}}




{{% details title="<font color=Gray size=3>3. ***多个直方图：*** df.hist()</font>" closed="true" %}}
```python {linenos=table, linenostart=1}
df = train.copy()

df.hist(figsize=(18, 8), color='Coral', edgecolor='gray', alpha=1
    , bins=20
    , layout=(3,5)  # 指定子图的布局为 3 行 3 列
    , sharex=False  # 表示子图不共享 x 轴
    )

plt.show()

```
{{% /details %}}




{{% details title="<font color=Gray size=3>4. ***密度图：*** df['Age'].plot.kde()</font>" closed="true" %}}
```python {linenos=table, linenostart=1}
df['Age'].plot.kde(figsize=(5, 3), color='Coral', alpha=1)
```
{{% /details %}}




{{% details title="<font color=Gray size=3>5. ***多个密度图：*** df.plot(kind= 'kde')</font>" closed="true" %}}
```python {linenos=table, linenostart=1}
df.plot(figsize=(18, 8)
    , kind= 'kde' # 'kde' 或 'density' 
    , subplots=True # 表示为每个列绘制单独的子图
    , layout=(3,5)  # 指定子图的布局为 3 行 3 列
    , sharex=False  # 表示子图不共享 x 轴
    )
plt.show()
```
{{% /details %}}




{{% details title="<font color=Gray size=3>6. ***多个箱线图：*** df.boxplot()</font>" closed="true" %}}
```python {linenos=table, linenostart=1}
df.boxplot(figsize=(12, 4)
    , vert=False # 横向排列
    , sym="r+" # 指定异常值的标记样式。r 表示标记的颜色为红色（"red"），+ 表示使用加号 + 作为标记符号。
    )

plt.show()
```
{{% /details %}}




{{% details title="<font color=Gray size=3>7. ***多个箱线图：*** df.plot(subplots=True)</font>" closed="true" %}}
```python {linenos=table, linenostart=1}
df.plot(figsize=(18, 4)
    , kind= 'box' 
    , subplots=True # 当设置为 True 时，将为数据框中的每个列都创建一个单独的子图。默认为 False，此时所有的列将画在一个图表中。
    , sharex=False # 这是一个布尔值，默认值是 False。当设置为 True 时，所有的子图都会共享相同的 x 轴（也就是相同的刻度和范围）。
    # , vert=False # 横向排列
    , sym="r+" # 指定异常值的标记样式。r 表示标记的颜色为红色（"red"），+ 表示使用加号 + 作为标记符号。
    ) 

plt.show()
```
{{% /details %}}


<br><br>

### 4.2、多变量相

{{< cards >}}
  {{< card link="/docs/ai/end_to_end/crisp/custom_modules" title="EDA.corr_heatmap()" icon="back" >}}
  {{< card link="/docs/ai/end_to_end/crisp/custom_modules" title="EDA.class_bar()" icon="back" >}}
  {{< card link="/docs/ai/end_to_end/crisp/custom_modules" title="View.df_style()" icon="back" >}}
{{< /cards >}}


<br>

{{% details title="<font color=Gray size=3>1. df.plot.scatter(x,y)</font>" closed="true" %}}
```python {linenos=table, linenostart=1}
df.plot.scatter(figsize=(4, 3)
    , x = 'Age'
    , y = 'Fare'
    , alpha=0.5, color='Coral'
    )
plt.show()
```
{{% /details %}}




{{% details title="<font color=Gray size=3>2. pd.plotting.scatter_matrix()</font>" closed="true" %}}
```python {linenos=table, linenostart=1}
df = train.copy()

columns_select = ['Age', 'Fare']
columns_len = len(columns_select)

pd.plotting.scatter_matrix(
    df[columns_select]
    , figsize=(columns_len*2,columns_len*2), alpha=1
    , hist_kwds={'bins': 10 
                 , 'facecolor' : "Coral"
                 ,  'edgecolor': "indianred"}
    , s=30 # 散点图点大小
    , facecolor='dimgrey' # "grey" 
    #, marker='o' # 标记
    #, c = df['Survived'] # 分类显示字段
    #, colors  = 'Pastel1' # , cmap=mglearn.cm3
    #, diagonal="kde"
    )
plt.show()
```
{{% /details %}}




{{% details title="<font color=Gray size=3>3. sns.pairplot()</font>" closed="true" %}}
```python {linenos=table, linenostart=1}
import matplotlib 
matplotlib.rcdefaults() # 返回默认主题

df = train.copy()

cols = df.columns.tolist()
cols.remove('PassengerId')

sns.pairplot( df[cols]
    , size=1.5
    , hue='Survived' # 分类字段
    , corner=True  # 是显示下半部分
    )
plt.tight_layout()
# plt.savefig('images/10_03.png', dpi=300)
plt.show()
```
{{% /details %}}




{{% details title="<font color=Gray size=3>4. sns.PairGrid()</font>" closed="true" %}}
```python {linenos=table, linenostart=1}
#plt.style.use('classic')
#plt.style.use('ggplot')   # 'classic'\'ggplot'

df = train.copy()

cols = df.columns.tolist()
cols.remove('PassengerId')

g = sns.PairGrid(df[cols], height=1.5)
#g.map_upper(sns.scatterplot)
g.map_lower(sns.kdeplot) #kdeplot\scatterplot
g.map_diag(sns.kdeplot, lw=0.5, legend=False) # pairplot\kdeplot

plt.show()
```
{{% /details %}}




{{% details title="<font color=Gray size=3>5. pd.cut() + EDA.class_bar() + View.df_style()</font>" closed="true" %}}
```python {linenos=table, linenostart=1}
df = train.reset_index().copy()

class_name = 'Survived'
col_name = 'Age'

# ------------------------------------------------------------------------------------------
col_name_cut = col_name + "_team"

df[col_name].fillna(0, inplace=True)
df[col_name_cut] = pd.cut(df[col_name], bins=15, precision=2)

index   = [col_name_cut]
columns = [class_name]
values  = ['index']

df.head()

df_table, df_table_value, df_table_propration = EDA.class_table(df, values, index, columns)
EDA.class_bar(df_table_value, category='bar', bar_width=30, alpha=0.9, stacked=True)
EDA.class_bar(df_table_propration, category='bar', bar_width=30, alpha=0.9, stacked=True)

View.df_style(df_table)
```
{{% /details %}}




<br><br><br>



## 5、探索多变量关系

### 5.1、变量相关：相关系数

{{% details title="<font color=Gray size=3>1. df.corr(method='pearson')</font>" closed="true" %}}
```python {linenos=table, linenostart=1}
col_name = ['Age', 'Fare', 'Pclass']
df = train[col_name]

corr_matrix = df.corr(method='pearson')
corr_matrix
```
{{% /details %}}



{{% details title="<font color=Gray size=3>2. EDA.corr_heatmap(df)</font>" closed="true" %}}
```python {linenos=table, linenostart=1}
df = train.copy()
EDA.corr_heatmap(df)
```
{{% /details %}}


<br><br><br>



### 5.2、变量相关：统计检验



<br><br><br>











