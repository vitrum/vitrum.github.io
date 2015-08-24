title: Javascript Bitwise Operation
date: 2015-08-10 17:50:17
tags: Bitwise Operation, 位运算
---

话说有个编程题目，有两个整数a和b, 求他们的和, 但不能使用 + 等数学运算符。

这是[leetcode](https://oj.leetcode.com/problems/add-two-numbers/)上的题目，需要用[位运算](https://en.wikipedia.org/wiki/Bitwise_operation)处理。

![Rotate left logically](https://upload.wikimedia.org/wikipedia/commons/5/5c/Rotate_left_logically.svg)

例如：

    int Add(int a, int b)
    {
        return b ? Add(a^b, (a&b)<<1) : a;
    }


其实在Javascript中也有位运算，只是平时很少用到。例如下面这段摘抄的代码，可以猜猜生成什么：

    var a = "10"| 0 ;
    console.log("Bitwise Or a is : " +a);
    var b = "s1132"|0;
    console.log("Bitwise Or b is : " +b);
    var c = [1,3,2]&1 ;
    console.log("Bitwise And c is : " +c);
    var d = [1]|0;
    console.log("Bitwise Or d is : " +d);
    var e = ~function(){}();
    console.log("Bitwise Not e is : " +e);
    var f = ({})|0;
    console.log("Bitwise Or f is : " +f);
    var g = ([1])|0;
    console.log("Bitwise Or g is : " +g);
    var h = "1ss"^0;
    console.log("Bitwise Exclusive Or h is : " +h);
    
    

##javascript中的位运算

　　javascript中的位运算非常复杂，由于javascript试图创建完全无类型（弱类型）的数据，因此数字以64位浮点值存储，即双精度的浮点数。

　　正如大家所料，javascript中没有你想使用的Integer(整型)类型。当我们需要用到integer类型时，javascript会内部执行 Toint32方法(浏览器内部函数，外部不可调用)将值直接转化为32位的integer以供调用，并将原值瞬间转换回双精度浮点型。

　　javascript与其他语言的不同之一就是它奇怪的位运算。


##细节请参考

[Bitwise operators @ mozilla](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Bitwise_Operators)

[javascript位运算](http://www.cnblogs.com/wisdomoon/p/3338327.html)

[javascript位运算符](http://www.cnblogs.com/fengjun/archive/2012/01/16/2323413.html)

[知乎上关于javascript位运算性能的讨论](http://www.zhihu.com/question/20546013)


##位运算的应用


[位运算详解(介绍及用途)](http://www.doc88.com/p-998235083491.html)

[“位运算”在程序开发中的妙用！](http://androiddeveloper.diandian.com/post/2012-06-07/40027080498)