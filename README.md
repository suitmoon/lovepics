
---

### 4. 标准教科书级写法 (Best Practice)

最优雅的写法是**“每走一步，回头看一眼”**。不要等到跑完一圈再检查，要在修改边界的那一瞬间检查。

不需要你动脑子，直接背下这个**“四个if”**的模板，这是处理螺旋矩阵最稳的写法：

```cpp
class Solution {
public:
    vector<vector<int>> generateMatrix(int n) {
        vector<vector<int>> res(n, vector<int>(n, 0));
        int top = 0, bottom = n - 1, left = 0, right = n - 1;
        int num = 1;
        
        while(true) {
            // 1. 向右走
            for(int i = left; i <= right; i++) res[top][i] = num++;
            if(++top > bottom) break; // 走完第一行，top下移。如果你越过了bottom，说明填完了，立刻停！

            // 2. 向下走
            for(int i = top; i <= bottom; i++) res[i][right] = num++;
            if(--right < left) break; // 走完最右列，right左移。如果你越过了left，立刻停！

            // 3. 向左走
            for(int i = right; i >= left; i--) res[bottom][i] = num++;
            if(--bottom < top) break; // 走完最下行，bottom上移。

            // 4. 向上走
            for(int i = bottom; i >= top; i--) res[i][left] = num++;
            if(++left > right) break; // 走完最左列，left右移。
        }
        return res;
    }
};

```

