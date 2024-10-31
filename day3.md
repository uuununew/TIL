# 99클럽 코테 스터디 3일차 TIL : 문자열 나누기

#### 📚 문제 설명
문자열 s가 입력되었을 때 다음 규칙을 따라서 이 문자열을 여러 문자열로 분해하려고 합니다.

먼저 첫 글자를 읽습니다. 이 글자를 x라고 합시다.
이제 이 문자열을 왼쪽에서 오른쪽으로 읽어나가면서, x와 x가 아닌 다른 글자들이 나온 횟수를 각각 셉니다. 처음으로 두 횟수가 같아지는 순간 멈추고, 지금까지 읽은 문자열을 분리합니다.
s에서 분리한 문자열을 빼고 남은 부분에 대해서 이 과정을 반복합니다. 남은 부분이 없다면 종료합니다.
만약 두 횟수가 다른 상태에서 더 이상 읽을 글자가 없다면, 역시 지금까지 읽은 문자열을 분리하고, 종료합니다.
문자열 s가 매개변수로 주어질 때, 위 과정과 같이 문자열들로 분해하고, 분해한 문자열의 개수를 return 하는 함수 solution을 완성하세요.

#### 📌 제한 사항 
1 ≤ s의 길이 ≤ 10,000
s는 영어 소문자로만 이루어져 있습니다.

#### 💻 입출력 예
|s|result|
|---|:---|
|"banana"|3|
|"abracadabra"|6|
|"aaabbaccccabba"|3|

입출력 예 #1
s="banana"인 경우 ba - na - na와 같이 분해됩니다.

입출력 예 #2
s="abracadabra"인 경우 ab - ra - ca - da - br - a와 같이 분해됩니다.

입출력 예 #3
s="aaabbaccccabba"인 경우 aaabbacc - ccab - ba와 같이 분해됩니다.

---
### 📝 나의 풀이
```java
class Solution {
    public int solution(String s) {
        int answer = 1;
        int cnt = 1;
        char a = s.charAt(0);
        for(int i=1; i<s.length(); i++){
           if(cnt == 0){
               answer ++;
               a = s.charAt(i);
           }
            if(a == s.charAt(i)){
                cnt++;
            }else{
                cnt--;
            }
        }
        return answer;
    }
}
```



### ✏️ 다른 사람의 풀이
```java
class Solution {
    public int solution(String s) {
        int result = 0; // 결과를 저장할 변수 초기화
        // 문자 개수를 저장할 배열. [0]은 target의 개수, [1]은 다른 문자의 개수
        int[] countArr = new int[2]; 
        char target = s.charAt(0); // 첫 번째 문자를 target으로 설정
        
        for (int i = 0; i < s.length(); i++) {
            if (target == s.charAt(i)) { // target 문자와 일치하는 경우
                countArr[0]++; // target 문자의 개수 증가
            } else { // target 문자와 일치하지 않는 경우
                countArr[1]++; // 다른 문자의 개수 증가
            }
            
            // target 문자와 다른 문자의 개수가 같아졌을 때
            if (countArr[0] == countArr[1]) {
                result++; // 균형 잡힌 문자열이 완성되었으므로 결과를 1 증가
                countArr = new int[2]; // 카운트 배열 초기화
                target = s.charAt((i+1) % s.length()); // 다음 target 문자 설정
            }
        }
        
        // 반복이 끝난 후에도 균형이 맞지 않는 경우 마지막 문자열 처리
        if (countArr[0] != countArr[1]) {
            return result + 1; // 남아있는 문자열을 포함하여 결과 반환
        }
        return result; // 최종 결과 반환
    }
}

```
배열을 사용한 풀이

---
### 💡 회고

문제 설명을 해석(?)하는데 시간이 조금 걸렸다. 말이 조금 어려워서 그렇지 생각보다는 간단한 문제였다.
