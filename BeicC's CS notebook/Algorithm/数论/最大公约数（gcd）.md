（附带一提：最大公约数与最小公倍数的关系：最大公约数与最小公倍数的乘积就是这两个数的乘积） 

求a和b的最大公约数（Greatest Common Divisor）：方法辗转相除法（欧几里得算法）



![](D:\软件\Typora\notebook\Imagine\数论\最大公约数.png)

```c++
//超级简洁的板子，x和y的大小无所谓，就算是x比较小，那么下一次x和y也会换位。
inline int gcd(int x, int y) {
    return y ? gcd(y, x%y) : x;
}
```

STL里面有一个函数求最大公约数__gcd（int a，int b）；定义在<algorithm>中；