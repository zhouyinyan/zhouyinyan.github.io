---
layout: post
title: 优化SQL
---

- 优化SQL的一般步骤

	1. 通过show [session|global] status命令了解各种sql的执行频率

	`show global status like 'Com_%';`
	
	Com_xxx表示每个xxx语句的执行次数，通常关系如下几个统计参数：
	
	Com_insert:执行insert的次数，对于批量插入的操作，只累加1
	Com_select:执行select的次数
	Com_update:执行update的次数
	Com_delete:执行delete的次数
	
	针对innodb操作统计：
	Innodb_rows_read:select查询返回的行数
	Innodb_rows_inserted:insert操作插入的行数
	Innodb_rows_update:update操作更新的行数
	Innodb_rows_delete:delete操作删除的行数
	
	对于事务型应用，Com_commit,Com_rollback可以了解事务的提交和回滚情况
	
	Connections:试图连接服务器的次数
	Uptime:服务器工作时间
	Slow_querises:慢查询次数
	
	2. 定位执行效率低的sql

 	通过慢查询日志定位执行效率低的sql

	show processlist 查看当前msyql的线程，包括线程状态，是否锁表等。

	3. 通过explain分析执行效率低的sql
	
	explain的输出有select_type,table, type,possible_key,key,key_len,rows,extra

	4. 确定问题，并采取相应的优化措施

- 索引问题

	
	



