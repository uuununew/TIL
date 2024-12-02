# 더 맵게
>힙(Heap)

#### 📚 문제 설명
매운 것을 좋아하는 Leo는 모든 음식의 스코빌 지수를 K 이상으로 만들고 싶습니다. 모든 음식의 스코빌 지수를 K 이상으로 만들기 위해 Leo는 스코빌 지수가 가장 낮은 두 개의 음식을 아래와 같이 특별한 방법으로 섞어 새로운 음식을 만듭니다.

> 섞은 음식의 스코빌 지수 = 가장 맵지 않은 음식의 스코빌 지수 + (두 번째로 맵지 않은 음식의 스코빌 지수 * 2)

Leo는 모든 음식의 스코빌 지수가 K 이상이 될 때까지 반복하여 섞습니다.
Leo가 가진 음식의 스코빌 지수를 담은 배열 scoville과 원하는 스코빌 지수 K가 주어질 때, 모든 음식의 스코빌 지수를 K 이상으로 만들기 위해 섞어야 하는 최소 횟수를 return 하도록 solution 함수를 작성해주세요.



#### 📌 제한 사항 
scoville의 길이는 2 이상 1,000,000 이하입니다.
K는 0 이상 1,000,000,000 이하입니다.
scoville의 원소는 각각 0 이상 1,000,000 이하입니다.
모든 음식의 스코빌 지수를 K 이상으로 만들 수 없는 경우에는 -1을 return 합니다.


#### 💻 입출력 예
![](https://velog.velcdn.com/images/uunew/post/c154ee80-b42d-4329-9431-9f2c1c6a1246/image.png)

1. 스코빌 지수가 1인 음식과 2인 음식을 섞으면 음식의 스코빌 지수가 아래와 같이 됩니다.
새로운 음식의 스코빌 지수 = 1 + (2 * 2) = 5
가진 음식의 스코빌 지수 = [5, 3, 9, 10, 12]

2. 스코빌 지수가 3인 음식과 5인 음식을 섞으면 음식의 스코빌 지수가 아래와 같이 됩니다.
새로운 음식의 스코빌 지수 = 3 + (5 * 2) = 13
가진 음식의 스코빌 지수 = [13, 9, 10, 12]

모든 음식의 스코빌 지수가 7 이상이 되었고 이때 섞은 횟수는 2회입니다.




---
### 📝 나의 풀이
```java
import java.util.*;

class Solution {
    public int solution(int[] scoville, int K) {
        int answer = 0;
        PriorityQueue<Integer> queue = new PriorityQueue<>();
        for(int i : scoville){
            queue.add(i);
        }
        
        int min = queue.peek();
        while(min < K){
            if(queue.size() >= 2){
                queue.add(queue.poll() + (queue.poll() * 2));
                min = queue.peek();
                answer++;
            }else{
                return -1;
            }
        }
        return answer;
    }
}

```
PriorityQueue를 사용하였다.

### ✏️ 다른 사람의 풀이
```java
import java.util.*;

class Solution {
    public int solution(int[] scoville, int K) {
        int answer = 0;
        PriorityQueue<Integer> priorityqueue = new PriorityQueue<>();
        for(var element : scoville){
            priorityqueue.add(element);
        }
        while(priorityqueue.peek() < K){
            if(priorityqueue.size()<2) return -1;
            int leastspicy = priorityqueue.poll();
            int secondlyleastspicy = priorityqueue.poll();
            priorityqueue.add(mix(leastspicy,secondlyleastspicy));
            answer++;
        }
        
        return answer;
    }
    public int mix(int a, int b){
           return a+(b*2);
    }
}

```


---
### 💡 회고

Arrylist는 효율성 테스트를 통과하지 못한다. 우선순위 큐로 풀어야한다.



---
#### 🔗 문제 링크
비기너: https://school.programmers.co.kr/learn/courses/30/lessons/42626 (30분)
미들러: https://www.acmicpc.net/problem/2116 (1시간 30분)
챌린저: https://www.acmicpc.net/problem/2169 (1시간 15분)