# 모스 부호
> 문자열

#### 📚 문제 설명
혜민이는 요즘 모스 부호에 관심이 많아졌다. 모스 부호는 짧은 신호와 긴 신호를 적절히 조합하여 문자 기호를 표기하는 방식이다. 각 문자를 나타내는 방식은 미리 정해져 있는데, 예를 들어, 짧은 신호를 '.', 긴 신호를 '-'로 나타낸다면, 모스 부호로 알파벳 'A'는 '.-', 숫자 1은 '.----'와 같이 표기할 수 있다. 모스 부호를 알고 있으면 위험한 상황에서 구조 요청을 하는 데 유용할 것 같아, 혜민이는 평상시에 친구들과 연락을 주고받을 때도 모스 부호를 사용하려고 한다. 혜민이는 친구들이 보내온 모스 부호를 올바르게 해독했는지 바로바로 확인하고 싶어졌다. 알파벳 A-Z, 숫자 0-9, 기호 ',', '.', '?', ':', '-', '@'로 이루어진 길이 
$N$인 문자열을 변환한 모스 부호가 주어질 때, 주어진 모스 부호를 해독하여 원래의 문자열을 출력하는 프로그램을 작성해 보자.

각 문자를 모스 부호로 나타내는 방법은 아래 표에 정리되어 있다. (단, 표의 둘째, 넷째 열은 첫째, 셋째 열의 문자를 모스 부호로 변환한 결과를 나타내며, '.'는 짧은 신호를, '-'는 긴 신호를 의미한다.)

![](https://velog.velcdn.com/images/uunew/post/87c6b29d-7280-4876-899f-01a38cc0f1e1/image.png)



#### 📌 제한 사항 
첫째 줄에 모스 부호로 변환하기 전 문자열의 길이를 나타내는 정수 
$N(1 \leq N \leq 100)$이 주어진다.

둘째 줄에 원래의 문자열을 모스 부호로 변환한 메시지가 주어진다. 이 메시지에서 짧은 신호는 '.', 긴 신호는 '-'로 나타내며, 원래의 문자열을 구성하는 각각의 문자를 모스 부호로 변환한 결과는 공백으로 구분되어 있다.

위 표를 이용해 해독할 수 없는 메시지는 주어지지 않는다.

주어진 모스 부호를 해독하여 길이 
$N$인 문자열을 공백 없이 출력한다.

알파벳의 경우, 반드시 대문자로 출력한다.


#### 💻 입출력 예
![](https://velog.velcdn.com/images/uunew/post/12e5a699-bdd9-4b5d-8749-3b6a394289a8/image.png)


---
### 📝 나의 풀이
```java
import java.io.*;
import java.io.IOException;
import java.util.HashMap;

public class Main {
    public static void main(String[] args) throws IOException {

        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));

        int a = Integer.parseInt(br.readLine());
        String input = br.readLine();
        String[] arr = input.split(" ");

        HashMap<String, String > map = new HashMap<>();
        map.put(".-", "A");
        map.put("-...", "B");
        map.put("-.-.", "C");
        map.put("-..", "D");
        map.put(".", "E");
        map.put("..-.", "F");
        map.put("--.", "G");
        map.put("....", "H");
        map.put("..", "I");
        map.put(".---", "J");
        map.put("-.-", "K");
        map.put(".-..", "L");
        map.put("--", "M");
        map.put("-.", "N");
        map.put("---", "O");
        map.put(".--.", "P");
        map.put("--.-", "Q");
        map.put(".-.", "R");
        map.put("...", "S");
        map.put("-", "T");
        map.put("..-", "U");
        map.put("...-", "V");
        map.put(".--", "W");
        map.put("-..-", "X");
        map.put("-.--", "Y");
        map.put("--..", "Z");
        map.put(".----", "1");
        map.put("..---", "2");
        map.put("...--", "3");
        map.put("....-", "4");
        map.put(".....", "5");
        map.put("-....", "6");
        map.put("--...", "7");
        map.put("---..", "8");
        map.put("----.", "9");
        map.put("-----", "0");
        map.put("--..--", ",");
        map.put(".-.-.-", ".");
        map.put("..--..", "?");
        map.put("---...", ":");
        map.put("-....-", "-");
        map.put(".--.-.", "@");

        StringBuilder sb = new StringBuilder();

        for(String str : arr){
            sb.append(map.get(str));
        }

        bw.write(sb.toString());

        bw.flush();
        bw.close();
        br.close();
    }
}
```
귀찮지만,, 하나하나 map에 담아줬다. 
그리고 속도를 위해 print문 대신 BufferedWriter를 사용했다.


### ✏️ 다른 사람의 풀이
```java
import java.io.*;
import java.util.StringTokenizer;

public class Main {
	public static void main(String[] args) throws IOException{
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));
		String [] arrM = {".-","-...","-.-.","-..",".","..-.","--.","....","..",".---","-.-",".-..","--","-.","---",".--.","--.-",".-.","...","-","..-","...-",".--","-..-","-.--","--..",".----","..---","...--","....-",".....","-....","--...","---..","----.","-----","--..--",".-.-.-","..--..","---...","-....-",".--.-."};
		String [] arrC = {"A","B","C","D","E","F","G","H","I","J","K","L","M","N","O","P","Q","R","S","T","U","V","W","X","Y","Z","1","2","3","4","5","6","7","8","9","0",",",".","?",":","-","@"};
		
		int n = Integer.parseInt(br.readLine());
		StringTokenizer st = new StringTokenizer(br.readLine()," ");
		for(int i=0;i<n;i++) {
			String s = st.nextToken();
			for(int j=0;j<42;j++) {
				if(s.equals(arrM[j])) {
					bw.write(arrC[j]);
					break;
				}
			}
		}
		bw.flush();
	}
}

```
배열에 담는 방법도 있다.

---
### 💡 회고

제법 귀찮은 문제였다.!

#### 🔗 문제 링크
- 비기너: https://www.acmicpc.net/problem/29701
- 미들러: https://www.acmicpc.net/problem/24444
- 챌린저: https://www.acmicpc.net/problem/2457
