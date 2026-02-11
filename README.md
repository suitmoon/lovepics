        ListNode* nhead = new ListNode(0,head);
        ListNode* fast = nhead->next;
        ListNode* slow = nhead;
        while (fast) {
            if(fast->val == val){
                slow->next = fast->next;
                fast = fast->next;
            }else {
                slow = slow->next;
                fast = fast->next;
            }
        }
        return nhead->next;
