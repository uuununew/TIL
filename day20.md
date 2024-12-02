# N번째 큰 수
>힙(Heap)

#### 📚 문제 설명
![](https://velog.velcdn.com/images/uunew/post/ea69447d-2d0e-4e50-a1bb-f089b6206dca/image.png)


#### 📌 제한 사항 
첫째 줄에 N(1 ≤ N ≤ 1,500)이 주어진다. 다음 N개의 줄에는 각 줄마다 N개의 수가 주어진다. 표에 적힌 수는 -10억보다 크거나 같고, 10억보다 작거나 같은 정수이다.


#### 💻 입출력 예
첫째 줄에 N번째 큰 수를 출력한다.
![](https://velog.velcdn.com/images/uunew/post/3117e2b4-68ac-453e-bd4b-0824908c5a0f/image.png)





---
### 📝 나의 풀이
```java
import java.io.*;
import java.util.*;

public class Main {
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        PriorityQueue<Integer> queue = new PriorityQueue<>((o1, o2) -> o2-o1);
        int N = Integer.parseInt(br.readLine());
        for(int i=0; i<N;i++){
            StringTokenizer st = new StringTokenizer(br.readLine());
            for(int j=0;j<N;j++){
                queue.add(Integer.valueOf(st.nextToken()));
            }
        }
        for(int i=0; i<N-1;i++){
            queue.poll();
        }
        System.out.println(queue.poll());

    }
}

```
큐를 큰 순서대로 정렬시키고 N-1번을 poll 시킨 후 println에 poll()를 넣는다.

### ✏️ 다른 사람의 풀이
```java
import java.util.*;
import java.io.*;
 
class Main {
    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer st;
 
        int n = Integer.parseInt(br.readLine());
        int[] arr = new int[n*n];
        int idx =0;
 
        for(int i=0; i<n; i++) {
            st = new StringTokenizer(br.readLine());
            for(int j=0; j<n; j++) {
                arr[idx++] = Integer.parseInt(st.nextToken());
            }
        }
 
        Arrays.sort(arr);
 
        System.out.println(arr[n*n - n]);
    }
}
```
N*N 크기의 배열을 만들어서 수를 넣고 정렬한 풀이

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
비기너: https://www.acmicpc.net/problem/2075 (30분)
미들러: https://school.programmers.co.kr/learn/courses/30/lessons/42840 (1시간 15분)
챌린저: https://www.acmicpc.net/problem/1083 (1시간)