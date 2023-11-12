#242 Valid Anagram

###瞎写写
应该是写两个hash table a & b 然后判断一个里面的存在不在另一个里面
class Solution {
    public boolean isAnagram(String s, String t) {
        hashtable bla = hashtable(s啥的);
        hashtable blabla = hashtable(t啥的);
        for(int i = 0; i < bla.length; i++) {
            if(bla.key还是value 啥的 inside blabla) {
                continue;
            } else {
                return false;
            }
        }
    }
}
思路好想错了 这里可以直接用array 定义
然后 对于出现的次数进行记录，然后在另一个里面如果有出现减少次数 最后这个表为0 就是true 不然 false

class Solution {
public boolean isAnagram(String s, String t) {
        int table = new int[26];
        for (int i = 0; i < s.length; i++) {
            table[s.charAt(i) - 'a']++; //对应位置数字+1就行
        }
        for (int i = 0; i < t.length; i++) {
            table[t.charAt(i) - 'a']--; 
        }
        for (int count: table) {
            if (count != 0) {
                return false;
            }
        }
        return true;
    }
}

###Solution
/**
* 242. 有效的字母异位词 字典解法
* 时间复杂度O(m+n) 空间复杂度O(1)
  */
  class Solution {
  public boolean isAnagram(String s, String t) {
  int[] record = new int[26];
       for (int i = 0; i < s.length(); i++) {
           record[s.charAt(i) - 'a']++;     // 并不需要记住字符a的ASCII，只要求出一个相对数值就可以了
       }
       for (int i = 0; i < t.length(); i++) {
           record[t.charAt(i) - 'a']--;
       }
       for (int count: record) {
           if (count != 0) {               // record数组如果有的元素不为零0，说明字符串s和t 一定是谁多了字符或者谁少了字符。
               return false;
           }
       }
       return true;                        // record数组所有元素都为零0，说明字符串s和t是字母异位词
  }
  }