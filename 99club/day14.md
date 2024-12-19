# 큐
>스택/큐

#### 📚 문제 설명
정수를 저장하는 큐를 구현한 다음, 입력으로 주어지는 명령을 처리하는 프로그램을 작성하시오.

명령은 총 여섯 가지이다.

push X: 정수 X를 큐에 넣는 연산이다.
pop: 큐에서 가장 앞에 있는 정수를 빼고, 그 수를 출력한다. 만약 큐에 들어있는 정수가 없는 경우에는 -1을 출력한다.
size: 큐에 들어있는 정수의 개수를 출력한다.
empty: 큐가 비어있으면 1, 아니면 0을 출력한다.
front: 큐의 가장 앞에 있는 정수를 출력한다. 만약 큐에 들어있는 정수가 없는 경우에는 -1을 출력한다.
back: 큐의 가장 뒤에 있는 정수를 출력한다. 만약 큐에 들어있는 정수가 없는 경우에는 -1을 출력한다.


#### 📌 제한 사항 
첫째 줄에 주어지는 명령의 수 N (1 ≤ N ≤ 10,000)이 주어진다. 둘째 줄부터 N개의 줄에는 명령이 하나씩 주어진다. 주어지는 정수는 1보다 크거나 같고, 100,000보다 작거나 같다. 문제에 나와있지 않은 명령이 주어지는 경우는 없다.


#### 💻 입출력 예
출력해야하는 명령이 주어질 때마다, 한 줄에 하나씩 출력한다.
![](https://velog.velcdn.com/images/uunew/post/d304c501-b549-4df3-8741-1e4875bbb6ec/image.png)


---
### 📝 나의 풀이
```java
import java.io.*;
import java.util.*;

public class Main {

	public static void main(String[] args) throws NumberFormatException, IOException {
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));
        Queue<Integer> queue = new LinkedList<>();
        
        int N = Integer.parseInt(br.readLine());
        int last = -1;
        
        for(int i = 0; i<N; i++) {
        	String[] arr = br.readLine().split(" ");
        	
        	switch(arr[0]) {
        	
        	case "push":
        		last = Integer.parseInt(arr[1]);
        		queue.add(last);
        		break;
        		
        	case "pop":
        		if(!queue.isEmpty()) 
        			bw.write(queue.remove()+"\n");
        		else
        			bw.write("-1"+"\n");
        		break;
        	
        	case "size":
        		bw.write(queue.size()+"\n");
        		break;
        		
        	case "empty":
        		if(!queue.isEmpty())
        			bw.write("0"+"\n");
        		else
        			bw.write("1"+"\n");
        		break;
        	
        	case "front":
        		if(!queue.isEmpty())
        			bw.write(queue.peek()+"\n");
        		else
        			bw.write("-1"+"\n");
        		break;
        		
        	case "back":
        		if(!queue.isEmpty())
        			bw.write(last+"\n");
        		else
        			bw.write("-1"+"\n");
        		break;
        		
        	}
        }
        bw.flush();
        bw.close();
        br.close();
	}

}
```
12일차에 풀었던 문제와 거의 비슷하다. 


### ✏️ 다른 사람의 풀이
```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.ArrayDeque;
import java.util.Queue;

public class Main {
	public static void main(String[] args) throws NumberFormatException, IOException {
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		int n = Integer.parseInt(br.readLine());
		ArrayDeque<String> deque = new ArrayDeque<>();
		StringBuilder sb = new StringBuilder();
		while (n-- > 0) {
			String command = br.readLine();
			switch (command) {
			case "pop":
				if (deque.isEmpty()) sb.append(-1).append("\n");
				else sb.append(deque.pollFirst()).append("\n");
				break;
			case "size":
				sb.append(deque.size()).append("\n");
				break;
			case "empty":
				if (deque.isEmpty()) sb.append(1).append("\n");
				else sb.append(0).append("\n");
				break;
			case "front":
				if (deque.isEmpty()) sb.append(-1).append("\n");
				else sb.append(deque.peekFirst()).append("\n");
				break;
			case "back":
				if (deque.isEmpty()) sb.append(-1).append("\n");
				else sb.append(deque.peekLast()).append("\n");
				break;
			default:
				deque.offer(command.substring(5));
				break;
			}
		}
		System.out.print(sb);
	}
}
```
deque를 사용한 풀이


---
### 💡 회고
12일차 문제와 비슷했지만 back 부분을 구현하는데 살짝 막혔다.

*** back : queue에서 가장 뒤에 있는 정수 출력하기 ***
- 큐의 가장 뒷 부분을 출력하기 위해서 push에서 맨뒤에 있는 정수를 last에 담고 back에서 last를 출력하게 하였다.

---
#### 🔗 문제 링크
- 비기너: https://www.acmicpc.net/problem/10845
- 미들러:  https://www.acmicpc.net/problem/14916  (1시간 15분)
- 챌린저: https://school.programmers.co.kr/learn/courses/30/lessons/150365  (1시간 30분)
