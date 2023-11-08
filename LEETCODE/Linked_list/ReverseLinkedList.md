206.Reverse Linked list
###瞎写写
// 其实应该用双指针法
class Solution {
    public ListNode reverseList(ListNode head) {
        ListNode dummyhead = new Listnode();
        dummyhead.next = head; //搞错了好像
        for (int i = 0; i < head.length; i++) {
            ListNode temp = head.next.next;
            head.next.next = head;
            head.next = dummyhead;
            head = temp;
        }
    }
}

class Solution {
    public ListNode reverseList(ListNode head) {
        ListNode pre = null;
        ListNode cur = head;
        ListNode temp = null;
        for (int i = 0; i < head.length; i++) { // X!
            temp = pre.next;
            cur.next = pre;
            pre = cur;
            cur = temp; 
        }
        return prev;
    }
}

###Soltion
// 双指针
class Solution {
    public ListNode reverseList(ListNode head) {
        ListNode prev = null;
        ListNode cur = head;
        ListNode temp = null;
        while (cur != null) {
            temp = cur.next;// 保存下一个节点
            cur.next = prev;
            prev = cur;
            cur = temp;
        }
        return prev;
    }
}

// 递归 
// 会写双指针递归也非常好理解
class Solution {
    public ListNode reverseList(ListNode head) {
        return reverse(null, head);
    }
    private ListNode reverse(ListNode prev, ListNode cur) {
        if (cur == null) {
            return prev;
        }
        ListNode temp = null;
        temp = cur.next;// 先保存下一个节点
        cur.next = prev;// 反转
        // 更新prev、cur位置
        // prev = cur;
        // cur = temp;
        return reverse(cur, temp);
    }
}