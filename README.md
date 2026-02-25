/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode() : val(0), next(nullptr) {}
 *     ListNode(int x) : val(x), next(nullptr) {}
 *     ListNode(int x, ListNode *next) : val(x), next(next) {}
 * };
 */
class Solution {
public:
    bool isPalindrome(ListNode* head) {
        vector<int> res;
        while(head){
            res.push_back(head->val);
        }
        for(int i=0,j=res.size()-1;i<=j;)
            if(res[i++]!=res[j--])return false;
        return true;

    }
};
