---
sidebar: auto
sidebarDepth: 2
---

# 百度面试题

## 第一题
#### 1. 难度系数: ★★★★
#### 2. 相关技术点:
 1. 引用变量赋值
 2. 内存分析
 3. 函数调用传参
 4. 运算符的优先级

## 预热一
    var obj = {n: 1};
    var obj2 = obj;
    obj2.n = 2;
    console.log(obj.n) // ?

## 预热二
    function fn1(a) {
        a.n = 3;
    };
    fn1(obj);
    //console.log(obj.n); // ?

## 预热三
    function fn2(a) {
        a = {n:4};
    };
    fn2(obj);
    console.log(obj.n); // ?

## 预热四
    var a = {n: 1};
    var b = a;
    a.x = a = {n: 2};
    console.log(a.n, b.n); // ? ?
    console.log(a.x, b.x); // ? ?

## 第二题

#### 1. 难度系数: ★★★
#### 2. 技术点:
    1).原型与原型链
    2).对象属性查找

## 测试
    function A () {       
    }
    A.prototype.n = 1
    var b = new A()
    A.prototype = {
      n: 2,
      m: 3
    }
    var c = new A()
    console.log(b.n, b.m, c.n, c.m) // ? ? ? ?