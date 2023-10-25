#704 Binary Search
*升序，无重复数组

###瞎写写
low = 0;
high = nums.length;
mid = (high - low) / 2; (mid 位置有问题 应该每次重复计算)
while(left < right) {  (这里注意边界问题)
    if (target < nums[mid]) {
        high = mid;
    }
    else if (target > nums[mid]){
        low = mid + 1 ;
    } else {
        return mid;
    }
}

### Solution

class Solution {
    public int search(int[] nums, int target) {
        int left = 0, right = nums.length;
        while (left < right) {
            int mid = left + ((right - left) >> 1);
            if (nums[mid] == target)
                return mid;
            else if (nums[mid] < target)
                left = mid + 1;
            else if (nums[mid] > target)
                right = mid;
        }
        return -1;
    }
}

#35 Search Insert Position

###瞎写写
Class Solution{
    public int search(int nums[], int target) {
        left = 0;
        right = nums.length;
        while(left < right) {
            mid = (right - left) / 2;
            if(nums[mid] < target) {
                left = mid + 1;
            } else if(nums[mid] > target) {
                right = mid;
            } else {
                return mid;
            }
        }
        return right;
    }
}

### Solution

//第二种二分法：左闭右开
public int searchInsert(int[] nums, int target) {
    int left = 0;
    int right = nums.length;
    while (left < right) { //左闭右开 [left, right)
        int middle = left + ((right - left) >> 1);
        if (nums[middle] > target) {
            right = middle; // target 在左区间，在[left, middle)中
        } else if (nums[middle] < target) {
            left = middle + 1; // target 在右区间，在 [middle+1, right)中
        } else { // nums[middle] == target
            return middle; // 数组中找到目标值的情况，直接返回下标
        }
    }
    // 目标值在数组所有元素之前 [0,0)
    // 目标值插入数组中的位置 [left, right) ，return right 即可
    // 目标值在数组所有元素之后的情况 [left, right)，因为是右开区间，所以 return right
    return right;
}