---
layout: post
title: MySql Index
---

- 概述

所有Mysql列类型都可以被索引， 对相关列使用索引是提高select新能的最佳途径。
MyISAM和InnoDB表的默认都是BTREE索引。支持前缀索引。目前只有MyISAM支持FULLTEXT索引，且只限于CHAR,VARCHAR和TEXT列
可以使用create index语句和 alter table语句添加索引。

    create index idx_name on city(name);
    
    explain select * from city where name = 'haha' \G
    
    drop index idx_name on city;
    
    前缀索引
    
     create index idx_name on city(name(10));

- 索引设计原则

搜索条件的列，即最适合索引的列出现在where子句中的列或者连接子句中的列。
使用唯一索引，考虑列中的值的分布，基数越大，效果越好。
使用短索引，对字符串进行索引，应该指定一个前缀长度，尽可能这么做
利用最左前缀
不要过渡索引
对于InnoDB表，尽量指定主键，且主键尽可能选择短的数据类型（因为其他索引会保存主键的键值）


- BTREE索引和HASH索引

HASH索引只能匹配精确值，即= in操作，但是速度非常快
BTREE索引能范围匹配，即> < 等操作。



