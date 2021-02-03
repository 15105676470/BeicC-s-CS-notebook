BFS实际是在图中进行的算法，找出源节点到目标节点的最小值，其他的一些地方像什么迷宫都是一种特殊的图。

BFS正确性的保证：需要借助队列，队列中的结点距原点的距离一定是递增的，只有这样才能保证算法的正确性（BFS像水波一样一层一层往外拓展，当拓展到目标节点时，算法结束，得到答案）

0/1BFS：在求最短路径的时候，如果每条边都相等，就可以使用BFS，但如果每条边不一样，就需要用其他的方法来求了(无负权边可以考虑Dijkstra，有负权边用SPAFA)，原理如上，但如果边权值只有两种，就可以使用0/1BFS进行求最短路。

0/1BFS与普通的BFS唯一不同的地方就是普通的BFS使用的是普通队列，而0/1BFS使用的是双向队列deque

例题：https://leetcode-cn.com/problems/minimum-cost-to-make-at-least-one-valid-path-in-a-grid/

坑哥详解：https://www.bilibili.com/video/av92847643?p=5