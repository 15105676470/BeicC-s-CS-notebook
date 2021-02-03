## Date structure

tuple（元组）: 这个就是一个静态的list，允许访问，不允许修改，优点是访问的时候比list快，所以有一块区间只需要来回访问的时候，最好用tuple来储存。**用圆括号来声明，当只有一个元素的时候，最后要加一个**tuple进行比较的时候，与C中的string比较方法一样，从左往右逐渐比较

range：生成一个序列 range(i) : 0~i-1 , range(i, j) :i ~ j-1, range(i, j, k):从i到j-1 每次增加k步

dict（字典）：就相当于c中的map

heapq（小根堆）:python中的heapq是实打实的小根堆，与C中的priority_queue相反（大根堆），用的时候需要import heapq.常用方法：heapq.heapify(list) 把一个list转化成一个小根堆.heapq.heappushpop(list,val)把最小的弹出，并插入val

## Some function

sort：python中内置的sort函数只适用于list，用list.sort即可调用，将list变成有序列表

sorted：如果其他的数据类型想要排序就要用sorted函数，与sort函数不同的是，sort不返回，而sorted函数返回一个有序答案

enumerate：enumerate(list) 从list中逐个取（idx, val）

ord(c)：将字符c转化为对应的ascll码

## 杂七杂八

from ... import 与 import的区别:from a import b 是从a这整个类里面取出来b这个函数，而import a，就是把整个类a给导入进来              参考：https://www.zhihu.com/question/38857862