#383 Ransom Note

###瞎写写 
//我这个方法空间是不值得的 因为只有26个字母 浪费这么多空间
```java
class Solution {
    public boolean canConstruct(String ransomNote, String magazine) {
        HashMap<String, Integer> map = new HashMap<>();
        //先把magazine 整个放到一个map里
        for (int i : magazine) [x这里错啦] {
            map.put(magazine[i], map.getOrDefault(magazine[i], 0) + 1);
        }
        //然后再用一个循环对比是否存在
        for (int i : ransomNote) [same 错了] {
            if (map.containsKey(ransomNote[i])) {
                int currentVal = map.get(ransomNote[i]);
                map.put(ransomNote[i], currentVal - 1); //update the value;
                continue;
            } else {
                return false;
            }
        }
        return true;
    }
}
```

###Solution

```java
class Solution {
    public boolean canConstruct(String ransomNote, String magazine) {
        // shortcut
        if (ransomNote.length() > magazine.length()) {
            return false;
        }
        // 定义一个哈希映射数组
        int[] record = new int[26];

        // 遍历
        for(char c : magazine.toCharArray()){
            record[c - 'a'] += 1;
        }

        for(char c : ransomNote.toCharArray()){
            record[c - 'a'] -= 1;
        }
        
        // 如果数组中存在负数，说明ransomNote字符串总存在magazine中没有的字符
        for(int i : record){
            if(i < 0){
                return false;
            }
        }

        return true;
    }
}

```