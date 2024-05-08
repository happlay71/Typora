```
# 查询
# 查询所有数据库
show databases;
# 查询当前数据库
select dateabase();
# 创建
create database [if not exists] 数据库名 [default charset 字符集] [coliate 排序规则];
# 删除
drop database [if exists] 数据库名;
# 使用
use 数据库名;
	# 查询当前数据库所有表
	show tables;
	# 查询表的结构
	desc 表名;
	# 查询指定表的jian'bia语句
	show create table 表名;
```

![](https://happlay-docs.oss-cn-beijing.aliyuncs.com/docs/屏幕截图 2023-08-28 170153.png)

![屏幕截图 2023-08-28 170614](https://happlay-docs.oss-cn-beijing.aliyuncs.com/docs/屏幕截图 2023-08-28 170614.png)



```
# 添加字段
alter table 表名 add 字段名 类型（长度） [comment 注释] [约束];
# 修改数据类型
alter table 表名 modify 字段名 新数据类型（长度）;
# 修改字段名和字段类型
alter table 表名 change 旧字段名 新字段名 类型（长度）[comment 注释] [约束];
# 删除字段
alter table 表名 drop 字段名;

# 修改表名
alter table 表名 rename to 新表名; 
# 删除表
drop table [if exists] 表名;
# 删除指定表并重新创建创建该表;
truncate table 表名;
```

