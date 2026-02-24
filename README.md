class Solution {
public:
    int remove(ListNode* head, int n) {
		if(!head->next)return 1;
		int now_n = remove(head->next) + 1;
		if (now_n == n+1) 
			head->next = head->next->next;
		return now_n;
    }
    ListNode* removeNthFromEnd(ListNode* head, int n) {
        ListNode node;
		node.next = head;
		remove(&node,n+1);
		return node.next;:
    }
};
