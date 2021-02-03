题目链接：https://www.luogu.com.cn/problem/P1074；

通过这一题我明白了一下几点：

1：如果把dfs看作从土里向上生长的一棵树的话，那么他的根越细，这样越快；反之，根越粗，这个程序跑的越慢；（很好理解，下面越细越好，因为下面细那上面就要粗一点，但上面粗一点没有任何关系，因为走两步这个程序就到头了）。

2：一个函数（除主函数外），他的计算越简单总程序跑的越快，枚举比计算要快（即使这个计算非常简单！！！）。	

例如：

```c++
int getlittle(int i,int j){
		int p,q;
		if(i % 3 == 0) p = i/3;
		else p = i/3+1;
		if(j % 3 == 0) q = j/3;
		else q = j/3+1;
		return stand[p][q];
}//用这个TLE

int getlittle(int x,int y){
    if(x>=1&&x<=3){
        if(y>=1&&y<=3)  return 1;
        else if(y>=4&&y<=6) return 2;
        else    return 3;
    }
    if(x>=4&&x<=6){
        if(y>=1&&y<=3)  return 4;
        else if(y>=4&&y<=6) return 5;
        else    return 6;
    }
    if(x>=7&&x<=9){
        if(y>=1&&y<=3)  return 7;
        else if(y>=4&&y<=6) return 8;
        else    return 9;
    }
}//用这个AC  ==！
```

