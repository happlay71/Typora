[TOC]

# [Knife4j](https://doc.xiaominfo.com/docs/quick-start)

- 为Java MVC框架集成Swagger生成API文档提供了增强解决方案，前身是swagger-bootstrap-ui

首先，引用Knife4j的starter,Maven坐标如下：

```xml
<dependency>
    <groupId>com.github.xiaoymin</groupId>
    <artifactId>knife4j-openapi3-jakarta-spring-boot-starter</artifactId>
    <version>4.4.0</version>
</dependency>
```

引入之后，其余的配置，开发者即可完全参考[springdoc-openapi](https://springdoc.org/)的项目说明，Knife4j只提供了增强部分，如果要启用Knife4j的增强功能，可以在配置文件中进行开启

部分配置如下:

```yml
# springdoc-openapi项目配置
springdoc:
  swagger-ui:
    path: /swagger-ui.html
    tags-sorter: alpha
    operations-sorter: alpha
  api-docs:
    path: /v3/api-docs
  group-configs:
    - group: 'default'
      paths-to-match: '/**'
      packages-to-scan: com.xiaominfo.knife4j.demo.web
# knife4j的增强配置，不需要增强可以不配
knife4j:
  enable: true
  setting:
    language: zh_cn
```