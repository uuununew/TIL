
# 센티와 마법의 뿅망치
>힙(Heap)

#### 📚 문제 설명
센티는 마법 도구들을 지니고 여행을 떠나는 것이 취미인 악당이다.

거인의 나라에 도착한 센티는 자신보다 키가 크거나 같은 거인들이 있다는 사실이 마음에 들지 않았다.

센티가 꺼내 들은 마법 도구는 바로 마법의 뿅망치로, 이 뿅망치에 맞은 사람의 키가 ⌊ 뿅망치에 맞은 사람의 키 / 2 ⌋로 변하는 마법 도구이다. 단, 키가 1인 경우 더 줄어들 수가 없어 뿅망치의 영향을 받지 않는다.

하지만 마법의 뿅망치는 횟수 제한이 있다. 그래서 센티는 마법의 뿅망치를 효율적으로 사용하기 위한 전략을 수립했다. 바로 매번 가장 키가 큰 거인 가운데 하나를 때리는 것이다.

과연 센티가 수립한 전략에 맞게 마법의 뿅망치를 이용한다면 거인의 나라의 모든 거인이 센티보다 키가 작도록 할 수 있을까?


#### 📌 제한 사항 
번째 줄에는 센티를 제외한 거인의 나라의 인구수 N (1 ≤ N ≤ 105)과 센티의 키를 나타내는 정수 Hcenti (1 ≤ Hcenti ≤ 2 × 109), 마법의 뿅망치의 횟수 제한 T (1 ≤ T ≤ 105)가 빈칸을 사이에 두고 주어진다. 

두 번째 줄부터 N개의 줄에 각 거인의 키를 나타내는 정수 H (1 ≤ H ≤ 2 × 109)가 주어진다.


#### 💻 입출력 예
마법의 뿅망치를 센티의 전략대로 이용하여 거인의 나라의 모든 거인이 센티보다 키가 작도록 할 수 있는 경우, 첫 번째 줄에 YES를 출력하고, 두 번째 줄에 마법의 뿅망치를 최소로 사용한 횟수를 출력한다.

마법의 뿅망치를 센티의 전략대로 남은 횟수 전부 이용하고도 거인의 나라에서 센티보다 키가 크거나 같은 거인이 있는 경우, 첫 번째 줄에 NO를 출력하고, 두 번째 줄에 마법의 뿅망치 사용 이후 거인의 나라에서 키가 가장 큰 거인의 키를 출력한다.

![](https://velog.velcdn.com/images/uunew/post/c60a9575-3bee-421e-a92b-da5048fc865c/image.png)






---
### 📝 나의 풀이
```java
import java.io.*;
import java.util.*; 
public class Main {	
    public static void main(String[] args) throws Exception{		
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));		
        StringTokenizer st = new StringTokenizer(br.readLine());
        int i, n=Integer.parseInt(st.nextToken());
        int h=Integer.parseInt(st.nextToken());
        int t=Integer.parseInt(st.nextToken());		
        PriorityQueue<Integer> queue = new PriorityQueue<Integer>(Collections.reverseOrder());	
        for(i=0;i<n;i++){
            queue.add(Integer.parseInt(br.readLine()));
        }					
        for(i=0;i<t;i++){						
            if(queue.peek()<h){
                break;
            }else if(queue.peek()>1){
               queue.add(queue.poll()/2); 
            }				
            
        }		
        if(queue.peek()>=h){
            System.out.println("NO\n"+queue.peek());
        }else{
            System.out.println("YES\n"+i);
        }		
    }
}


```


### ✏️ 다른 사람의 풀이
```java
import java.io.IOException;
import java.util.Comparator;
import java.util.PriorityQueue;

class Main {
    public static void main(String[] args) throws IOException {
        int n = read();
        int h = read();
        int t = read();

        PriorityQueue<Integer> pq = new PriorityQueue<>(Comparator.reverseOrder());
        while (n-- > 0) {
            pq.add(read());
        }

        int cnt = 0;
        while (cnt < t && pq.peek() >= h) {
            int x = pq.poll();
            if (x > 1) {
                pq.add(x / 2);
            } else {
                pq.add(x);
            }
            cnt++;
        }

        StringBuilder sb = new StringBuilder();
        if (cnt == t && pq.peek() >= h) {
            sb.append("NO").append('\n').append(pq.peek());
        } else {
            sb.append("YES").append('\n').append(cnt);
        }
        System.out.println(sb);
    }
    
    public static int read() throws IOException {
        int c, n = System.in.read() & 15;
        while ((c = System.in.read()) > 32) {
            n = (n << 3) + (n << 1) + (c & 15);
        }
        return n;
    }
}
```

---
### 💡 회고
여러번 풀다 보니 이제는 감이 조금 더 오는 것 같기도,,?

*** 힙(Heap) ***
: 완전 이진트리 형태로 최대, 최솟값을 빠르게 찾아내는데 유용한 자료구조


---
#### 🔗 문제 링크
비기너: https://www.acmicpc.net/problem/19638 (30분)
미들러: https://school.programmers.co.kr/learn/courses/30/lessons/42842 (1시간 15분)
챌린저: https://www.acmicpc.net/problem/17182 (1시간 30분)
