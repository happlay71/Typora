[TOC]

## 数组对象

JavaScript中Array对象用于定义数组。

```javascript
// 长度可变 类型可变

// 方式一
var 变量名 = new Array(元素列表);
var arr = new Array(1, 2, 3, 4);
// 方式二
var 变量名 = [元素列表];
var arr = [1, 2, 3, 4]

// 访问
arr[索引] = 值;
arr[10] = "hello";
```

| 属性   | 描述                       |
| ------ | -------------------------- |
| length | 设置或返回数组中元素的数量 |

| 方法      | 描述                                             |
| --------- | ------------------------------------------------ |
| forEach() | 遍历数组中的每个优质的元素，并调用一次传入的函数 |
| push()    | 将新元素添加到数组的末尾，并返回新的长度         |
| splice()  | 从数组中删除元素                                 |

```javascript
// ES6 箭头函数：
arr.forEach((e) => {
    console.log(e);
})

// push：添加元素到数组末尾
arr.push(7, 8, 9);
console.log(arr);

// splice：删除元素
arr.splice(2, 2); // 从索引开始，进行n个
```

## 字符串对象

```javascript
// 方式一
var 变量名 = new String("……");
var str = new String("Hello");
// 方式二
var 变量名 = "……";
var str = "Hello";
var str = 'hello';
```

| 属性   | 描述         |
| ------ | ------------ |
| length | 字符串的长度 |

| 方法        | 描述                                             |
| ----------- | ------------------------------------------------ |
| charAt()    | 返回在指定位置的字符                             |
| indexof()   | 检索字符串                                       |
| trim()      | 去除字符串两边的空格                             |
| substring() | 提取字符串中两个指定的索引号之间的字符，左闭右开 |

## 自定义对象

```javascript
var 对象名 = {
    属性名1:属性值1,
    属性名2:属性值2,
    函数名称:function(形参列表) {}
};

var user = {
    name:"Tom",
    age:20,
    gender:"male",
    eat: function(){
        alert("用膳~");
    }
    
    eat(){
        alert("用膳~");
    }
};

// 调用格式
对象名.属性名;
对象名.函数名();
console.log(user.name);
user.eat();
```

## JSON(JavaScript Object Notation)

通过JavaScript对象标记法书写的文本

```JSON
var 变量名 = '{"key1":value1, "key2":value2}';

var userStr = '{
	"name":"Tom",
	"age":20,
	"gender":"male"
}';
```

value的数字类型：

​	数字(整数或浮点数)

​	字符串(在双引号中)

​	逻辑值(true或false)

​	数组(在方括号中)

​	对象(在花括号中)

​	null

```
// JSON字符串转为JS对象
var jsObject = JSON.parse(userStr);

// JS对象转为JSON字符串
var jsonStr = JSON.stringify(jsObject);
```

## BOM(Browser Object Model) 浏览器对象模型

浏览器对象模型，允许JavaScript与浏览器对话，JavaScript将浏览器的各个组成部分封装为对象。

组成：

​	Window：浏览器窗口对象

​		获取：直接使用window，其中window.可以省略。

```javascript
window.alert("Hello Window");
alert("Hello Window");
```

| 属性      |                                               |
| --------- | --------------------------------------------- |
| history   | 对History对象的只读引用。                     |
| location  | 用于空窗口或框架的Location对象。/地址栏对象。 |
| navigator | 对Navigator对象的只读引用                     |

获取：使用window.location获取，其中window.可以省略。

属性：

​	href：设置或返回完整的URL。

```javascript
location.href = "https://www.bilibili.com";
```



| 方法          |                                                |
| ------------- | ---------------------------------------------- |
| alert()       | 显示带有一段消息和一个确认按钮的警告框         |
| confirm()     | 显示带有一段消息以及确认按钮和取消按钮的对话框 |
| setlnterval() | 按照指定的周期(以毫秒计)来调用函数或计算表达式 |
| setTimeout()  | 在指定的毫秒数后调用函数或计算表达式           |

```javascript
// setInterval
var i = 0;
setInterval(function(){
    i++;
    console.log("定时器执行" + i + "次");
}, 2000);

// setTimeout
setTimeout(function(){
    alert("JS");
}, 3000);
```

​	Navigator：浏览器对象

​	Screen：屏幕对象

​	History：历史记录对象

​	Location：地址栏对象

## DOM(Document Object Model) 文档对象模型

将标记语言的各个组成部分封装成为对应的对象：

​	Document：整个文档对象

​	Element：元素对象

​	Attribute：属性对象

​	Text：文本对象

​	Comment：注释对象

JavaScript通过DOM，就能够对HTML进行操作：

​	改变HTML元素的内容

​	改变HTML元素的样式(CSS)

​	对HTML DOM事件作出反应

​	添加和删除HTML元素
