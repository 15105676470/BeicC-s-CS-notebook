## 写在前头

每种dp方法有每种套路，可是在实际做题的过程中，到底怎么才能知道这题可以用dp来解呢？

​	我好像发现个规律，凡是用dfs感觉要超时的时候，这时候就要考虑dp了

## 博弈论

自己的想法：博弈论真的是自己跟自己玩，一般都是记忆化搜索，就是一个dp的过程

参考博客：https://blog.csdn.net/hanyanwei123/article/details/79871079

为了防止博客丢失：

1.ACM博弈题，不会的时候觉得难于上青天，会的时候觉得没有比博弈更水的题了；

博弈题看到的第一眼觉得是难题，代码敲完顿觉水题。你可能花半个小时去找规律，然后仅花2分钟敲代码。

2.博弈是单人游戏，也可以说是自己跟自己玩，因为“双方都做出最优决策”这一点限制了，最后的结果不取决

于你是谁，不取决于你的智商，只取决于你面对的**局面**；

3.**局面，**这是博弈里面最最最重要的东西！！！（所谓SG也是指这一局面的SG），博弈是一种不公平的游戏

因为游戏开始的时候已经结束了，影响你胜负的就是你所面对的局面，因为双方采取最优策略

故而局面必然会以双方当前对自己最优的路径走下去，所以结局已经确定了

4.当你面对一个局面的时候如何做出最优的决策呢？你一定是走到了最后一步才确定了胜负，所以当前的局面

往往需要从最终的局面逆推而来（也就是从一个已知胜负的局面一步步推导其他的局面，有了这样的思想，SG

也就不那么难理解了）

5.关于***\*SG：\****

入门了博弈的人都知道，博弈里面常常用到一个重要的概念 – SG。但是SG是什么？你去百度的话会有非常专业的解答，

但是那些所谓的专业绝对让人看的头疼。这里说说我所理解的博弈里面的SG（仅限博弈）

挑程里是这样解释SG值的：

​     ***\*除\** \**任意一步所能转移到的子局面的SG值\**\**以外\****的**最小非**负整数**。**

仔细体会一下这句话，你会发现，这里对SG值的定义是**递归**定义的！

当前局面的SG是什么呢？请先去找当前局面的子局面的SG值。

显然，递归是有一个边界的，SG是一种递归，那么它也是有边界的，

不难发现，它的边界是没有子局面的局面（也就无法再转移的局面）

什么样的局面没有子局面呢，也就是胜负已定的局面。在第4点说到，

当前局面的最优策略是从胜负已定的最终局面逆推来的，这里的SG其实也是

说了这些，那么SG到底是什么呢？

联想当年学习递归的一个例子：

f(n)  =  1     , n = 1

​      f(n-1) +1  ,n > 1

这样一个函数是我们学习递归时的经典例子，你说这里的F到底是什么？其实它不过是一个函数而已。

SG也是一样，它只是一个函数而已，函数这个词翻译成英语再翻译成中文，就成了“功能、作用”

那么SG的作用是什么呢？

举一个最简单的例子：

有一堆石头数量为n,两个人轮流从石堆拿{a1,a2,a3,……,ak}个石头，先取完所有石头者胜。

根据前面说的，首先找胜负已定的局面，当n=0的时候，石头被拿完了，败态

那么sg[0] = 0表示面对0个石头的局面者败，然后根据sg的定义，我们可以求出其他局面的sg值

（为了使每种局面确保有可以转移的子局面，我们假设{a1,a2,a3……,ak}里面一定有1，例如假设没有1的话

，假设为{5，6,7}那么局面4没有可以转移的子局面，这样会出现平局的情况，我们后面再说平局）

这样可以求出所有局面的sg值,然后sg的作用出来了~

我们发现，若sg[x] = 0,那么x是败态，这其中很神奇，鶸也说不清楚，只说一下胜态败态的转移

（其实光理解的话可能还是不知道什么是SG，但是看了后面的题目就能理解了并知道怎么用SG找到游戏的胜态败态了）

6.胜态与败态：

之前说了，博弈里面，游戏开始的时候已经结束了，影响你胜负的就是你所面对的局面。

也就是说，这个局面觉得了你的胜负，我们称能让你走向胜利的局面称为胜态，也是必胜态，专业术语也叫P态（积极的英语单词怎么写？）

称让你走向失败的状态称为败态，也是必败态，专业也叫N态（消极的英语单词鶸也不会拼。。。）

有一个很显然的规律：

只要当前状态可以转移到的状态中有一个是败态，那么当前状态就是胜态。

如果当前状态可以转移到的所有状态都是胜态，那么当前状态就是败态。

这两句话互为逆否命题，一眼就看出是对的就不解释了。

可以胜态败态的角度去理解下SG。

7.Nim游戏：

关于这个Nim游戏，百度的话又是一大堆乱七八糟看不下去的东西，

它的最原始的版本大概是说有N堆石头，{a1,a2,a3……,an}表示每堆的数量，两个人轮流选一个石堆拿若干石头（不能不拿），

如果轮到某个人时所有的石子堆都已经被拿空了，则判负。

这个游戏有个非常完美的结论：

令  s  =  a1^a2^a3….^an(^符号表示异或运算)

若 s = 0,则此局面为败态，否则为胜态

对于上面的式子，我们不难发现，当你从一个石堆拿走一些石头（即改变一个ai），一定会发生胜态和败态的转变

胜态一定会转移成败态，败态也一定有策略转移成胜态

当这个结论与SG结合，神奇的事发生

我们发现sg异或和为0的状态也是败态，否则胜态。

另外，很多游戏都可以转变为Nim的形式，例如POJ 1704(挑程上有讲解)

8.关于平局：

我们发现，一个必胜态的获得，必然是因为它可以转移到一个败态，那么是不是说相比于平局我们更倾向于败态呢？

如果有更多的败态，理论上可以转移出更多的胜态，但是孩子别太天真了啊~

博弈将“对敌人的仁慈就是对自己的残忍”这句话发挥的淋漓尽致，当你选择败态的时候，对方却不会傻傻按照你的想法给你转移胜态的

该你输的时候你还是得输，所以，在博弈里的决策，一定要是对自己最有利对对手最不利的策略才是最优策略，、

也就是说，如果实在不能赢，你一定宁可平局，也不要选择败态。例如今年HDU 多校题5754 里面马的情况

9.当初关于博弈看了很多但是都只是似懂非懂，只有做多了题才有更多的·体会

### update 21.1.20

​	对于博弈论，其实就是谁先手谁win(or lose)的问题，也就是说胜负取决于谁先手。对于某个人的turn来讲，如果他想赢，无非就以下几种条件

1. 走到一些可以直接赢的状态
2. 走到对方的必败态
3. 否则，就输掉了

对于博弈论问题，作为编码者的我们，是从一个上帝视角来进行编码的，也就是说一个总状态要同时能够反映出两个人的当前状态

例题：[1728. 猫和老鼠 II](https://leetcode-cn.com/problems/cat-and-mouse-ii/)

```c++
/*
    所谓的博弈论：谁先手谁赢(or 输) 事先就已经确定了
    老鼠赢 1  猫赢 0
    老鼠赢: 得到食物 1
            尝试所有的可能，如果能够走到猫的必败态，那就赢 1
            else 0
    猫赢：得到食物 0
          抓到老鼠 0
          走到老鼠的必败态 0
          走的步数超过了1000次
          else 1
    以上帝视角进行编写代码       
*/
int dx[4] = {0,0,1,-1};
int dy[4] = {1,-1,0,0};
class Solution {
public:
    vector<string> G;
    int cj,mj,n,m;
    int dp[8][8][8][8][150];
    bool dfs(int cx, int cy, int mx, int my, int step){
        if (step >= 150) return 0;
        if (dp[cx][cy][mx][my][step] != -1) return dp[cx][cy][mx][my][step];
        if (step % 2){ // cat
            for (int i = 0; i < 4; i++){
                for (int j = 0; j <= cj; j++){
                    int nx = cx+dx[i]*j, ny = cy+dy[i]*j;
                    if (nx < 0 || nx >= n || ny < 0 || ny >= m || G[nx][ny] == '#') break;
                    if (nx == mx && ny == my) dp[cx][cy][mx][my][step]=0;
                    else if (G[nx][ny] == 'F') dp[cx][cy][mx][my][step]=0;
                    else if (!dfs(nx,ny,mx,my,step+1)) dp[cx][cy][mx][my][step]=0;
                }
            }
            if (dp[cx][cy][mx][my][step] == -1) dp[cx][cy][mx][my][step]=1;
        }else{ // mouse
            for (int i = 0; i < 4; i++){
                for (int j = 0; j <= mj; j++){
                    int nx = mx+dx[i]*j, ny = my+dy[i]*j;
                    if (nx < 0 || nx >= n || ny < 0 || ny >= m || G[nx][ny] == '#') break;
                    if (nx == cx && ny == cy) continue;
                    else if (G[nx][ny] == 'F') dp[cx][cy][mx][my][step] = 1;
                    else if (dfs(cx,cy,nx,ny,step+1)) dp[cx][cy][mx][my][step] = 1;
                }
            }
            if (dp[cx][cy][mx][my][step] == -1) dp[cx][cy][mx][my][step] = 0;
        }
        return dp[cx][cy][mx][my][step];
    }
    bool canMouseWin(vector<string>& grid, int catJump, int mouseJump) {
        G = grid;
        cj = catJump; mj = mouseJump;
        int cx,cy,mx,my;
        n = grid.size(), m = grid[0].size();
        for (int i = 0; i < n; i++){
            for (int j = 0; j < m; j++){
                if (grid[i][j] == 'C'){
                    cx = i; cy = j;
                }else if (grid[i][j] == 'M'){
                    mx = i; my = j;
                }
            }
        }
        memset(dp, -1, sizeof(dp));
        return dfs(cx, cy, mx, my, 0);
    }
};
```



## 背包问题

著名的背包九讲：https://www.cnblogs.com/jbelial/articles/2116074.html

一.0-1背包

## 	三进制的状压dp

例题：https://leetcode-cn.com/problems/maximize-grid-happiness/

maxCount：都三进制了，不要在傻乎乎的用<< 或者 >> 符号了，那些符号是将一个数的二进制进行左移或者右移，正确方法：

```c++
int maxCount = 1;
for (int i = 0; i < n; i++) maxCount *= 3;//n 是三进制的位数
```

最后一位的情况：在二进制中，可以直接用state & 1来看最后一位是0 还是1，对于三进制来说，肯定就不能用位运算了，方法：

```c++
while (x){
	if (x % 3 == 1) cnt1++;
    else if (x % 3 == 2) cnt2++;//在草稿纸上写一下按位组成就明白了
	x /= 3;//同理，三进制往右移一位，用/3
}
```
