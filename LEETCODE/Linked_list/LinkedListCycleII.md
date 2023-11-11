# Linked List Cycle II

# 应该是两个指针 一快一慢
# 问题是如何坚持cycle
public class Solution {
public ListNode detectCycle(ListNode head) {
    # 一个一次走两步 一个一步
    # 一定会相遇因为如果有环 快的比慢的多走 会追上

    }
}

###Soltuion
public class Solution {
    public ListNode detectCycle(ListNode head) {
        ListNode slow = head;
        ListNode fast = head;
        while (fast != null && fast.next != null) {
            slow = slow.next;
            fast = fast.next.next;
            if (slow == fast) {// 有环
                ListNode index1 = fast;
                ListNode index2 = head;
                // 两个指针，从头结点和相遇结点，各走一步，直到相遇，相遇点即为环入口
                while (index1 != index2) {
                    index1 = index1.next;
                    index2 = index2.next;
                }
                return index1;
            }
        }
        return null;
    }
}