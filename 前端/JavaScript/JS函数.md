函数(方法)是被设计为执行特定任务的代码块

```javascript
function fuctionName(参数1，参数2……){
//代码
}

function add(a, b){
    return a + b;
}
// 或
var functionName = function(参数1，参数2){
    //代码
}

```

注：

​	形式参数不需要类型。因为JavaScript是弱类型语言

​	返回值也不需要定义类型，可以在函数内部直接使用return返回

调用：函数名称(实际参数列表)

```
var result = add(10, 20);
alert(result);
```

