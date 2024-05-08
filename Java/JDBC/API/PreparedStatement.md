```java
// 获取链接
        String url = "jdbc:mysql:///test?useSSL=true";
        String username = "root";
        String password = "547118";
        Connection conn =  DriverManager.getConnection(url, username, password);

        // 接受用户输入，用户名和密码
        String name = "zhangsan";
        String pwd = "123";

        String sql = "select * from tb_user where username = '"+ name +"' and '"+ pwd +"'";

        Statement stmt = conn.createStatement();

        ResultSet rs = stmt.executeQuery(sql);

        if (rs.next()) {
            System.out.println("登陆成功");
        } else {
            System.out.println("登录失败");
        }

        rs.close();
        stmt.close();
        conn.close();
```

## SSL加密

```
String url = "jdbc:mysql:///test?useSSL=true";

SSL协议提供服务主要：
1）认证用户服务器，确保数据发送到正确的服务器； 　　 .
2）加密数据，防止数据传输途中被窃取使用；
3）维护数据完整性，验证数据在传输过程中是否丢失；
当前支持SSL协议两层：
SSL记录协议（SSL Record Protocol）：建立靠传输协议（TCP）高层协议提供数据封装、压缩、加密等基本功能支持
SSL握手协议（SSL Handshake Protocol）：建立SSL记录协议用于实际数据传输始前通讯双进行身份认证、协商加密
算法、 交换加密密钥等。

```



## 开启预编译功能

```
String url = "jdbc:mysql:///test?&useServerPrepStmts=";
```



## 作用

1.预编译SQL语句并执行：预防SQL注入问题

```java
// 获取PreparedStatement对象
// SQL语句中的参数值，使用？占位符替代
String sql = "select * from user where username = ? and password = ?";
// 通过Connection对象获取，并传入对应的sql语句
PreparedStatement pstmt = conn.prepareStatement(sql);

// 设置参数值
PreparedStatement对象：setXxx(参数1，参数2)：给？赋值
    Xxx：数据类型；如setlnt(参数1，参数2)
    参数：
    	参数1：？的位置编号，从1开始
    	参数2：？的值
    
// 执行SQL
executeUpdate();/executeQuery; : 不需要再传递sql 
```

## SQL注入

​	SQL注入是通过操作输入来修改事先定义好的SQL语句，用以达到执行代码对服务器进行攻击的方法

```java
String name = "ahslja";  // 乱写
String pwd = "' or '1' = '1";
```

