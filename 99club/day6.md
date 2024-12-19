# 할리갈리
> 해시

#### 📚 문제 설명
《할리갈리》는 단추가 달린 종 하나와 과일이 그려진 카드들로 구성된 보드게임입니다.

카드에는 총 $4$종류의 과일이 최대 $5$개까지 그려져 있습니다. 그려진 과일의 종류는 딸기, 바나나, 라임, 그리고 자두입니다. 그려진 과일의 종류는 딸기, 바나나, 라임, 그리고 자두입니다.

게임을 시작할 때 플레이어들은 카드 뭉치를 공평하게 나눠가지며 자신이 가진 카드를 전부 소모하면 패배합니다.

게임은 시작 플레이어가 본인의 카드 뭉치에서 카드 한 장을 공개하는 것으로 시작합니다. 이후 반시계 방향으로 돌아가며 본인의 카드를 한 장씩 공개합니다.

펼쳐진 카드들 중 한 종류 이상의 과일이 정확히 
$5$개 있는 경우 종을 눌러야 하며 가장 먼저 종을 누른 플레이어가 모든 카드를 모아 자신의 카드 뭉치 아래에 놓습니다. 종을 잘못 누른 경우 다른 모든 플레이어에게 카드를 한 장씩 나누어줘야 합니다.

《할리갈리》를 처음 해보는 한별이는 할리갈리 고수인 히나에게 이기기 위해 여러분에게 도움을 청했습니다. 한별이를 도와 펼쳐진 카드들의 목록이 주어졌을 때, 한별이가 종을 쳐야 하는지 알려주세요.

첫 번째 줄에 펼쳐진 카드의 개수 
$N$이 주어집니다.

두 번째 줄부터 
$N$개의 줄에 걸쳐 한 줄에 하나씩 펼쳐진 카드의 정보가 주어집니다.

카드의 정보는 공백으로 구분된, 과일의 종류를 나타내는 문자열 
$S$와 과일의 개수를 나타내는 양의 정수 
$X$로 이루어져 있습니다.

 
$S$는 STRAWBERRY, BANANA, LIME, PLUM 중 하나입니다.

한별이가 종을 쳐야 하면 YES을, 아니면 NO를 출력해주세요.



#### 📌 제한 사항 
$1 \le N \le 100\,000$ 
 
$1 \le X \le 5$ 
입력으로 주어지는 모든 수는 정수입니다.


#### 💻 입출력 예
![](https://velog.velcdn.com/images/uunew/post/e989fa82-208e-4e39-ae87-927e458d6cc3/image.png)


---
### 📝 나의 풀이
```java
import java.util.*;
import java.io.*;
import java.util.StringTokenizer;


public class Main {
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        int n = Integer.parseInt(br.readLine());
        Map<String, Integer> map = new HashMap<>();
        for(int i=0; i<n; i++){
            String[] arr = br.readLine().split(" ");
            String fruit = arr[0];
            int num = Integer.parseInt(arr[1]);
            
            if(map.containsKey(fruit)){
                int a = map.get(fruit) + num;
                map.put(fruit, a);
            }else{
                map.put(fruit, num);
            }          
        }
        
        if(map.containsKey("STRAWBERRY") && map.get("STRAWBERRY")==5 
           || map.containsKey("BANANA") && map.get("BANANA")==5 
           || map.containsKey("LIME") && map.get("LIME")==5
           || map.containsKey("PLUM") && map.get("PLUM")==5){
            System.out.println("YES");
        }else{
            System.out.println("NO");
        }
        br.close();
    }
}
```

### ✏️ 다른 사람의 풀이
```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.HashMap;
import java.util.Map;
import java.util.StringTokenizer;

public class Main {

	public static void main(String[] args) throws IOException {
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		StringTokenizer st;
		
		int N = toInt(br.readLine());
		Map<String, Integer> map = new HashMap<>();
		for (int n = 0; n < N; n++) {
			st = new StringTokenizer(br.readLine());
			String S = st.nextToken();
			int X = toInt(st.nextToken());
			if (map.containsKey(S)) {
				map.put(S, map.get(S) + X);
			} else {
				map.put(S, X);
			}
		}
		String ans = "NO";
		if (map.containsValue(5)) ans = "YES";
		System.out.println(ans);
		
		br.close();
	}
	
	static int toInt(String string) {
		return Integer.parseInt(string);
	}

}


```
map.containsValue()가 있다는 사실을 처음 알았다. 

---
### 💡 회고
처음에 키값이 없는 경우를 생각을 하지 못하여서 null pointer 에러가 계속 났다. 그래서 키값을 검사하는 코드를 넣어줬다. 
다음에는 로직을 조금 더 잘 고민해봐야겠다. 그리고 다음엔 getOrDefault()메서드로 리팩토링 해봐야지,,!


- [ ] getOrDefault() 메서드로 리팩토링 해보기

#### 🔗 문제 링크
- 비기너: https://www.acmicpc.net/problem/27160
- 미들러: https://www.acmicpc.net/problem/2805
- 챌린저: https://www.acmicpc.net/problem/2458
