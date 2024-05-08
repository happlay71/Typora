作用：执行SQL语句

```
int executeUpdate(sql):执行DML、DDL语句
> 返回值：(1)DML语句影响的行数(2)DDL语句执行后，执行成功也可能返回0
ResultSet executeQuery(sql):执行DQL语句
> 返回值：ResultSet结果集对象
```

```java
@Test
    public void testDML() throws Exception {
        // 注册驱动
//        Class.forName("com.mysql.cj.jdbc.Driver");

        // 获取链接
        String url = "jdbc:mysql:///test";
        String username = "root";
        String password = "547118";
        Connection conn =  DriverManager.getConnection(url, username, password);

        // 定义sql
        String sql = "update user set money = 3000 where id = 4";

        // 获取执行sql的对象 Statement
        Statement stmt = conn.createStatement();
        // 执行sql
        int count = stmt.executeUpdate(sql); // 受影响的行数
//        System.out.println(count);
        if (count > 0) {
            System.out.println("修改成功");
        } else {
            System.out.println("修改失败");
        }

        // 释放资源
        stmt.close();
        conn.close();
    }
```

