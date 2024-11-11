# 스택
>스택/큐

#### 📚 문제 설명
정수를 저장하는 스택을 구현한 다음, 입력으로 주어지는 명령을 처리하는 프로그램을 작성하시오.

명령은 총 다섯 가지이다.

push X: 정수 X를 스택에 넣는 연산이다.
pop: 스택에서 가장 위에 있는 정수를 빼고, 그 수를 출력한다. 만약 스택에 들어있는 정수가 없는 경우에는 -1을 출력한다.
size: 스택에 들어있는 정수의 개수를 출력한다.
empty: 스택이 비어있으면 1, 아니면 0을 출력한다.
top: 스택의 가장 위에 있는 정수를 출력한다. 만약 스택에 들어있는 정수가 없는 경우에는 -1을 출력한다.


#### 📌 제한 사항 
첫째 줄에 주어지는 명령의 수 N (1 ≤ N ≤ 10,000)이 주어진다. 둘째 줄부터 N개의 줄에는 명령이 하나씩 주어진다. 주어지는 정수는 1보다 크거나 같고, 100,000보다 작거나 같다. 문제에 나와있지 않은 명령이 주어지는 경우는 없다.


#### 💻 입출력 예
출력해야하는 명령이 주어질 때마다, 한 줄에 하나씩 출력한다.
![](https://velog.velcdn.com/images/uunew/post/3733d400-ab08-4270-9068-3214566eaf9d/image.png)






---
### 📝 나의 풀이
```java
import java.io.*;
import java.util.*;

public class Main{
    public static void main(String[] args) throws IOException{
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        int n = Integer.parseInt(br.readLine());
        List<Integer> list = new ArrayList<>();
        StringTokenizer st;
        for(int i = 0; i<n; i++){
            st = new StringTokenizer(br.readLine());            
            String operator = st.nextToken();
            
            switch(operator){
                case "push":
                    int num = Integer.parseInt(st.nextToken());
                    list.add(num);
                    break;
                case "top":
                    if(list.size()==0){
                        System.out.println("-1");
                    }else{
                        System.out.println(list.get(list.size()-1));
                    }
                    break;
                    
                case "size":
                    System.out.println(list.size());
                    break;
                
                case "empty":
                    if(list.size()==0){
                        System.out.println("1");
                    }else{
                        System.out.println("0");
                    }
                    break;
                
                case "pop":
                    if(list.size()==0){
                        System.out.println("-1");
                    }else{
                        System.out.println(list.remove(list.size()-1));
                    }
                    break;
                
            }   
                
        }
        
    }
}
```
list를 사용해서 풀어보았다.


### ✏️ 다른 사람의 풀이
```java
import java.io.*;
import java.util.*;

public class Main {

	public static void main(String[] args) throws Exception {
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		StringTokenizer st;

		int N = Integer.parseInt(br.readLine());
		Stack stack = new Stack(10101);
		StringBuilder sb = new StringBuilder();
		while (N-- > 0) {
			st = new StringTokenizer(br.readLine());
			String cmd = st.nextToken();
			if (cmd.equals("push")) {
				int x = Integer.parseInt(st.nextToken());
				stack.push(x);
			} else if (cmd.equals("pop")) {
				sb.append(stack.pop()).append("\n");
			} else if (cmd.equals("size")) {
				sb.append(stack.size()).append("\n");
			} else if (cmd.equals("empty")) {
				sb.append(stack.isEmpty() ? 1 : 0).append("\n");
			} else if (cmd.equals("top")) {
				sb.append(stack.top()).append("\n");
			} else {
				throw new IllegalStateException();
			}
		}
		System.out.println(sb.toString());
		br.close();
	}
}

class Stack {
	private final int[] stack;
	private int top;

	Stack(int size) {
		this.stack = new int[size];
		this.top = -1;
	}

	void push(int x) {
		stack[++top] = x;
	}

	int pop() {
		return isEmpty() ? -1 : stack[top--];
	}

	int size() {
		return top + 1;
	}

	boolean isEmpty() {
		return top == -1;
	}

	int top() {
		return isEmpty() ? -1 : stack[top];
	}
}
```
stack class 구현해서 풀이한 문제이다. 재사용성 측면에서 효율적인 것 같다.!
아마 문제의 의도는 이렇게 푸는 것이지 않을까?


---
### 💡 회고

오늘은 list로 문제를 풀이해보았다. 다음에는 stack 구현해서 써봐야겠다.
https://www.jdoodle.com/online-java-compiler 사용했는데 편하다.!

---
#### 🔗 문제 링크
- 비기너: https://www.acmicpc.net/problem/10828 (30분)
- 미들러: https://www.acmicpc.net/problem/7569 (1시간 15분)
- 챌린저: https://school.programmers.co.kr/learn/courses/30/lessons/258711 (1시간 30분)