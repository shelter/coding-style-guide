# HTML Style Guide

## 文档目录

1. [编码风格](#1-编码风格)
2. [HTML规则](#2-HTML规则)

## 1 编码风格

### 1.1 html文件使用小写英文单词命名, 多个单词之间使用`-`连接。
```
  // bad
  courseList.html
  课程列表.html
  
  // good
  course-list.html
```

### 1.2 使用2个空格soft tabs缩进。
```
  // bad
  <ul class="list">
  ∙∙∙∙<li class="list-item">item 1</li>
  ∙∙∙∙<li class="list-item">item 2</li>
  ∙∙∙∙<li class="list-item">item 3</li>
  </ul>
  
  // good
  <ul class="list">
  ∙∙<li class="list-item">item 1</li>
  ∙∙<li class="list-item">item 2</li>
  ∙∙<li class="list-item">item 3</li>
  </ul>
```

### 1.3 html标签属性值统一使用双引号。
```
  // bad
  <img class='pic' src='some/path/some-img.png' />
  
  // good
  <img class="pic" src="some/path/some-img.png" />
```

### 1.4 html标签统一使用小写。
```
  // bad
  <DIV></DIV>
  <SPAN></span>
  
  // good
  <div></div>
  <span></span>
```

### 1.5 引入css，js时省略`type="text/css"`和`type="text/javascript"`属性。
```
  // bad
  <link type="text/css" href="external-style.css" />
  <style type="text/css">
    ...
  </style>
  
  <script type="text/javascript" src="external-script.js"></script>
  <script type="text/javascript">
    ...
  </script>
  
  // good
  <link rel="stylesheet" href="external-style.css" />
  <style>
    ...
  </style>
  
  <script src="external-script.js"></script>
  <script>
    ...
  </script>
```

### 1.6 注释标签与注释文本前后各保留一个空格。
```
  // bad
  <!--注释-->
  
  // good
  <!-- 注释 -->
```

## 2 HTML规则

### 2.1 html文件必须以`<!DOCTYPE html>`开头。
```
  // bad
  <html>
    <head>
      <title>Page title</title>
    </head>
    <body>
      <!-- page content -->
    </body>
  </html>
  
  // good
  <!DOCTYPE html>
  <html>
    <head>
      <title>Page title</title>
    </head>
    <body>
      <!-- page content -->
    </body>
  </html>
```

### 2.2 html字符编码使用`utf-8`编码。
```
  // bad
  <head>
    <meta charset="gb2312">
  </head>

  // good
  <head>
    <meta charset="utf-8">
  </head>
```

### 2.3 css外部引用必须保留`rel="stylesheet"`属性。
```
  // bad
  <link href="external-style.css" />
  
  // good
  <link rel="stylesheet" href="external-style.css" />
```

### 2.4 `img`标签`src`属性值不得为空或使用中文。
```
  // bad
  <img src="" />
  <img src="用户头像.png" />
  
  // good
  <img src="portrait.png" />
```
