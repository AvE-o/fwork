24.Swap Nodes in Pairs

###瞎写写
// 两两交换
// 有问题的八嘎
class Solution {
    public ListNode swapPairs(ListNode head) {
        ListNode temp = null;
        ListNode cur = head.next;
        ListNode headf = head.next;
        ListNode prev = head;
        while (cur != null) {
            temp = cur.next;
            cur.next = prev;
            prev.next = temp;
            cur = temp.next;
            prev = temp;
        }
        return headf;
    }
}

class Solution {
    public ListNode swapPairs(ListNode head) {
        ListNode dummy = new ListNode(-1);
        dummy.next = head;
        ListNode cur = dummy;
        ListNode temp;
        ListNode firstNode;
        ListNode secondNode;
        while(cur.next != null && cur.next.next != null) {
            temp = cur.next.next.next;
            firstNode = cur.next;
            secondNode = cur.next.next;
            cur.next = secondNode;
            secondNode.next = firstNode;
            firstNode.next = temp;
            cur = firstNode;
        }
        return dummy.next;
        
    }
}

###Soltion
class Solution {
  public ListNode swapPairs(ListNode head) {
        ListNode dumyhead = new ListNode(-1); // 设置一个虚拟头结点
        dumyhead.next = head; // 将虚拟头结点指向head，这样方便后面做删除操作
        ListNode cur = dumyhead;
        ListNode temp; // 临时节点，保存两个节点后面的节点
        ListNode firstnode; // 临时节点，保存两个节点之中的第一个节点
        ListNode secondnode; // 临时节点，保存两个节点之中的第二个节点
        while (cur.next != null && cur.next.next != null) {
            temp = cur.next.next.next;
            firstnode = cur.next;
            secondnode = cur.next.next;
            cur.next = secondnode;       // 步骤一
            secondnode.next = firstnode; // 步骤二
            firstnode.next = temp;      // 步骤三
            cur = firstnode; // cur移动，准备下一轮交换
        }
        return dumyhead.next;  
    }
}

// 递归版本
class Solution {
    public ListNode swapPairs(ListNode head) {
        // base case 退出提交
        if(head == null || head.next == null) return head;
        // 获取当前节点的下一个节点
        ListNode next = head.next;
        // 进行递归
        ListNode newNode = swapPairs(next.next);
        // 这里进行交换
        next.next = head;
        head.next = newNode;
        return next;
    }
} 