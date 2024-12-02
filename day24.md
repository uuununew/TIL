# 국회의원 선거
>힙(Heap)

#### 📚 문제 설명
다솜이는 사람의 마음을 읽을 수 있는 기계를 가지고 있다. 다솜이는 이 기계를 이용해서 2008년 4월 9일 국회의원 선거를 조작하려고 한다.

다솜이의 기계는 각 사람들이 누구를 찍을 지 미리 읽을 수 있다. 어떤 사람이 누구를 찍을 지 정했으면, 반드시 선거때 그 사람을 찍는다.

현재 형택구에 나온 국회의원 후보는 N명이다. 다솜이는 이 기계를 이용해서 그 마을의 주민 M명의 마음을 모두 읽었다.

다솜이는 기호 1번이다. 다솜이는 사람들의 마음을 읽어서 자신을 찍지 않으려는 사람을 돈으로 매수해서 국회의원에 당선이 되게 하려고 한다. 다른 모든 사람의 득표수 보다 많은 득표수를 가질 때, 그 사람이 국회의원에 당선된다.

예를 들어서, 마음을 읽은 결과 기호 1번이 5표, 기호 2번이 7표, 기호 3번이 7표 라고 한다면, 다솜이는 2번 후보를 찍으려고 하던 사람 1명과, 3번 후보를 찍으려고 하던 사람 1명을 돈으로 매수하면, 국회의원에 당선이 된다.

돈으로 매수한 사람은 반드시 다솜이를 찍는다고 가정한다.

다솜이가 매수해야하는 사람의 최솟값을 출력하는 프로그램을 작성하시오.


#### 📌 제한 사항 
첫째 줄에 후보의 수 N이 주어진다. 둘째 줄부터 차례대로 기호 1번을 찍으려고 하는 사람의 수, 기호 2번을 찍으려고 하는 수, 이렇게 총 N개의 줄에 걸쳐 입력이 들어온다. N은 50보다 작거나 같은 자연수이고, 득표수는 100보다 작거나 같은 자연수이다.


#### 💻 입출력 예
첫째 줄에 다솜이가 매수해야 하는 사람의 최솟값을 출력한다.
![](https://velog.velcdn.com/images/uunew/post/5985dd72-11c5-4339-b55a-773bf9400571/image.png)
국회의원 선거





---
### 📝 나의 풀이
```java
import java.io.*;
import java.util.*;

public class Main {
    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        int n = Integer.parseInt(br.readLine());
        if (n == 1) {
            System.out.println(0);
            return;
        }
        int a = Integer.parseInt(br.readLine());
        int[] arr = new int[n-1];
        for (int i = 0; i < n-1; i++) arr[i] = Integer.parseInt(br.readLine());
        int cnt = 0;
        while (true) {
            Arrays.sort(arr);
            if (arr[n-2] < a) break;
            cnt++;
            arr[n-2]--;
            a++;
        }
        System.out.println(cnt);
    }

}

```
다솜이가 처음 얻은 득표수에 나머지 득표수들을 -시키면서 다솜이의 득표수를 +할 때 나머지 득표수 중 가장 큰 득표수보다 다솜이의 득표수보다 커지면 된다.

### ✏️ 다른 사람의 풀이
```java
import java.util.*;
import java.io.*;

class Main {
	public static void main(String[] args) throws Exception {
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

		// 입력 및 pq 삽입
		int N = Integer.parseInt(br.readLine()) - 1;
		int dasom = Integer.parseInt(br.readLine());
		PriorityQueue<Integer> pq = new PriorityQueue<>(Collections.reverseOrder());
		for (int i = 0; i < N; i++) {
			pq.add(Integer.parseInt(br.readLine()));
		}

		int count = 0;
		while (!pq.isEmpty() && pq.peek() >= dasom) {		
			++dasom;
			pq.add(pq.poll() - 1);
			++count;
		}

		System.out.println(count);
	}
}
```
다솜이를 제외한 모든 후보들의 득표수를 MaxHeap(PriorityQueue)에 넣고 heap에서 값을 꺼낸 후 다솜이의 득표 수와 비교하는 방식이다.

---
### 💡 회고

*** 그리디(탐욕법, Greedy) ***
: 최적의 값을 구해야 하는 상황에서 사용되는 근시안적인 방법론
: 각 단계에서 최적이라고 생각되는 것을 선택해 나가는 방식으로 진행하여 최종적인 해답에 도달하는 알고리즘

- 탐욕 선택 속성(Greedy Choice Property)
: 이전의 선택이 이후에 영향을 주지 않음을 의미

- 최적 부분 구조(Optimal Substructure)
: 부분 문제의 최적결과가 전체에도 그대로 적용될 수 있어야 함




---
#### 🔗 문제 링크
비기너: https://www.acmicpc.net/problem/1417 (30분)
미들러: https://school.programmers.co.kr/learn/courses/30/lessons/86971 (1시간 15분)
챌린저: https://www.acmicpc.net/problem/2437 (1시간 15분)