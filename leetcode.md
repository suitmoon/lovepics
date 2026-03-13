class Solution {
public:
    int subarraysDivByK(vector<int>& nums, int k) {
        int sum=0,res=0;
        unordered_map<int,int> umap;
        umap[0]=1;
        for(int i:nums){
            sum+=i;
            int mod = (sum%k+k)%k;
            res+=umap[mod];
            umap[mod]++;
        }
        return res;
    }
};
