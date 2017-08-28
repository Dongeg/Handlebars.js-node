# handlebars.js

### 介绍

Handlebars 是一个前端模板引擎，据说能兼容到IE6

### 用法

直接这么用

<script type="text/javascript" src=".js/handlebars.js"></script> 

一个最简单的案例

```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title></title>
</head>
<body id="main">
    <script src="https://cdn.bootcss.com/jquery/3.2.1/jquery.min.js"></script>
	<script src="handlebars-v4.0.10.js"></script>
	<script id="tpl" type="text/x-handlebars-template">  
	<div class="demo">  
        <h1>{{title}}</h1>
        <p>{{content}}</p>
	</div>
	</script>  
	<script>
    var tpl   =  $("#tpl").html();
    //预编译模板
    var template = Handlebars.compile(tpl);
    //模拟json数据
    var context = { title: "zhaoshuai", content: "learn Handlebars"};
    //匹配json内容
    var html = template(context);
    //输入模板
    $("#main").html(html);
	</script>
</body>
</html>
```

### Block表达式


Handlebars模板
```
<ul>  
{{#programme}}
    <li>{{language}}</li>
{{/programme}}
</ul> 
```
json数据

```
{
  programme: [
    {language: "JavaScript"},
    {language: "HTML"},
    {language: "CSS"}
  ]
}
```

渲染效果

```
<ul>  
  <li>JavaScript</li>
  <li>HTML</li>
  <li>CSS</li>
</ul>  

```

### 数组循环

模板

```
<ul>  
    {{#each name}}
        <li>{{this}}</li>
    {{/each}}
</ul>  
```

数据

```
{
    name: ["html","css","javascript"]
};
```

结果

```
<ul>  
  <li>JavaScript</li>
  <li>HTML</li>
  <li>CSS</li>
</ul>  

```

### if else

模板

//如果list数组存在
```
{{#if list}}
<ul id="list">  
    {{#each list}}
        <li>{{this}}</li>
    {{/each}}
</ul>  
{{else}}
    <p>{{error}}</p>
{{/if}}
```

数据


```
var data = {  
    list:['HTML5','CSS3',"WebGL"],
    "error":"数据取出错误"
}
```

### unless

{{#unless data}} 条件不存在则触发
