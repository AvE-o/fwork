#202 Happy Number

###瞎写写
```java
//用set 因为set具有唯一性
class Solution {
    public boolean isHappy(int n) {
        Set<Integer> record = new HashSet<>();
        while (n != 1 && !record.contains(n)) {
            record.add(n);
            n = getNextNumber(n);
        }
        
        return n == 1;
    }
    private int getNextNumber(int n) {
        int res = 0;
        //计算每一位数的^2
        while (n > 0) {
            int temp = n % 10;
            res = temp * temp;
            n = n / 10;
        }
        return result;
    }
}
```

###Solution

class Solution {
    public boolean isHappy(int n) {
        Set<Integer> record = new HashSet<>();
        while (n != 1 && !record.contains(n)) {
            record.add(n);
            n = getNextNumber(n);
        }
        return n == 1;
    }

    private int getNextNumber(int n) {
        int res = 0;
        while (n > 0) {
            int temp = n % 10;
            res += temp * temp;
            n = n / 10;
        }
        return res;
    }
}