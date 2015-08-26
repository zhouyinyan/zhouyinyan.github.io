---
layout: post
title: MySql View
---

- 概述

视图是虚拟存在的表，对于使用视图的用户来说是透明的。其优势主要有：
简单：使用视图的用户不用关心后面对应的表结构，关联条件，筛选条件，对用户来说已经是过滤好的复合条件的结果集。
安全：使用视图的用户只能访问他们被允许查询的结果集
数据独立：一旦视图结构确定了，可以屏蔽表结构变化对用户的影响。

- 操作
	
操作包括创建，修改，删除和查询定义。

    create or replace view city_country_view as 
    select c.id as cid, c.name as cname, c.countrycode as countrycode, t.name as tname,t.continent, t.region from city c, country t where c.countrycode = t.code and c.id > 400 and c.id < 800;
    
    show tables;
    
    show create view city_country_view \G

视图的可更新性和视图的定义有关，下面这些情况不能更新
如果定义中包括某些关键字，如sum，min，max，count，distinct，group by， having，union等，
常量视图，select 包含 子查询语句，join 等等。

with [cascaded|local] check option 决定了是否允许更新数据使记录不满足视图的条件。默认cascade。
    
    drop view city_country_view;
 




