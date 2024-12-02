# Delete Greatest Value in Each Row
>힙(Heap)

#### 📚 문제 설명
You are given an m x n matrix grid consisting of positive integers.

Perform the following operation until grid becomes empty:

Delete the element with the greatest value from each row. If multiple such elements exist, delete any of them.
Add the maximum of deleted elements to the answer.
Note that the number of columns decreases by one after each operation.

Return the answer after performing the operations described above.


#### 📌 제한 사항 
m == grid.length
n == grid[i].length
1 <= m, n <= 50
1 <= grid[i][j] <= 100



#### 💻 입출력 예
![](https://velog.velcdn.com/images/uunew/post/5c12d7d4-807a-4ad0-88f6-78ff8109a4d7/image.png)







---
### 📝 나의 풀이
```java
import java.util.*;

class Solution {
    public int deleteGreatestValue(int[][] grid) {
        int sum = 0;
        for (int i = 0; i < grid.length; i++) {
            Arrays.sort(grid[i]);
        }
        for (int j = 0; j < grid[0].length; j++) {
            int max = Integer.MIN_VALUE;
            for (int i = 0; i < grid.length; i++) {
                if (grid[i][j] > max) {
                    max = grid[i][j];
                }
            }
            sum += max;
        }
        return sum;
    }
}


```


### ✏️ 다른 사람의 풀이
```java
class Solution {
    public int deleteGreatestValue(int[][] grid) {
        for (var row : grid) {
            Arrays.sort(row);
        }
        int ans = 0;
        for (int j = 0; j < grid[0].length; ++j) {
            int t = 0;
            for (int i = 0; i < grid.length; ++i) {
                t = Math.max(t, grid[i][j]);
            }
            ans += t;
        }
        return ans;
    }
}
```

---
### 💡 회고
리트코드는,, 아직 적응이 되지 않는다,,

---
#### 🔗 문제 링크
비기너: https://leetcode.com/problems/delete-greatest-value-in-each-row/description/ (30분)
미들러: https://school.programmers.co.kr/learn/courses/30/lessons/42839 (1시간 15분)
챌린저: https://www.acmicpc.net/problem/15686 (1시간 15분)