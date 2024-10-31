# 99클럽 코테 스터디 2일차 TIL : 크기가 작은 부분 문자열

#### 📚 문제 설명
숫자로 이루어진 문자열 t와 p가 주어질 때, t에서 p와 길이가 같은 부분문자열 중에서, 이 부분문자열이 나타내는 수가 p가 나타내는 수보다 작거나 같은 것이 나오는 횟수를 return하는 함수 solution을 완성하세요.

예를 들어, t="3141592"이고 p="271" 인 경우, t의 길이가 3인 부분 문자열은 314, 141, 415, 159, 592입니다. 이 문자열이 나타내는 수 중 271보다 작거나 같은 수는 141, 159 2개 입니다.

#### 📌 제한 사항 
1 ≤ p의 길이 ≤ 18
p의 길이 ≤ t의 길이 ≤ 10,000
t와 p는 숫자로만 이루어진 문자열이며, 0으로 시작하지 않습니다.

#### 💻 입출력 예
|t|p|result|
|---|:---|:---|
|"3141592"|"271"|2|
|"500220839878"|"7"|8|
|"10203"|"15"|3|

입출력 예 #1
본문과 같습니다.

입출력 예 #2
p의 길이가 1이므로 t의 부분문자열은 "5", "0", 0", "2", "2", "0", "8", "3", "9", "8", "7", "8"이며 이중 7보다 작거나 같은 숫자는 "5", "0", "0", "2", "2", "0", "3", "7" 이렇게 8개가 있습니다.

입출력 예 #3
p의 길이가 2이므로 t의 부분문자열은 "10", "02", "20", "03"이며, 이중 15보다 작거나 같은 숫자는 "10", "02", "03" 이렇게 3개입니다. "02"와 "03"은 각각 2, 3에 해당한다는 점에 주의하세요

---
### 📝 나의 풀이
```java
class Solution {
    public int solution(String t, String p) {
        int answer = 0;
        int len = p.length();
        long num = Long.parseLong(p);
        for(int i=0; i<t.length() - len + 1; i++){
            long a = Long.parseLong(t.substring(i, i + len));
            if (a <= num) {
                answer++;
            }
        }
        return answer;
    }
}
```
p의 길이를 담을 len을 만들어준다.
이 문제의 핵심같은데 p의 길이가 최대 18임을 보고 Long 타입을 써야한다.
그리고 substring과 Long.parseLong을 사용해서 String과 Long 사이의 타입 변환을 해준다.

### ✏️ 다른 사람의 풀이
```java
class Solution {
    public int solution(String t, String p) {
        //p의 최대 길이 18 -> int 범위 초과 long 타입 필요
        int len = p.length();
        Long pLong = Long.parseLong(p);
        int cnt = 0;
        
        for(int i=0; i<t.length() - len + 1; i++) {
            String str = t.substring(i, i+len);
            
            if(Long.parseLong(str) <= pLong) {
                cnt++;
            }
        }

        return cnt;
    }
}

```


---
### 💡 회고

처음에는 int형으로 선언해서 풀었는데 잘 풀리지 않았다. p의 길이가 최대 18임을 보고 Long 타입을 써야한다는 생각이 오래걸렸다.
