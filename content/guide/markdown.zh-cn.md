---
title: Markdown
weight: 1
#next: /step1
prev: /guide
#editURL: "https://example.com/edit/this/page"
type: "docs"
toc: true
math: true
---
这篇文章提供了一些基础的 Markdown 语法样例，这些可以在 Hugo 的内容文件中使用。

<!--more-->

## 0_目录

```markdown
<font color=DarkCyan face=Georgia align=left><h1>**目录**</h1></font>

[**1.定义问题**](#1.定义问题)<br>
  [1.1.问题是什么？](#1.1.问题是什么？)<br>
  [1.2.为什么需要解决问题？](#1.2.为什么需要解决问题？)<br>
  [1.3.探索如何解决问题？](#1.3.探索如何解决问题？)<br>

<font color=DarkCyan face=Georgia align=left> <h1>**1.定义问题**</h1></font>
⬆️ [**返回目录**](#目录)

<font color=DarkCyan face=Georgia align=left> <h2>**1.1.问题是什么？**</h2></font>
⬆️ [**返回目录**](#目录)

测试

<font color=DarkCyan face=Georgia align=left> <h2>**1.2.为什么需要解决问题？**</h2></font>
⬆️ [**返回目录**](#目录)

测试

<font color=DarkCyan face=Georgia align=left> <h2>**1.3.探索如何解决问题？**</h2></font>
⬆️ [**返回目录**](#目录)

测试
```

[**1. 基础语法**](#1_基础语法)`<br>`
[**2. THML格式调整**](#2_html格式调整)`<br>`
[**参考网址**](#参考网址)`<br>`

`<br><br>``<br>`

## 1_基础语法

### 1.1. 标题

⬆️ [**返回目录**](#0_目录)

```
# 一级标题
## 二级标题
### 三级标题
#### 四级标题
##### 五级标题
###### 六级标题
```

`<br><br>``<br>`

### 1.2. 列表

```test
* 项目 1
* 项目 2
  * 项目 2a
  * 项目 2b

- 项目 1
- 项目 2
  - 项目 2a
  - 项目 2b
```

* 项目 1
* 项目 2
  * 项目 2a
  * 项目 2b

<br>

```test
1. 项目 1
2. 项目 2
3. 项目 3
   1. 项目 3a
   2. 项目 3b
```

1. 项目 1
2. 项目 2
3. 项目 3
   1. 项目 3a
   2. 项目 3b

`<br><br>``<br>`

### 1.3. 文字（加粗\斜体）

```test
*这段文字将是斜体*
_这也将是斜体_

**这段文字将是粗体**
__这也将是粗体__

_你 **可以** 组合它们_
```

*这段文字将是斜体*`<br>`
_这也将是斜体_

**这段文字将是粗体**`<br>`
__这也将是粗体__

_你 **可以** 组合它们_

`<br><br>``<br>`

### 1.4. 表格

```markdown
| Syntax    | Description | Description | Description |
| --------- | :----------- | -----------: |:-----------: |
| Header    | Title       |Title       |Title       |
| Paragraph | Text        |Text        |Text        |
```

| Syntax    | Description | Description | Description |
| --------- | :---------- | ----------: | :---------: |
| Header    | Title       |       Title |    Title    |
| Paragraph | Text        |        Text |    Text    |

`<br><br>``<br>`

### 1.5. 图片

```markdown
![GitHub Logo](https://github.githubassets.com/images/modules/logos_page/GitHub-Mark.png)
```

![GitHub Logo](https://github.githubassets.com/images/modules/logos_page/GitHub-Mark.png)

`<br><br>``<br>`

### 1.6. 链接

```markdown
[Hugo](https://gohugo.io)
```

- [Hugo](https://gohugo.io)

`<br><br>``<br>`

### 1.7. 引用

```markdown
牛顿曾说：

> 如果我看得更远，那是因为我站在巨人的肩膀上。
```

牛顿曾说：

> 如果我看得更远，那是因为我站在巨人的肩膀上。

`<br><br>``<br>`

### 1.8. 代码

````markdown
```go
func main() {
    fmt.Println("Hello World")
}
```
````

```go
func main() {
    fmt.Println("Hello World")
}
```

`<br><br>``<br>`

### 1.9. 行内代码

```markdown
行内 `代码` 有 `反引号` 包围。
```

行内 `代码` 有 `反引号` 包围。

`<br><br>``<br>`

### 1.10. 情符号

- https://github.com/zhouie/markdown-emoji

| 类别 |                               符号                               |
| :--: | :---------------------------------------------------------------: |
| 数字 | 0️⃣ 1️⃣ 2️⃣ 3️⃣ 4️⃣ 5️⃣ 6️⃣ 7️⃣ 8️⃣ 9️⃣ 🔟 🔢 |
| 使用 |                            ⚓ ✍ 👻 ❓                            |


`<br><br>``<br>`

### 1.11. 公式

{{< callout >}}

- [公式识别 (simpletex.cn)](https://www.simpletex.cn/ai/latex_ocr)
- [支持的功能 ·卡特克斯 (katex.org)](https://katex.org/docs/supported)
  {{< /callout >}}

```markdown
$\textcolor{DarkCyan}{ D=\{(x_1,y_1), (x_2,y_2),...,(x_m,y_m)\}}$  
$$\textcolor{DarkCyan}{ D=\{(x_1,y_1), (x_2,y_2),...,(x_m,y_m)\}}$$
这是一个公式：$\small{ D=\{(x_1,y_1), (x_2,y_2),...,(x_m,y_m)\}}$ 
这是一个公式：$$\small{ D=\{(x_1,y_1), (x_2,y_2),...,(x_m,y_m)\}}$$
```

$\textcolor{DarkCyan}{ D=\{(x_1,y_1), (x_2,y_2),...,(x_m,y_m)\}}$

$$
\textcolor{DarkCyan}{ D=\{(x_1,y_1), (x_2,y_2),...,(x_m,y_m)\}}
$$

这是一个公式：$\small{ D=\{(x_1,y_1), (x_2,y_2),...,(x_m,y_m)\}}$

这是一个公式：

$$
\small{ D=\{(x_1,y_1), (x_2,y_2),...,(x_m,y_m)\}}
$$

`<br><br>`

```markdown
${\tiny x = y + z}$
${\scriptsize x = y + z}$
${\small x = y + z}$
${\normalsize x = y + z}$
${\large x = y + z}$
${\Large x = y + z}$
${\LARGE x = y + z}$
${\huge x = y + z}$
${\Huge x = y + z}$
```

${\tiny x = y + z}$`<br>`
${\scriptsize x = y + z}$`<br>`
${\small x = y + z}$`<br>`
${\normalsize x = y + z}$`<br>`
${\large x = y + z}$`<br>`
${\Large x = y + z}$`<br>`
${\LARGE x = y + z}$`<br>`
${\huge x = y + z}$`<br>`
${\Huge x = y + z}$`<br>`

`<br><br>`

```markdown
$\mathfrak{x = y + z}$
$\mathcal{x = y + z}$
$\mathbf{ x = y + z}$
$\mathsf{ x = y + z}$
$\mathtt{ x = y + z}$
```

$\mathfrak{x = y + z}$`<br>`
$\mathcal{x = y + z}$`<br>`
$\mathbf{ x = y + z}$`<br>`
$\mathsf{ x = y + z}$`<br>`
$\mathtt{ x = y + z}$`<br>`

`<br><br>``<br>`

### 1.12. 花体

```markdown
| ID  | 花体设置| 案例 |
| --- | ----------- | ---------------------------------------------------------------------------------  | 
| 1   | \mathbb{}   | $\mathbb{ABCDEFGHIJKLMNOPQRSTUVWXYZ}$   <br>$\mathbb{abcdefghijklmnopqrstuvwxyz}$  | 
| 2   | \mathcal{}  | $\mathcal{ABCDEFGHIJKLMNOPQRSTUVWXYZ}$  <br>$\mathcal{abcdefghijklmnopqrstuvwxyz}$ |
| 3   | \mathscr{}  | $\mathscr{ABCDEFGHIJKLMNOPQRSTUVWXYZ}$  <br>$\mathscr{abcdefghijklmnopqrstuvwxyz}$ |
| 4   | \mathrm{}   | $\mathrm{ABCDEFGHIJKLMNOPQRSTUVWXYZ}$   <br>$\mathrm{abcdefghijklmnopqrstuvwxyz}$  |
| 5   | \mathbf{}   | $\mathbf{ABCDEFGHIJKLMNOPQRSTUVWXYZ}$   <br>$\mathbf{abcdefghijklmnopqrstuvwxyz}$  |
| 6   | \mathit{}   | $\mathit{ABCDEFGHIJKLMNOPQRSTUVWXYZ}$   <br>$\mathit{abcdefghijklmnopqrstuvwxyz}$  |
| 7   | \mathsf{}   | $\mathsf{ABCDEFGHIJKLMNOPQRSTUVWXYZ}$   <br>$\mathsf{abcdefghijklmnopqrstuvwxyz}$  |
| 8   | \mathtt{}   | $\mathtt{ABCDEFGHIJKLMNOPQRSTUVWXYZ}$   <br>$\mathtt{abcdefghijklmnopqrstuvwxyz}$  |
| 9   | \mathfrak{} | $\mathfrak{ABCDEFGHIJKLMNOPQRSTUVWXYZ}$ <br>$\mathfrak{abcdefghijklmnopqrstuvwxyz}$|
```

| ID | 花体设置    | 案例                                                                                        |
| -- | ----------- | ------------------------------------------------------------------------------------------- |
| 1  | \mathbb{}   | $\mathbb{ABCDEFGHIJKLMNOPQRSTUVWXYZ}$   `<br>`$\mathbb{abcdefghijklmnopqrstuvwxyz}$   |
| 2  | \mathcal{}  | $\mathcal{ABCDEFGHIJKLMNOPQRSTUVWXYZ}$  `<br>`$\mathcal{abcdefghijklmnopqrstuvwxyz}$  |
| 3  | \mathscr{}  | $\mathscr{ABCDEFGHIJKLMNOPQRSTUVWXYZ}$  `<br>`$\mathscr{abcdefghijklmnopqrstuvwxyz}$  |
| 4  | \mathrm{}   | $\mathrm{ABCDEFGHIJKLMNOPQRSTUVWXYZ}$   `<br>`$\mathrm{abcdefghijklmnopqrstuvwxyz}$   |
| 5  | \mathbf{}   | $\mathbf{ABCDEFGHIJKLMNOPQRSTUVWXYZ}$   `<br>`$\mathbf{abcdefghijklmnopqrstuvwxyz}$   |
| 6  | \mathit{}   | $\mathit{ABCDEFGHIJKLMNOPQRSTUVWXYZ}$   `<br>`$\mathit{abcdefghijklmnopqrstuvwxyz}$   |
| 7  | \mathsf{}   | $\mathsf{ABCDEFGHIJKLMNOPQRSTUVWXYZ}$   `<br>`$\mathsf{abcdefghijklmnopqrstuvwxyz}$   |
| 8  | \mathtt{}   | $\mathtt{ABCDEFGHIJKLMNOPQRSTUVWXYZ}$   `<br>`$\mathtt{abcdefghijklmnopqrstuvwxyz}$   |
| 9  | \mathfrak{} | $\mathfrak{ABCDEFGHIJKLMNOPQRSTUVWXYZ}$ `<br>`$\mathfrak{abcdefghijklmnopqrstuvwxyz}$ |

`<br><br>``<br>`

## 2_html格式调整

⬆️ [**返回目录**](#0_目录)

### 2.1. 文字（字体\颜色）

```markdown
<font color=DarkCyan face=Georgia  align=left><h1>Title_1</h1></font>
<font color=DarkCyan face=Georgia  align=left><h2>Title_2</h2></font>
<font color=DarkCyan face=Georgia  align=left><h3>Title_3</h3></font>
<font color=DarkCyan face=Georgia  align=left><h4>Title_4</h4></font>
<font color=DarkCyan face=Georgia  align=left><h5>Title_5</h5></font>
<font color=DarkCyan face=Georgia  align=left><h6>Title_6</h6></font>

<font color=DarkCyan face=Georgia  align=left size=1>kaggle.com</font><br>
<font color=DarkCyan face=Georgia  align=left size=2>kaggle.com</font><br>
<font color=DarkCyan face=Georgia  align=left>kaggle.com</font><br>
<font color=DarkCyan face=Georgia  align=left size=4>kaggle.com</font><br>
<font color=DarkCyan face=Georgia  align=left size=5>kaggle.com</font><br>
```

<font color=DarkCyan face=Georgia  align=left size=1>kaggle.com</font><br>
<font color=DarkCyan face=Georgia  align=left size=2>kaggle.com</font><br>
<font color=DarkCyan face=Georgia  align=left>kaggle.com</font><br>
<font color=DarkCyan face=Georgia  align=left size=4>kaggle.com</font><br>
<font color=DarkCyan face=Georgia  align=left size=5>kaggle.com</font><br>

`<br><br>`

```markdown
<div 
     style= 
            "
              color:DarkCyan      /*字体颜色 https://www.runoob.com/cssref/css-colornames.html */
             ;font-size:40px      /*字体大小*/
             ;font-family:Georgia /*字体格式*/
             ;text-align:center   /*字体居中*/
             ;font-weight:900;    /*字体粗细*/
            /*;background-color:WhiteSmoke    /*背景颜色 https://www.runoob.com/cssref/css-colornames.html*/
            "
        >
        Title
    <br>
</div>

<p 
    style=
            "
             color:DimGray                    /*字体颜色 https://www.runoob.com/cssref/css-colornames.html*/     /*CadetBlue*/
            ;font-size:15px                   /*字体大小*/
            ;text-align:center                /*字体居中*/
            ;font-weight:800;                 /*字体粗细*/
                /*;font-family:Georgia          /*字体格式*/
                /*;background-color:CadetBlue   /*背景颜色 WhiteSmoke https://www.runoob.com/cssref/css-colornames.html*/
            "
    >
    Source: Kaggle (https://www.kaggle.com/competitions/titanic) <br>
    Motive: study <br>
</p>

<p 
    style=
            "
             color:Coral                     /*字体颜色 https://www.runoob.com/cssref/css-colornames.html*/     /*CadetBlue*/
            ;font-size:15px                   /*字体大小*/
            ;text-align:left                /*字体居中*/
            ;font-weight:800;                 /*字体粗细*/
                /*;font-family:Georgia          /*字体格式*/
                /*;background-color:CadetBlue   /*背景颜色 WhiteSmoke https://www.runoob.com/cssref/css-colornames.html*/
            "
    >
    Reference website: <br>
         1. https://www.kaggle.com <br>
         2. https://www.kaggle.com
</p>
```

<div 
     style= 
            "
              color:DarkCyan      /*字体颜色 https://www.runoob.com/cssref/css-colornames.html */
             ;font-size:40px      /*字体大小*/
             ;font-family:Georgia /*字体格式*/
             ;text-align:center   /*字体居中*/
             ;font-weight:900;    /*字体粗细*/
            /*;background-color:WhiteSmoke    /*背景颜色 https://www.runoob.com/cssref/css-colornames.html*/
            "
        >
        Title
    <br>
</div>

<p 
    style=
            "
             color:DimGray                    /*字体颜色 https://www.runoob.com/cssref/css-colornames.html*/     /*CadetBlue*/
            ;font-size:15px                   /*字体大小*/
            ;text-align:center                /*字体居中*/
            ;font-weight:800;                 /*字体粗细*/
                /*;font-family:Georgia          /*字体格式*/
                /*;background-color:CadetBlue   /*背景颜色 WhiteSmoke https://www.runoob.com/cssref/css-colornames.html*/
            "
    >
    Source: Kaggle (https://www.kaggle.com/competitions/titanic) <br>
    Motive: study <br>
</p>

<p 
    style=
            "
             color:Coral                     /*字体颜色 https://www.runoob.com/cssref/css-colornames.html*/     /*CadetBlue*/
            ;font-size:15px                   /*字体大小*/
            ;text-align:left                /*字体居中*/
            ;font-weight:800;                 /*字体粗细*/
                /*;font-family:Georgia          /*字体格式*/
                /*;background-color:CadetBlue   /*背景颜色 WhiteSmoke https://www.runoob.com/cssref/css-colornames.html*/
            "
    >
    Reference website: <br>
         1. https://www.kaggle.com <br>
         2. https://www.kaggle.com
</p>

`<br><br>``<br>`

### 2.2. 分割线

```markdown
<hr style="border: 1px solid blue">
<hr style="border: 1px solid red">
<hr style="border: 1px solid gray">
<hr style="border: 2px solid DarkCyan">
```

<hr style="border: 1px solid blue"><br>
<hr style="border: 1px solid red"><br>
<hr style="border: 1px solid gray"><br>
<hr style="border: 2px solid DarkCyan"><br>

`<br><br>``<br>`

### 2.3. 表格

```markdown
<table border="2" style="font-family: Georgia; font-weight: 300; font-size: 14px; border-collapse: collapse; width: 500 ; text-align: center" > 
    <tr> 
        <th>id </th> 
        <th> value </th> 
        <th> explain </th> 
    </tr> 
    <tr> 
        <td>1</td> 
        <td >BOOK</td> 
        <td>《Approaching(Almost) Any Machine Learning Problem》</td> 
    </tr> 
    <tr> 
        <td>2</td> 
        <td >WEB</td> 
        <td>https://www.kaggle.com/</td> 
    </tr> 
</table>
```

<table 
  border="2" 
  style="font-family: Georgia; font-weight: 300; font-size: 14px; border-collapse: collapse; width: 500 ; text-align: center" > 
    <tr> 
        <th>id </th> 
        <th> value </th> 
        <th> explain </th> 
    </tr> 
    <tr> 
        <td>1</td> 
        <td >BOOK</td> 
        <td>《Approaching(Almost) Any Machine Learning Problem》</td> 
    </tr> 
    <tr> 
        <td>2</td> 
        <td >WEB</td> 
        <td>https://www.kaggle.com/</td> 
    </tr> 
</table>

`<br><br>``<br>`

### 2.4. 表格（合并多格）

```markdown
<table border="2" style="font-family: Georgia; font-weight: 300; font-size: 14px; border-collapse: collapse; width: 600 ; text-align: center" > 
    <tr> 
        <th>id </th> 
        <th> value </th> 
        <th> explain </th> 
    </tr> 
    <tr> 
        <td>1</td> 
        <td rowspan="2">任务</td> 
        <td>test</td>  
    </tr> 
    <tr> 
        <td>2</td> 
        <td>test</td> 
    </tr> 
    <tr> 
        <td>3</td> 
        <td>test</td>
        <td>test</td>
    </tr> 
    <tr> 
        <td>4</td> 
        <td  colspan="2">任务</td> 
    </tr> 
    <td>5</td> 
        <td>test</td> 
        <td>test</td> 
</table>
```

<table border="2" style="font-family: Georgia; font-weight: 300; font-size: 14px; border-collapse: collapse; width: 600 ; text-align: center" > 
    <tr> 
        <th>id </th> 
        <th> value </th> 
        <th> explain </th> 
    </tr> 
    <tr> 
        <td>1</td> 
        <td rowspan="2">任务</td> 
        <td>test</td>  
    </tr> 
    <tr> 
        <td>2</td> 
        <td>test</td> 
    </tr> 
    <tr> 
        <td>3</td> 
        <td>test</td>
        <td>test</td>
    </tr> 
    <tr> 
        <td>4</td> 
        <td  colspan="2">任务</td> 
    </tr> 
    <td>5</td> 
        <td>test</td> 
        <td>test</td> 
</table>

`<br><br>``<br>`

### 2.5. 内容（加边框）

```markdown
<div style="border: 0.5px solid DarkCyan; border-radius: 10px; width: 100%; border-left-width: 5px; padding: 10px;">
  这是有边框的文字<br>
  这是有边框的文字<br>
  这是有边框的文字<br>
  ......
</div>
```

<div style="border: 0.5px solid DarkCyan; border-radius: 10px; width: 100%; border-left-width: 5px; padding: 10px;">
  这是有边框的文字<br>
  这是有边框的文字<br>
  这是有边框的文字<br>
  ......
</div>

`<br><br>``<br>`

### 2.6. 内容（分栏）

```markdown
<div style="display: flex; justify-content: center; width: 100%;">
  <div style="flex: 33%; padding: 10px; box-sizing: border-box; text-align: center;"> 第 1 栏 </div>
  <div style="flex: 33%; padding: 10px; box-sizing: border-box; text-align: center;"> 第 2 栏 </div>
  <div style="flex: 33%; padding: 10px; box-sizing: border-box; text-align: center;"> 第 3 栏 </div>
</div>
```

<div style="display: flex; justify-content: center; width: 100%;">
  <div style="flex: 33%; padding: 10px; box-sizing: border-box; text-align: center;"> <font color=DarkCyan face=Georgia  ><b><i>第 1 栏</i></b></font> </div>
  <div style="flex: 33%; padding: 10px; box-sizing: border-box; text-align: center;"> <font color=DarkCyan face=Georgia  ><b><i>第 2 栏</i></b></font> </div>
  <div style="flex: 33%; padding: 10px; box-sizing: border-box; text-align: center;"> <font color=DarkCyan face=Georgia  ><b><i>第 3 栏</i></b></font> </div>
</div>

`<br><br>``<br>`

### 2.7. 引用

```markdown
<div style="background-color: #f0f8ff; border-left: 4px solid #1e90ff; padding: 12px; margin-bottom: 16px;">
  <input type="checkbox" disabled> <strong>Note</strong><br>
  Useful information that users should know, even when skimming content.
</div>

<div style="background-color: #f0fff0; border-left: 4px solid #2e8b57; padding: 12px; margin-bottom: 16px;">
  <input type="checkbox" checked disabled> <strong>Tip</strong><br>
  Helpful advice for doing things better or more easily.
</div>

<div style="background-color: #fffaf0; border-left: 4px solid #ffa500; padding: 12px; margin-bottom: 16px;">
  <input type="checkbox" disabled> <strong>Important</strong><br>
  Key information users need to know to achieve their goal.
</div>

<div style="background-color: #fff0f5; border-left: 4px solid #ff69b4; padding: 12px; margin-bottom: 16px;">
  <input type="checkbox" disabled> <strong>Warning</strong><br>
  Urgent info that needs immediate user attention to avoid problems.
</div>

<div style="background-color: #f5f5f5; border-left: 4px solid #a9a9a9; padding: 12px; margin-bottom: 16px;">
  <input type="checkbox" disabled> <strong>Caution</strong><br>
  Advises about risks or negative outcomes of certain actions.
</div>
```

<div style="background-color: #f0f8ff; border-left: 4px solid #1e90ff; padding: 12px; margin-bottom: 16px;">
  <input type="checkbox" disabled> <strong> Note</strong><br>
  Useful information that users should know, even when skimming content.
</div>

<div style="background-color: #f0fff0; border-left: 4px solid #2e8b57; padding: 12px; margin-bottom: 16px;">
  <input type="checkbox" checked disabled> <strong> Tip</strong><br>
  Helpful advice for doing things better or more easily.
</div>

<div style="background-color: #fffaf0; border-left: 4px solid #ffa500; padding: 12px; margin-bottom: 16px;">
  <input type="checkbox" disabled> <strong>Important</strong><br>
  Key information users need to know to achieve their goal.
</div>

<div style="background-color: #fff0f5; border-left: 4px solid #ff69b4; padding: 12px; margin-bottom: 16px;">
  <input type="checkbox" disabled> <strong>Warning</strong><br>
  Urgent info that needs immediate user attention to avoid problems.
</div>

<div style="background-color: #f5f5f5; border-left: 4px solid #a9a9a9; padding: 12px; margin-bottom: 16px;">
  <input type="checkbox" disabled> <strong>Caution</strong><br>
  Advises about risks or negative outcomes of certain actions.
</div>

`<br><br>``<br>`

### 2.8. 背景

```markdown
<span style="background-color: yellow;">黄色背景</span>
```

`<span style="background-color: yellow;">`黄色背景

`<br><br>``<br>`

## 参考网址

⬆️ [**返回目录**](#0_目录)

- [Markdown Syntax](https://www.markdownguide.org/basic-syntax/)
- [Hugo Markdown](https://gohugo.io/content-management/formats/#markdown)
- [Markdown 数学符号、公式、花体字母_markdown 花体_一半西瓜的博客-CSDN博客](https://blog.csdn.net/qq_37672864/article/details/127497148)
- [markdown中数学公式字体大小的方法 - 胡文强的个人博客 (huwenqiang.cn)](https://www.huwenqiang.cn/articles/2020/10/22/1603372559446.html)
