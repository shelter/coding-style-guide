# CSS Style Guide

## 文档目录

1. [编码风格](#1-编码风格)
2. [CSS规则](#2-CSS规则)

## 1 代码风格

### 1.1 css文件使用小写英文单词命名, 多个单词之间使用`-`连接。
```
  // bad
  courseList.css
  课程列表.css
  
  // good
  course-list.css
```

### 1.2 使用2个空格soft tabs缩进。
```
  // bad
  .selecter {
  ∙∙∙∙margin: 0;
  }
  
  // good
  .selecter {
  ∙∙margin: 0;
  }
```

### 1.3 css选择器使用小写英文单词命名, 多个单词之间使用`-`连接。
```
  // bad
  .imgList {
    margin: 0;
  }
  
  // good
  .img-list {
    margin: 0;
  }
```

### 1.4 选择器 与 `{ `之间保留一个空格。
```
  // bad
  .selector{
    margin: 0;
  }

  /* good */
  .selector {
    margin: 0;
  }
```

### 1.5 css属性值与冒号`:`间保留一个空格。
```
  // bad
  .selector {
    padding:0;
  }

  /* good */
  .selector {
    padding: 0;
  }
```

### 1.6 css属性在一行显示时，起始大括号`{`和结束大括号`}`间各保留一个空格并且每个属性间保留一个空格。
```
  // bad
  .selector {padding:0;margin:0;}

  /* good */
  .selector { padding: 0; margin: 0; }
```

### 1.7 css每条属性以分号`;`结尾。
```
  // bad
  .selector{
    margin: 0
  }

  /* good */
  .selector {
    margin: 0;
  }
```

### 1.8 css属性定义超过3条每行显示一条属性。
```
  // bad
  .selector { margin: 0; padding: 0; list-style: none; height: 100px; }
  
  // good
  .selector {
    height: 0;
    margin: 0;
    padding: 0;
    list-style: none;
  }
```

### 1.9 css属性定义尽可能使用简写, `0px`省略后面`px`, 色号`#ff000`缩写为`#f00`形式, `0.5`缩写为`.5`。
```
  // bad
  .selector {
    padding-top: 0px;
    padding-right: 10px;
    padding-bottom: 0px;
    padding-left: 10px;
    background-color: #ffffff;
  }
  
  // good
  .selector {
    padding: 0 10px;
    background-color: #fff;
  }
```

### 1.10 多个选择器共用一组属性，每个选择器占一行。
```
  // bad
  .post, .page, .comment {
    line-height: 1.5;
  }
  
  // good
  .post,
  .page,
  .comment {
    line-height: 1.5;
  }
```

### 1.11 css属性书写顺序
1. Positioning
2. Box model 盒模型
3. Typographic 排版
4. Visual 外观
```
  // bad
  .selector {
    height: 10px;
    width: 100px;
    line-height: 1.5;
    position: relative;
  }
  
  // good
  .selector {
    position: relative;
    width: 100px;
    height: 10px;
    line-height: 1.5;
  }
```

## 2 CSS规则

### 2.1 css文件编码格式使用utf-8。

### 2.2 选择器命名尽可能语义化，避免过度使用`pt20`, `mt10`此类只用作样式的选择器。
```
  // bad
  .s1 {
    ...
  }
  .s1 .bottom {
    ...
  }
  
  // good
  .news-list {
    ...
  }
  .news-list-item {
    ...
  }
  .news-list-item-hot {
    ...
  }
```

### 2.3 尽可能降低样式属性的影响范围，避免对公共标签，选择器设置样式属性。
```
  // bad
  div {
    height: 10px;
  }
  .active {
    color: #f00;
  }
  
  // good
  .goods-list-item {
    height: 10px;
  }
  .goods-list-item-active {
    color: #f00;
  }
  
  // 或
  .goods-list-item.active {
    color: #f00;
  }
```
