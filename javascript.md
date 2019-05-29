# JavaScript Style Guide

## 文档目录

1. [编码风格](#1-编码风格)
2. [JS规则](#2-JS规则)

## 1 编码风格

### 1.1 js文件使用小写英文单词命名, 多个单词之间使用`-`连接。
```
  // bad
  courseList.js
  课程列表.js
  
  // good
  course-list.js
```

### 1.2 变量名, 函数名使用小驼峰表示法。
```
  // bad
  function my_function () { }
  let my_var = 'hello';
  
  // good
  function myFunction () { }
  let myVar = 'hello';
```

### 1.3 构造函数名, 类名使用大驼峰表示法。
```
  // bad
  function animal() {}
  class people {
    ...
  }

  // good
  function Animal() {}
  class People {
    ...
  }
```

### 1.4 使用2个空格soft tabs缩进。
```
  // bad
  function hello (name) {
  ∙∙∙∙console.log('hi', name)
  }
  
  // good
  function hello (name) {
  ∙∙console.log('hi', name)
  }
```

### 1.5 js代码中字符串统一使用单引号。
```
  // bad
  let str = "this is a string";
  
  // good
  let str = 'this is a string';
```

### 1.6 关键字`if`, `else`, `for`, `while`等后保留一个空格。
```
  // bad
  if(condition) { ... } 
  
  // good
  if (condition) { ... } 
```

### 1.7 同一行语句中，结束小括号`)`与起始大括号`{`之间保留一个空格。
```
  // bad
  while (condition){
    ...
  } 
  
  // good
  while (condition) {
    ...
  } 
```

### 1.8 同一行语句中，逗号`,`后保留一个空格。
```
  // bad
  let list = [1,2,3,4];
  function greet (name,options) { ... }
  
  // good
  let list = [1, 2, 3, 4];
  function greet (name, options) { ... }
```

### 1.9 对象字面量仅在冒号`:`后保留一个空格。
```
  // bad
  const obj = {type : 'string', message:'hello'};
  
  // good
  const obj = { type: 'string', message: 'hello' };
```

### 1.10 同一行语句中，运算符`+`, `-`, `*`, `/`, `=`等前后各保留一个空格。 
```
  // bad
  let x=2;
  let message='hello, '+name+'!';
  
  // good
  let x = 2;
  let message = 'hello, ' + name + '!';
```

### 1.11 同一行非空语句中，大括号`{`后和`}`前各保留一个空格。
```
  // bad
  const obj = {type : 'string', message:'hello'};
  function foo() {return 'hi';}
  
  // good
  const obj = { type: 'string', message: 'hello' };
  function foo() { return 'hi'; }
```

### 1.12 `else`语句跟随`if`语句结束大括号`{`并保留一个空格。
```
  // bad
  if (condition)
  {
    // ...
  }
  else
  {
    // ...
  }
  
  // good
  if (condition) {
    // ...
  } else {
    // ...
  }
```

### 1.13 一行语句结束后不允许留白
```
  // bad
  let value = 'hello world';∙∙∙
  if (condition) {∙∙∙
    // ...
  }
  
  // good
  let value = 'hello world';
  if (condition) {
    // ...
  }
```

### 1.14 函数定义中函数名和括号间不留空格，匿名函数保留一个空格。
```
  // bad
  function foo () {}
  const bar = function() {}

  // good
  function foo() {}
  const bar = function () {}
```

### 1.15 函数调用中函数名和括号间不留空格。
```
  // bad
  foo ();
  
  // good
  foo();
```

### 1.16 语句与语句之间不允许出现多个空行。
```
  // bad
  let value = 'hello world';
  
  
  
  console.log(value);
  
  // good
  let value = 'hello world';
  console.log(value);
```
### 1.17 在多行语句中，三元运算符定义在行首。
```
  // bad
  let location = env.development ?
    'localhost':
    'www.api.com'
  
  // good
  let location = env.development
    ? 'localhost'
    : 'www.api.com'
```

### 1.18 在多行语句中，`.`运算符定义在行首。
```
  // bad
  console.
    log('hello');
  
  // good
  console
    .log('hello');
```

### 1.17 判断条件长时单个条件定义一行，条件运算符`||`，`&&`等定义在行尾。 
```
  // bad
  if (
    num > 0
    && num < 100
  ) {
    ...
  }
  
  // good
  if (
    num > 0 &&
    num < 100
  ) {
    ...
  }
```

### 1.18 在多行语句中，逗号`,`定义在行尾。 
```
  // bad
  const obj = {
    type: 'string'
    ,message: 'hello'
  };
  const arr = [
    'a'
    ,'b'
  ];
  
  // good
  const obj = {
    type: 'string',
    message: 'hello'
  };
  const arr = [
    'a',
    'b'
  ];
```

### 1.19 对象字面量最后一个属性末尾不保留逗号`,`。
```
  // bad
  const obj = {
    type: 'string',
    message: 'hello',
  };
  
  // good
  const obj = {
    type: 'string',
    message: 'hello'
  };
```

### 1.20 赋值语句必须以分号`;`结尾。
```
  // bad
  let value = 'hello world'
  const obj = { message: 'hello' }

  // good
  let value = 'hello world';
  const obj = { message: 'hello' };
```

### 1.21 单行注释 `//`双斜线后保留1个空格。
```
  //bad

  // good
```

### 1.22 多行注释使用`/** ... */`。
```
  // bad
  // make() returns a new element
  // based on the passed in tag name
  //
  // @param {String} tag
  // @return {Element} element
  function make(tag) {
      
      // ...stuff...
      
      return element;
  }
  
  // good
  /**
  * make() returns a new element
  * based on the passed in tag name
  *
  * @param {String} tag
  * @return {Element} element
  */
  function make(tag) {
    // ...stuff...
    return element;
  }
```

### 1.23 除语句末尾注释外，其他注释与上一行代码之间保留一行空行。
```
  // bad
  const fn = () => {};
  // 注释
  const foo = () => {};
  
  // good
  const fn = () => {};
  
  // 注释
  const foo = () => {};
```

### 1.24 js文件末尾保留一行空行
```
  // bad
  let value = 'hello world';
  console.log(value);
  
  // good
  let value = 'hello world';
  console.log(value);
  ∙∙∙
```

## 2 js规则

### 2.1 使用关键字`let`, `const` 代替`var`。
```
  // bad
  var value = 'hello world';
  var obj = { message: 'hello' };

  // good
  let value = 'hello world';
  const obj = { message: 'hello' };
```

### 2.2 使用`===`, `!==`代替`==`, `!=`, null和undefined判断除外。
```
  // bad
  if (name == 'John')
  if (name != 'John')
     
  // good
  if (name === 'John')
  if (name !== 'John')
```

### 2.3 使用对象字面量代替`new Object()`。
```
  // bad
  const obj = new Object();

  // good
  const obj = {};
```

### 2.4 使用数组字面量代替`new Array()`。
```
  // bad
  const arr = new Array();

  // good
  const arr = [];
```

### 2.5 确保函数在调用之前已经被声明
```
  // bad
  foo();
  
  function foo() {}
  
  // good
  function foo() {}
  
  foo();
```

### 2.6 禁止在`if`, `while`等代码块中定义函数
```
  // bad
  if (currentUser) {
    function test() {
      console.log('Nope.');
    }
  }
  
  // good
  let test;
  if (currentUser) {
    test = () => {
      console.log('Yup.');
    };
  }
```

### 2.7 仅用于JS钩子的class,或id使用大写`J_`加大驼峰表示
```
  // bad
  #toolbar
  .toolbar-item
  
  // good
  #J_Toolbar
  .J_ToolbarItem  
```
