# CSS Guide

## 文档目录

1. [命名规范](#1-命名规范)
2. [代码风格](#2-代码风格)
3. [通用](#3-通用)
4. [值与单位](#4-值与单位)
5. [文本编排](#5-文本编排)
6. [媒体查询](#6-媒体查询)
7. [代码注释](#7-代码注释)



## 1 命名规范

### 1.1 命名思想

区块、模块、组件等一个整个的结构遵循BEM命名思想；

* `.block` 代表了更高级别的抽象或组件；
* `.block_element` 代表`.block`的后代，用于形成一个完整的`.block`的整体；
* `.block--modifier` 代表`.block`的不同状态或不同版本;
* `.is-` | `.has-` | `.ext-` 代表`.block`的修饰符，**不使用双中划线`--`**。

示例：

```css
.person {
    margin: 0;
}

.person_hand {
    margin: 0;
}

.person--female {
    margin: 0;
}

.person--female_hand {
    margin: 0;
}
.person_hand--left {
    margin: 0;
}

```

!!!不可使用全局类名，前边必须要加上命名空间或父类;

示例：

```css
/* Not so great */

.show {
    margin: 0;
}

/* Better */

.person .show {
    margin: 0;
}

```
引用第三方样式，按其默认命名规则，可以不遵循BEM；

### 1.2 多词连接

多个单词使用小驼峰式命名，不允许使用中划线或者下划线连接多个单词；

示例：

```css
.newsList {
    margin: 0;
}

.stepFirstLine {
    margin: 0;
}

```

### 1.3 命名空间

* **布局**：以`g`为命名空间，例如：`.g-wrap` 、`.g-header`、`.g-content`、`.g-mian`、`.g-aside` 等；
* **工具**：以`u`为命名空间，**表示不耦合业务逻辑的、可复用的的工具**，例如：`.u-clearfix`、`.u-ellipsis` 等；
* **状态**：以`is`为命名空间，**表示动态的、具有交互性质的状态**，例如：`.is-open`、`.is-active`、`.is-selected` 等；
* **组件**：以`ui`或者`mod`为命名空间，**表示可复用、移植的组件模块**，例如：`.ui-slider`、`.mod-dropMenu`等；
* **扩展**：以`ext`为命名空间，**表示对组件基类的视觉形态的扩展**，例如：`.ext-cover、`、`.ext-alignLeft` 等；

**状态类或扩展类一般出现在组件的父级节点，并且不允许单独使用。举个例子，同一个页面有可能会在不同的地方都会使用`is-active`，并且每个`is-active`所操纵的节点的是不同的，所以要使用`.ui-userCard.is-active` 或 `.ui-userCard .is-active`来定义**

### 1.4 图片命名

* **图标**：以`ico`作为命名空间，例如：`.ico-close` 等；
* **内容图像**：以`img`作为命名空间，例如：`.img-userGuide` 等；

### 1.5 区块命名

**【推荐】** 一般区块都可以划分为头部、身体和尾部，因此建议给你的区块分别以 `hd`、`bd`、`ft`来划分；

示例：

```css
.ui-card__hd {
    margin: 0;
}

.ui-card__bd {
    margin: 0;
}

.ui-card__ft {
    margin: 0;
}
```


## 2 代码风格

### 2.1 空格

选择器 与 `{ `之间必须包含空格；

```css
/* Not so great */
.selector{
    margin: 0;
}

/* Better */
.selector {
    margin: 0;
}
```

`>`、`+`、`~` 选择器的两边各保留一个空格;

```css
/* Not so great */
main>nav {
    padding: 10px;
}
label+input {
    margin-left: 5px;
}
input:checked~button {
    background-color: #69C;
}

/* Better */
main > nav {
    padding: 10px;
}
label + input {
    margin-left: 5px;
}
input:checked ~ button {
    background-color: #69C;
}
```

### 2.2 属性

属性定义必须另起一行；

```css
/* Not so great */
.selector { margin: 0; padding: 0;}

/* Better */
.selector {
    margin: 0;
    padding: 0;
}
```

### 2.3 选择器

当一个 rule 包含多个 selector 时，每个选择器声明必须独占一行；

示例：

```css
/* Not so great */
.post, .page, .comment {
    line-height: 1.5;
}

/* Better */
.post,
.page,
.comment {
    line-height: 1.5;
}
```

## 3 通用

### 3.1 选择器

如无必要，不得为`id`、`class`选择器添加 *类型选择器* 进行限定；

示例：

```css
/* Not so great */
dialog#error,
p.danger-message {
    font-color: #c00;
}

/* Better */
#error,
.danger-message {
    font-color: #c00;
}
```

选择器的嵌套层级应该不大于 **3** 级，位置靠后的限定条件应可能精确;

示例：

```css
/* Not so great */
.comment ul li a span {

}
#top-hero .hero-avatar li.avatar .pic em {

}

/* Better */
.comment .date {

}
#top-hero .pic em {

}
```

### 3.2 属性
属性选择器中的值必须用双引号包围。不允许使用单引号，不允许不使用引号;

示例：

```css
/* Not so great */
article[character='juliet'] {
    voice-family: "Vivien Leigh", victoria, female
}

/* Better */
article[character="juliet"] {
    voice-family: "Vivien Leigh", victoria, female
}
```

## 4 值与单位

### 4.1 数值

当数值为 **0 - 1** 之间的小数时，省略整数部分的 **0**；

示例：

```css
/* Not so great */
.selector {
    opacity: 0.8;
}

/* Better */
.selector {
    opacity: .8;
}
```

### 4.2 长度

长度为 **0** 时须省略单位；

示例：

```css
/* Not so great */
.selector {
    margin: 0px 10px;
}

/* Better */
.selector {
    margin: 0 10px;
}
```

### 4.3 url()

url() 函数中的路径不加引号；

示例：

```css
/* Not so great */
.selector {
    background: url("bg.png");
}

/* Better */
.selector {
    background: url(bg.png);
}
```

### 4.4 颜色

RGB颜色值必须使用十六进制记号形式 `#rrggbb`，不允许使用 `rgb()`，带有alpha的颜色信息可以使用 `rgba()`；颜色值不允许使用命名色值；

示例：

```css
/* Not so great */
.selector {
    box-shadow: 0 0 2px rgba(0,128,0,.3);
    border-color: rgb(0, 128, 0);
    color: gray;
}

/* Better */
.selector {
    box-shadow: 0 0 2px rgba(0, 128, 0, .3);
    border-color: #008000;
    color: #999;
}
```

## 5 文本编排

### 5.1 字体

`font-family` 应当遵循以下顺序：

1. 西文字体在前，中文字体在后；
2. 效果佳 (质量高/更能满足需求) 的字体在前，效果一般的字体在后的顺序编写；
3. 最后必须指定一个通用字体族( serif / sans-serif )；
4. 定义中文字体时，应使用Unicode；

常用字体Unicode编码：

宋体			`\5B8B\4F53`

新宋体			`\65B0\5B8B\4F53`

黑体			`\9ED1\4F53`

微软雅黑		`\5FAE\8F6F\96C5\9ED1`

楷体_GB2312	`\6977\4F53_GB2312`

隶书			`\96B6\4E66`

幼园			`\5E7C\5706`

华文细黑		`\534E\6587\7EC6\9ED1`

细明体			`\7EC6\660E\4F53`

新细明体		`\65B0\7EC6\660E\4F53`

## 6 媒体查询

`Media Query` 不得单独编排，必须与相关的规则一起定义；

不要将他们一起放到一个独立的样式文件中，或者丢在文档的最底部，这样做只会让大家以后更容易忘记他们。

## 7 代码注释

### 7.1 单行注释

星号与内容之间必须保留一个空格；

示例：

```css
/* 课程任务列表 */
```

### 7.2 多行注释

星号要一列对齐，星号与内容之间必须保留一个空格；

示例：

```css
/**
 *  英语扩展听力列表
 */
```

### 7.3 文件注释

文件顶部必须包含文件注释，用 `@file` 标识文件说明。星号要一列对齐，星号与内容之间必须保留一个空格，标识符冒号与内容之间必须保留一个空格；
```css
/**
 * @file: 文件概要描述
 * @author: author-name
 *          author-name2
 * @update: 2017-10-19 10:30
 */
```

* `@update`为可选项，建议每次改动都更新一下；
* 当该业务项目主要由固定的一个或多个人负责时，需要添加`@author`标识；
