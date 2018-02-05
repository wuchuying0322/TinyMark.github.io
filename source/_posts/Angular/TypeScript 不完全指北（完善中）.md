---
title: TypeScript 不完全指北
tags: 
- 框架
- Angular
categories: 
- JS框架
- Angular
---

# 什么是 TypeScript
* TypeScript是一种由微软开发的自由和开源的编程语言
* 它是JavaScript的一个超集，可以编译成纯JavaScript
* 而且本质上向这个语言添加了可选的静态类型和基于类的面向对象编程。
* [详见官网](https://www.tslang.cn/)

# 快速上手（新特性）
## 类型注释
* 类型注解 是一种轻量级的为函数或变量添加约束的方式
~~~ts
// 指定了 greeter函数 的参数 person 为 string类型
function greeter(person: string) {
    return "Hello, " + person;
}
var user = "Jane User";
console.log(greeter(user));

// 如果传入一个数组则会报错
var user = [0, 1, 2];
console.log(greeter(user));
// greeter.ts(7,26): error TS2345: Argument of type 'number[]' is not assignable to parameter of type 'string'. 
// 虽然报错，但仍然会完成 JS 编译
~~~

## 接口
* 接口 只在两个类型内部的结构兼容，那么这两个类型就是兼容的（？有点绕？）
~~~ ts
// 1.定义 Person接口
interface Person {
    firstName: string;
    lastName: string;
}

// 2.greeter函数 传入 形参person 指定为 Person接口
function greeter(person: Person) {
    return "Hello, " + person.firstName + " " + person.lastName;
}

// 定义 实参user 对象
var user = { 
    firstName: "Jane", 
    lastName: "User" 
};

// 调用 函数greeter，传入 实参user
console.log(greeter(user));
~~~

## 类
* 类 基于类的面向对象编程（同es6，这个不用解释了）
* 类 和 接口 可以一起共作，程序员可以自行决定抽象的级别
~~~ ts
// 定义 Student类
class Student {
    fullName: string;
    constructor(public firstName, public middleInitial, public lastName) {
        this.fullName = firstName + " " + middleInitial + " " + lastName;
    }
}

// 定义 Person接口
interface Person {
    firstName: string;
    lastName: string;
}

// greeter函数 传入 形参person 指定为 Person接口
function greeter(person : Person) {
    return "Hello, " + person.firstName + " " + person.lastName;
}

// 实例化 实参user对象
var user = new Student("Jane", "M.", "User");

// 调用 函数greeter，传入 实参user
console.log(greeter(user));
~~~

# API
## 基础类型
> 类似JavaScript
* 布尔值（boolean）
    > true / false
    ~~~ ts
    let isDone: boolean = false;
    ~~~
* 浮点数（number）
    ~~~ ts
    // 整型
    let decLiteral: number = 6;
    // 十六进制
    let hexLiteral: number = 0xf00d;
    // 二进制
    let binaryLiteral: number = 0b1010;
    // 八进制    
    let octalLiteral: number = 0o744;
    ~~~
* 字符串（string）
    ~~~ ts
    let name: string = "bob";
    name = "smith";
    ~~~
