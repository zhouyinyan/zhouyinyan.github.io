---
layout: post
title: MySql 基础
---


# MySql BASE #
----------
### DDL语句 ###

1. 创建数据库
	
    create database test1;

2. 删除数据库
	
    drop database test1;

3. 创建表

    create table emp(ename varchar(10), hiredate date, sal decimal(10,2), deptno int(2));

4. 查看创建语句

    show create table emp \G

5. 删除表
	
	drop table emp;

6. 修改表
	
	- 修改表类型
		
    	alter table emp modify ename varchar(20);
	
	- 添加字段
	
		alter table emp add column age int(3);

	- 删除字段
		
		alter table emp drop column age;

	- 字段改名

		alter table emp change age age1 int(4);		

	- 修改字段排列顺序

		alter table emp add brith date after ename;		

	- 修改表名
		
		alter table emp rename emp1;
		
### DML语句 ###

1. 插入记录
	
    insert into emp(ename, hiredate, sal, daptno) values('lisa','2013-02-01','3000',2);

	一次插入多条记录

	insert into emp(ename, hiredate, sal, deptno) values('zzxx','2013-02-01','1000',1),('xxyy','2013-07-01','9000',1)
	
2. 更新记录
	
	update emp set sal=4000 where ename='lisa';	
	
	同时更新多表数据

	update emp t1,emp t2 set t1.sal = t1.sal * t2.deptno, t2.ename = concat(t2.ename,'aa') where t1.deptno = t2.deptno;
	
3. 删除记录

	delete from emp where ename = 'lisaaaa';
	
	同时删除多条数据
	
	delete t1,t2 from emp t1,emp t2 where t1.ename=t2.ename and t1.deptno = 1;	

4. 查询记录
	
	select * from emp;
	
	不重复记录查询
	
	select distinct deptno from emp;

	条件查询 where

	select * from emp where deptno=2;

	排序和限制 order by & limit

	select * from emp order by sal limit 3；

	聚合 group by & having

	select count(1) from emp;
	select deptno, count(1) from emp group by deptno ;
	select deptno, count(1) from emp group by deptno with rollup;
	select deptno, count(1) as c from emp group by deptno having c > 1;

	表连接 内连，左外连，右外连
	
	select t1.ename,t2.deptname from emp t1, dept t2 where t1.deptno = t2.deptno;

	select t1.ename,t2.deptname from emp t1 left join dept t2 on t1.deptno = t2.deptno;

    select t1.ename,t2.deptname from emp t1 right join dept t2 on t1.deptno = t2.deptno;

	子查询	
	
	select * from emp where deptno in ( select deptno from dept);

	记录联合 union & union all
	
	select deptno from emp 
	union all
	select deptno from dept;

### DCL语句 ###

    grant select,insert on sakila.* to 'zl'@'localhost' identified by '123';

	revoke insert on sakila.* from 'zl'@'localhost';
    	

	

	










