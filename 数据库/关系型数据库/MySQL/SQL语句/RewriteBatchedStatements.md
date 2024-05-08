*application.yaml*

```yaml
# mysql配置   rewriteBatchedStatements=true
# 在实现批量处理数据时不再是一条一条插入，而是打包起来
spring:
  datasource:
    url: jdbc:mysql://127.0.0.1:3306/mp?useUnicode=true&characterEncoding=UTF-8&autoReconnect=true&serverTimezone=Asia/Shanghai&rewriteBatchedStatements=true
```

