---
title: JavaScript设计模式 笔记（一）
tags: 设计模式
categories: 
- FrontEnd
- JavaScript
- 设计模式
---

# 1 灵活的JavaScript
## 1.1 函数
~~~ js
function checkName(){
    // 验证姓名
}
function checkEmail(){
    // 验证邮箱
}
function checkPassword(){
    // 验证密码
}
~~~
> 几个函数而已，但也是全局变量~
> 此处为 【函数声明】 方式声明函数

## 1.2 函数的另一种形式
~~~ js
var checkName = function (){
    // 验证姓名
}
var checkEmail = function (){
    // 验证邮箱
}
var checkPassword =  function (){
    // 验证密码
}
~~~
> 创建了3个全局变量来保存函数，会造成全局污染
> 此处为 【函数表达式（又称字面量）】 方式声明函数

## 1.3 使用对象收编变量
~~~ js
var CheckObject = {
    checkName: function (){
        // 验证姓名
    },
    checkEmail: function (){
        // 验证邮箱
    },
    checkPassword: function (){
        // 验证密码
    }
}
~~~
> 使用 CheckObject.checkName() 点语法来使用方法

## 1.4 对象的另一种形式
~~~ js
var CheckObject = function(){};
CheckObject.checkName = function (){
        // 验证姓名
    }
CheckObject.checkEmail = function (){
        // 验证邮箱
    }
CheckObject.checkPassword = function (){
        // 验证密码
    }
}
~~~
> 函数也是对象，所以可以这样写
> 但是使用 new 关键字创建新对象时，新对象无法继承这些方法

## 1.5 真假对象
~~~ js
var CheckObject = function(){
    return {
        checkName: function (){
            // 验证姓名
        },
        checkEmail: function (){
            // 验证邮箱
        },
        checkPassword: function (){
            // 验证密码
        }
    }
}

// 使用：
var a = CheckObject();
a.checkName();
~~~
> 并不是正真 【类】 的创建
> 创建的新对象a，跟CheckObject对象没有关系

## 1.6 类
~~~ js
var CheckObject = function (){
    this.checkName = function (){
        // 验证姓名        
    }
    this.checkEmail = function (){
        // 验证邮箱
    }
    this.checkPassword = function (){
        // 验证密码
    }
}

// 使用：
var a = new CheckObject();
a.checkName();
~~~
> 使用 关键字new 来创建
> 创建的时候会对类的 this 上的属性进行复制，消耗太大

## 1.7  原型
~~~ js
// 方法1：
var CheckObject = function(){};
ChecekObject.prototype.checkName = function(){
    // 验证姓名            
}
ChecekObject.prototype.checkEmail = function(){
    // 验证邮箱            
}
ChecekObject.prototype.checkPassword = function(){
    // 验证密码            
}

// 方法2：
var CheckObject = function(){};
ChecekObject.prototype = {
    checkName: function(){
        // 验证姓名            
    },
    checkEmail: function(){
        // 验证邮箱            
    },
    checkPassword: function(){
        // 验证密码            
    }
}

// 使用：
var a = new CheckObject();
a.checkName();
a.checkEmail();
a.checkPassword();
~~~
> 两种方法不能混用

## 1.8 链式编程
~~~ js
var CheckObject = function(){};
ChecekObject.prototype = {
    checkName: function(){
        // 验证姓名    
        return this;
    },
    checkEmail: function(){
        // 验证邮箱      
        return this;
    },
    checkPassword: function(){
        // 验证密码            
        return this;    
    }
}

// 使用：
var a = new CheckObject();
a.checkName().checkEmail().checkPassword();
~~~
> 在方法最后使用 return this 来实现链式编程

## 1.9 原生Function
~~~ js
// 为了不污染原生Function，抽象出一个统一 添加方法 的方法
Function.prototype.addMethod = function (name,fn) {
    this[name] = fn;
}

var methods = new Function();
// 或者 var methods = function (){};
methods.addMethod("checkName",function(){
    // 验证姓名
});
methods.addMethod("checkEmail",function(){
    // 验证邮箱
});
methods.addMethod("checkPassword",function(){
    // 验证密码
});

// 使用：
methods.checkName();
methods.checkEmail();
methods.checkPassword();
~~~
> 1.给Function.prototype增加一个【添加方法】的方法
> 2.每次创建函数对象的时候会继承这个方法，就可以给新对象增加方法

## 1.10 实现链式添加与链式调用
~~~ js
Function.prototype.addMethod = function (name,fn) {
    this[name] = fn;
    return this; // 链式添加方法
}

var methods = new Function();
// 或者 var methods = function (){};
methods.addMethod("checkName",function(){
    // 验证姓名
    return this; // 链式调用方法
}).addMethod("checkEmail",function(){
    // 验证邮箱
    return this; // 链式调用方法    
}).addMethod("checkPassword",function(){
    // 验证密码
    return this; // 链式调用方法   
});

// 使用：
methods.checkName().checkEmail().checkPassword();
~~~
> 在prototype的addMethod方法中使用return this来实现方法的链式添加
> 在方法最后使用return this来实现链式调用 

## 1.11 添加到prototype中
~~~ js
// 给【原生Function.prototype】增加【添加原型方法】的方法
Function.prototype.addMethod = function (name,fn) {
    this.prototype[name] = fn;
    return this; // 链式添加方法
}

// 构造函数
function Methods(){};
// 使用Function中的addMethod方法来给构造函数Methods的原型对象添加方法
Methods.addMethod("checkName",function(){
    // 验证姓名
    return this; // 链式调用方法
}).addMethod("checkEmail",function(){
    // 验证邮箱
    return this; // 链式调用方法   
}).addMethod("checkPassword",function(){
    // 验证密码
    return this; // 链式调用方法    
});

// 需要通过【new关键字】来使用：
var m = new Methods();
m.checkName().checkEmail().checkPassword();
~~~
> 借助Function.prototype.addMethod来给所有构造函数添加公共方法
> 当创建一个构造函数的时候，该构造函数就可以使用addMethod方法来给自己的原型对象添加方法（使用return this实现链式添加）
> 使用【new关键字】实例化出一个新对象时，该对象就会继承我们给构造函数Methods的原型对象添加的方法了