#15 3Sum

# 瞎写写
# 这里可能用到Set 每找出一组 加到set 以免重复（注: 浪费时间）
# Set(Integer) record = new HashSet<>();

# double pointer
# 这里还要考虑去重 
class Solution {
    public List<List<Integer>> threeSum(int[] nums) {
        List<List<Integer>> result = new ArrayList<>();
        Array.sort(nums);
        for (int i = 0; i < nums.length; i++) {
            if (nums[i] > 0) {
                break;
            }
            if (i > 0 && nums[i] == nums[i - 1]) {
                continue;
            }
            int left = i + 1;
            int right = nums.length - 1;
            while(left < right) {
                int sum = nums[i] + nums[left] + nums[right];
                if(sum > 0) {
                    right--;
                } if(sum < 0) {
                    left++;
                } else {
                    result.add(Arrays.asList(num[i] + num[left] + num[right]));
                    while(right > left && nums[right] == nums[right + 1]) right--;
                    while(right > left && nums[left] == nums[left + 1]) left++;
                    right--;
                    left++;    
                }
            }      
        }
        return result;
    }
}

# Solution
class Solution {
    public List<List<Integer>> threeSum(int[] nums) {
        List<List<Integer>> result = new ArrayList<>();
        Arrays.sort(nums); // 首先进行排序
	// 找出a + b + c = 0
        // a = nums[i], b = nums[left], c = nums[right]
        for (int i = 0; i < nums.length; i++) {
	    // 排序之后如果第一个元素已经大于零，那么无论如何组合都不可能凑成三元组，直接返回结果就可以了
            if (nums[i] > 0) { 
                return result;
            }
            if (i > 0 && nums[i] == nums[i - 1]) {  // 去重a
                continue;
            }
            int left = i + 1;
            int right = nums.length - 1;
            while (right > left) {
                int sum = nums[i] + nums[left] + nums[right];
                if (sum > 0) {
                    right--;
                } else if (sum < 0) {
                    left++;
                } else {
                    result.add(Arrays.asList(nums[i], nums[left], nums[right]));
		    // 去重逻辑应该放在找到一个三元组之后，对b 和 c去重
                    while (right > left && nums[right] == nums[right - 1]) right--;
                    while (right > left && nums[left] == nums[left + 1]) left++;
                    right--; 
                    left++;
                }
            }
        }
        return result;
    }
}