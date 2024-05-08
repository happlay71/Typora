[TOC]

#### 事件

HTML事件是发生在HTML元素上的“事情”。

​	按钮被点击

​	鼠标移动到元素上

​	按下键盘按键

#### 事件监听

JavaScript可以在事件被侦测到时执行代码。

#### 事件绑定

##### 方式一：通过HTML标签中的事件属性进行绑定

```html
<input type="button" onclick="on()" value="按钮1">
<script>
	function on(){
        alert('我被点击');
    }
</script>
```

##### 方式二：通过DOM元素属性绑定

```html
<input type="button" id="btn" value="按钮2">
<script>
	document.getElementById('btn').onclick=function(){
        alert('我被点击');
    }
</script>
```

#### 常见事件

|   事件名    |                  说明                  |
| :---------: | :------------------------------------: |
|   onclick   |              鼠标单击事件              |
|   onblur    |              元素失去焦点              |
|   onfocus   |              元素获得焦点              |
|   onload    |        某个页面或图像被完成加载        |
|  onsubmit   | 当表单提交时触发该事件(作用在表单标签) |
|  onkeydown  |           某个键盘的键被按下           |
| onmouseover |          鼠标被移到某元素之上          |
| onmouseout  |            鼠标从某元素移开            |

