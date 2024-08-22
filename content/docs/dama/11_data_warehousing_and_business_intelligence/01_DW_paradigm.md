---
title: 数仓基础 1：范式
weight: 3211
#next: /step1
#prev: /docs
editURL: "https://example.com/edit/this/page"
toc: true
---

## ***<font face=Georgia>1、定义</font>***

在数据库领域，范式（Normal Form）是符合某一种级别的关系模式的集合，用于规范数据库设计，减少数据冗余和异常。常见的范式包括第一范式（1NF）、第二范式（2NF）、第三范式（3NF）等。

<br><br>


## **<font face=Georgia>2、零范式</font>**

- 零范式：<i><b><font color=Coral face=Georgia>数据中不存在重复数据</font></b></i>
    
> 1. 它只满足一个最基本的条件 — <b>数据中不存在重复数据</b>
> 2. 零范式（Zero Normal Form，0NF）并非数据库设计中常见的正式范式。

{{< callout type="warning" >}}
  在数据库设计中，一般从第一范式（1NF）开始讨论。零范式可以被认为是一种不符合任何正式范式规则的状态，即数据可能存在大量的冗余、不一致和潜在的错误。
{{< /callout >}}

<br><br>

## **<font face=Georgia>3、一范式</font>**

- 一范式：<i><b><font color=Coral face=Georgia>每个属性都必须是不可再分的原子值。</font></b></i>也就是说，表中的每个字段只能包含一个值，不能包含多个值或者可分割的数据。
    
> 1. 第一范式（1NF）是关系数据库中的一种 <b>基本范式要求</b>。

<br>

| 学生 ID | 学生姓名 | 课程 ID | 课程名称 | 课程成绩 |
| ---- | ---- | ---- | ---- | ---- |
| 1 | 张三 | 101 | 数学 | 85 |
| 2 | 李四 | 102 | 英语 | 90 |
| 3 | 王五 | 103 | 物理 | 78 |
| 4 | 赵六 | 104 | 化学 | 88 |



{{< callout type="warning" >}}
  第一范式虽然是关系数据库设计的基础，但它也存在一些不足之处：
  1. <i><b><font color=DarkCyan face=Georgia>数据冗余</font></b></i>：可能存在大量的重复数据。例如，在一个包含学生信息和课程信息的表中，如果每个学生选修的每门课程都要重复记录学生的基本信息，就会导致数据冗余。
  2. <i><b><font color=DarkCyan face=Georgia>插入异常</font></b></i>：当试图插入某些数据时，可能由于部分关键信息缺失而无法插入。比如，如果一个学生还没有选修任何课程，而表结构要求必须同时记录学生和课程的关联信息，就无法插入该学生的基本信息。
  3. <i><b><font color=DarkCyan face=Georgia>删除异常</font></b></i>：可能会因为删除某些数据而意外丢失其他有用的信息。例如，若删除某门课程的所有记录，可能会连带删除了选修该课程的学生的其他相关信息。
  4. <i><b><font color=DarkCyan face=Georgia>更新异常</font></b></i>：当需要更新某些重复的数据时，必须同时更新多个地方，否则会导致数据不一致。
{{< /callout >}}

<br><br>


## **<font face=Georgia>4、二范式</font>**
