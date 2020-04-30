2.2.
####用个计数器计算链表长度
####然后计算节点位置，返回
package data;

public class Solution2II {

    public class ListNode {
        int val;
        ListNode next;
        ListNode(int x) { val = x; }
    }
    public int kthToLast(ListNode head, int k) {
        ListNode pre = head;
        ListNode pur = head;
        int ans = 0;
        while (pur != null){
            ans ++;
            pur = pur.next;
        }
        int index = 0;
        while (pre != null){
            index ++;
            if(index == ans - k+1)
                return pre.val;
            pre = pre.next;
        }
        return 0;
    }
    public static void main(String[] args) {

    }
}


25
#####1.创造一个新链表
#####2.对两个链表元素进行比较，添加进新链表，依此循环
package data;

public class Solution25 {

    public class ListNode {
        int val;
        ListNode next;

        ListNode(int x) {
            val = x;
        }
    }
    public ListNode mergeTwoLists(ListNode l1, ListNode l2) {
        if (l1 == null)
            return l2;
        if (l2 == null)
            return l1;
        ListNode l3 = null;
        if (l1.val <= l2.val){
            l3 = l1;
            l1 = l1.next;
        }else {
            l3 = l2;
            l2 = l2.next;
        }
        while (l1 != null && l2 != null){
            if (l1.val <= l2.val){
                l3.next = l1;
                l1 = l1.next;
            }else {
                l3.next = l2;
                l2 = l2.next;
            }
            l3 = l3.next;
        }
        if (l1 == null)
            l3.next = l2;
        else
            l3.next = l1;
        return l3;
    }
}

