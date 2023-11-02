#27 Spiral Matrix II


###瞎写写

求行和列的边界
class Solution {
    int loop = 0;
    int start = 0;//Starting point for every loop
    int cur = 1;//starting with number 1 in 1.1.
    int i,j; // i - rwo; j - col
    public int[][] generateMatrix(int n) {
        //first row 记得边界
        while(loop++ < n/2){ //转几圈
            for (int j = start; j < n; j++) { //左到右
                int[start][j] = cur++;
            } for (int i = start; i < n; i++) { //上到下
                int[i][j] = cur++;
            } for (,j >= loop; j--) { //右到左
                int[i][j] = cur++;
            } for (, i>= loop; i--) { //下到上
                int[i][j] = cur++;
            }                                               *写到这里发现边界定义搞错了 不清楚
            if (n % 2 == 1) {
                int[start][start] = cur;
            }
        }
        
    }
}

###Soltion
class Solution {
    public int[][] generateMatrix(int n) {
        int loop = 0;  // 控制循环次数
        int[][] res = new int[n][n];
        int start = 0;  // 每次循环的开始点(start, start)
        int count = 1;  // 定义填充数字
        int i, j;
        while (loop++ < n / 2) { // 判断边界后，loop从1开始
            // 模拟上侧从左到右
            for (j = start; j < n - loop; j++) {
                res[start][j] = count++;
            }
            // 模拟右侧从上到下
            for (i = start; i < n - loop; i++) {
                res[i][j] = count++;
            }
            // 模拟下侧从右到左
            for (; j >= loop; j--) {
                res[i][j] = count++;
            }
            // 模拟左侧从下到上
            for (; i >= loop; i--) {
                res[i][j] = count++;
            }
            start++;
        }
        if (n % 2 == 1) {
            res[start][start] = count;
        }
        return res;
    }
}