# clickjacking js bypass

目前较好的防御方法
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
