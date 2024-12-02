# 숫자놀이
> 정렬

#### 📚 문제 설명
79를 영어로 읽되 숫자 단위로 하나씩 읽는다면 "seven nine"이 된다. 80은 마찬가지로 "eight zero"라고 읽는다. 79는 80보다 작지만, 영어로 숫자 하나씩 읽는다면 "eight zero"가 "seven nine"보다 사전순으로 먼저 온다.

문제는 정수 M, N(1 ≤ M ≤ N ≤ 99)이 주어지면 M 이상 N 이하의 정수를 숫자 하나씩 읽었을 때를 기준으로 사전순으로 정렬하여 출력하는 것이다.
 

#### 💻 입출력 예
첫째 줄에 M과 N이 주어진다.

M 이상 N 이하의 정수를 문제 조건에 맞게 정렬하여 한 줄에 10개씩 출력한다.

![](https://velog.velcdn.com/images/uunew/post/874d761d-ec37-4c01-9198-ccdcab2577c4/image.png)


---
### 📝 나의 풀이
```java
import java.io.*;
import java.util.*;

public class Main {

	public static void main(String[] args) throws Exception {
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		StringBuilder sb = new StringBuilder();
		StringTokenizer st = new StringTokenizer(br.readLine());
		
		int M = Integer.parseInt(st.nextToken());
		int N = Integer.parseInt(st.nextToken());
		
		int[] dic = {8,5,4,9,1,7,6,3,2,0};
		
		int cnt = 0;
		
		for(int i = 0; i<10; i++) {
			if(dic[i]>=M && dic[i]<=N) {
				sb.append(dic[i]).append(" ");
				
				if(++cnt%10 == 0) sb.append("\n");
			}

			if(dic[i]*10>=M-10) {
				for(int k = 0; k < 10; k++) {
					int num = dic[i]*10 + dic[k];
                    
					if(num < 10 || num<M || num>N) {
                        continue;
                    }
					sb.append(num).append(" ");
					if(++cnt%10 == 0) sb.append("\n");
				}
			}
		}
		System.out.println(sb);
	}
}

```


### ✏️ 다른 사람의 풀이
```java
import java.io.*;

public class Main {

	public static void main(String[] args) throws IOException {
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		String[] mn = br.readLine().split(" "); // 입력 mn
		int M = Integer.parseInt(mn[0]);
		int N = Integer.parseInt(mn[1]);
		
		int[] ztot = {8, 5, 4, 9, 1, 10, 7, 6, 3, 2}; // 1~10의 자리 순서
		int[] ttonn = {8, 5, 4, 9, 1, 7, 6, 3, 2, 0}; // 10~99의 일의 자리 순서
		
		int[] sort = new int[N-M+1]; // 결과 배열
		// 순서대로 숫자가 정렬되어 있는 배열
		int[] arr = new int[100];
		int x = 0;
		for(int i=0; i<10; i++) {
			if(ztot[i] == 10) continue;
			arr[x++] = ztot[i];
			for(int j=1; j<=10; j++) {
				arr[x++] = ztot[i]*10 + ttonn[j-1];
			}
		}		
		
		// 순서대로 정렬된 배열을 돌며 범위내의 숫자가 발견되면 결과배열에 넣어준다. 
		int k = 0;
		for(int i=0; i<arr.length; i++) {
			// 범위 내 -> 결과에 넣어줌
			if(arr[i]>=M && arr[i]<=N) {
				sort[k++] = arr[i];
			}
			if(k == N-M+1) break;
		}
		
		// 형식에 맞게 결과 출력 -> r이 k가 되면 sort를 전부 다 출력했으므로 종료
		int r = 0;
		while(r < k) {
			for(int i=0; i<10; i++) {
				if(r == k) break;
				System.out.print(sort[r++]+" ");
			}
			System.out.println();
		}
		
	}
}
```


---
#### 🔗 문제 링크
비기너: https://www.acmicpc.net/problem/1755 (45분)
미들러: https://www.acmicpc.net/problem/2631 (1시간 30분)
챌린저: https://www.acmicpc.net/problem/5972 (1시간 30분)