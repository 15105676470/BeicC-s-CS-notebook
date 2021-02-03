LIS：Longest Increasing Subsequence 

O^2求法：

```c++
//核心代码 这个是求最长不下降子序列的长度
	for(int i = 1; i <= n; i++){
		for(int j = 1; j < i; j++){
			if(node[i].W > node[j].W){ //如果是最长不下降就是>,如果是最长上升的长度就是>=;
				f[i] = max(f[i],f[j]);
			}
		}
		f[i]++;
		maxn = max(maxn,f[i]);
	}
```

