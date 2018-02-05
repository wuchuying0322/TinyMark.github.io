---
title: JS的继承方式
tags: JS
categories: 
- FrontEnd
- JavaScript
---

# 继承的三种方式：
~~~
1.混入继承:遍历对象，将对象中定义的成员对应的新增到目标对象中
2.原型继承：替换原型，实现继承，将你想继承的对象赋值给当前构造函数的原型
3.混合式继承：利用混入式的方式为原型添加属性和方法
    
* 经典继承：使用ES5中内置的Object.create()方法
~~~

<!-- more --> 

## 1. 混入式继承:
~~~js
var me = {
    work: function () {
        console.log('打工');
    }
};
var mayun = {
    money: 9999999999,
    car: 'QQ',
    manager: function () {
        console.log('管理阿里巴巴。');
    }
}
// 使用混入继承
for (var key in mayun) {
    me[key] = mayun[key];
}
console.log(me);
~~~
## 2. 原型式继承
~~~js
function Person() {
    this.name = '人类';
    this.age = '20';
    this.sayHi = function () {
        console.log('向你问好');
    }
}
function Student() { };

// 使用原型继承
Student.prototype = new Person();

// 实例化
var stu = new Student();

console.log(stu);
~~~
 ## 3. 混合式继承
~~~js
function Student(name, age) {
    this.name = name;
    this.age = age;
}

// 预设的原型对象
var Painter = {
    draw: function () {
        console.log(this.name + ':我在画画');
    }
}

// 利用混入的方式，给原型对象添加属性和方法
Student.prototype.extend = function (obj) {
    for (var key in obj) {
    this[key] = obj[key];
    }
}

// 调用 原型方法 扩展
Student.prototype.extend(Painter);

// 实例化
var s1 = new Student('lilei', 20);

console.log(s1);
~~~
## * 经典继承：Object.create(obj1)
~~~js  
var obj1 = {
    name: 'lilei',
    age: 20,
    sayHello: function () {
        console.log('我是' + this.name + ',今年' + this.age);
    }
};
~~~
### ES5中内置的Object.create()方法可以让我们快速的继承
~~~js
var obj = Object.create(obj1);
obj.sayHello();
~~~
### 兼容低版本，运用了原型式继承
~~~js
function Object_Create(obj1) {
    if (Object.create) {
        return Object.create(obj1);
    } else {
        function F() { }
        F.prototype = obj1;
        return new F();
    }
}
~~~