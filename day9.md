# 민균이의 비밀번호
>해시

#### 📚 문제 설명
창영이는 민균이의 컴퓨터를 해킹해 텍스트 파일 하나를 자신의 메일로 전송했다. 파일에는 단어가 한 줄에 하나씩 적혀있었고, 이 중 하나는 민균이가 온라인 저지에서 사용하는 비밀번호이다.

파일을 살펴보던 창영이는 모든 단어의 길이가 홀수라는 사실을 알아내었다. 그리고 언젠가 민균이가 이 목록에 대해서 얘기했던 것을 생각해냈다. 민균이의 비밀번호는 목록에 포함되어 있으며, 비밀번호를 뒤집어서 쓴 문자열도 포함되어 있다.

예를 들어, 민균이의 비밀번호가 "tulipan"인 경우에 목록에는 "napilut"도 존재해야 한다. 알 수 없는 이유에 의해 모두 비밀번호로 사용 가능하다고 한다.

민균이의 파일에 적혀있는 단어가 모두 주어졌을 때, 비밀번호의 길이와 가운데 글자를 출력하는 프로그램을 작성하시오.


#### 📌 제한 사항 
첫째 줄에 단어의 수 N (2 ≤ N ≤ 100)이 주어진다. 다음 N개 줄에는 파일에 적혀있는 단어가 한 줄에 하나씩 주어진다. 단어는 알파벳 소문자로만 이루어져 있으며, 길이는 2보다 크고 14보다 작은 홀수이다.


#### 💻 입출력 예
첫째 줄에 비밀번호의 길이와 가운데 글자를 출력한다. 항상 답이 유일한 경우만 입력으로 주어진다.
![](https://velog.velcdn.com/images/uunew/post/e0dcb4ee-836f-4972-ae24-fe6973e2cd3f/image.png)





---
### 📝 나의 풀이
```java
import java.io.*;
import java.util.*;

public class Main{
    public static void main(String[] args) throws IOException{
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        int n = Integer.parseInt(br.readLine());
        Set<String> set = new HashSet<>();
        
        for(int i=0; i<n; i++){
            String pw = br.readLine();
            set.add(pw);
            
            StringBuilder sb = new StringBuilder(pw);
            String reverse = sb.reverse().toString(); //단어 뒤집기
            
            if(set.contains(reverse)){
                System.out.println(reverse.length() + " " + reverse.charAt(reverse.length() / 2));
                return;         
            }
        }
        br.close();
    }
}
```
HashSet과 reverse()를 이용해 문제를 풀었다. 


### ✏️ 다른 사람의 풀이
```java
import java.util.*;

public class Main{
	public static void main(String[] args) {
		Scanner scanner = new Scanner(System.in);
		int N = scanner.nextInt();
		ArrayList<String> list = new ArrayList<String>();
		
		for(int i=0; i<N; i++) {
			String s = scanner.next();
			String rs = new StringBuffer(s).reverse().toString();
			
			// 입력받은 문자를 뒤집은 문자(rs)가 이미 리스트에 존재하면, 정답
			if(list.contains(rs) || s.equals(rs)) {
				System.out.println(s.length() + " " + s.charAt(s.length()/2));
				return;
			} else {
				list.add(s);
			}
		}
	}
}

```
List를 이용한 풀이

---
### 💡 회고

HashSet 
- 객체를 중복해서 저장할 수 없으며, 하나의 null 값만 저장할 수 있다.
- 중복을 자동으로 제거해준다.