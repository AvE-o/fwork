# 209 Minimum Size Subarray Sum

###瞎写写

尝试定义一个窗口
i = 0;
j = 1;
Sum = 0;

思路是 大于Target时候 减去左手边第一个数字 找到最小的窗口
-> 这里忘记记录了所需要的长度
while (j != nums.length) { (x) #这里应该用for好点
    Sum += nums[j]
    while(Sum >= target) {
        Sum -= nums[i];
        i++;
    }
    j++;
}


###Solution
class Solution {
    // 滑动窗口
    public int minSubArrayLen(int s, int[] nums) {
        int left = 0;
        int sum = 0;
        int result = Integer.MAX_VALUE;
        for (int right = 0; right < nums.length; right++) {
            sum += nums[right];
            while (sum >= s) {
                result = Math.min(result, right - left + 1); // 长度 
                sum -= nums[left++];
            }
        }
        return result == Integer.MAX_VALUE ? 0 : result;
    }
}


# 904 Fruit Into Baskets

###瞎写写
利用一个窗口记录水果 怎么知道窗口里两种？
HASH?
int i = 0;
Result = 0;
// 用来记录水果种类
count = 0; 
HashMap<Integer, Integer> window = new HashMap<>();

for (int j = 0; j < nums.length; j++) {
    检查contain Key 2 个水果{
        count++;
    }
    XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
    
}

###Solution
lass Solution {
    public int totalFruit(int[] tree) {
        //创建哈希表记录水果类型及其数量
        HashMap<Integer, Integer> window = new HashMap<>();
        //水果类型数量
        int count = 0;
        //左右边界
        int left = 0;
        int right = 0;
        //最大长度（也是水果总量的最大值）
        int maxlen = 0;
        //进入循环
        while(right < tree.length) {
            //如果这是一种新类型的水果，count+1
            if(!window.containsKey(tree[right]) || window.get(tree[right]) == 0)
                count++;
            //将right所指记录在window中
            window.put(tree[right], window.getOrDefault(tree[right], 0) + 1);
            right++;
            //实时更新长度
            if(count <= 2) {
                if(right - left > maxlen) {
                    maxlen = right - left;
                }
            }
            //遇到第三种类型，开始缩小窗口
            while(count > 2) {
                //将left所指的水果类型数量 - 1
                window.put(tree[left], window.getOrDefault(tree[left], 0) - 1);
                //如果某种水果类型的数量变为0，则水果类型数量count--
                if(window.get(tree[left]) == 0)
                    count--;
                left++;
            }
        }
        return maxlen;
    }
}