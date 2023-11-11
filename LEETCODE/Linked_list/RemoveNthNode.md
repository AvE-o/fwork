#19 Remove Nth Node From End of List

###瞎写写
我这里思路是求长度 然后计算位置
忘记删除了!
class Solution {
public ListNode removeNthFromEnd(ListNode head, int n) {
        int m = 0;
        ListNode headlen = head;
        while(headlen ! = null) {
            headlen = headlen.next;
            m += 1;
        }
        int k = m - n;
        if (k > 0) {
            while (k > 0) {
                head = head.next;
                k--;
            }
        } else {
            return;
        }
        return head;
    }
}

#双指针的话
class Solution {
public ListNode removeNthFromEnd(ListNode head, int n) {
        ListNode dummy = new ListNode(0);
        dummy.next = head;
        ListNode slow = dummy;
        ListNode fast = dummy;
        *这里注意 fast 多移动一步会让slow先一步停在被删节点前 方便删除操作
        for (n; n + 1 > 0; n--) {
            fast = fast.next;
        }
        xxxxxxxxxxxxxx
    }
}

###Solution
public ListNode removeNthFromEnd(ListNode head, int n){
ListNode dummyNode = new ListNode(0);
dummyNode.next = head;
    ListNode fastIndex = dummyNode;
    ListNode slowIndex = dummyNode;
    // 只要快慢指针相差 n 个结点即可
    for (int i = 0; i <= n  ; i++){ 
        fastIndex = fastIndex.next;
    }
    while (fastIndex != null){
        fastIndex = fastIndex.next;
        slowIndex = slowIndex.next;
    }
    //此时 slowIndex 的位置就是待删除元素的前一个位置。
    //具体情况可自己画一个链表长度为 3 的图来模拟代码来理解
    slowIndex.next = slowIndex.next.next;
    return dummyNode.next;
}