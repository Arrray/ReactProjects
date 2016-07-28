JSX 一种语法,而不是一种语言

jsx特点

类XML 语法,更容易接受
增强JS 语法
结构清晰
抽象程度高
代码模块化


react中

1.首字母大小写

自定义节点--首字母大写
dom 标准节点--首字母小写

2.组件嵌套


3.求值表达式
语句不可以进行运算
表达式可以进行运算

函数本身可以作为一个表达式使用，进行求值

4.驼峰命名

5.htmlFor和 className 别名代替

6.注释，需要大括号包括
{
这里是注释
}

多行注释 /*  */
单行注释 //

css 样式

嵌套

条件判断的四种写法

条件判断的四种写法


1.三元表达式法
分为三部分,'?',':'和属性值'name="lihua"',若有属性值,则显示属性的值,若没有属性值,则显示':'后面的内容
{this.props.name ? this.props.name : "World"}
name="lihua"

完整代码
<script type="text/jsx">
var style = {
color: "red",
border: "1px #000 solid"
};
var HelloWorld; HelloWorld = React.createClass({
render: function () {
return <p>Hello , {this.props.name ? this.props.name : "World"}</p>
}
});
ReactDOM.render(<div style={style}><HelloWorld name="lihua"></HelloWorld></div> ,document.body);
</script>


2.使用变量
写一个 getName 的方法,获取到name之后将其传递给一个变量,然后输出

完整代码
<script type="text/jsx">
var style = {
color: "red",
border: "1px #000 solid"
};
var HelloWorld; HelloWorld = React.createClass({
getName:function () {
if (this.props.name)
return this.props.name;
else
return "World"
},
render: function () {
var name = this.getName();
return <p>Hello , {name}</p>
}
});
ReactDOM.render(<div style={style}><HelloWorld name="lihua"></HelloWorld></div> ,document.body);
</script>


3.通过 get 方法直接输出。直接使用函数调用
也可以不讲获取到的属性传递给变量,而是直接输出
完整代码
<script type="text/jsx">
var style = {
color: "red",
border: "1px #000 solid"
};
var HelloWorld; HelloWorld = React.createClass({
getName:function () {
if (this.props.name)
return this.props.name;
else
return "World"
},
render: function () {
return <p>Hello , {this.getName()}</p>
}
});
ReactDOM.render(<div style={style}><HelloWorld name="lihua"></HelloWorld></div> ,document.body);
</script>


4.使用或运算符
如果左边的值为真,直接输出左边的值,反之,输出右边的值
<script type="text/jsx">
var style = {
color: "red",
border: "1px #000 solid"
};
var HelloWorld; HelloWorld = React.createClass({
render: function () {
return <p>Hello , {this.props.name || "World"}</p>
}
});
ReactDOM.render(<div style={style}><HelloWorld name="lihua"></HelloWorld></div> ,document.body);
</script>



万能的函数表达式
<script type="text/jsx">
var style = {
color: "red",
border: "1px #000 solid"
};
var HelloWorld; HelloWorld = React.createClass({
render: function () {
return <p>Hello , {
(function (obj) {
if (obj.props.name)
return obj.props.name;
else
return "World"
})(this)
}</p>
}
});
ReactDOM.render(<div style={style}><HelloWorld name="lihua"></HelloWorld></div> ,document.body);
</script>

另外一种写法,将(this)包含在括号里面
<script type="text/jsx">
var style = {
color: "red",
border: "1px #000 solid"
};
var HelloWorld; HelloWorld = React.createClass({
render: function () {
return <p>Hello , {
(function (obj) {
if (obj.props.name)
return obj.props.name;
else
return "World"
}(this))
}</p>
}
});
ReactDOM.render(<div style={style}>
<HelloWorld name="lihua"></HelloWorld>
</div>, document.body);
</script>



非DOM 属性
dangerouslySetlnnerHTML ,ref ,key

dangerouslySetlnnerHTML:在JSX 直接插入代码
演示代码
<script type="text/jsx">
var style = {
color: "red",
border: "1px #000 solid"
};
var rawHtml = {
__html:"<h1>I`m inner HTML</h1>"
};
var HelloWorld; HelloWorld = React.createClass({
render: function () {
return <p>Hello , World</p>
}
});
ReactDOM.render(<div style={style} dangerouslySetInnerHTML={rawHtml}></div> ,document.body);
</script>


ref:父组件"引用"子组件
演示代码
<p ref="childp"></p>


key:提高渲染性能
演示代码
<script type="text/jsx">
var style = {
color: "red",
border: "1px #000 solid"
};
var HelloWorld; HelloWorld = React.createClass({
render: function () {
return <ul>
<li key="1">1</li>
<li key="2">2</li>
<li key="3">3</li>
<li key="4">4</li>
</ul>
}
});
ReactDOM.render(<div style={style} ><HelloWorld></HelloWorld></div> ,document.body);
</script>


源码阅读方法

1.从执行顺序入手

2.适当忽略细节

3.重视烂笔头

4.反复阅读


理解解释器架构

入口函数->载入所有模块->解析JSX 文件->执行JS


入口函数:判断环境,并引用大函数














































