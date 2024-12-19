# 최소 힙
>힙(Heap)

#### 📚 문제 설명
널리 잘 알려진 자료구조 중 최소 힙이 있다. 최소 힙을 이용하여 다음과 같은 연산을 지원하는 프로그램을 작성하시오.

배열에 자연수 x를 넣는다.
배열에서 가장 작은 값을 출력하고, 그 값을 배열에서 제거한다.
프로그램은 처음에 비어있는 배열에서 시작하게 된다.

#### 📌 제한 사항 
첫째 줄에 연산의 개수 N(1 ≤ N ≤ 100,000)이 주어진다. 다음 N개의 줄에는 연산에 대한 정보를 나타내는 정수 x가 주어진다. 만약 x가 자연수라면 배열에 x라는 값을 넣는(추가하는) 연산이고, x가 0이라면 배열에서 가장 작은 값을 출력하고 그 값을 배열에서 제거하는 경우이다. x는 231보다 작은 자연수 또는 0이고, 음의 정수는 입력으로 주어지지 않는다.


#### 💻 입출력 예
입력에서 0이 주어진 횟수만큼 답을 출력한다. 만약 배열이 비어 있는 경우인데 가장 작은 값을 출력하라고 한 경우에는 0을 출력하면 된다.
![](https://velog.velcdn.com/images/uunew/post/965c3098-4307-478e-8734-fb1ccdff1012/image.png)




---
### 📝 나의 풀이
```java
import java.util.*;
import java.io.*;

public class Main {
	public static void main(String[] args) throws IOException {
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		PriorityQueue<Integer> queue = new PriorityQueue<>();
		int N = Integer.parseInt(br.readLine());
		
		for(int i=0; i<N; i++) {
			int val = Integer.parseInt(br.readLine());
			
			if(val == 0) {
				if(queue.isEmpty()){
					System.out.println("0");
				}else{
					System.out.println(queue.poll());
				}
			}else
				queue.add(val);
		}
	}
}
```


### ✏️ 다른 사람의 풀이
```java
import java.io.*;

public class Main {

	public static void main(String[] args) throws IOException {
		StringBuilder sb = new StringBuilder();

		int n = readInt();

		MinHeap minHeap = new MinHeap();

		while (n-- > 0) {
			int x = readInt();

			if (x != 0) minHeap.offer(x);
			else sb.append(minHeap.poll()).append("\n");
		}

		System.out.println(sb);
	}

	private static class MinHeap {
		int[] heap = new int[100001];
		int size = 0;

		void offer(int x) {
			heap[++size] = x;
			int idx = size;

			while (idx != 1) {
				int cur = idx/2;

				if (heap[idx] > heap[cur]) break;

				swap(idx, cur);

				idx = cur;
			}
		}

		int poll() {
			if (size == 0) return 0;

			int r = heap[1];
			heap[1] = heap[size--];
			int idx = 1;

			while (idx * 2 <= size) {
				int left = idx * 2;
				int right = left + 1;
				int min = left;

				if (right <= size && heap[right] < heap[left]) min = right;
				if (heap[min] >= heap[idx]) break;

				swap(min, idx);

				idx = min;
			}

			return r;
		}

		void swap(int x, int y) {
			int tmp = heap[x];
			heap[x] = heap[y];
			heap[y] = tmp;
		}
	}

	private static int readInt() throws IOException {
		int input, output = 0;
		while (!((input = System.in.read()) == ' ' || input == '\n')) {
			output = ((output * 10) + input) - 48;
		}
		return output;
	}
}
```


---
### 💡 회고

*** 힙(Heap) ***
: 완전 이진트리 형태로 최대, 최솟값을 빠르게 찾아내는데 유용한 자료구조

- 최소 힙(Min Heap)
: 루트노드가 최솟값이 되고, 부모노드의 key는 자식노드의 key보다 작아야 한다

- 최대힙(Max Heap) 
: 루트노드가 최댓값이 되고, 부모노드의 key가 자식 노드의 key보다 커야 한다







---
#### 🔗 문제 링크
비기너: https://www.acmicpc.net/problem/1927 (30분)
미들러: https://www.acmicpc.net/problem/1374 (1시간 30분)
챌린저: https://www.acmicpc.net/problem/1022 (1시간 15분)
