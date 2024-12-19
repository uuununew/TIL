# 같은 숫자는 싫어
>스택/큐

#### 📚 문제 설명
배열 arr가 주어집니다. 배열 arr의 각 원소는 숫자 0부터 9까지로 이루어져 있습니다. 이때, 배열 arr에서 연속적으로 나타나는 숫자는 하나만 남기고 전부 제거하려고 합니다. 단, 제거된 후 남은 수들을 반환할 때는 배열 arr의 원소들의 순서를 유지해야 합니다. 예를 들면,

arr = [1, 1, 3, 3, 0, 1, 1] 이면 [1, 3, 0, 1] 을 return 합니다.
arr = [4, 4, 4, 3, 3] 이면 [4, 3] 을 return 합니다.
배열 arr에서 연속적으로 나타나는 숫자는 제거하고 남은 수들을 return 하는 solution 함수를 완성해 주세요.

#### 📌 제한 사항 
배열 arr의 크기 : 1,000,000 이하의 자연수
배열 arr의 원소의 크기 : 0보다 크거나 같고 9보다 작거나 같은 정수

#### 💻 입출력 예
입출력 예 #1,2
문제의 예시와 같습니다.

|arr|answer|
|---|:---|
|[1,1,3,3,0,1,1]|[1,3,0,1]|
|[4,4,4,3,3]|[4,3]|


---
### 📝 나의 풀이
```java
import java.util.*;

public class Solution {
    public int[] solution(int []arr) {
        int[] answer = {};
        Stack<Integer> stack = new Stack<>();
        
        for(int i=0; i<arr.length; i++){
            // 스택이 비어있거나 i가 직전에 담긴 값과 다를 경우 i 넣기
            if(stack.empty() || stack.peek() != arr[i]){
                stack.push(arr[i]);
            }
        }
        
        answer = new int[stack.size()];
        for(int i=stack.size()-1; i>=0; i--){
            answer[i] = stack.pop();
        }
        return answer;
    }
}
```
스택을 사용하여 풀어보았다. 
스택이 비어있으면 1개를 넣고 같은 값이면 넣지 않고, 값이 다르면 값을 스택에 넣는다.


### ✏️ 다른 사람의 풀이
```java
import java.util.*;

public class Solution {
    public Stack<Integer> solution(int []arr) {

        Stack<Integer> stack = new Stack<>();

        for(int num : arr){
            if(stack.size() == 0 || stack.peek() != num){
                stack.push(num);
            }
        }
        return stack;
    }
}
```
return 타입을  stack으로 바꿔서 훨씬 간결한 코드이다.


---
### 💡 회고
*** stack ***
- peek() 
: 스택의 마지막 요소를 반환하며, 스택에는 변화를 주지 않음
: 즉, 스택에 가장 먼저 사용될 요소를 반환
: 스택이 비어있을 경우 peek() 메서드 호출 시 NoSuchElementException 예외 발생

- empty()
: 스택이 비어있는지의 여부를 반환
: 비어있을 경우 true, 비어있지 않을 경우 false를 반환

- pop()
: 스택의 마지막 요소 제거함과 동시에 해당 값을 반환


---
#### 🔗 문제 링크
- 비기너: https://school.programmers.co.kr/learn/courses/30/lessons/12906 (30분)
- 미들러: https://www.acmicpc.net/problem/13417 (1시간 15분)
- 챌린저: https://www.acmicpc.net/problem/2665 (1시간 30분)
