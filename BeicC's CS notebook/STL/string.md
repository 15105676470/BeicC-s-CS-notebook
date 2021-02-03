1：string比大小：

string a = “123”；string b = “234”；<u>是自动的！</u>==c++中比较两个string的大小是每个字符比较ascall码，知道出现不同的字符为止；==

2： 如何用printf来输出string？

我们都知道，string是一个封装好的类，并不属于内部结构，所以肯定不能直接用printf来输出string，但我们可以用printf("% s ", string . c_str())来输出。// c_str()接口是string类的一个函数,返回的是字符串的首地址,返回值类型是const char *的