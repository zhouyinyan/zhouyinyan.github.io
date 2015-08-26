---
layout: post
title: SQL MODE
---

- SQL MODE 简介

Mysql可以运行在不同的sql mode下，sql mode定义了mysql应支持的sql语法，数据校验等。常用sqlmode解决如下问题
设置sqlmode，完成不同严格程度的数据校验
设置sqlmode为ANSI，保证sql符合标准的sql语法，便于迁移到不同数据库
设置sqlmode，可以方便数据迁移到目标数据库中。

查看sqlmode

    select @@sql_mode;

可以通过sql-mode="modes"全局配置

- 常用的sql mode 组合

ANSI 
STRICT_TRANS_TABLES
TRADITIONAL

如何在异构数据库之间迁移数据的话，那么Mysql提供的数据库组合模式会对数据迁移过程有所帮助

DB2
MAXDB
MSSQL
ORACLE
POSTGERSQL