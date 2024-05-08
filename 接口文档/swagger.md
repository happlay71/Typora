[TOC]

# [Swagger](https://swagger.io/)

- API框架，RsetFul Api文档在线自动生成工具=>API文档与API定义同步更新。
- 直接运行，可以在线测试API接口

在项目使用Swagger需要springbox：

- swagger2

- ui


| 注解                                               | 说明                                                         |
| -------------------------------------------------- | ------------------------------------------------------------ |
| @Api(tags="xxx模块说明")                           | 作用在模块类上                                               |
| @ApiParam("xxx参数说明")                           | 作用在参数、方法、和字段上，required为true表示必须传参数     |
| @ApiModel("xxxPOJO说明")                           | 作用在模型类上                                               |
| @ApiOperation("xxx接口说明")                       | 作用在接口方法上                                             |
| @ApiModelProperty(value="xxx属性说明",hidden=true) | 作用在类方法和属性上，hidden为true可以隐藏该属性，required为true表示添加或修改数据时必须填参数 |

