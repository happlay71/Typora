```java
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.Statement;

		// 注册驱动
        Class.forName("com.mysql.cj.jdbc.Driver");  // 可省略

        // 获取链接
        String url = "jdbc:mysql://127.0.0.1:3306/test";
		// 若路由为默认值则可改为
		// jdbc:mysql://
        String username = "root";
        String password = "547118";
        Connection conn =  DriverManager.getConnection(url, username, password);

        // 定义sql
        String sql = "update user set money = 1000 where id = 1";

        // 获取执行sql的对象 Statement
        Statement stmt = conn.createStatement();

        // 执行sql
        int count = stmt.executeUpdate(sql); // 受影响的行数

        // 处理结果
        System.out.println(count);

        // 释放资源
        stmt.close();
        conn.close();
```

