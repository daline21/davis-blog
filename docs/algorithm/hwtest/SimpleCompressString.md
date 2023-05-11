### 代码
```java

import java.util.Stack;

public class CompressStr {
    public static void main(String[] args) {
        String str = "{CCA2B1{ASC}3}3";
        System.out.println(solution(str));
    }

    public static String solution(String ss) {
        Stack<String> stack = new Stack<>();
        char[] cc = ss.toCharArray();
        int count = 0;
        for (int i = 0; i < cc.length; i++) {
            char curChar = cc[i];
            if (isNumber(curChar)) {
                count = count * 10 + (curChar - '0');
                if (i == cc.length - 1 || i + 1 < cc.length && !isNumber(cc[i + 1])) {
                    String trans = translate(stack.pop(), count);
                    stack.add(trans);
                    count = 0;
                }
            } else if (curChar == '}') {
                String sub = "";
                while (!stack.peek().equals("{")) {
                    sub = stack.pop() + sub;
                }
                stack.pop();
                stack.add(sub);
            } else {
                stack.add(curChar + "");
            }
        }
        String result = "";
        while (!stack.isEmpty()) {
            result = stack.pop() + result;
        }
        return result;
    }

    public static boolean isNumber(char c) {
        return c >= '0' && c <= '9';
    }

    public static String translate(String ss, Integer count) {
        StringBuffer sb = new StringBuffer();
        while (count-- > 0) {
            sb.append(ss);
        }
        return sb.toString();
    }
}

```