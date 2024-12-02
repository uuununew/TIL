# Largest Number After Digit Swaps by Parity
> 정렬

#### 📚 문제 설명
You are given a positive integer num. You may swap any two digits of num that have the same parity (i.e. both odd digits or both even digits).

Return the largest possible value of num after any number of swaps.

#### 📌 제한 사항 
1 <= num <= 109

#### 💻 입출력 예
Example 1:

Input: num = 1234
Output: 3412
Explanation: Swap the digit 3 with the digit 1, this results in the number 3214.
Swap the digit 2 with the digit 4, this results in the number 3412.
Note that there may be other sequences of swaps but it can be shown that 3412 is the largest possible number.
Also note that we may not swap the digit 4 with the digit 1 since they are of different parities.
Example 2:

Input: num = 65875
Output: 87655
Explanation: Swap the digit 8 with the digit 6, this results in the number 85675.
Swap the first digit 5 with the digit 7, this results in the number 87655.
Note that there may be other sequences of swaps but it can be shown that 87655 is the largest possible number.


---
### 📝 나의 풀이
```java
class Solution {
    public int largestInteger(int num) {
        int n=String.valueOf(num).length();
       PriorityQueue<Integer>a=new PriorityQueue<>(Collections.reverseOrder());
       PriorityQueue<Integer>b=new PriorityQueue<>(Collections.reverseOrder());
       String s=String.valueOf(num);
       int[]ans=new int[n];
       for (int i = 0; i < n; i++) {
           if((s.charAt(i)-'0')%2==0){
               ans[i]=0;
               b.add(s.charAt(i)-'0');
           }else{
               ans[i]=1;
               a.add(s.charAt(i)-'0');
           }
       }
       for (int i = 0; i < s.length(); i++) {
          if(ans[i]==0){
           ans[i]=b.poll();
          }else{
           ans[i]=a.poll();
          }
       }
       int k=ans[0];
       for (int i = 1; i < n; i++) {
           k=k*10+ans[i];
       }
       return k; 
    }
}

```


### ✏️ 다른 사람의 풀이
```java
class Solution {
    public int largestInteger(int num) {
        int[] ans = new int[10];
        int x = num;
        while (x != 0) {
            ans[x % 10]++;
            x /= 10;
        }
        x = num;
        int result = 0;
        int t = 1;
        while (x != 0) {
            int v = x % 10;
            x /= 10;
            for (int y = 0; y < 10; ++y) {
                if (((v ^ y) & 1) == 0 && ans[y] > 0) {
                    ans[y]--;
                    result += y * t;
                    t *= 10;
                    break;
                }
            }
        }
        return result;
    }
}
```

---
#### 🔗 문제 링크
비기너: https://leetcode.com/problems/largest-number-after-digit-swaps-by-parity/description/ (30분)
미들러: https://www.acmicpc.net/problem/9461 (1시간 15분)
챌린저: https://www.acmicpc.net/problem/11657 (1시간 30분)