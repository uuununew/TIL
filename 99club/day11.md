# 완주하지 못한 선수
>해시

#### 📚 문제 설명
수많은 마라톤 선수들이 마라톤에 참여하였습니다. 단 한 명의 선수를 제외하고는 모든 선수가 마라톤을 완주하였습니다.

마라톤에 참여한 선수들의 이름이 담긴 배열 participant와 완주한 선수들의 이름이 담긴 배열 completion이 주어질 때, 완주하지 못한 선수의 이름을 return 하도록 solution 함수를 작성해주세요.

#### 📌 제한 사항 
마라톤 경기에 참여한 선수의 수는 1명 이상 100,000명 이하입니다.
completion의 길이는 participant의 길이보다 1 작습니다.
참가자의 이름은 1개 이상 20개 이하의 알파벳 소문자로 이루어져 있습니다.
참가자 중에는 동명이인이 있을 수 있습니다.


#### 💻 입출력 예

|participant|	completion	|return|
|---|:---|:---|
|["leo", "kiki", "eden"]|	["eden", "kiki"]|	"leo"|
|["marina", "josipa", "nikola", "vinko", "filipa"]|	["josipa", "filipa", "marina", "nikola"]|	"vinko"|
|["mislav", "stanko", "mislav", "ana"]|	["stanko", "ana", "mislav"]|	"mislav"|

예제 #1
"leo"는 참여자 명단에는 있지만, 완주자 명단에는 없기 때문에 완주하지 못했습니다.

예제 #2
"vinko"는 참여자 명단에는 있지만, 완주자 명단에는 없기 때문에 완주하지 못했습니다.

예제 #3
"mislav"는 참여자 명단에는 두 명이 있지만, 완주자 명단에는 한 명밖에 없기 때문에 한명은 완주하지 못했습니다.

---
### 📝 나의 풀이
```java
import java.util.*;

class Solution {
    public String solution(String[] participant, String[] completion) {
        String answer = "";
        Map<String, Integer> map = new HashMap<>();
        
        for(String p : participant){
            map.put(p, map.getOrDefault(p, 0) + 1);
        }      
        for(String c : completion){
            map.put(c, map.get(c) - 1);
        }
        for(String key : map.keySet()){
            if(map.get(key) !=0){
                answer = key;
                break;
            }
        }
        
        return answer;
    }
}
```
HashMap을 사용하여 문제를 풀었다.
for문을 돌며 Map에 저장된 value 값이 0이 아닌 사람의 이름을 출력했다.



### ✏️ 다른 사람의 풀이
```java
import java.util.*;
class Solution {
    public String solution(String[] participant, String[] completion) {
        Arrays.sort(participant);
        Arrays.sort(completion);
        int i;
        for ( i=0; i<completion.length; i++){

            if (!participant[i].equals(completion[i])){
                return participant[i];
            }
        }
        return participant[i];
    }
}

```
정렬을 하고 앞에서 부터 하나씩 비교하는 풀이

---
### 💡 회고

getOrDefault(Object key, V DefaultValue)
- key : map 요소의 키
- defaultValue : 지정된 키로 매핑된 값이 없거나 null이면 반환하는 기본 값

---
#### 🔗 문제 링크
- 비기너: https://school.programmers.co.kr/learn/courses/30/lessons/42576 (45분)
- 미들러: https://www.acmicpc.net/problem/25195 (1시간 15분)
- 챌린저: https://www.acmicpc.net/problem/1461 (1시간)
