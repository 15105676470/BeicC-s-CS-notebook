string的find()函数用于找出字母在字符串中的位置。

find(str,position)

find()的两个参数：

str：是要找的元素

position：字符串中的某个位置，表示从从这个位置开始的字符串中找指定元素。

可以不填第二个参数，默认从字符串的开头进行查找。

返回值为目标字符的位置，当没有找到目标字符时返回npos(-1)。

```c++
//查找s 中flag 出现的所有位置。
    flag="a";
    position=0;
    int i=1;
    while((position=s.find(flag,position))!=string::npos)
    {
        cout<<"position  "<<i<<" : "<<position<<endl;
        position++;
        i++;
    }
```

