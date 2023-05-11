### 代码

```java
public class FindLongestSub {
    public static void main(String[] args) {
        char shield = 'D';
        String base = "ABC132";
        System.out.println(solution(shield, base));
    }

    public static int solution(char shield, String base) {
        int[] count = new int[128];
        int left = 0, right = 0;
        char[] charArr = base.toCharArray();
        int max = 0;
        while (right < charArr.length) {
            char curChar = charArr[right];
            if (shield == curChar) {
                right++;
                left = right;
                continue;
            }
            if (count[curChar] < 2) {
                count[curChar]++;
                right++;
                max = Math.max(max, right - left);
            } else {
                count[charArr[left]]--;
                left++;
            }
        }
        return Math.max(max, right - left);
    }
}

```