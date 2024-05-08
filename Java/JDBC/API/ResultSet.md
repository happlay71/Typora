## 结果集对象

作用：封装了DQL查询语句的结果

```
ResultSet stmt.executeQuery(sql):执行DQL语句，返回ResultSet对象
```

获取查询结果

```
boolean next():(1)将光标从当前位置向前移动一行 (2)判断当前行是否为有效行
> 返回值：
		true：有效行，当前行有数据
		false：无效行，当前行没有数据
```

```
xxx getXxx(参数)：获取数据
> xxx：数据类型；如：int getInt(参数);String getString(参数)
> 参数：
		int：列的编号，从1开始
		String：列的名称
```

