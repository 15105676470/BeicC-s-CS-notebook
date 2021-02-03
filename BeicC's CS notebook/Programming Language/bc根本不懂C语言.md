1：getchar（）：[奇葩的输入](http://poj.org/problem?id=2503)   [参考的题解](https://www.cnblogs.com/lyy289065406/archive/2011/07/30/2122250.html) （我竟然不会看他的题解而是看怎么输入的💀）

getchar这个东西是会吃回车的，如果前面用了scanf或者cin来输入，后面又用了getchar来输入单个字符，这个时候就要在两个输入之间加个getchar了，因为getchar会把上次输入后的回车键当作字符，并且储存的是' \n '.

2：^ 操作 [题目来源](https://leetcode-cn.com/problems/stone-game-iii/)

```c++
　//　异或运算的作用
　//　**参与运算的两个值，如果两个相应bit位相同，则结果为0，否则为1。
　　即：
　　0^0 = 0，
　　1^0 = 1，
　　0^1 = 1，
　　1^1 = 0
```

3：[题目](https://www.luogu.com.cn/problem/P4310)   &（按位与）的优先级 是低于 == 或 ！= 的，如果在if语句里写&记得加括号

4：int的范围是[-2^31^,2^31^-1] ,约21亿，而float和double的范围就要大的多的多，float的范围为-2^128^ ~ +2^128^，也即-3.40E+38 ~ +3.40E+38；double的范围为-2^1024^ ~ +2^1024^，也即-1.79E+308 ~ +1.79E+308。

## 指针问题

```c

void GetMemory(char *p)
{
   p = (char *)malloc(100);
}
void Test(void)
{
    char *str = NULL; //申明字符串指针str并让它指向空地址
    GetMemory(str);
    strcpy(str, "hello world");
    printf(str);
}
```

 GetMemory(str)中*p接收到的是str的一个备份，并不能去改变str里面的内容，如果想要改变str里的内容，要不用return，要不用二级指针https://www.cnblogs.com/ymonke/p/3184906.html	

## char数组的输入

scanf 对字符类型有 %c 和 %s 两种格式(printf 同理，下同)，其中 %c 用来输入单个字符，%s 用来输入一个字符串并存在字符数组里。%c 格式能识别 **空格** 跟 **换行** 并将其输入，而 %s 通过 **空格** 或 **换行** 来识别一个字符串的结束

printf输出long long 的时候要用"lld" ！！