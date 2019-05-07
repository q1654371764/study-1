---
sidebar: auto
sidebarDepth: 2
---

# 阿里面试题

## 第一题
#### 1. 难度系数: ★★★
#### 2. 相关技术点:
    1). 变量提升
    2). 函数提升
    3). 预处理

## 预热一
    var a = 2
    function fn() { // 预计处理:
      /*
       var a;
       console.log(a)
       a = 3
      */
      console.log(a)
      var a = 3
    }
    fn() // ?
    function fn2() { // 预计处理:
      console.log(a)
      a = 3  // a是全局变量
    }
    fn2() // ?

## 预热二 预计先处理的是变量还是函数?
    function b() {
    }
    var b
    console.log(typeof b) // ?
## 预热三 
    /*
    var c
    function c(c) {
        console.log(c)
        var c = 3
    }
    c = 1
    console.log(c) // 1
    c(2) //报错
    */


    var c = 1
    function c(c) {
        console.log(c)
        var c = 3
    }
    console.log(c) // ? 1
    c(2) // ?
#### 1. 收集用var声明变量 2. 收集用function声明函数 函数与变量区别: 名=函数  名=非函数

## 第二题

#### 1. 难度系数: ★★★
#### 2. 技术点:
    1). 定时器
    2). 意外全局变量
    3). 作用域与作用域链
    4). 变量查找

## 测试
    var a = 6
    setTimeout(function () {
        console.log(0)
        alert(a)
        a = 666
    }, 0)
    console.log(1)
    a = 66
####  先执行1 还是先执行0 

## 第三题

#### 1. 难度系数: ★★★
#### 2. 技术点:
    1). this
    2). 闭包

## 测试
    var name = "A"
    var object = {
      name: "B",
      getNameFunc: function () {
        return function () {
          return this.name  // this是谁?  window
        }
      }
    }
    console.log(object.getNameFunc()())  // ?  


    var name2 = "A"
    var object2 = {
      name2: "B",
      getNameFunc: function () {
        var that = this  // 缓存this ? object2
        return function () {
          return that.name2
        }
      }
    }
    console.log(object2.getNameFunc()()) // ?   

## 第四题

#### 1. 难度系数: ★★★★
#### 2. 技术点:
    1). 变量提升
    2). this
    3). 运算符优先级
    4). 原型与原型链
    5). 全局变量污染

## 测试
    function Person() {
        getAge = function () {
            console.log(10)
        }
        return this
    }

    Person.getAge = function () {
        console.log(20)
    }

    Person.prototype.getAge = function () {
        console.log(30)
    }   

    var getAge = function () {
        console.log(40)
    }

    function getAge() {
        console.log(50)
    }
    Person.getAge() // ?
    getAge() // ?
    Person().getAge() // ?
    getAge() // ?
    new Person.getAge() // ?
    new Person().getAge() // ?
