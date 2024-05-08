![](https://happlay-docs.oss-cn-beijing.aliyuncs.com/docs/屏幕截图 2023-09-01 142636.png)

```
# 基础查询
# 查询多个字段
select 字段1，字段2，…… from 表名;
select * from 表名;
# 设置别名 可不加as
select 字段1 [as 别名1], 字段2 [as 别名2] …… from 表名;
# 去除重复记录
select distinct 字段列表 from 表名;

# 条件查询
select 字段列表 from 表名 where 条件列表;
```

![](https://happlay-docs.oss-cn-beijing.aliyuncs.com/docs/屏幕截图 2023-09-01 151418.png)

```mysql
# 查询条件
select * from employee where age > 80;
select * from employee where idcard is null;
select * from employee where age != 88;
select * from employee where age <> 88;
select * from employee where age > 15 and age < 18; # 或&&
select * from employee where age between 15 and 18; # 闭区间，不能写反
select * from employee where age = 18 or age = 20 or age = 80;
select * from employee where age in(18, 20, 80);
select * from employee where name like '___';  # 查询字符串的个数
select * from employee where idcard like '%x'; # 查询结尾为x的数据
```

```
# 聚合函数
select 聚合函数(字段列表) from 表名;
```

![](https://happlay-docs.oss-cn-beijing.aliyuncs.com/docs/屏幕截图 2023-09-01 174916.png)

```mysql
-- 聚合函数 null不计入统计
select count(*) from employee; # 统计数量
select count(idcard) from employee;
select avg(age) from employee; # 统计平均数
select max(age) from employee;
select min(age) from employee;
select avg(age) from employee where workaddress = '西安';
```

```
# 分组查询
select 字段列表 from 表名 [where 条件] group by 分组字段名 [having 分组后过滤条件];
```

where 和 having 区别

​	>执行时机不同：where是分组之前进行过滤，不满足where条件，不参与分组；而having是分组之后对结果进行过滤。

​	>判断条件不同：where不能对聚合函数进行判断，而having可以。

```mysql
-- 分组查询
select gender, count(*) from employee group by gender; # 根据性别分组，统计男女生数量
select gender, avg(age) from employee group by gender; # 根据性别分组，统计男女生平均年龄
select workaddress, count(*) address_count from employee where age < 45 group by workaddress having address_count >= 2;
```

```
# 排序查询
select 字段列表 from 表名 order by 字段1 排序方式, 字段2 排序方式2;  asc：升序(默认) desc：降序
```

```mysql
-- 排序查询
select * from employee order by age asc;
select * from employee order by entrydate desc;
select * from employee order by age asc, entrydate desc; # 先按时间排序，再按时间进行降序排序
```

```
# 分页查询
select 字段列表 from 表名 limit 起始索引，查询记录数;

```

注意

·起始索引从0开始，起始索引=（查询页码-1）*每页显示记录数。

·分页查询是数据库的方言，不同的数据库有不同的实现，MySQL中是LIMIT。

·如果查询的是第一页数据，起始索引可以省略，直接简写为limit 10。

```mysql
-- 分页算法
# 查询第1页员工数据，每页展示10条记录
select * from employee limit 0, 10;
select * from employee limit 10;
select * from employee limit 10, 10;
```

| 语句的执行顺序 |                |
| -------------- | -------------- |
| from           | 表名列表       |
| where          | 条件列表       |
| group by       | 分组字段列表   |
| having         | 分组后条件列表 |
| select         | 字段列表       |
| order by       | 排序字段列表   |
| limit          | 分页参数       |

```mysql
-- --------------DQL 语句练习 --------------
# 查询年龄为20，21，22，23岁的女性员工信息
select * from employee where gender = '女' and age between 20 and 23;
# 查询性别为男、且年龄在20-40岁以内的姓名为三个字的员工
select * from employee where gender = '男' and (age between 20 and 40) and name like '___';
# 统计员工表中，年龄小于60的、男性员工和女性员工的人数
select gender, count(*) from employee where age < 60 group by gender;
# 查询所有年龄小于等于35岁的员工的姓名和年龄，并对查询结果按年龄升序排序，如果年龄相同按入职时间降序排序
select name, age from employee where age <= 35 order by age asc, entrydate desc;
# 查询性别为男，且年龄在20-40岁以内的前5个员工信息，对查询结果按年龄升序排序，年龄相同按入职时间升序排序。
select * from employee where gender = '男' and (age between 20 and 40) order by age asc, entrydate desc limit 5;
```

