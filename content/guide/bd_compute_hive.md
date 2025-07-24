---
title: Hive
weight: 7302
#next: /step1
prev: /guide
#editURL: "https://example.com/edit/this/page"
type: "docs"
toc: true
math: true
---



## 一、Hive 概述

### 1.1、Hive 是什么？

Hive是由 Facebook 开源，基于 Hadoop 的一个数据仓库工具，可以将结构化的数据文件映射为一张表，并提供类SQL 查询功能。

<br><br>

### 1.2. Hive 本质

Hive是一个Hadoop客户端，用于将 HQL（Hive SQL）转化成 MapReduce 程序。

{{< callout emoji=📝 type='default' >}}
- Hive中每张表的数据存储在HDFS
- Hive分析数据底层的实现是 MapReduce（也可配置为Spark或者Tez） 
- 执行程序运行在Yarn上
{{< /callout >}}

<br><br>


## 二、Hive 安装


<br><br>


## 三、Hive DDL（数据定义）

### 3.1、数据库

在 HiveSQL 中，你可以使用 `CREATE DATABASE` 语句来创建数据库。以下为你详细介绍其语法、参数说明以及提供一些具体案例。

{{< tabs items="1️⃣ 语法, 2️⃣案例" >}}

  {{< tab >}}
```sql
CREATE (DATABASE|SCHEMA) [IF NOT EXISTS] database_name
  [COMMENT database_comment]
  [LOCATION hdfs_path]
  [WITH DBPROPERTIES (property_name=property_value, ...)];
```

- **`(DATABASE|SCHEMA)`**：`DATABASE` 和 `SCHEMA` 是同义词，二者使用效果相同，用于指定创建的对象是数据库。
- **`IF NOT EXISTS`**：这是一个可选参数。如果使用该参数，当要创建的数据库已经存在时，不会抛出错误，而是跳过创建操作；若不使用该参数，当数据库已存在时会报错。
- **`database_name`**：此为必选参数，用于指定要创建的数据库的名称，名称需符合 Hive 的命名规则。
- **`COMMENT database_comment`**：可选参数，用于为数据库添加注释信息，方便后续对数据库进行描述和管理。
- **`LOCATION hdfs_path`**：可选参数，用于指定数据库在 HDFS（Hadoop Distributed File System）中的存储路径。若不指定，Hive 会使用默认路径。
- **`WITH DBPROPERTIES (property_name=property_value, ...)`**：可选参数，用于为数据库设置一些自定义属性，属性以键值对的形式存在。

  {{< /tab >}}

  {{< tab >}}
***案例 1：创建一个简单的数据库***

```sql
CREATE DATABASE my_database;
```

此语句创建了一个名为 `my_database` 的数据库，使用的是 Hive 的默认存储路径，且没有添加注释和自定义属性。

<br>

***案例 2：使用 `IF NOT EXISTS` 创建数据库***

```sql
CREATE DATABASE IF NOT EXISTS my_database;
```

当 `my_database` 数据库不存在时，会创建该数据库；若已存在，则不会进行任何操作，也不会报错。

***案例 3：创建带有注释的数据库***
```sql
CREATE DATABASE my_database_with_comment
COMMENT 'This is a test database for demonstration purposes';
```
此语句创建了一个名为 `my_database_with_comment` 的数据库，并为其添加了注释信息，方便后续了解该数据库的用途。

<br>

***案例 4：创建指定存储路径的数据库***
```sql
CREATE DATABASE my_database_with_location
LOCATION '/user/hive/warehouse/my_database_location';
```
该语句创建了一个名为 `my_database_with_location` 的数据库，并将其存储在 HDFS 的 `/user/hive/warehouse/my_database_location` 路径下。

<br>

***案例 5：创建带有自定义属性的数据库***
```sql
CREATE DATABASE my_database_with_properties
WITH DBPROPERTIES ('owner' = 'John', 'created_date' = '2024-01-01');
```
此语句创建了一个名为 `my_database_with_properties` 的数据库，并为其设置了两个自定义属性：`owner` 的值为 `John`，`created_date` 的值为 `2024-01-01`。这些属性可以用于数据库的元数据管理。 

  {{< /tab >}}

{{< /tabs >}}


























