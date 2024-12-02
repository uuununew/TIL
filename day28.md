# Relative Ranks
> 정렬

#### 📚 문제 설명
You are given an integer array score of size n, where score[i] is the score of the ith athlete in a competition. All the scores are guaranteed to be unique.

The athletes are placed based on their scores, where the 1st place athlete has the highest score, the 2nd place athlete has the 2nd highest score, and so on. The placement of each athlete determines their rank:
The 1st place athlete's rank is "Gold Medal".
The 2nd place athlete's rank is "Silver Medal".
The 3rd place athlete's rank is "Bronze Medal".
For the 4th place to the nth place athlete, their rank is their placement number (i.e., the xth place athlete's rank is "x").
Return an array answer of size n where answer[i] is the rank of the ith athlete.


#### 📌 제한 사항 
n == score.length
1 <= n <= 104
0 <= score[i] <= 106
All the values in score are unique.

#### 💻 입출력 예
Example 1:

Input: score = [5,4,3,2,1]
Output: ["Gold Medal","Silver Medal","Bronze Medal","4","5"]
Explanation: The placements are [1st, 2nd, 3rd, 4th, 5th].
Example 2:

Input: score = [10,3,8,9,4]
Output: ["Gold Medal","5","Bronze Medal","Silver Medal","4"]
Explanation: The placements are [1st, 5th, 3rd, 2nd, 4th].




---
### 📝 나의 풀이
```java
class Solution {
    public String[] findRelativeRanks(int[] score) {
        Map<Integer,Integer> map = new TreeMap<>();
        for(int i=0 ; i< score.length ; i++){
            map.put(score[i],i);
        }

        int i = 0;
        String[] rank = new String[score.length];
        for(Integer val: map.values()){
            if(i == score.length -3){
                rank[val] = "Bronze Medal";
            }else if(i == score.length -2){
                rank[val] = "Silver Medal";
            }else if(i == score.length -1){
                rank[val] = "Gold Medal";
            }else{
                rank[val] = String.valueOf(score.length - i);        
            }
            i++;
        }
        return rank;
    }
}

```


### ✏️ 다른 사람의 풀이
```java
class Solution {
    public String[] findRelativeRanks(int[] score) {
        int n = score.length;
        Integer[] indexes = new Integer[n];
        for (int i = 0; i < n; i++) {
            indexes[i] = i;
        }

        Arrays.sort(indexes, (a, b) -> score[b] - score[a]);

        String[] result = new String[n];
        for (int i = 0; i < n; i++) {
            if (i == 0) result[indexes[i]] = "Gold Medal";
            else if (i == 1) result[indexes[i]] = "Silver Medal";
            else if (i == 2) result[indexes[i]] = "Bronze Medal";
            else result[indexes[i]] = String.valueOf(i + 1);
        }

        return result;
    }
}
```


---
#### 🔗 문제 링크
비기너: https://leetcode.com/problems/relative-ranks/description/ (30분)
미들러: https://www.acmicpc.net/problem/11055 (1시간 15분)
챌린저: https://school.programmers.co.kr/learn/courses/30/lessons/150368 (1시간 30분)