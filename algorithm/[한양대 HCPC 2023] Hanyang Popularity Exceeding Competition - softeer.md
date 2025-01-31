> Lv.3

#### 📚 문제 설명
한양대학교는 2023년부터 Hanyang Popularity Exceeding Competition을 열게 되었다. 이 대회는 일정 기간 진행되며, 대회가 끝나는 시점에 인기도가 가장 높은 학생이 우승한다. 철민이는 Hanyang Popularity Exceeding Competition의 참가자이지만, 이제 막 학교에 다니기 시작한 철민이는 인기도가 0밖에 되지 않는다.

철민이는 한양대학교 내의 유명인 N명과 만난다는 우승 계획을 세웠다. 이를 위해 철민이는 1번 유명인부터 N번 유명인까지 차례대로 만날 계획을 세웠다.

하지만 현실은 생각보다 복잡해서, 유명인들과 만난다고 항상 인기도가 올라가지는 않는다. 한쪽의 유명도가 다른 한쪽에 비해 너무 높으면 한쪽의 인기에 다른 쪽이 묻혀버리기 때문이다. 엄밀히 말해서, 철민이의 현재 인기도를 X라고 하고, i번 유명인의 인기도를 Pi​, 친화력을 Ci​라고 하자. 이때, ∣Pi​−X≤Ci​∣여야 철민이의 인기도가 1 올라간다. ∣Pi​−X>Ci​∣라면 철민이의 인기도는 변하지 않는다.

그래서 철민이는 모든 유명인을 다 만나는 대신, 일부 유명인만을 골라 만나서 인기도를 최대화하려고 한다. 이때, 철민이가 도달할 수 있는 최대 인기도는 얼마일까?

유명인들은 바쁜 삶을 보내기 때문에, 유명인과 만나는 시간을 변경할 수는 없다. 즉, 번호가 더 높은 유명인을 먼저 만나도록 계획을 변경할 수는 없다.

#### 📌 제한사항
1≤N≤200000

1≤Pi​,Ci​≤500


#### 💻 입출력 예

- 입력

첫 번째 줄에 한양대학교의 유명인들의 수 N이 주어진다.

다음 N개의 줄의 i번째 줄에는 i번 유명인의 인기도와 친화력을 의미하는 두 정수 Pi​,Ci​ 가 공백으로 구분되어 주어진다.

- 출력

첫 번째 줄에 철민이가 도달할 수 있는 최대 인기도를 출력한다.


![](https://velog.velcdn.com/images/uunew/post/c11be3c8-6e0b-42df-90ca-23485c2e8238/image.png)



#### 🔗 문제 링크
https://softeer.ai/practice/9495

---

#### 📝 나의 풀이
``` java
import java.io.*;
import java.util.*;

public class Main {

    public static void main(String[] args) throws IOException{
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        int n = Integer.parseInt(br.readLine());
        int x = 0; //철민
        for(int i=0; i<n; i++){
            StringTokenizer st = new StringTokenizer(br.readLine());
            int p = Integer.parseInt(st.nextToken());
            int c = Integer.parseInt(st.nextToken());

            if(Math.abs(p-x) <= c){
                x++;
            }
        }
        System.out.println(x);
    }
}
```
절댓값을 구하는 Math.abs()를 사용하여 구현하였다.


#### 💡 회고
``` java
 @IntrinsicCandidate
    public static int abs(int a) {
        return (a < 0) ? -a : a;
    }
```