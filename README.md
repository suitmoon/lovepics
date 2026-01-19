# lovepics
class Solution {
public:
    int removeElement(vector<int>& nums, int val) {
       int head = 0,tail = nums.size()-1,res = 0;
       while(head<=tail){
	if(nums[head]!=val){
		head++;
		res++;
		continue;
	}
	if(nums[tail]!=val){
	  nums[head]=nums[tail];
	  nums[tail]=val;
	  head++;tail--;res++;
	}
	if(nums[tail]==val){tail--;}
       }
       return res;
  }
};

不要说错在哪 ，直说是大错还是小错
