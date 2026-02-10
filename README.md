Program received signal SIGSEGV, Segmentation fault.
0x0000555555555cd2 in std::vector<int, std::allocator<int> >::operator[] (this=0x55495556ded0, __n=18446744071562067972) at /usr/include/c++/11/bits/stl_vector.h:1046
1046            return *(this->_M_impl._M_start + __n);  
#include <vector>
#include <iostream>
using namespace std;
class Solution {
public:
    vector<vector<int>> generateMatrix(int n) {
         vector<vector<int>> res(n,vector<int>(n,0));
	 if(n==1)return{{1}};
	 int top = 0, left = 0 ,bottom = n - 1,right = n - 1;
	 int num = 1;
	 while(1){
	   if(top==bottom||left==right)break;	 
           for(int i = left;i <= right;i++){  
		res[top][i] = num++;               
	   }
	   top++;
	   for(int i = top;i<=bottom;i++){
	     res[i][right] = num++;
	   }
	   right--;
	   for(int i = right;i>=left;i--){
             res[bottom][i] = num++;	
	   }
	   bottom--;
	   for(int i = bottom;i>=top;i--){
	     res[i][left]  = num++;
	   }
	   left++;
	 }
         return res;
    }
};
int main(){
   Solution example = Solution();
   auto res = example.generateMatrix(4);
   //for(auto i:res){
     //for(auto k:i) {
       //cout<< k << " ";
     //}
     //cout<<endl;
   //}
}
gdb已开启 慢慢一步一步教我怎么排错 现在就按熟悉流程来 我就不怎么思考了
