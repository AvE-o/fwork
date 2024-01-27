# 55.右旋字符串

### 瞎写写
v1.
// 我这里直接用StringBuilder 加了
// 感觉要反转
class Solution {
    public String reverseStr(String s, int k) {
        int start = 0;
        int end = s.length() - 1;
        StringBuilder sb = new StringBuilder();
        while (end > (s.length() - k - 1)) {
            sb.append(s.charAt(end));
            end--;
        }
        while (start < s.length() - k - 1) {
            sb.append(s.charAt(start));
            start++;
        }
        return sb.toString();
    }
}

v2.
class Solution {
    public String reverseStr(String s, int k) {
        int start = 0;
        int end = s.length() -1;
        char[] ch = s.toCharArray();
        reverseString(ch, start, end);
        reverseString(ch, start, k - 1);
        reverseString(ch, k, end);
    }
    private void reverseString(char[] ch, int start, int end) {
        while (start < end) {
            char temp = ch[start];
            ch[start] = ch[end];
            ch[end] = temp;
            start++;
            end--;
        }
    }
}


### Solution
// 版本一
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner in = new Scanner(System.in);
        int n = Integer.parseInt(in.nextLine());
        String s = in.nextLine();

        int len = s.length();  //获取字符串长度
        char[] chars = s.toCharArray();
        reverseString(chars, 0, len - 1);  //反转整个字符串
        reverseString(chars, 0, n - 1);  //反转前一段字符串，此时的字符串首尾尾是0,n - 1
        reverseString(chars, n, len - 1);  //反转后一段字符串，此时的字符串首尾尾是n,len - 1
        
        System.out.println(chars);

    }

    public static void reverseString(char[] ch, int start, int end) {
        //异或法反转字符串，参照题目 344.反转字符串的解释
        while (start < end) {
            ch[start] ^= ch[end];
            ch[end] ^= ch[start];
            ch[start] ^= ch[end];
            start++;
            end--;
        }
    }
}


// 版本二
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner in = new Scanner(System.in);
        int n = Integer.parseInt(in.nextLine());
        String s = in.nextLine();

        int len = s.length();  //获取字符串长度
        char[] chars = s.toCharArray();
        reverseString(chars, 0, len - n - 1);  //反转前一段字符串，此时的字符串首尾是0,len - n - 1
        reverseString(chars, len - n, len - 1);  //反转后一段字符串，此时的字符串首尾是len - n,len - 1
        reverseString(chars, 0, len - 1);  //反转整个字符串

        System.out.println(chars);

    }

    public static void reverseString(char[] ch, int start, int end) {
        //异或法反转字符串，参照题目 344.反转字符串的解释
        while (start < end) {
            ch[start] ^= ch[end];
            ch[end] ^= ch[start];
            ch[start] ^= ch[end];
            start++;
            end--;
        }
    }
}