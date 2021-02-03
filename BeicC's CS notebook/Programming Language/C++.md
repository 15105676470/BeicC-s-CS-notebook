## this指针

http://c.biancheng.net/view/170.html（好好看，好好学）

## 取模运算

c++中的% 和java中的% 一样，都是使得商尽可能大，所以-3 % 2 == -1 

参考博客：https://blog.csdn.net/wj1066/article/details/82632294

## const

参考博客：https://www.cnblogs.com/qingergege/p/7609533.html

<类型标志符>函数名（参数表）const ：函数参数表屁股后面带不带const是两个函数，一个最明显的例子

```c++
//结构体中的运算符重载函数
struct Node{
    int x,y,z;
    Node(int _x,int _y,int _z) : x(_x), y(_y), z(_z) {};
    bool operator < (const Node& that)const{
        return z > that.z;
    }
};
//如果屁股后面不带const，把Node放进priority_queue中就会报错
	//但是不带const，放进sort里面就不会报错....
```

const的作用：

1.修饰类的成员函数时，表示其为一个常函数，意味着成员函数将不能修改类成员变量的值。

在函数中形参用const int&，这样速度快

参考博客：https://www.cnblogs.com/oaoa/p/11115460.html

## lambda表达式

c++11新特性，就是一个匿名函数

参考博客：https://www.jianshu.com/p/96e9dba6e7a9

## 运算符重载

运算符重载其实就相当于一个重载函数

<返回值类型> operator <重载符号> （参数列表）{ 函数体 }

bool operator < (const Node& a)const{val > a.val;}

函数中的两个const意义：第一个const修饰的是变量a，表示这个函数既可以接收const变量，也可以接收非const变量； 第二个const修饰的是函数本身，表示在函数体里面进行的操作不会影响到类中的成员变量

参考博客：https://blog.csdn.net/qq_36770641/article/details/89884807

## template

用<template typename T>来声明

假如有个函数，其参数我不仅想传入小根堆，也想传入大根堆。如果按常规思路想就要写两个函数，但是引入tamplate后就可以完美的解决这个问题

```c++
 template<typename T>
void solve(T& heap){
     //do something
}
```

## public、private

当一个类中的成员变量用private修饰时，在主函数中你就不能通过 对象. 的方式来访问类的成员变量，想要修改或访问成员变量，就只能通过public的类方法来实现