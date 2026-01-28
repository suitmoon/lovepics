       int slow = 0,fast = 0;
       for(;fast<nums.size();){
         if(nums[fast]==val){fast++;}
         else{
           nums[slow++] = nums[fast++];
         }
       }
       return slow;
