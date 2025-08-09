---
title: Python_Matplotlib
weight: 3006
#next: /step1
prev: /guide
#editURL: "https://example.com/edit/this/page"
type: "docs"
toc: true
math: true
---

<br>

## 0. 速查表

|*对象*|*设置*|*方法*|***`OO-style`***|***`pyplot-style`***|
|:---:|:---:|:---:|:---|:---|
|创建|`Figure`|_|`fig = plt.figure(figsize=(3,3))`      |`plt.figure(figsize=(3,3))`   |
|创建|`Axes`  |_|`fig, ax = plt.subplots(figsize=(3,3))`|`plt.plot()`                  |
|<br><br>||||
|标题|内容|_|`ax.set_title('Title')`                   |`plt.title('Title')`          |
|标题|格式|参数|`ax.set_title('Title', loc='left', font='Georgia', size=12, color='gray', weight='bold')`|`plt.title('Title', loc='left', font='Georgia', size=12, color='gray', weight='bold')`|
|标题|格式|参数字典|`format_dir = {'fontproperties': 'Georgia', 'fontsize': 15, 'color': 'Gray', 'fontweight': 'bold'}`<br><br>`ax.set_title('Title', loc='left', **format_dir)`|`format_dir = {'fontproperties': 'Georgia', 'fontsize': 15, 'color': 'Gray', 'fontweight': 'bold'}`<br><br>`plt.title('Title', loc='left', **format_dir)`|
|标题|位置|简单设置|`ax.set_title('Title', loc='left')` <br> <font color=Gray size=2> \<loc>: 'left','center','right'</font>|`plt.title("Title", loc='left')` <br> <font color=Gray size=2> \<loc>: 'left','center','right'</font>|
|<br><br>||||
|||||
|||||
|||||
|||||
|||||
|||||
|||||
|||||
|||||
|||||




<br><br><br><br><br>

|***设置类容***|***`OO-style`***|***`pyplot-style`***|
|:---:|:---|:---|
|***关闭*** 坐标轴|`ax.axis('off')`<font color=Gray size=2># 关闭所有坐标轴</font> <br> `ax.spines['top'].set_visible(False)`|`plt.axis('off')` <font color=Gray size=2># 关闭所有坐标轴</font> <br> `plt.gca().spines['top'].set_visible(False)`|
|坐标轴 ***颜色***|`ax..spines['bottom'].set_color('red')`|`plt.gca().spines['bottom'].set_color('red')`|
|坐标轴 ***粗细***|`ax.spines['left'].set_linewidth(0.5)`|`plt.gca().spines['left'].set_linewidth(0.5)`|
|坐标轴 ***位置 1***<br> 单个参数|`ax.spines["right"].set_position()`<br><font color=Gray size=2># </font>|``|
|坐标轴 ***位置 1***|`ax.spines["right"].set_position(("outward", 5))`<br><font color=Gray size=2># "inward"：向内，"outward"：向外</font>|`plt.gca().spines["right"].set_position(("outward", 5))` <br><font color=Gray size=2># "inward"：向内，"outward"：向外</font>|
||``|``|

<br><br><br>


## 1. 概述

### 1.1. 编码风格

#### (1). the OO-style

```python
import numpy as np
import matplotlib.pyplot as plt

x = np.linspace(0, 2, 100)  # Sample data.


fig, ax = plt.subplots(figsize=(3.5, 3), layout='constrained') # Create a figure 

ax.plot(x, x, label='linear')  # Plot some data on the Axes.
ax.plot(x, x**2, label='quadratic')  # Plot more data on the Axes...

ax.set_title("Simple Plot")  # Add a title to the Axes.

ax.set_xlabel('x label')  # Add an x-label to the Axes.
ax.set_ylabel('y label')  # Add a y-label to the Axes.

ax.legend()  # Add a legend.

plt.show() # Show the figure.
```

<br><br>

#### (2). pyplot-style

```python
import numpy as np
import matplotlib.pyplot as plt

x = np.linspace(0, 2, 100)  # Sample data.


plt.figure(figsize=(3.5, 3), layout='constrained')

plt.plot(x, x, label='linear')  # Plot some data on the (implicit) Axes.
plt.plot(x, x**2, label='quadratic')  # etc.

plt.title("Simple Plot")

plt.xlabel('x label')
plt.ylabel('y label')

plt.legend()  # Add a legend.

plt.show() # Show the figure.
```



<br><br><br>



### 1.2. 图形结构

#### (1). Figure

{{< callout emoji=📝 type='default' >}}
- ***`Figure`*** 是整个窗体，你可以把它想象成一个画板，我们在其上面创建图形进，这是最为外层的对象。
- ***`Figure`*** 可以将其看作是整个绘图区域的容器
- 一个 ***`Figure`*** 对象可以包含一或多个 ***`Axes`*** （子图）对象。
{{< /callout >}}

{{< tabs items="OO-style,pyplot-style" >}}
  {{< tab >}}
```python
import matplotlib.pyplot as plt

# an empty figure with no Axes
fig = plt.figure(figsize=(3.5, 3), layout='constrained')             

plt.show()
```
> 输出结果如下：
```small
<Figure size 350x300 with 0 Axes>
```
  {{< /tab >}}

  {{< tab >}}
```python
import matplotlib.pyplot as plt

# an empty figure with no Axes
plt.figure(figsize=(3.5, 3), layout='constrained')

plt.show()
```
> 输出结果如下：
```small
<Figure size 350x300 with 0 Axes>
```
  {{< /tab >}}
{{< /tabs >}}


<br><br>


#### (2). Axes

{{< callout emoji=📝 type='default' >}}
- ***`Axes`*** （子图）对象，是实际进行绘图操作的区域，包含坐标轴、数据点、线条、图例等元素。
- ***`Axes`***  可以将其看作是包含绘图元素（例如线、点、刻度、标签、图例等）的一个容器。
- ***`Axes`*** 指子图，每个子图可以用任一种坐标系表示。如笛卡尔坐标系（直角坐标系），它包含两个 `Axis` 对象。每个 `Axes` 都有一个标题，一个 `x` 标签和一个 `y` 标签。在这个坐标系内，我们可以绘制各种图形。
{{< /callout >}}

{{< tabs items="OO-style,pyplot-style" >}}
  {{< tab >}}
```python
import matplotlib.pyplot as plt 

# Create a figure with a single Axes
fig, ax = plt.subplots(figsize=(3.5, 3))      

plt.show()
```
> 输出结果如下：
  {{< /tab >}}

  {{< tab >}}
```python
import matplotlib.pyplot as plt

# Create a figure
plt.figure(figsize=(3.5, 3))

# Create a single Axes
plt.plot() 

plt.show()
```
> 输出结果如下：
  {{< /tab >}}
{{< /tabs >}}


<br><br>


#### (3). Axis 

{{< callout emoji=📝 type='default' >}}
- ***`Axis`*** （轴）对象，用于控制图形中的刻度、刻度标签和网格线。
- 每个 ***`Axes`*** 对象有一个 `XAxis` 对象和一个 `YAxis` 对象。
- ***`Axis`*** 的主要功能包括：设置标签格式；刻度位置；刻度标签、字体、颜色；刻度线粗细、颜色；网格线显示与否、样式等；
{{< /callout >}}

{{< tabs items="OO-style,pyplot-style" >}}
  {{< tab >}}
```python
import matplotlib.pyplot as plt

# Create a figure containing a single Axes.
fig, ax = plt.subplots(figsize=(3.5, 3))             

# Plot some data on the Axes.
ax.plot([1, 2, 3, 4], [1, 4, 2, 3])  

# Create label formatting dictionary
label_format = {'fontproperties': 'Georgia', 'fontsize': 10, 'color': 'Gray', 'fontweight': 'bold'}

# Set title
ax.set_title('This is Title', **label_format, size=15)

# Set labels for the x-axis and y-axis
ax.set_xlabel('X Axis Title Here', **label_format)
ax.set_ylabel('Y Axis Title Here', **label_format)

# Show the figure
plt.show()                           
```
> 输出结果如下：
  {{< /tab >}}

  {{< tab >}}
```python
import matplotlib.pyplot as plt

plt.figure(figsize=(3.5, 3))             

plt.plot([1, 2, 3, 4], [1, 4, 2, 3])  

# Create label formatting dictionary
label_format = {'fontproperties': 'Georgia', 'fontsize': 10, 'color': 'Gray', 'fontweight': 'bold'}

plt.title('This is Title', **label_format, size=15)

plt.xlabel('X Axis Title Here', **label_format)
plt.ylabel('Y Axis Title Here', **label_format)

plt.show() 
```
> 输出结果如下：
  {{< /tab >}}
{{< /tabs >}}


<br><br><br>



## 2. 颜色


<br><br><br>


## 3. 文本


<br><br><br>



## 4. Figure 图形设置



## 5. Axes 子图细节设置

### 5.1. 标题：

{{< tabs items="1️⃣ OO-style 位置, 2️⃣ OO-style 格式参数, 3️⃣ OO-style 格式字典, 4️⃣ pyplot-style 位置, 5️⃣ pyplot-style 格式参数, 6️⃣ pyplot-style 格式字典" >}}
  {{< tab >}}
```python
import matplotlib.pyplot as plt

fig, ax = plt.subplots(figsize=(3,3))

ax.plot([1, 2, 3, 4], [8, 4, 2, 3])

ax.set_title('Title', loc='left')

plt.show()                    
```
  {{< /tab >}}

  {{< tab >}}
```python
import matplotlib.pyplot as plt

fig, ax = plt.subplots(figsize=(3,3))

ax.plot([1, 2, 3, 4], [8, 4, 2, 3])

# Set title
ax.set_title('This is Title', loc='left', font='Georgia', size=12, color='gray', weight='bold')

plt.show()
```
  {{< /tab >}}

  {{< tab >}}
```python
import matplotlib.pyplot as plt

fig, ax = plt.subplots(figsize=(3,3))

ax.plot([1, 2, 3, 4], [8, 4, 2, 3])

# Create label formatting dictionary
format_dir = {'fontproperties': 'Georgia', 'fontsize': 15, 'color': 'Gray', 'fontweight': 'bold'}

# Set title
ax.set_title('This is Title', loc='left', **format_dir)

plt.show()              
```
  {{< /tab >}}

  {{< tab >}}
```python
import matplotlib.pyplot as plt

# Create a figure
plt.figure(figsize=(3, 3))

# Create a single Axes
plt.plot([1, 2, 3, 4], [8, 4, 2, 3])

plt.title("Title", loc='left')  # 将标题设置在左侧

plt.show()
```
  {{< /tab >}}

  {{< tab >}}
```python
import matplotlib.pyplot as plt

plt.figure(figsize=(3,3))

plt.plot([1, 2, 3, 4], [8, 4, 2, 3])

# Set title
plt.title('Title', loc='left', font='Georgia', size=12, color='gray', weight='bold')

plt.show()                 
```
  {{< /tab >}}

  {{< tab >}}
```python
import matplotlib.pyplot as plt

plt.figure(figsize=(3, 3))

plt.plot([1, 2, 3, 4], [8, 4, 2, 3])

# Create label formatting dictionary
format_dir = {'fontproperties': 'Georgia', 'fontsize': 15, 'color': 'Gray', 'fontweight': 'bold'}

# Set title
plt.title('Title', loc='left', **format_dir)

plt.show()
```
  {{< /tab >}}
{{< /tabs >}}


<br><br>


### 5.2. 坐标轴：

{{< tabs items="OO-style,pyplot-style" >}}
  {{< tab >}}
```python
                         
```
> 输出结果如下：
  {{< /tab >}}

  {{< tab >}}
```python
 
```
> 输出结果如下：
  {{< /tab >}}
{{< /tabs >}}



<br><br><br>



## 6. 多子图绘制

### 6.1. 
















