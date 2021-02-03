1. 如果定义个longlong变量，而你是用int变量给他赋值的，那前面一定要记得乘个1LL，否则就会WA

```c++
	LL r = 1LL*(b-a-1)*(a-1);//这个1LL非常必要！！
```

2.从[这道题](https://www.luogu.com.cn/problem/P5788)中实打实得感受到了scanf printf  真的要比cin cout 要快 ，手写数组模拟数据结构真的要比STL运算的快，而且快的还不少    //当题目输入数据接近1e6得时候，输入一定要用scanf而不能用cin，不然必TLE

3.LL 和 int  是不能直接比较的，最起码在codeforces的判断系统中是不能直接比较的

4.一般来说%一般是在int范围内进行的，但如果

```c++
int ans = A % MOD //如果A的范围已经超过了int，这样写会出错，需要写成
int ans = A*1LL%MOD //先把A转换成LL，在进行取模运算
```

==5.当数据量比较大的时候还是老老实实用scanf和printf吧，什么算大呢，超过五个零就别用cin和cout了==

6.手写if比较函数比直接调用min，max函数要来的快

7.注意！！

```c++
for(auto &v : V) ....  //这个&一定要带，不要问为什么
    //https://www.bilibili.com/video/BV1Ma4y1a7fv
```

