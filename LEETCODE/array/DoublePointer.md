#27 Remove Element


###瞎写写

int a = 0;


for (int b = 0; b < nums.length - 1; b++){
    if (nums[b] != val) {
        nums[a] = nums[b];
        a++;
    }
}
return nums;

###Soltion

class Solution {
    public int removeElement(int[] nums, int val) {
        // 快慢指针
        int slowIndex = 0;
        for (int fastIndex = 0; fastIndex < nums.length; fastIndex++) {
            if (nums[fastIndex] != val) {
                nums[slowIndex] = nums[fastIndex];
                slowIndex++;
            }
        }
        return slowIndex;
    }
}

#26 Remove Duplicates from Sorted Array

###瞎写写
(x)
int slowindex = 0;
for (int fastindex = 1; fastindex++; fastindex < nums.length - 1) {
    if (nums[slowindex] == nums[fastindex]) {
        nums[slowindex] = nums[fastindex];
        slowindex++;
    }

}

### Solution
class Solution {
    public int removeDuplicates(int[] nums) {
        int j = 1;
        for (int i = 1; i < nums.length; i++) {
            if (nums[i] != nums[i - 1]) {
                nums[j] = nums[i];
                j++;
            }
        }
        return j;
    }
}


# 977 Squares of Sorted Array

###瞎写写
应该是前后两个pointer 
(x)
int i = 0;
int j = nums.length - 1;
int n = 0;
while (i < j) {
    if (nums[i] * nums[i] > nums[j] * nums[j]) {
        nums[n] = nums[i] * nums[i];
        i++;
        n++;
    } else {
        nums[n] = nums[j] * nums[j];
        j++;
        n++;
    }
}
这里出现问题 应该是从后往前排序 因为是比大小 大的在后

### Solution

class Solution {
    public int[] sortedSquares(int[] nums) {
        int right = nums.length - 1;
        int left = 0;
        int[] result = new int[nums.length];
        int index = result.length - 1;
        while (left <= right) {
            if (nums[left] * nums[left] > nums[right] * nums[right]) {
                // 正数的相对位置是不变的， 需要调整的是负数平方后的相对位置
                result[index--] = nums[left] * nums[left];
                ++left;
            } else {
                result[index--] = nums[right] * nums[right];
                --right;
            }
        }
        return result;
    }
}