# 세준세비
> 정렬

#### 📚 문제 설명
세준이와 세비는 온라인 게임을 즐겨한다. 이 온라인 게임에서는 군대를 서로 키울 수 있다. 세준이는 N명의 병사를 키웠고, 세비는 M명의 병사를 키웠다.

이제 서로 전쟁을 하려고 한다.

전쟁은 여러 번의 전투로 이루어진다. 각 전투에서 살아있는 병사중 제일 약한 병사가 죽는다. 만약 제일 약한 병사가 여러 명이고, 제일 약한 병사가 모두 같은 편에 있다면, 그 중에 한 명이 임의로 선택되어 죽는다. 하지만, 제일 약한 병사가 여러 명이고, 양 편에 모두 있다면, 세비의 제일 약한 병사 중 한 명이 임의로 선택되어 죽는다.

전쟁은 한 명의 병사를 제외하고 모두 죽었을 때 끝난다. 전쟁의 승자를 출력하는 프로그램을 작성하시오.

#### 📌 제한 사항 
1 ≤ N, M ≤ 1,000,000
병사들의 힘은 300,000,000보다 작거나 같은 자연수이다. 

#### 💻 입출력 예
첫째 줄에 테스트 케이스의 개수 T가 주어진다. T는 100보다 작거나 같다. 각 테스트 케이스는 다음과 같이 이루어져 있다. 첫째 줄에 N과 M이 들어오고, 둘째 줄에는 세준이의 병사들의 힘이 들어오고, 셋째 줄에는 세비의 병사들의 힘이 들어온다. 힘은 정수이고, 이 값이 클수록 강하고, 작을수록 약하다.

각 테스트 케이스는 줄 바꿈으로 구분되어 있다.


각 테스트 케이스에 대해서 한 줄에 하나씩 차례대로 승자를 출력한다. 세준이가 이기면 S를 세비가 이기면 B를 둘다 아닐 경우에는 C를 출력한다.
![](https://velog.velcdn.com/images/uunew/post/8df35771-2ad2-42cc-b228-30ce35b22ebe/image.png)


---
### 📝 나의 풀이
```java
import java.util.*;
import java.io.*;

public class Main {
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

        int t = Integer.parseInt(br.readLine());
        for (int i = 0; i < t; i++) {
            br.readLine();
            StringTokenizer st = new StringTokenizer(br.readLine());
            int n = Integer.parseInt(st.nextToken());
            int m = Integer.parseInt(st.nextToken());

            int max_sj = 0, max_sb = 0;

            st = new StringTokenizer(br.readLine());
            for (int j = 0; j < n; j++) {
                int sejun = Integer.parseInt(st.nextToken());
                if (max_sj < sejun) max_sj = sejun;
            }

            st = new StringTokenizer(br.readLine());
            for (int j = 0; j < m; j++) {
                int sebi = Integer.parseInt(st.nextToken());
                if (max_sb < sebi) max_sb = sebi;
            }

            if (max_sj >= max_sb) {
                System.out.println("S");
            } else {
                System.out.println("B");
            }
        }
    }
}

```


### ✏️ 다른 사람의 풀이
```java
import java.util.*;
import java.io.*;

class Main{		
  public static void main(String[] args) throws IOException{
     BufferedReader br= new BufferedReader(new InputStreamReader(System.in));
     int T = Integer.parseInt(br.readLine());
     char[] answer = new char[T];
     
     for(int i=0;i<T;i++) {
    	 //문제의 공백 처리 blank
    	 String blank = br.readLine();
    	 StringTokenizer st = new StringTokenizer(br.readLine()," ");
    	 int sj = Integer.parseInt(st.nextToken());
    	 int sb = Integer.parseInt(st.nextToken());
    
    	 
    	 int max_sb =-1;
    	 int max_sj =-1;
    	 st = new StringTokenizer(br.readLine()," ");
    	 for(int j=0;j<sj;j++) {
    		 int power = Integer.parseInt(st.nextToken());
    		 if(max_sj<power) max_sj = power;
    		 
    	 }
    	 st = new StringTokenizer(br.readLine()," ");
    	 for(int j=0;j<sb;j++) {
    		 int power = Integer.parseInt(st.nextToken());
    		 if(max_sb<power) max_sb = power;
    		 
    	 }
    	 if(max_sj>=max_sb) answer[i]='S';
    	 else answer[i]='B';
    	 
    	 
     }
     for(int i=0;i<T;i++) {
    	 System.out.println(answer[i]);
     }
     
  }
}
```



---
#### 🔗 문제 링크
비기너: https://www.acmicpc.net/problem/1524 (30분)
미들러: https://www.acmicpc.net/problem/1965 (1시간 15분)
챌린저: https://school.programmers.co.kr/learn/courses/30/lessons/150369 (1시간 30분)