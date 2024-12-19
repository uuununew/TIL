# 단어 순서 뒤집기
>스택/큐

#### 📚 문제 설명
스페이스로 띄어쓰기 된 단어들의 리스트가 주어질때, 단어들을 반대 순서로 뒤집어라. 각 라인은 w개의 영단어로 이루어져 있으며, 총 L개의 알파벳을 가진다. 각 행은 알파벳과 스페이스로만 이루어져 있다. 단어 사이에는 하나의 스페이스만 들어간다.

#### 📌 제한 사항 
첫 행은 N이며, 전체 케이스의 개수이다.

N개의 케이스들이 이어지는데, 각 케이스는 스페이스로 띄어진 단어들이다. 스페이스는 라인의 처음과 끝에는 나타나지 않는다. N과 L은 다음 범위를 가진다.

N = 5
1 ≤ L ≤ 25


#### 💻 입출력 예
각 케이스에 대해서, 케이스 번호가 x일때  "Case #x: " 를 출력한 후 그 후에 이어서 단어들을 반대 순서로 출력한다.






---
### 📝 나의 풀이
```java
import java.io.*;
import java.util.*;
import java.util.stream.*;

public class Main{
    public static void main(String[] args) throws IOException{
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        int n = Integer.parseInt(br.readLine());
        List<String> list = new ArrayList<>();
        for(int i=0; i<n; i++){
            String[] arr = br.readLine().split(" ");
            String str = "";
            
            for(int j=arr.length - 1; j>=0; j--){
                str += arr[j];
                if(j != 0) {
                    str += " ";
                }
            }
            // 위 for문 -> stream사용
            // IntStream.range(0, arr.length)
            //     .map(j -> 0 + (arr.length - 1 - j))
            //     .forEach(j -> System.out.println(arr[j]))   
            
            String result = String.format("Case #%d: %s", i+1, str);
            System.out.println(result);
        }
    }
}
```

완벽하지는 않지만 stream을 살짝(?) 사용해보았다.

### ✏️ 다른 사람의 풀이
```java
import java.io.*;
import java.util.*;
import java.util.stream.*;

public class Main{
    public static void main(String[] args) throws IOException{
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        int n = Integer.parseInt(br.readLine());
        List<String> list = new ArrayList<>();
        for(int i=0; i<n; i++){
            String[] arr = br.readLine().split(" ");
    
            
            String str = IntStream.range(0, arr.length) //0부터 arr.length -1까지 순회(0,1,2,3)
                .map(j -> 0 + (arr.length - 1 - j))//0,1,2,3을 3,2,1,0으로 바꿔줌
                .mapToObj(j -> arr[j])//위 행에서 3이 j로 들어옴 -> arr[3]접근한 결과를 return
                .collect(Collectors.joining(" "));//return한 결과를 인자로 전달 -> 이거를 joining을 통해하나의 string으로 만듦(arr[3] arr[2] arr[1] arr[0]) 
                
                
            String result = String.format("Case #%d: %s", i+1, str);
            System.out.println(result);
        }
    }
}

```
stream으로 구현한 풀이에 내 나름대로 주석을 추가해보았다.

---
### 💡 회고

*** list를 스택처럼 사용하기  ***
- 스택은 LIFO(후입선출)이다.
- 그래서 index에 거꾸로 접근하여 스택과 동일하게 동작한다.

*** 새롭게 알게 된 사실***
- stream의 반환 형식은 최종연산이 결정한다.!

---
#### 🔗 문제 링크
- 비기너: https://www.acmicpc.net/problem/12605 (30분)
- 미들러: https://www.acmicpc.net/problem/27961  (1시간 15분)
- 챌린저: https://www.acmicpc.net/problem/30689 (1시간)
