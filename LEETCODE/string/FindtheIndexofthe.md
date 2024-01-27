# 28.Find the Index of the First Occurrence in a String
// KMP -> 主要应用在字符串匹配上
// next is a prefix table
// 目的是为了不要浪费匹配的时间
### 瞎写写
// 这里因为不想使用O(2) 时间所以先阅读KMP
// v1
class Solution {
    public int strStr(String haystack, String needle) {
        for (int i = 0; i < haystack.length(); i++) {
            
        }
    }
}

// v2

class Solution {
    private void getNext(int[] next, string s) {
        next[0] = 0;
        int j = 0; // 前缀表的首字母
        // i是后缀表的尾字母
        for (int i = 1; i < s.length(); i++) {
            // 解决不相等情况
            while (j > 0 && next[j] != next[i]) {
                // 回退j
                j = next[j - 1];
            }
            if (next[j] == next[i]) {
                j++;
            }
            next[i] = j;
        }              
    }
    public int strStr(String haystack, String needle) {
        if (needle.length() == 0) return 0;
        int[] next = new int[needle.length()];
        getNext(next, needle);
        // 开始匹配
        int j = 0;
        for (int i = 0; i < haystack.length(); i++) {
            while (j > 0 && needle.charAt(j) != haystack.charAt(i)) {
                j = next[j - 1];
            }
            if (needle.charAt(j) == haystack.charAt(i)) {
                j++;
            }
            if (j == needle.length()) {
                return i - needle.length() + 1;
            }
            return -1;
        }
    }
}

### Solution
class Solution {
    //前缀表（不减一）Java实现
    public int strStr(String haystack, String needle) {
        if (needle.length() == 0) return 0;
        int[] next = new int[needle.length()];
        getNext(next, needle);

        int j = 0;
        for (int i = 0; i < haystack.length(); i++) {
            while (j > 0 && needle.charAt(j) != haystack.charAt(i)) 
                j = next[j - 1];
            if (needle.charAt(j) == haystack.charAt(i)) 
                j++;
            if (j == needle.length()) 
                return i - needle.length() + 1;
        }
        return -1;

    }
    
    private void getNext(int[] next, String s) {
        int j = 0;
        next[0] = 0;
        for (int i = 1; i < s.length(); i++) {
            while (j > 0 && s.charAt(j) != s.charAt(i)) 
                j = next[j - 1];
            if (s.charAt(j) == s.charAt(i)) 
                j++;
            next[i] = j; 
        }
    }
}