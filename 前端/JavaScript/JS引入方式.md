#### 内部脚本：将JS代码定义在HTML页面中

JavaScript代码必须位于<script></script>标签之间

在HTML文档中，可以在任意地方，放置任意数量的<script>

一般会把脚本置于<body>元素的底部，可改善显示速度

```html
<script>
	alert("Hello JavaScript")
</script>
```



#### 外部脚本：将JS代码定义在外部JS文件中，然后引入到HTML页面中

外部JS文件中，只包含JS代码，不包含<script>标签

<script>标签不能自闭合

```html
<script src="js/demo.js"></script>
```

```javascript
alert("Hello JavaSc")
```

