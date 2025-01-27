> Lv.2

#### 📚 문제 설명
환경 파괴범 때문에 화가 난 숲의 요정은 나무 공격을 진행하려 합니다. 나무 공격 진행시 투사체 5개가 생성되어 지정된 방향으로 전진합니다. 각 투사체와 최초로 접촉한 환경 파괴범은 사라지게 되며 이때 투사체 역시 동시에 사라지게 됩니다. 만약 투사체가 환경 파괴범과 마주치지 않는다면 조용히 사라지게 됩니다.


이는 n×m 크기의 격자에서 진행됩니다. 초기에 격자의 각 칸에는 숫자 0 또는 1이 적혀있으며 0은 비어있음을, 1은 환경 파괴범이 해당 위치에 서있음을 뜻합니다.
![](https://velog.velcdn.com/images/uunew/post/f26acffc-c4cf-483b-b680-06a6b992702c/image.png)


숲의 요정은 항상 격자의 왼쪽 방향에서 나무 공격을 진행하며, 총 2회 진행합니다. 공격은 특정 행 L부터 행 R까지의 구간에 한하여 투사체를 만들어 진행하게 되며, 모든 투사체는 행 변화 없이 정확히 오른쪽 방향으로만 진행하게 됩니다. 투사체는 처음으로 만나는 환경 파괴범과 함께 사라지게 되며, 끝까지 만나지 않는 투사체는 조용히 사라지게 됩니다. L과 R의 차이는 항상 4이기 때문에 투사체는 항상 5개가 만들어짐에 유의합니다. 다음은 1~5 행에 걸쳐 공격을 진행한 경우입니다.

![](https://velog.velcdn.com/images/uunew/post/e4702b64-ae1a-416a-88b6-a7dd8e5fc4be/image.png)


따라서 위의 예시에서는 2번의 공격 이후 남아있는 서로 다른 환경 파괴범의 수가 2명이 됩니다.

초기 격자의 정보와 2번의 공격에 대한 정보가 주어졌을 때, 공격을 순서대로 진행한 이후 격자에 남아있는 서로 다른 환경 파괴범의 수를 구하는 프로그램을 작성해보세요.


#### 📌 제한 사항 
[조건 1] 5 ≤ n, m ≤ 100

[조건 2] 1 ≤ L1, L2, R1, R2 ≤ n


#### 💻 입출력 예

- 입력

첫 번째 줄에는 격자의 크기를 나타내는 n과 m이 공백을 사이에 두고 주어집니다.

두 번째 줄부터는 n개의 줄에 걸쳐 각 행에 해당하는 m개의 격자 정보가 공백을 사이에 두고 주어집니다. 격자 내 숫자는 0, 1로만 주어지며 0은 비어있는 칸을, 1은 환경 파괴범이 있는 칸임을 뜻합니다.

n+2번째 줄에는 첫 번째 공격 정보에 해당하는 L1​,R1​값이 공백을 사이에 두고 주어집니다. 이는 L1​번째 행부터 R1​번째 행까지 공격이 이루어짐을 뜻하며, R1​−L1​은 항상 4임을 가정해도 좋습니다.

n+3번째 줄에는 두 번째 공격 정보에 해당하는 L2​,R2​값이 공백을 사이에 두고 주어집니다. 이는 L2​번째 행부터 R2​번째 행까지 공격이 이루어짐을 뜻하며, R2​−L2​는 항상 4임을 가정해도 좋습니다.


- 출력

첫 번째 줄에 두 번의 공격 이후 격자에 남아있는 서로 다른 환경 파괴범의 수를 출력합니다.


![](https://velog.velcdn.com/images/uunew/post/ac83f283-d111-46ce-89c8-d817836bb31b/image.png)


#### 🔗 문제 링크
https://softeer.ai/practice/9657

---

#### 📝 나의 풀이
``` java
import java.io.*;
import java.util.*;

public class Main {

    public static void main(String[] args) throws IOException{
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer st = new StringTokenizer(br.readLine());
        
        int n = Integer.parseInt(st.nextToken());
        int m = Integer.parseInt(st.nextToken());

        int[][]arr = new int [n][m];

        for(int i=0; i<n; i++){
            st = new StringTokenizer(br.readLine());
            for(int j=0; j<m; j++){
                arr[i][j] = Integer.parseInt(st.nextToken());
            }
        }

        st = new StringTokenizer(br.readLine());
        int firstN = Integer.parseInt(st.nextToken()) -1;
        int firstM = Integer.parseInt(st.nextToken());
        attack(arr, m, firstN, firstM);

        st = new StringTokenizer(br.readLine());
        int secondN = Integer.parseInt(st.nextToken()) -1;
        int secondM = Integer.parseInt(st.nextToken());
        attack(arr, m, secondN, secondM);

        int total = 0;
        for(int i=0; i<n; i++){
            for(int j=0; j<m; j++){
                if(arr[i][j] == 1){
                    total ++;
                }
            }
        }
        System.out.println(total);
    }

    private static void attack(int[][]arr, int columns, int start, int end){
        for(int i = start; i < end; i++) {
            for(int j = 0; j < columns; j++) {
                if(arr[i][j] == 1) {
                    arr[i][j] = 0;
                    break;
                }
            }
        }
    }
}
```

1. n과m을 입력받고 n, m의 크기를 가진 배열 arr 생성

2. 배열 arr 값 입력받기

3. 첫 번째 공격(first)을 입력받는다. 이때 n은 -1을 함

4. 공격로직은 attack을 호출하고 값을 전달
4-1. 입력받은 값을 가지고 배열을 확인, 값이 1이면 0으로 바꾸고 for 문 종료

5. 두 번째 공격(second)을 입력받는다. n은 - 1을 계산하고 attack을 호출함

6. 남은 환경 파괴범의 수 = total 

7. for문을 통해 arr의 값이 1이면 total++

8. total출력 


#### ✏️ 다른 사람의 풀이
``` java
import java.io.*;
import java.util.*;

public class Main {
    public static final int MAX_N = 100;
    public static final int MAX_M = 100;

    public static int n, m;
    public static int[][] attackArr = new int[2][2];
    public static int[] cntArr = new int[MAX_N];
    public static int ans = 0;
    
    public static void main(String[] args) throws IOException {
        init();

        for (int i = 0; i < 2; i++) {
            for (int s = attackArr[i][0]; s <= attackArr[i][1]; s++) {
                if (cntArr[s] > 0) {
                    cntArr[s]--;
                }
            }
        }

        for (int i = 0; i < n; i++) {
            ans += cntArr[i];
        }

        System.out.println(ans);
    }

    public static void init() throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer st = new StringTokenizer(br.readLine());

        n = Integer.parseInt(st.nextToken());
        m = Integer.parseInt(st.nextToken());

        for (int i = 0; i < n; i++) {
            st = new StringTokenizer(br.readLine());
            int cnt = 0;
            
            for (int j = 0; j < m; j++) {
                int temp = Integer.parseInt(st.nextToken());

                if (temp == 1) cnt++;
            }

            cntArr[i] = cnt;
        }

        
        st = new StringTokenizer(br.readLine());
        attackArr[0][0] = Integer.parseInt(st.nextToken()) - 1;
        attackArr[0][1] = Integer.parseInt(st.nextToken()) - 1;
        
        st = new StringTokenizer(br.readLine());
        attackArr[1][0] = Integer.parseInt(st.nextToken()) - 1;
        attackArr[1][1] = Integer.parseInt(st.nextToken()) - 1;
        
    }
}

```
각 행마다 인원 수를 세어 공격마다 1씩 줄여주는 로직
