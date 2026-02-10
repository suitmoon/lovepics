         vector<vector<int>> res(n,vector<int>(n,0));
	       int top = 0,bottom = n-1,left = 0,right = n-1,num=1;
         while(1){
            for (int i = left; i<=right; i++) res[top][i]=num++;
            if(++top>bottom)break;
            for (int i = top; i<=bottom; i++) res[i][right]=num++;
            if(--right<left)break;
            for(int i = right; i>=left; i--) res[bottom][i]=num++;
            if(--bottom<top)break;
            for(int i = bottom; i>=top; i--) res[i][left]=num++;
            if(++left>right)break;            
	       }
         return res;
