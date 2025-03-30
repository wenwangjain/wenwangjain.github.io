---
title: Markdown 语法指南
date: 2020-01-01
authors:
  - name: wenwangjian
    link: 
excludeSearch: true
categories: ["其他"]
tags: ["Markdown", "指南"]
---

这篇文章提供了一些基础的 Markdown 语法样例，这些可以在 Hugo 的内容文件中使用。

<!--more-->

## 基础语法

### 1、标题

```
# 一级标题
## 二级标题
### 三级标题
#### 四级标题
##### 五级标题
###### 六级标题
```



<br><br><br>



### 2、列表

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



<br><br><br>



### 3、文字加粗\斜体

```test
*这段文字将是斜体*
_这也将是斜体_

**这段文字将是粗体**
__这也将是粗体__

_你 **可以** 组合它们_
```

*这段文字将是斜体*<br>
_这也将是斜体_

**这段文字将是粗体**<br>
__这也将是粗体__

_你 **可以** 组合它们_




<br><br><br>



## 特殊案例：

### 1、内容加 “边框”

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



<br><br><br>



### 2、内容 “分栏”

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



<br><br><br>



## 基础语法






### 图片

```markdown
![GitHub Logo](https://github.githubassets.com/images/modules/logos_page/GitHub-Mark.png)
```

![GitHub Logo](https://github.githubassets.com/images/modules/logos_page/GitHub-Mark.png)

### 链接

```markdown
[Hugo](https://gohugo.io)
```

[Hugo](https://gohugo.io)

### 块引用

```markdown
牛顿曾说：

> 如果我看得更远，那是因为我站在巨人的肩膀上。
```

> 如果我看得更远，那是因为我站在巨人的肩膀上。

### 行内代码

```markdown
行内 `代码` 有 `反引号` 包围。
```

行内 `代码` 有 `反引号` 包围。

### 代码块

#### 语法高亮

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

### 表格

```markdown
| Syntax    | Description |
| --------- | ----------- |
| Header    | Title       |
| Paragraph | Text        |
```

| Syntax    | Description |
| --------- | ----------- |
| Header    | Title       |
| Paragraph | Text        |

## 参考

- [Markdown Syntax](https://www.markdownguide.org/basic-syntax/)
- [Hugo Markdown](https://gohugo.io/content-management/formats/#markdown)
