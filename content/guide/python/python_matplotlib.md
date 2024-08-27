---
title: Python_Matplotlib
weight: 306
#next: /step1
prev: /guide
#editURL: "https://example.com/edit/this/page"
type: "docs"
toc: true
math: true
---

## 1. Matplotlib 

### 1.1. Coding styles

#### 1.1.1. the OO-style

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

#### 1.1.2. pyplot-style

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



### 1.2. Parts of a Figure

#### 1.2.1. Figure

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


#### 1.2.2. Axes

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
fig, ax = plt.subplots(figsize=(5, 2.7))      

plt.show()
```
> 输出结果如下：
  {{< /tab >}}

  {{< tab >}}
```python
import matplotlib.pyplot as plt

# Create a figure
plt.figure(figsize=(3.5, 3), layout='constrained')

# Create a single Axes
plt.plot() 

plt.show()
```
> 输出结果如下：
  {{< /tab >}}
{{< /tabs >}}


<br><br>


#### 1.2.3. Axis 

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
fig, ax = plt.subplots(figsize=(5, 2.7))             

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
```
> 输出结果如下：
  {{< /tab >}}
{{< /tabs >}}


<br><br>



















