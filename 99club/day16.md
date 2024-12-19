# 카드1

>스택/큐

#### 📚 문제 설명
N장의 카드가 있다. 각각의 카드는 차례로 1부터 N까지의 번호가 붙어 있으며, 1번 카드가 제일 위에, N번 카드가 제일 아래인 상태로 순서대로 카드가 놓여 있다.

이제 다음과 같은 동작을 카드가 한 장 남을 때까지 반복하게 된다. 우선, 제일 위에 있는 카드를 바닥에 버린다. 그 다음, 제일 위에 있는 카드를 제일 아래에 있는 카드 밑으로 옮긴다.

예를 들어 N=4인 경우를 생각해 보자. 카드는 제일 위에서부터 1234 의 순서로 놓여있다. 1을 버리면 234가 남는다. 여기서 2를 제일 아래로 옮기면 342가 된다. 3을 버리면 42가 되고, 4를 밑으로 옮기면 24가 된다. 마지막으로 2를 버리고 나면, 버린 카드들은 순서대로 1 3 2가 되고, 남는 카드는 4가 된다.

N이 주어졌을 때, 버린 카드들을 순서대로 출력하고, 마지막에 남게 되는 카드를 출력하는 프로그램을 작성하시오.

#### 📌 제한 사항 
첫째 줄에 정수 N(1 ≤ N ≤ 1,000)이 주어진다.


#### 💻 입출력 예
첫째 줄에 버리는 카드들을 순서대로 출력한다. 제일 마지막에는 남게 되는 카드의 번호를 출력한다.

|예제 입력|예제 출력|
|---|:---|
|7|1 3 5 7 4 2 6|



---
### 📝 나의 풀이
```java
import java.io.*;
import java.util.*;

public class Main {
  public static void main(String[] args) throws Exception {
    BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
    BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));

    int N = Integer.parseInt(br.readLine());
    Queue<Integer> queue = new LinkedList<>();
    StringBuilder sb = new StringBuilder();

    for (int i = 1; i <= N; i++)
      queue.add(i);

    while (!queue.isEmpty()) {
      sb.append(queue.remove());
      if (!queue.isEmpty()) {
        sb.append(' ');
        queue.add(queue.remove());
      }
    }

    bw.write(sb.toString());

    bw.flush();
    br.close();
    bw.close();
  }
}
```
큐를 사용하여 풀었다.
큐에서 원소 하나를 제거하여 출력하고 큐가 비어있지 않으면 하나를 제거해서 다시 큐에 넣는 작업을 큐가 비어있을 때까지 반복해줬다.


### ✏️ 다른 사람의 풀이
```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.*;


public class Main {			
	public static void main(String[] args) throws IOException {
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		StringTokenizer st = new StringTokenizer(br.readLine());
		int N = Integer.parseInt(st.nextToken());
		Queue<Integer> Q = new LinkedList<>();
		StringBuilder answer = new StringBuilder();
		
		for (int i = 1; i <= N ; i++) {
			Q.add(i);
		}
		
		while(Q.size() >= 2) {
			int top = Q.poll();
			answer.append(top).append(" ");
			Q.add(Q.poll());
		}
		answer.append(Q.poll());
		System.out.println(answer);
	}
	
}
```
큐의 poll 메서드를 사용하였다.


---
### 💡 회고

처음에 카드가 1부터 시작인 것을 잊고(?) n을 0으로 잡아서 약간 헤맸다.

*** queue ***
- FIFO
- add() 
: 값 추가
: 반환 값(boolean): 삽입 성공 시 true / 실패 시  Exception발생

- offer()
: 값 추가
: 반환 값(boolean): 삽입 성공 시 true / 실패 시 false 반환

- poll()
: 객체 하나를 가져옴
: 가져온 객체는 큐에서 제거

- peek()
: 객체 하나를 가져옴
: 가져온 객체는 큐에서 제거하지 않음





---
#### 🔗 문제 링크
비기너: https://www.acmicpc.net/problem/2161 (30분)
미들러: https://www.acmicpc.net/problem/2847 (1시간 15분)
챌린저: https://www.acmicpc.net/problem/2179 (1시간 15분)
