class Solution {
public:
    ListNode* removeNthFromEnd(ListNode* head, int n) {
        ListNode newhead;
        newhead.next = head;
        ListNode* fast = &newhead;
        fast = fast->next;
        int length = 0;
        while(fast){
          length++;
          fast = fast->next;
        }
        ListNode* front = &newhead;
        for(int i = 0;i<length-n;i++)front=front->next;
        front->next = front->next->next;
        return newhead.next;
    }
};
