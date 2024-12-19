# 식당 입구 대기 줄
>스택/큐

#### 📚 문제 설명
여러 명의 학생이 식사하기 위하여 학교 식당을 향해 달려가고 있다. 학교 식당에 도착한 학생은 식당 입구에 줄을 서서 대기한다. 학교 식당에 먼저 도착한 학생이 나중에 도착한 학생보다 식당 입구의 앞쪽에서 대기한다. 식사는 1인분씩 준비된다. 식사 1인분이 준비되면 식당 입구의 맨 앞에서 대기 중인 학생 1명이 식당으로 들어가서 식사를 시작한다. 식사를 시작한 학생은 항상 식사를 마친다.

학생이 학교 식당에 도착하고 식사가 준비되는 n개의 정보가 저장된 A가 주어진다. A에 저장된 첫 번째 정보부터 n번째 정보까지 순서대로 처리한 다음, 식당 입구에 줄을 서서 대기하는 학생 수가 최대가 되었던 순간의 학생 수와 이때 식당 입구의 맨 뒤에 대기 중인 학생의 번호를 출력하자. 대기하는 학생 수가 최대인 경우가 여러 번이라면 맨 뒤에 줄 서 있는 학생의 번호가 가장 작은 경우를 출력하자.

A에 저장된 n개의 정보는 아래 두 가지 유형으로 구분된다. 첫 번째가 유형 1, 두 번째가 유형 2이다.

1 a: 학생 번호가 양의 정수 a인 학생 1명이 학교 식당에 도착하여 식당 입구의 맨 뒤에 줄을 서기 시작한다.
2: 식사 1인분이 준비되어 식당 입구의 맨 앞에서 대기 중인 학생 1명이 식사를 시작한다.
식사 1인분이 준비될 때는 식당 입구에서 대기 중인 학생이 항상 존재한다. 식당 입구에 줄을 서서 대기하였으나 식사가 준비 안 된 학생은 식사를 못 한다.

#### 📌 제한 사항 
1 ≤ n ≤ 100,000
A에는 유형 1, 유형 2만 저장되어 있다.
1 ≤ a ≤ n, 모든 양의 정수 a의 값은 서로 다르다.


#### 💻 입출력 예
첫 번째 줄에 n이 주어진다.
다음 줄부터 n개의 줄에 걸쳐 한 줄에 하나의 정보가 주어진다. 주어지는 정보는 유형 1, 2중 하나이다.

첫 번째 정보부터 n번째 정보까지 순서대로 처리한 다음, 식당 입구에 줄을 서서 대기하는 학생 수가 최대가 되었던 순간의 학생 수와 이때 식당 입구의 맨 뒤에 대기 중인 학생의 번호를 빈칸을 사이에 두고 순서대로 출력한다. 
대기하는 학생 수가 최대인 경우가 여러 번이라면 맨 뒤에 줄 서 있는 학생의 번호가 가장 작은 경우를 출력한다.
![](https://velog.velcdn.com/images/uunew/post/04a7ef6a-a41e-49f8-83ed-2ba71f354e78/image.png)



---
### 📝 나의 풀이
```java
import java.io.*;
import java.util.*;

public class Main {
  public static void main(String[] args) throws Exception {
    BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
    BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));
    StringTokenizer st;

	int n = Integer.parseInt(br.readLine());
    Queue<Integer> queue = new LinkedList<>();
    StringBuilder sb = new StringBuilder();
    
    int count = 0;
    // 제일 작은 학생번호
    int num = Integer.MAX_VALUE;

		for(int i = 0;i<n;i++){
            st = new StringTokenizer(br.readLine());
            int type = Integer.parseInt(st.nextToken());

            if(type == 1){
                // 추가된 학생번호
                int studentNumber = Integer.parseInt(st.nextToken());
                queue.offer(studentNumber);

                if(queue.size() >= count) {
                    if(queue.size() == count){
                         if(num > studentNumber){
                             num = studentNumber;
                         }
                    }else {
                        count = queue.size();
                        num = studentNumber;
                    }
                }
            }else {
                queue.poll();
            }

        }
        br.close();
        bw.write(count+" "+num);
        bw.close();
  }
}
```


### ✏️ 다른 사람의 풀이
```java
import java.io.*;
import java.util.*;
import static java.lang.Integer.parseInt;

public class Main {
    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));

        StringTokenizer st = new StringTokenizer(br.readLine());
        int n = parseInt(st.nextToken());

        Deque<Integer> que = new LinkedList<>();
        int minStudent = Integer.MAX_VALUE;
        int maxSize = Integer.MIN_VALUE;
        for (int i = 0; i < n; i++) {
            st = new StringTokenizer(br.readLine());

            int operator = parseInt(st.nextToken());

            if (operator == 1) {
                que.offer(parseInt(st.nextToken()));
                if (que.size() > maxSize) {
                    maxSize = que.size();
                    minStudent = que.peekLast();
                } else if (que.size() == maxSize) {
                    minStudent = Math.min(minStudent, que.peekLast());
                }
            }

            if (operator == 2) {
                que.poll();
            }
        }

        bw.write(maxSize + " " + minStudent);
        bw.flush();
        bw.close();
        br.close();
    }
}
```
Deque를 사용한 풀이


---
### 💡 회고

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
비기너: https://www.acmicpc.net/problem/26042 (45분)
미들러: https://www.acmicpc.net/problem/2212 (1시간 30분)
챌린저: https://school.programmers.co.kr/learn/courses/30/lessons/214288 (1시간 30분)
