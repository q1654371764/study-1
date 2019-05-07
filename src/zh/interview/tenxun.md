---
sidebar: auto
sidebarDepth: 2
---

# 腾讯面试题

## 第一题
#### 1. 难度系数: ★★★
#### 2. 相关技术点:
    1). 作用域与作用域链
    2). 变量查找

## 测试
    var x = 10
    function fn() {
      console.log(x)
    }
    function show(fns) {
      var x = 20
      fns()
    }
    show(fn); // 执行结果为？


## 第二题

#### 1. 难度系数: ★★★
#### 2. 技术点:
    1). 变量提升
    2). IIFE
    3). 作用域与作用域链
    4). 变量查找

## 测试
    var name = 'World!';
    (function () {
        /*
        var name
        .....
        */
        if (typeof name === 'undefined') {
            var name = 'Jack'
            console.log(name)
        } else {
            console.log(name)
        }
    })()

## 第三题

#### 1. 难度系数: ★★★
#### 2. 技术点:
    1). DOM事件处理
    2). 闭包
#### 3. 需求: 点击某个按钮, 提示"第n个
#### 4. 问题: 下面的实现代码是否正确, 如果不正确, 请正确实现
    /*var btns = document.getElementsByTagName('button')
    for(var i=0,length=btns.length;i<length;i++) { // i是一个全局变量, 遍历后是3
      var btn = btns[i]
      btn.onclick = function () {
        alert('第'+(i+1)+'个')
      }
    }*/
## 测试
    var btns = document.getElementsByTagName('button')
    for(var i=0,length=btns.length;i<length;i++) { // i是一个全局变量, 遍历后是3
        (function (i) {
        var btn = btns[i]
        btn.onclick = function () {
            alert('第'+(i+1)+'个')
        }
        })(i) // 使用了闭包--->内存中产生了1+3个i
    }


    function fn1() {
        var a = 2
        function fn2 () {
        a++
        console.log(a)
        }
        return fn2
    }
    var f = fn1()
    f()
    f()