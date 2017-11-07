# JavaScript Style Guide

## 文档目录

1. [对象](#1-对象)
2. [数组](#2-数组)
3. [字符串](#3-字符串)
4. [方法](#4-方法)
5. [变量](#5-变量)
6. [比较运算符](#6-比较运算符)
7. [代码块](#7-代码块)
8. [注释](#8-注释)
9. [留白](#9-留白)
10. [逗号](#10-逗号)
11. [分号](#11-分号)
12. [类型转换](#12-类型转换)
13. [命名规则](#13-命名规则)
14. [构造函数](#14-构造函数)
15. [事件](#15-事件)
16. [模块](#16-模块)
17. [jQuery](#17-jQuery)
18. [ES6相关内容参考airbnb](https://github.com/airbnb/javascript)




## 1 对象

### 1.1 使用字面量创建对象

```
    // bad
    var obj = new Object();
    obj.title = 'hello word';
    obj.author = 'zhangsan';
    
    // good
    var obj = {
        title: 'hello word',
        author: 'zhangsan'
    };
```

### 1.2 使用`.`操作符访问对象属性

```
    var luke = {
        jedi: true,
        age: 28
    };
    
    // bad
    var isJedi = luke['jedi'];
    
    // good
    var isJedi = luke.jedi;
```

### 1.3 使用`[]`操作符访问属性名为变量的对象属性

```
    var luke = {
        jedi: true,
        age: 28
    };
    
    function getProp(prop) {
        return luke[prop];
    }
    
    var isJedi = getProp('jedi');
```


## 2 数组

### 2.1 使用字面量创建数组

```
    // bad
    var arr = new Array('a', 'b', 'c');
    
    // good
    var arr = [ 'a', 'b', 'c' ];
```

### 2.2 添加数组元素时使用Array的push实例方法代替直接赋值

```
    var someStack = [];
    
    // bad
    someStack[someStack.length] = 'abracadabra';
    
    // good
    someStack.push('abracadabra');
```

### 2.3 使用Array的slice实例方法复制数组

```
    var len = items.length;
    var itemsCopy = [];
    var i;
    
    // bad
    for (i = 0; i < len; i++) {
        itemsCopy[i] = items[i];
    }
    
    // good
    itemsCopy = items.slice();
```

### 2.4 使用Array的slice实例方法将类数组转换为真是数组

```
    function trigger() {
        var args = Array.prototype.slice.call(arguments);
        ...
    }
```


## 3 字符串

### 3.1 使用单引号`''`创建字符串

```
    // bad
    var str = "bad case";
    
    // good
    var str = 'good case';
    
    // bad
    var str = "bad" + this.otherStr;
    
    // good
    var str = 'good' + this.otherStr;
```

### 3.2 字符串单行不应超过80字符

```
    // bad
    var errorMessage = 'This is a super long error that was thrown because of Batman. When you stop to think about how Batman had anything to do with this, you would get nowhere fast.';
    
    // bad
    var errorMessage = 'This is a super long error that was thrown because \
    of Batman. When you stop to think about how Batman had anything to do \
    with this, you would get nowhere \
    fast.';
    
    // good
    var errorMessage = 'This is a super long error that was thrown because ' +
        'of Batman. When you stop to think about how Batman had anything to do ' +
        'with this, you would get nowhere fast.';
```


## 4. 方法

### 4.1 方法声明方式

```
    // normal function
    function foo() {
        ...
    }
    
   // anonymous function expression
   var anonymous = function () {
        return true;
   };
   
   // immediately-invoked function expression (IIFE)
   (function () {
     console.log('Welcome to the Internet. Please follow me.');
   }());
```

### 4.2 不要在非函数代码块中声明方法如`if`, `for`等

```
    //bad
    if (currentUser) {
        function test() {
            console.log('Nope.');
        }
    }
    
    // good
    var test;
    if (currentUser) {
        test = function test() {
            console.log('Yup.');
        };
    }
```

### 4.3 不要使用保留字`arugments`作为方法的参数

```
    // bad
    function nope(name, options, arguments) {
        ...
    }

    // good
    function yup(name, options, args) {
        ...
    }
```


## 5 变量

### 5.1 使用变量前确保使用`var`关键字声明该变量

```
   // bad
   superPower = new SuperPower();
   
   // good
   var superPower = new SuperPower(); 
```

### 5.2 声明多个变量时使用`var`关键字为每一个变量单独声明

```
    // bad
    var items = getItems(),
        goSportsTeam = true,
        dragonball = 'z';
    
    // bad
    // (compare to above, and try to spot the mistake)
    var items = getItems(),
        goSportsTeam = true;
        dragonball = 'z';
    
    // good
    var items = getItems();
    var goSportsTeam = true;
    var dragonball = 'z';
```

### 5.3 声明变量时将暂未赋值变量声明在已赋值变量后

```
    // bad
    var i, len, dragonball,
        items = getItems(),
        goSportsTeam = true;
    
    // bad
    var i;
    var items = getItems();
    var dragonball;
    var goSportsTeam = true;
    var len;
    
    // good
    var items = getItems();
    var goSportsTeam = true;
    var dragonball;
    var length;
    var i;
```


## 6 比较运算符

### 6.1 使用`===` 和 `!==`代替`==` 和 `!=`


## 7 代码块

### 7.1 多行代码块使用`{}`包裹

```
    // bad
    if (test)
        return false;
    
    // good
    if (test) return false;
    
    // good
    if (test) {
        return false;
    }
    
    // bad
    function () { return false; }
    
    // good
    function () {
        return false;
    }
```

### 7.2 `if` `else`语句`else`跟随`if`结束大括号并保留1个空格

```
    // bad
    if (test) {
        thing1();
        thing2();
    }
    else {
        thing3();
    }
    
    // good
    if (test) {
        thing1();
        thing2();
    } else {
        thing3();
    }
```


## 8 注释

### 8.1 多行注释（`/** ... */`）并注明传递参数和返回值等，参考:@jsdoc

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

### 8.2 单行注释 (`//`)双斜线后保留1个空格

```
    // bad
    var active = true;  // is current tab
    
    // good
    // is current tab
    var active = true;
    
    // bad
    function getType() {
        console.log('fetching type...');
        // set the default type to 'no type'
        var type = this.type || 'no type';
        
        return type;
    }
    
    // good
    function getType() {
        console.log('fetching type...');
        
        // set the default type to 'no type'
        var type = this.type || 'no type';
        
        return type;
    }
```


## 9 留白

### 9.1 缩进使用4个空格

```
    // bad
    function () {
    ∙∙var name;
    }
    
    // bad
    function () {
    ∙var name;
    }
    
    // good
    function () {
    ∙∙∙∙var name;
    }
```

### 9.2 起始`{`大括号前保留1个空格

```
    // bad
    function test(){
        console.log('test');
    }
    
    // good
    function test() {
        console.log('test');
    }
    
    // bad
    dog.set('attr',{
        age: '1 year',
        breed: 'Bernese Mountain Dog'
    });
    
    // good
    dog.set('attr', {
        age: '1 year',
        breed: 'Bernese Mountain Dog'
    });
```

### 9.3 `if` 和 `for` 等语句的小括号前保留1个空格
```
    // bad
    if(isJedi) {
        fight ();
    }
    
    // good
    if (isJedi) {
        fight();
    }
    
    // bad
    function fight () {
        console.log ('Swooosh!');
    }
    
    // good
    function fight() {
        console.log('Swooosh!');
    }
```

### 9.4 运算符（`+`, `-`, `*`, `/`, `=`）等前后各保留1个空格

```
    // bad
    var x=5+y;
    
    // good
    var x = 5 + y;
```

### 9.5 文件底部保留1行空行

```
    // bad
    (function (global) {
        // ...stuff...
    })(this);
```
```
    // bad
    (function (global) {
        // ...stuff...
    })(this);↵
    ↵
```
```
    // good
    (function (global) {
        // ...stuff...
    })(this);↵
```

### 9.6 方法,逻辑块之间保留1行空行

```
    // bad
    if (foo) {
        return bar;
    }
    return baz;
    
    // good
    if (foo) {
        return bar;
    }
    
    return baz;
    
    // bad
    var obj = {
        foo: function () {
        },
        bar: function () {
        }
    };
    return obj;
    
    // good
    var obj = {
        foo: function () {
        },
        
        bar: function () {
        }
    };
    
    return obj;
```

### 9.7 注释前面保留1行空行

```
    // annotation
    function foo() {
        ...
    }
    
    // ...
    function poop() {
        ...
    }
```

## 10 逗号

### 10.1 逗号跟在每行的末尾

```
    // bad
    var story = [
          once
        , upon
        , aTime
    ];
    
    // good
    var story = [
        once,
        upon,
        aTime
    ];
    
    // bad
    var hero = {
          firstName: 'Bob'
        , lastName: 'Parr'
        , heroName: 'Mr. Incredible'
        , superPower: 'strength'
    };
    
    // good
    var hero = {
        firstName: 'Bob',
        lastName: 'Parr',
        heroName: 'Mr. Incredible',
        superPower: 'strength'
    };
```


## 11 分号

```
    // bad
    (function () {
        var name = 'Skywalker'
        return name
    })()
    
    // good
    (function () {
        var name = 'Skywalker';
        return name;
    })();
    
    // good (guards against the function becoming an argument when two files with IIFEs are concatenated)
    ;(function () {
        var name = 'Skywalker';
        return name;
    })();
```


## 12 类型转换

### 12.1 字符串

```
    //  => this.reviewScore = 9;
    
    // bad
    var totalScore = this.reviewScore + '';
    
    // good
    var totalScore = '' + this.reviewScore;
    
    // bad
    var totalScore = '' + this.reviewScore + ' total score';
    
    // good
    var totalScore = this.reviewScore + ' total score';
```

### 12.2 数字

```
   var inputValue = '4';
   
   // bad
   var val = new Number(inputValue);
   
   // bad
   var val = +inputValue;
   
   // bad
   var val = inputValue >> 0;
   
   // bad
   var val = parseInt(inputValue);
   
   // good
   var val = Number(inputValue);
   
   // good
   var val = parseInt(inputValue, 10);
```

### 12.3 布尔型

```
    var age = 0;
    
    // bad
    var hasAge = new Boolean(age);
    
    // good
    var hasAge = Boolean(age);
    
    // good
    var hasAge = !!age;
```


## 13 命名规则

### 13.1 使用有意义的描述命名

```
// bad
function q() {
    // ...stuff...
}

// good
function query() {
    // ..stuff..
}
```

### 13.2 使用小骆驼拼写法命名变量名，方法名，实例名和对象名

```
    // bad
    var OBJEcttsssss = {};
    var this_is_my_object = {};
    var o = {};
    function c() {}
    
    // good
    var thisIsMyObject = {};
    function thisIsMyFunction() {}
```

### 13.3 使用大骆驼拼写法命名构造函数名

```
    // bad
    function user(options) {
        this.name = options.name;
    }
    
    var bad = new user({
        name: 'nope'
    });
    
    // good
    function User(options) {
        this.name = options.name;
    }
    
    var good = new User({
        name: 'yup'
    });
```

### 13.4 用大写字母命名常量，如多个单词用`_`连接

```
    // bad
    var className = 'className';
    
    // good
    var CLASS_NAME = 'className';
```

### 13.5 特殊情况

* 使用到URL的地方一定全大写, 比如说 baseURL
* 涉及Android的，一律大写第一个字母
* 涉及iOS的，一律小写第一个，大写后两个字母


## 14 构造函数

### 14.1 添加方法到原型对象上，而不是覆盖原型对象

```
function Jedi() {
    console.log('new jedi');
}

// bad
Jedi.prototype = {
    fight: function fight() {
        console.log('fighting');
    },
    
    block: function block() {
        console.log('blocking');
    }
};

// good
Jedi.prototype.fight = function fight() {
    console.log('fighting');
};

Jedi.prototype.block = function block() {
    console.log('blocking');
};
```


## 15 事件

### 参数在事件中传递使用hash代替原始参数

```
// bad
$(this).trigger('listingUpdated', listing.id);

...

$(this).on('listingUpdated', function (e, listingId) {
    // do something with listingId
});

```

```
// good
$(this).trigger('listingUpdated', { listingId : listing.id });

...

$(this).on('listingUpdated', function (e, data) {
    // do something with data.listingId
});
```


## 16 模块

```
function (global) {
    'use strict';

    var previousFancyInput = global.FancyInput;
    
    function FancyInput(options) {
        this.options = options || {};
    }
    
    FancyInput.noConflict = function noConflict() {
        global.FancyInput = previousFancyInput;
        return FancyInput;
    };
    
    global.FancyInput = FancyInput;
}(this);
```


## 17 jQuery

### 17.1 jQuery对象变量以`$`开头

```
    // bad
    var sidebar = $('.sidebar');
    
    // good
    var $sidebar = $('.sidebar');
```

### 17.2 缓存jQuery查询结果

```
    // bad
    function setSidebar() {
        $('.sidebar').hide();
        
        // ...stuff...
        
        $('.sidebar').css({
            'background-color': 'pink'
        });
    }
    
    // good
    function setSidebar() {
        var $sidebar = $('.sidebar');
        $sidebar.hide();
        
        // ...stuff...
        
        $sidebar.css({
            'background-color': 'pink'
        });
    }
```

### 17.3 使用`$('.sidebar ul')`或`$('.sidebar > ul')`进行dom查询

### 17.4 使用`find`语句对缓存后的jQuery对象进行查询

```
    // bad
    $('ul', '.sidebar').hide();
    
    // bad
    $('.sidebar').find('ul').hide();
    
    // good
    $('.sidebar ul').hide();
    
    // good
    $('.sidebar > ul').hide();
    
    // good
    $sidebar.find('ul').hide();
```
