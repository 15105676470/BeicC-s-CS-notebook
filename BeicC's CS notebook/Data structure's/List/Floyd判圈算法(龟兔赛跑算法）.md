Floyd判圈算法(龟兔赛跑算法）

##### 1:用途

判断一个链表是否含有环，如果有，确定环的长度和起点

##### 2：方法

###### 基本思想：

龟兔解法的基本思想可以用我们跑步的例子来解释，如果两个人同时出发，如果赛道有环，那么快的一方总能追上慢的一方。进一步想，追上时快的一方肯定比慢的一方多跑了几圈，即多跑的路的长度是圈的长度的倍数。

###### 判断是否有环：

基于上述思想，我们定义一个fast指针来模拟跑的快的人，slow指针模拟跑的慢的人，如果fast指针能和slow指针相遇，就说明有环，而如果fast指针跑到了链表的尾部，则说明无环。

对应例题：https://leetcode-cn.com/problems/linked-list-cycle/

```c++
class Solution {
public:
    bool hasCycle(ListNode *head) {
        if(head == NULL) return false;
        ListNode* fast = head,*slow = head;
        int ans = true;
        do{
            if(fast->next == NULL || fast->next->next == NULL){ //这里假设fast比slow快了两倍，其实只要fast比slow快就行，这里设成两倍比较好写
                ans = false;
                break;
            }
            fast = fast->next->next;
            slow = slow->next;
        }while(fast != slow);
        return ans;
    }
};
```

###### 判断环的长度：

当fast指针和slow指针第一次相遇时，fast肯定比slow多跑一圈，所以分别记录两个指针所走过的路程即可。

###### 判断环的起点：

假设第一次相遇的时候slow走过的节点个数为i，设链表头部到环的起点的长度为m，环的长度为n，相遇的位置与起点位置距离为k。

我们可以得到式子：i = m + a * n + k

又因为fast指针的速度是slow的两倍，所以有：2*i = m + b * n + k

两式相减得：i = (b-a)*n 

因为此时slow和fast相遇，且与起点的距离为i，这时候把slow拿到起点，fast不动，两者以相同的速度前进m，此时slow到达了环的起点，而fast走的距离为i+m，可以理解为fast从链表起点走到了环的起点，然后围着环绕了几圈，所以此时slow和fast必相遇  ----==最终我们得出结论：当fast和slow指针以各自的速度相遇后，把slow指针拿到起点，再让slow和fast以相同的速度往前走，当他俩相遇的位置就是环的起点==

相关题目：https://leetcode-cn.com/problems/linked-list-cycle-ii/

```c++
class Solution {
public:
    ListNode *detectCycle(ListNode *head) {
        if(head == NULL) return NULL;
        ListNode *fast = head,*slow = head;
        bool flag = true;
        do{
            if(fast->next == NULL || fast->next->next == NULL){
                flag = false;
                break;
            }
            fast = fast->next->next;
            slow = slow->next;
        }while(fast != slow);
        if(flag == false) return NULL;
        slow = head;
        while(slow != fast){
            slow = slow->next;
            fast = fast->next;
        }
        return slow;
    }
};
```

##### 3:参考博客：

https://blog.csdn.net/thestoryofsnow/article/details/6822576

https://blog.csdn.net/xiaoquantouer/article/details/51620657?utm_medium=distribute.pc_relevant.none-task-blog-baidujs-2