定义在<algorithm>中，用来排序

主要是sort中自己要写的cmp函数

```c++
#include<algorithm> 
using namespace std;

sort(num, num + n, cmp);

```

如果cmp返回结果为假, 那么函数就会将他们互换位置；

如果cmp返回结果为真，就会保持原来位置不变。

sort的cmp还能这样用?

其实手写的cmp是sort的一个排序规则，可以按照你自己想法让数组进行排序

详情：https://leetcode-cn.com/problems/rank-teams-by-votes/