```
# 管理用户
# 查询用户
use mysql;
select * from user;
# 创建用户
create user '用户名'@'主机名' identified by '密码';
# 修改用户密码
alter user '用户名'@'主机名' identified with mysql_native_password by '新密码';
# 删除用户
drop user '用户名'@'主机名';
```

```mysql
# 创建用户itcast，只能在当前主机localhost访问
create user 'itcast'@'localhost' identified by '123456';
# 创建用户heima，可在任意主机访问该数据库
create user 'heima'@'%' identified by '123456';
# 修改用户heima的访问密码
alter user 'heima'@'%' identified with mysql_native_password by '1234';
# 删除用户
drop user 'itcast'@'localhost';
```

权限控制

| 权限                | 说明               |
| ------------------- | ------------------ |
| all, all privileges | 所有权限           |
| select              | 查询数据           |
| insert              | 插入数据           |
| update              | 修改数据           |
| delete              | 删除数据           |
| alter               | 修改表             |
| drop                | 修改数据库/表/视图 |
| create              | 创建数据库/表      |

```
# 查询权限
show grants for '用户名'@'主机名';
# 授予权限
grant 权限列表 on 数据库名.表名 to '用户名'@'主机名';
# 撤销权限
revoke 权限列表 on 数据库名.表名 from '用户名'@'主机名';
```

