1. 获取执行SQL的对象

   ```
   # 普通执行SQL对象
   Statement createStatement()
   # 预编译SQL的执行SQL对象：防止SQL注入
   PreparedStatement prepareStatement(sql)
   # 执行存储过程的对象
   CallableStatement prepareCall(sql)
   ```

   

2. JDBC管理事务

   ```
   开启事务：setAutoCommit(boolean autoCommit): true为自动提交事务，false为手动提		交事务，开启事务
   提交事务：commit()
   回滚事务：rollback()
   ```

   ```java
   # 例子
   try {
               // 开启事务
               conn.setAutoCommit(false);
               
               // 执行sql
               int count1 = stmt.executeUpdate(sql1); // 受影响的行数
               System.out.println(count1);
   
               int count2 = stmt.executeUpdate(sql2);
               // 处理结果
               System.out.println(count2);
   
               // 提交事务
               conn.commit();
           } catch (Exception e) {
               // 回滚事务
               conn.rollback();
               e.printStackTrace();
           }
   ```

   