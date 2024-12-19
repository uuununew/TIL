# 근무 지옥에 빠진 푸앙이 (Small)
>해시

#### 📚 문제 설명
군대에 간 푸앙이는 4교대 근무를 서게 된다. 근무 시간대는 08:00~12:00, 12:00~18:00, 18:00~22:00, 22:00~08:00 으로 각각 4, 6, 4, 10시간의 근무로 구성되어 있다.

푸앙이와 동기들은 근무 시간이 최대한 공평하게 배분되기를 원한다. 그래서 근무표 전체에서 각 인원의 근무 시간이 12시간 이하로 차이 나게 해서 최대 50주 치 근무표를 짜려고 한다.

푸앙이는 원래 똑똑해서 이 정도는 한눈에 계산이 가능했지만 어째서인지 푸앙이는 계산이 불가능해졌다. 푸앙이를 위해서 대신 근무표가 공평한지 계산해주자.


#### 📌 제한 사항 
첫 번째 줄에 주의 개수인 
$N$이 입력된다. 
$(1 \leq N \leq 50)$ 

둘째 줄부터 근무표가 주어진다. 각 주는 4개의 줄로 표현되며, 그중 첫째 줄은 각 날의 08:00~12:00에 근무하는 사람의 이름 또는 '-', 둘째 줄은 12:00~18:00, 셋째 줄은 18:00~22:00, 넷째 줄은 22:00~08:00을 나타낸다. '-'는 근무자가 없음을 의미한다. 근무자의 이름은 모두 알파벳 소문자로 이루어져 있고 20글자를 넘지 않는다.

각 날에는 4개의 시간대에 모두 근무자가 있거나 모두 근무자가 없다. 예를 들어 12:00~18:00에만 근무자가 있는 날은 없다.

근무표에 적히지 않은 근무자는 없으며, 근무자 수는 최대 
$100$명이다.


#### 💻 입출력 예
![](https://velog.velcdn.com/images/uunew/post/3a0ec986-e8f9-474a-90e1-0168ba8bf211/image.png)


#### 🪄 힌트
첫 번째 예제에서 둘째 주 첫날 08:00~12:00 근무자는 puang, 12:00~18:00 근무자는 cony, 18:00~22:00 근무자는 choco, 22:00~08:00 근무자는 choco이다.

두 번째 예제에서 둘째 주 첫날 08:00~12:00 근무자는 pangyo, 12:00~18:00 근무자는 moon, 18:00~22:00 근무자는 moon, 22:00~08:00 근무자는 leonard이다.



---
### 📝 나의 풀이
```java
import java.io.*;
import java.util.*;

public class Main {
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

        int n = Integer.parseInt(br.readLine());

        Map<String, Integer> workTime = new HashMap<>();

        int[] shiftTimes = {4, 6, 4, 10};

        for (int week = 0; week < n; week++) {
            for (int day = 0; day < 7; day++) {
                for (int shift = 0; shift < 4; shift++) {
                    String line = br.readLine();

                    if (line == null || line.isEmpty()) {
                        continue;
                    }

                    StringTokenizer st = new StringTokenizer(line);
                    while (st.hasMoreTokens()) {
                        String worker = st.nextToken();
                        if (!worker.equals("-")) {
                            workTime.put(worker, workTime.getOrDefault(worker, 0) + shiftTimes[shift]);
                        }
                    }
                }
            }
        }

        if (workTime.isEmpty()) {
            System.out.println("Yes");
            return;
        }

        int maxTime = Collections.max(workTime.values());
        int minTime = Collections.min(workTime.values());

        if (maxTime - minTime <= 12) {
            System.out.println("Yes");
        } else {
            System.out.println("No");
        }
    }
}
```



### ✏️ 다른 사람의 풀이
```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.HashMap;
import java.util.StringTokenizer;

public class Main {
	public static void main(String[] args) throws IOException {
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		
		int n = Integer.parseInt(br.readLine());
		
		HashMap<String, Integer> map = new HashMap<>();
		
		int[] arr = {4, 6, 4, 10};
		while(n --> 0) {
			for(int i = 0; i < 4; i++) {
				StringTokenizer st = new StringTokenizer(br.readLine());
				for(int j = 0; j < 7; j++) {
					String s = st.nextToken();
					
					if(!s.equals("-")) {
						map.put(s, map.containsKey(s) ? map.get(s) + arr[i] : arr[i]);
					}
				}
			}
		}
		
		int min = Integer.MAX_VALUE, max = Integer.MIN_VALUE;
		for(String key : map.keySet()) {
			if(min > map.get(key)) {
				min = map.get(key);
			}
			
			if(max < map.get(key)) {
				max = map.get(key);
			}
		}
		
		System.out.print(max - min > 12 ? "No" : "Yes");
	}
}

```


---
### 💡 회고

문제 이해가 정말 오래 걸렸다,,
map 사용하는게 편리하다.

참고 : 
[출처]https://notes1615.tistory.com/entry/99%ED%81%B4%EB%9F%BD-%EC%BD%94%ED%85%8C-%EC%8A%A4%ED%84%B0%EB%94%94-8%EC%9D%BC%EC%B0%A8-TIL

#### 🔗 문제 링크
- 비기너: https://www.acmicpc.net/problem/25593
- 미들러: https://www.acmicpc.net/problem/2644
- 챌린저: https://www.acmicpc.net/problem/4485
