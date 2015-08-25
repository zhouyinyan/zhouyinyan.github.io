### MySql 存储引擎 ###

----------
1. 概述

	MySql支持的存储引擎包括MyISAM，InnoDB，MEMORY，MERGE，NDB等，其中MyISAM和InnoDB最常用。
	默认情况下，新表创建不指定存储引擎，会使用默认存储引擎，在参数文件中配置default-table-type。查看默认存储引擎，可使用show engines;

	在创建表时，可以指定新表的存储引擎
	create table ai (i bigint(20) not null auto_increment, primary key (i)) engine = myisam;

	show create table ai \G

	将已存在的表修改为其他存储引擎。
	alter table ai engine = innodb ;

2. MyISAM 存储引擎
	
	不支持事务，不支持外键，表锁，对事务完整性没有要求，主要以select，insert操作为主的表。有非常好的访问速度。
	MyISAM在磁盘上存储为3个文件，文件名和表名相同，分别为 .frm(存储表定义） .MYD(存储数据） .MYI(存储索引）
	MyISAM表支持3中存储格式，分别为
	静态表（固定长度，默认），动态表，压缩表
	

3. InnoDB 存储引擎

	支持事务，支持外键，行锁，效率比MyISAM低。
	InnoDB使用过程中注意的点
	自动增长列必须是索引，如果是组合索引，也必须是组合索引的第一列。
	外键约束注意
	存储方式2种
	使用共享表空间存储，表结构保存在.frm文件中，数据和索引保存在innodb_data_home_dir和innodb_data_file_path定义的表空间中。
	使用多表空间存储，表结构保存在.frm文件中，但是每个表的数据和索引单独保存在.ibd中
	

4. MEMORY 存储引擎

	主要用于内容变化不频繁的代码表，或作为统计操作的中间表存在。
		
5. MERGE 存储引擎

	Merge是一组MyIsam表组合，这些MyISAM表结构必须完全一样。Merge表本身没数据，对它的操作实际上是对内部的MyISAM表操作。
	存储为.frm和.mrg两个文件。



