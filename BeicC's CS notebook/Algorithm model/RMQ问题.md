## ST表

参考博客：https://www.jvruo.com/archives/481/

利用的是倍增思想

板子：

```c++
#include <iostream>
#include <cstdio>
#include <algorithm>
using namespace std;
const int maxn = 1e5+50;
int bin[30],logg[maxn];
int f[maxn][30];
int my_max(int x,int y){
	if(x > y) return x;
	return y;
}

int main()
{
	
	int N,M;
	scanf("%d%d",&N,&M);
	
	bin[0] = 1;for(int i = 1; i < 30; i++) bin[i] = bin[i-1]*2;
	logg[0] = -1;for(int i = 1; i <= N; i++) logg[i] = logg[i/2]+1;
	//ini
	for(int i = 1; i <= N; i++) scanf("%d",&f[i][0]);
	for(int len = 1; len <= logg[N]; len++){
		for(int i = 1; i <= N; i++){
			if(i+bin[len]-1 <= N){
				f[i][len] = my_max(f[i][len-1],f[i+bin[len-1]][len-1]);
			}
		} 
	}
	//Query
	for(int i = 1; i <= M; i++){
		int x,y;
		scanf("%d%d",&x,&y);
		int len = y-x+1;
		int ans = my_max(f[x][logg[len]],f[y-bin[logg[len]]+1][logg[len]]);
		printf("%d\n",ans);
	}
	return 0;
}

```

