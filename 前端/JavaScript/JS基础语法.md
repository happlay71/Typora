[TOC]

#### 书写语法

区别大小写：与Java一样，变量名。函数名以及其他一切东西都是

结尾的分号可有可无

注释：

​	单行注释：//注释内容

​	多行注释：/*注释内容 */

大括号表示代码块

```javascript
//判断
if (count == 3) {
    alert(count);
}
```

#### 输出语句

使用window.alert()写入警告框

使用document.write()写入HTML输出

使用console.log()写入浏览器控制台

```html
<script>
    window.alert("Hello JavaScrupt");//浏览器弹出警告框
	document.write("Hello HavaScript");//写入HTML，在浏览器展示
	console.log("Hello JavaScript");//写入浏览器控制台
</script>
```

#### 变量

JavaScript中用var关键字(variable的缩写)来声明变量。

JavaScript是一门弱类型语言，变量可以存放不同类型的值。

变量名需要遵循如下规则：

​	组成字符可以是任何字母、数字、下划线(……)或美元符号($)

​	数字不能开头

​	建议使用驼峰命名

##### var

```javascript
// 全局变量、可重复定义
var a = 20;
a = "张三";
```

##### let

```javascript
// 非全局变量、不可重复定义
{
    let x = 1;
    alert(x);
}
```

##### const

```javascript
const:常量，不能改变
const pi = 3.14;
```

#### 数据类型

使用typeof运行符可以获取数据类型

```javascript
var a = 20;
alert(typeof a);
```



|                          原始类型                           |
| :---------------------------------------------------------: |
|         number:数字(整数、小数、NaN(Not a Number))          |
|                  string:字符串，单双引皆可                  |
|                  boolean:布尔。true,false                   |
|                        null:对象为空                        |
| undefined:当声明的变量未初始化是，该变量的默认值是undefined |

#### 运算符

| 运算符     |                                                             |
| ---------- | ----------------------------------------------------------- |
| 算术运算符 | +，-，*，/，%，++，--                                       |
| 赋值运算符 | =，+=，-=，*=，/=，%=                                       |
| 比较运算符 | >，<，>=，<=，!=，==(会进行类型转换)，===(不会进行类型转换) |
| 逻辑运算符 | &&，\|\|，!                                                 |
| 三元运算符 | 条件表达式？true_value:false_value                          |

#### 类型转换

字符串类型转换为数字：

​	将字符串字面值转为数字。如果字面值不是数字，则转为Nan。

```javascript
alert(parseInt("12a2")) //12 
```

其他类型转为boolean：

​	Number：0和Nan为false，其他均转为true。

​	String：空字符串为false，其他均转为true。

​	Null和undefined：均转为false。

#### 流程控制语句

| break         | 终止 switch 或循环。                              |
| ------------- | ------------------------------------------------- |
| continue      | 跳出循环并在顶端开始。                            |
| debugger      | 停止执行 JavaScript，并调用调试函数（如果可用）。 |
| do ... while  | 执行语句块，并在条件为真时重复代码块。            |
| for           | 标记需被执行的语句块，只要条件为真。              |
| function      | 声明函数。                                        |
| if ... else   | 标记需被执行的语句块，根据某个条件。              |
| return        | 退出函数。                                        |
| switch        | 标记需被执行的语句块，根据不同的情况。            |
| try ... catch | 对语句块实现错误处理。                            |

