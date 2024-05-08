有点问题

## PO中创建UserInfo实体类

- @AllArgsConstructor(staticName = "of")：有参构造，静态方法of，可以通过UserInfo.of来设置属性

```java
@Data
@NoArgsConstructor
@AllArgsConstructor(staticName = "of")  // 有参构造，静态方法of，可以通过UserInfo.of来设置属性
public class UserInfo {
    private Integer age;
    private String intro;
    private String gender;
}
```

## 修改User类

- @TableName(value = "tb_user", autoResultMap = true)：指定表名，自动结果集映射
- @TableField(typeHandler = JacksonTypeHandler.class)：设置类型处理器的类型

```java
@Data
@TableName(value = "tb_user", autoResultMap = true)  // 指定表名，自动结果集映射
public class User {
	………………
	/**
     * 详细信息
     */
//    private String info;
    // 设置类型处理器的类型
    @TableField(typeHandler = JacksonTypeHandler.class)
    private UserInfo info;
    ………………
}
```

## 修改 VO中对应的属性

```java
//    private String info;
    private UserInfo info;
```



## 修改调用的语句

```java
//        user.setInfo("{\"age\": 24, \"intro\": \"英文老师\", \"gender\": \"female\"}");
        user.setInfo(UserInfo.of(24, "英语老师", "female"));
```

