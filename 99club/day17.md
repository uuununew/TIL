# 기술 연계마스터 임스
>스택/큐

#### 📚 문제 설명
임스는 연계 기술을 사용하는 게임을 플레이 중에 있다. 연계 기술은 사전 기술과 본 기술의 두 개의 개별 기술을 순서대로 사용해야만 정상적으로 사용 가능한 기술을 말한다.

하나의 사전 기술은 하나의 본 기술과만 연계해서 사용할 수 있으며, 연계할 사전 기술 없이 본 기술을 사용했을 경우에는 게임의 스크립트가 꼬여서 이후 사용하는 기술들이 정상적으로 발동되지 않는다. 그렇지만 반드시 사전 기술을 사용한 직후에 본 기술을 사용할 필요는 없으며, 중간에 다른 기술을 사용하여도 연계는 정상적으로 이루어진다.

임스가 사용할 수 있는 기술에는 
$1$~$9$, $L$, $R$, $S$, $K$가 있다. 
$1$~$9$는 연계 없이 사용할 수 있는 기술이고, $L$은 $R$의 사전 기술, $S$은 $K$의 사전 기술이다.

임스가 정해진 순서대로 $N$개의 기술을 사용할 때, 기술이 몇 번이나 정상적으로 발동하는지를 구해보자.

단, 연계 기술은 사전 기술과 본 기술 모두 정상적으로 발동되었을 때만 하나의 기술이 발동된 것으로 친다.
#### 📌 제한 사항 
첫 번째 줄에는 총 기술 사용 횟수 $N$이 주어진다. ($1 \le N \le 200\,000$)

두 번째 줄에는 임스가 사용할 $N$개의 기술이 공백 없이 주어진다.


#### 💻 입출력 예

임스가 정상적으로 기술을 사용한 총 횟수를 출력한다.
![](https://velog.velcdn.com/images/uunew/post/1799ff32-8210-4cfe-818b-7efcef82390e/image.png)





---
### 📝 나의 풀이
```java
import java.io.*;
import java.util.*;

public class Main {
	public static void main(String[] args) throws IOException{
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		Stack<Character> stack = new Stack<>(), stack1 = new Stack<>();
		br.readLine();
		int answer = 0;
        
		for(char c : br.readLine().toCharArray()) {
			if(c == 'L') {
				stack.add(c);
			}
            else if(c == 'S') {
				stack1.add(c);
			}
			else if(c == 'R') {
				if(!stack.isEmpty()) {
					answer++;
					stack.pop();
				}
				else {
					break;
				}
			}
			else if(c == 'K') {
				if(!stack1.isEmpty()) {
					answer++;
					stack1.pop();
				}
				else {
					break;
				}
			}
			else {
				answer++;
			}
		}
		System.out.print(answer);
	}
}
```



### ✏️ 다른 사람의 풀이
```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.Stack;

public class _25497_ { // 기술 연계마스터 임스

	public static void main(String[] args) throws IOException {
		BufferedReader bf = new BufferedReader(new InputStreamReader(System.in));

		int n = Integer.parseInt(bf.readLine());
		String str = bf.readLine();

		Stack<Character> sStack = new Stack<>();
		Stack<Character> lStack = new Stack<>();
		int result = 0;

		for (int i = 0; i < n; i++) {
			char x = str.charAt(i);
			if (Character.isDigit(x)) {
				result += 1;
			} else if (x == 'L') {
				lStack.add(x);
			} else if (x == 'S') {
				sStack.add(x);
			} else if (x == 'R') {
				if (!lStack.isEmpty()) {
					lStack.pop();
					result += 1;
				} else {
					break;
				}
			} else if (x == 'K') {
				if (!sStack.isEmpty()) {
					sStack.pop();
					result += 1;
				} else {
					break;
				}
			}
		}
		System.out.println(result);
	}
}
```
Stack을 2개 사용하여 하나는 R의 사전 기술인 L을 저장하고, 다른 하나는 K의 사전 기술인 S를 저장한 풀이이다.


---
### 💡 회고
if else를 많이 써서 한눈에 보기 어려운 것 같다. 다음엔 조금 더 간결하고 이해하기 쉽게 코드를 짜봐야겠다.



---
#### 🔗 문제 링크
비기너: https://www.acmicpc.net/problem/25497 (45분)
미들러: https://www.acmicpc.net/problem/31926 (1시간 15분)
챌린저: https://www.acmicpc.net/problem/2056 (1시간 15분)
