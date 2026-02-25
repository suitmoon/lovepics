
class Solution {
public:
    bool compare(ListNode* &front,ListNode* rear){
        if(!rear->next){
            int a = front->val;
            int b = rear->val;
            front = front->next;
            return a==b;
        }else{
            if(compare(front,rear->next)){
                int a = front->val;
                int b = rear->val;
                front = front->next;
                return a==b;
            }
            return false;    
        }    
    }
    bool isPalindrome(ListNode* head) {
        int length = 0;
        ListNode* len = head;
        while(head){head = head->next;length++;}
        head = len;
        if(length==1) return true;
        ListNode* rear = head;
        for(int i=0;i<length/2;i++)rear=rear->next;
        ListNode* temp = rear->next;
        rear->next = nullptr;
        rear=temp;
        if(length%2!=0)rear=rear->next;
        return compare(head,rear);
    }
};
