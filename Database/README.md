# 数据库知识

## 前言

1.数据的定义：文字、图像、地理位置信息(坐标、经纬度)等

2.数据库管理系统的定义：建立、存取和管理数据，保证数据安全和完整性的软件

3.常见的数据库管理系统：

* 关系型：MySQL、Oracle、SQL Server、Db2等
* 非关系型：MongoDB、Redis、HBase等

4.NoSQL简介

NoSQL=Not Only SQL，支持类似SQL的功能， 与Relational Database相辅相成

其适用于性能较高，不使用SQL意味着没有结构化的存储要求(SQL为结构化的查询语句)，没有约束之后架构更加灵活

优势：高可扩展性、分布式计算、没有复杂的关系、低成本、架构灵活、半结构化数据

* 列存储：Hbase
* 键值(Key-Value)存储：Redis
* 图像存储：Neo4J
* 文档存储：MongoDB

## MongoDB

MongoDB特性：最像关系型数据库的NoSQL

### 数据存储格式
1. JSON

MongoDB使用JSON(JavaScript ObjectNotation)文档存储记录，JSON数据库语句可以容易被解析，Web应用大量使用，NAME-VALUE配对

2. BSON（二进制的JSON，JSON文档的二进制编码存储格式）

BSON有JSON没有的Date和BinData，MongoDB中document以BSON形式存放，数据格式灵活-文档里嵌入文档

