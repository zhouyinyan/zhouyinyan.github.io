---
layout: post
title: MySql Transaction
---

- 事务控制

MySql通过set autocommit,START TRANSACTION,COMMIT,ROLLBACK等语句支持本地事务
默认情况下，Mysql是autocommit(自动提交)，如果需要明确的commit和rollback来提交和回滚事务，那么需要明确的事务命令来开启事务。
start transaction 或 begin -- 开启新的事务
commit 或 rollback -- 提交或回滚事务
chain 或 release -- 定义事务提交或回滚之后的操作
set autocommit -- 修改当前连接的提交方式，设置0后，所有事务都需要明确的命令进行提交或回滚


- 分布式事务

MySql分布式事务只支持InnoDB存储引擎，一个分布式事务会涉及多个行动，这些行动本身是事务性的。所有行动必须一起成功完成，或者一起全部回滚。
Mysql中，使用分布式事务会涉及一个TM（事务管理器）和多个RM（资源管理器），采用两阶段提交实现。
Mysql的分布式事务还存在缺陷，在数据库和应用异常的情况下，会导致分布式事务的不完整性，对事务完整性要求高的系统不推荐使用。