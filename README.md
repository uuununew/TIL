# 99클럽 코테 스터디 1일차 TIL : 문자열

## 문자열 내 p와 y의 개수 
> 오늘의 학습 키워드 : 문자열

#### 📚 문제 설명
대문자와 소문자가 섞여있는 문자열 s가 주어집니다. s에 'p'의 개수와 'y'의 개수를 비교해 같으면 True, 다르면 False를 return 하는 solution를 완성하세요. 'p', 'y' 모두 하나도 없는 경우는 항상 True를 리턴합니다. 단, 개수를 비교할 때 대문자와 소문자는 구별하지 않습니다.

예를 들어 s가 "pPoooyY"면 true를 return하고 "Pyy"라면 false를 return합니다.

#### 📌 제한 사항 
문자열 s의 길이 : 50 이하의 자연수
문자열 s는 알파벳으로만 이루어져 있습니다.

#### 💻 입출력 예
|s|answer|
|---|:---|
|"pPoooyY"|true|
|"Pyy"|false|

입출력 예 #1
'p'의 개수 2개, 'y'의 개수 2개로 같으므로 true를 return 합니다.

입출력 예 #2
'p'의 개수 1개, 'y'의 개수 2개로 다르므로 false를 return 합니다.

---
### 📝 나의 풀이
```java
class Solution {
    boolean solution(String s) {
        s = s.toLowerCase();
        int cnt1 = 0;
        int cnt2 = 0;
        for(int i=0; i<s.length(); i++){
            if(s.charAt(i) == 'p'){
                cnt1++;
            }else if(s.charAt(i) == 'y'){
                cnt2++;
            }
        }
        if(cnt1 == cnt2){
            return true;
        }else{
            return false;
        }     
    }
}
```

문자열을 모두 소문자로 바꾼 후 'p'면 cnt1이 증가하고, y면 cnt2가 증가한다.
그 뒤 cnt1과 cnt2를 비교하여 return 한다. 지금 보니 코드가 지저분한 것 같기도,,?

### ✏️ 다른 사람의 풀이
```java
class Solution {
    boolean solution(String s) {
        int count = 0;
        
        s = s.toLowerCase();
        
        for (int i = 0; i < s.length(); i++) {

            if (s.charAt(i) == 'p') {
                count++;
            }else if (s.charAt(i) == 'y') {
                count--;
            }
        }
        
        return count == 0;
    }
}

```

변수를 하나만 사용해서 확실히 깔끔하다.

---
### 💡 회고

처음에는 '대소문자 구분없이'에만 꽂혀서 compareToIgnoreCase()를 사용했는데 이 문제는 p와 y일 때 count만 해주면 되는 문제라 저건 필요 없었다. 문제 전체를 잘 파악해야겠다.