数位dp就是dfs加记忆化数组。

他就相当与暴力，只不过其中加入了记忆化数组来加速这个过程......

```c++
///HDU 2089http://acm.hdu.edu.cn/showproblem.php?pid=2089
#include<bits/stdc++.h>
using namespace std;
typedef long long LL;
 
int digit[20];
LL dp[20][2];
 
///if4=>status(状态)是否是6
LL dfs(int len,bool if6,bool limit){
    if(len==0) return 1ll;
    if(!limit && dp[len][if6]) return dp[len][if6];
 
    LL cnt=0,up_bound=(limit?digit[len]:9);
    for(int i=0;i<=up_bound;++i){
        if(if6 && i==2)///=>找到一个49
            continue;
        if(i==4) continue;//剪枝
        cnt+=dfs(len-1,i==6,limit&&i==up_bound);
    }
    if(!limit) dp[len][if6]=cnt;
    return cnt;
}
///统计的是没有62的个数
LL solve(LL num){  //这个digit数组是从1开始的。
    int k=0;
    while(num){
        digit[++k]=num%10; 
        num/=10;
    }
    return dfs(k,false,true);
}
 
int main(){
 
    LL N,M;
    while(cin>>N>>M && N+M){
 
//注意0 0 的特判  当n=0时，n-1=-1，这时solve（-1）代入跑dfs，得出的结果就还真是0
//所以我感觉这套板子的强度很大！！！   满足卡特判的活！！！
//精髓在   ！！！卡特判！！！
        cout<<solve(M)-solve(N-1)<<endl;
    }
    return 0;
}
```

