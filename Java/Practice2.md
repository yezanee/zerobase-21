> 제로베이스 백엔드 스쿨 21기

</br>

Practice 2-1
===

문제 설명
---
로마 숫자 표기를 정수형으로 변환하는 프로그램을 작성하세요.

로마 숫자 표기법은 I, V, X, L, C, D, M 으로 이루어져있다.

|로마 숫자|정수형|
|---|---|
|I|1|
|V|5|
|X|10|
|L|50|
|C|100|
|D|500|
|M|1000|


로마 숫자 표기 방식
* 큰 기호에서 작은 기호 방향으로 작성 (XI, VI, II, ...)
* 다음의 경우 작은 기호가 큰 기호 앞에 올 수 있다.
  * I 는 V 와 X 의 앞에 올 수 있다. (IV: 4, IX: 9)
  * X 는 L 과 C 의 앞에 올 수 있다. (XL: 40, XC: 90)
  * C 는 D 와 M 의 앞에 올 수 있다. (CD: 400, CM: 900)
  
    
입출력 예시
---

|입력|출력|
|---|---|
|"III"|3|
|"IV"|4|
|"VI"|6|
|"XIII"|13|
|"XXVI"|26|
|"MCMXCIV"|1994|


</br>

```java
import java.util.HashMap;

public class Practice1 {
    public static void solution(String s) {
        HashMap<Character, Integer> map = new HashMap<>();
        map.put('I', 1);
        map.put('V', 5);
        map.put('X', 10);
        map.put('L', 50);
        map.put('C', 100);
        map.put('D', 500);
        map.put('M', 1000);

        int sum = 0;
        char[] arr = s.toCharArray();
        for (int i = 0; i < arr.length - 1; i++) { // index 오버 에러 방지
            if (map.get(arr[i]) < map.get(arr[i + 1])) { // 작은 기호가 더 앞에 오는 경우
                sum -= map.get(arr[i]); // sum 값에서 해당 값을 빼준다.
            } else {
                sum += map.get(arr[i]); // 그 외의 경우는 더해준다.
            }
        }
        sum += map.get(arr[arr.length - 1]); // 마지막 값도 한번 더 더해준다.
        System.out.println(sum);

    }

    public static void main(String[] args) {
        // Test code
        solution("III");
        solution("IV");
        solution("VI");
        solution("XIII");
        solution("XXVI");
        solution("MCMXCIV");
    }
}
```

</br>

Practice 2-2
===

문제 설명
---
정수형 숫자를 로마 숫자 표기로 변환하는 프로그램을 작성하세요.

로마 숫자 표기법은 I, V, X, L, C, D, M 으로 이루어져있다.

|로마 숫자|정수형|
|---|---|
|I|1|
|V|5|
|X|10|
|L|50|
|C|100|
|D|500|
|M|1000|


로마 숫자 표기 방식
* 큰 기호에서 작은 기호 방향으로 작성 (XI, VI, II, ...)
* 다음의 경우 작은 기호가 큰 기호 앞에 올 수 있다.
    * I 는 V 와 X 의 앞에 올 수 있다. (IV: 4, IX: 9)
    * X 는 L 과 C 의 앞에 올 수 있다. (XL: 40, XC: 90)
    * C 는 D 와 M 의 앞에 올 수 있다. (CD: 400, CM: 900)

입출력 예시
---

|입력|출력|
|---|---|
|3|"III"|
|4|"IV"|
|6|"VI"|
|13|"XIII"|
|26|"XXVI"|
|1994|"MCMXCIV"|

</br>

```java
import java.util.HashMap;

public class Practice2 {

    public static String solution(int num){
        String result = "";

        String[] roman = {"M", "CM", "D", "CD", "C", "XC", "L", "XL", "X", "IX", "V", "IV", "I"};
        int[] values = {1000, 900, 500, 400, 100, 90, 50, 40, 10, 9, 5, 4, 1};

        int i = 0;
        while (num > 0) {
            while (num >= values[i]) {
                num -= values[i];
                result += roman[i];
            }
            i++;
        }

        return result;
    }

    public static void main(String[] args) {
        // Test code
        System.out.println(solution(3));
        System.out.println(solution(4));
        System.out.println(solution(6));
        System.out.println(solution(13));
        System.out.println(solution(26));
        System.out.println(solution(1994));
    }
}
```

</br>

Practice 2-3
===

문제 설명
---
간단한 편집기를 구현하려고 한다.

편집기에는 문자열과 편집 명령어가 주어지는데, 명령어의 동작은 다음과 같다.
- L : 커서를 왼쪽으로 한 칸 옮김 (커서가 문장의 맨 앞이면 무시)
- D	: 커서를 오른쪽으로 한 칸 옮김 (커서가 문장의 맨 뒤이면 무시)
- B	: 커서 왼쪽에 있는 문자를 삭제 (커서가 문장의 맨 앞이면 무시)
- P x : x라는 문자를 커서 왼쪽에 추가

여기서 커서는 문자열에서 편집이 시작되는 기준 위치로,  
문장의 맨 앞, 맨 뒤, 중간에 위치할 수 있다.

편집기에 문자열과 명령어들이 주어졌을 때,  
편집을 완료한 후의 문자열을 출력하는 프로그램을 작성하시오.  
(초기 커서의 위치는 문장의 맨 뒤에서 시작한다.)  
(문자열은 소문자만 입력 가능하다.)


입출력 예시
---
|초기 문자열|명령어|결과 출력|
|---|---|---|
|"aba"|"L B"|"aa"|
|"abcd"|"P x L P y"|"abcdyx"|
|"abc"|"L L L P x L B P y"|"yxabc"|
|"a"|"B B L L D D P a P b P c"|"abc"|

</br>

```java
import java.util.ArrayList;

public class Practice3 {
    public static String solution(String input, String cmd) {
        StringBuffer sb = new StringBuffer(input);
        ArrayList<String> cmdArr = new ArrayList<>();

        for (String s: cmd.split(" ")) {
            cmdArr.add(s);
        }

        int curSor = sb.length();
        int cmdIdx = 0;
        while (cmdIdx != cmdArr.size()) {
            String cur = cmdArr.get(cmdIdx);

            if (cur.equals("L")) {
                curSor = Math.max(0, curSor - 1); // 음수로 가는 경우 방지
            } else if(cur.equals("D")) {
                curSor = Math.min(sb.length(), curSor + 1); // 문자열의 길이보다 커지는 경우 방지
            } else if(cur.equals("B")) {
                if (curSor == 0) {
                    cmdIdx++;
                    continue;
                }
                sb.delete(curSor - 1, curSor); // 좌측에 있는 한 데이터 지우기
                curSor = Math.max(0, curSor - 1);
            } else if (cur.equals("P")) {
                String s = cmdArr.get(++cmdIdx);
                sb.insert(curSor, s);
                curSor += 1;
            }

            cmdIdx++;
        }
        return sb.toString();
    }

    public static void main(String[] args) {
        // test code
        System.out.println(solution("aba", "L B"));
        System.out.println(solution("abcd", "P x L P y"));
        System.out.println(solution("abc", "L L L P x L B P y"));
        System.out.println(solution("a", "B B L L D D P a P b P c"));
    }
}
```

</br>

Practice 2-4
===

문제 설명
---
특수 작전을 위해 상대방의 PC에 키보드 입력 내용을 얻을 수 있는 키로깅 프로그램을 설치했다.

해당 키로깅 프로그램으로부터는 아래와 같이 특정 값으로 내용이 수신된다.
* 8 : Backspace
* 16 : Shift
* 20 : Caps Lock
* 32 : Space bar
* 37 : 키보드 왼쪽 화살표
* 39 : 키보드 오른쪽 화살표
* 155: Insert
* 127: Delete
* 97~122: 알파벳 소문자 (기본 입력은 소문자 기준, Shift 나 Caps Lock 에 의해 변경)
* 48~57: 숫자 0~9

(이 외의 값은 들어오지 않는다고 가정)

키로깅 프로그램으로부터 수신된 데이터를 원래 내용으로 복구하는 프로그램을 작성하세요.


입출력 예시
---
|수신 내용|결과|
|---|---|
|16, 106, 101, 108, 108, 111, 37, 37, 37, 37, 37, 155, 16, 104|"Hello"|
|20, 104, 16, 105, 32, 20, 16, 106, 97, 118, 97|"Hi Java"|
|49 51 8 50 51 53 55 37 37 127 127 52 53|"12345"|
|20 65 66 16 67 16 68 49 50 51|"ABcd!@#|

</br>


```java
public class Practice4 {
    public static String solution(int[] keyLog) {
        final int BACK_SPACE = 8;
        final int SHIFT = 16;
        final int CAPS_LOCK = 20;
        final int SPACE_BAR = 32;
        final int KEY_LEFT = 37;
        final int KEY_RIGHT = 39;
        final int INSERT = 155;
        final int DELETE = 127;

        StringBuffer sb = new StringBuffer();

        int step = (int)('a' - 'A'); // 대소문자 변환때 이용

        int curSor = 0;
        int cmdIdx = 0;
        boolean isShift = false;
        boolean isCapsLock = false;
        boolean isInsert = false;
        while (cmdIdx != keyLog.length) { // keylog의 길이만큼 도달할 때 까지 반복문 돌림.
            int cur = keyLog[cmdIdx]; // 첫번째 꺼 하나 꺼내온다.


            if (curSor == BACK_SPACE) {
                if (curSor == 0) {
                    cmdIdx++;
                    continue;
                }
                sb.delete(curSor - 1, curSor);
                curSor = Math.max(0, curSor - 1);
            } else if (cur == SHIFT) {
                isShift = true;
            } else if (cur == CAPS_LOCK) {
                isCapsLock = !isCapsLock; // 기존의 값 변경.
            } else if (cur == SPACE_BAR) {
                inputData(sb, ' ', curSor, isInsert);
                curSor += 1;
            } else if (cur == KEY_LEFT) {
                curSor = Math.max(0, curSor - 1);
            } else if (cur == KEY_RIGHT) {
                curSor = Math.min(sb.length(), curSor + 1);
            } else if (cur == INSERT) {
                isInsert = !isInsert;
            } else if (cur == DELETE) {
                if (curSor == sb.length()) {
                    cmdIdx++;
                    continue;
                }
                sb.delete(curSor, curSor + 1);
            } else if (cur >= 97 && cur <= 122) {
                int data = cur;

                if (isCapsLock && isShift) {
                    data = cur;
                } else if (isCapsLock || isShift) {
                    data -= step;
                }
                inputData(sb, (char)data, curSor, isInsert);
                isShift = false;
                curSor += 1;
            } else if (cur >= 48 && cur <= 57) {
                if (isShift) {
                    char[] specialKey = {')', '!', '@', '#', '$', '%', '^', '&', '*', '('};
                    inputData(sb, specialKey[cur - '0'], curSor, isInsert);
                } else {
                    inputData(sb, (char)cur, curSor, isInsert);
                }

                isShift = false;
                curSor += 1;
            }

            cmdIdx++;
        }

        return sb.toString();
    }

    public static void inputData(StringBuffer sb, char data, int curSor, boolean isInsert) {
        if (isInsert == false) {
            sb.insert(curSor, data);
        } else {
            sb.setCharAt(curSor, data);
        }
    }

    public static void main(String[] args) {
        // Test code
        int[] keyLog = {16, 106, 101, 108, 108, 111, 37, 37, 37, 37, 37, 155, 16, 104};
        System.out.println(solution(keyLog));

        keyLog = new int[]{20, 104, 16, 105, 32, 20, 16, 106, 97, 118, 97};
        System.out.println(solution(keyLog));

        keyLog = new int[]{49, 51, 8, 50, 51, 53, 55, 37, 37, 127, 127, 52, 53};
        System.out.println(solution(keyLog));

        keyLog = new int[]{20, 97, 98, 16, 99, 16, 100, 16, 49, 16, 50, 16, 51};
        System.out.println(solution(keyLog));
    }
}
```

</br>

Practice 2-5
===

문제 설명
---

N 명의 아이들이 한 줄로 서있다.  
각각의 아이들은 점수 표를 가지고 있는데 점수 표에 따라 다음과 같은 규칙으로 사탕을 나누어 줘야 한다.

* 적어도 1개 이상의 사탕을 나누어줘야 한다.
* 점수가 높은 아이에게는 바로 옆의 아이 보다는 사탕을 많이 줘야 한다.

N 명의 아이들에 대한 점수 표가 ratings 배열에 주어질 때,  
나누어 줘야하는 최소한의 사탕 개수를 출력하세요.

입출력 예시
---

|입력|출력|
|---|---|
|1 2 3|6|
|3 2 1|6|
|1 0 2|5|
|1 2 2|4|
|1, 3, 5, 3, 1, 3, 5, 7, 5, 3, 1, 0|29|

</br>

```java
public class Practice5 {
    public static int solution(int[] ratings) {
        if (ratings == null || ratings.length == 0) {
            return 0;
        }


        int result = 1;
        int upCnt = 1;
        int downCnt = 0;
        int peak = 0;
        for (int i = 1; i < ratings.length; i++) {
            if (ratings[i] > ratings[i - 1]) {
                upCnt++;
                peak = upCnt;
                downCnt = 0;
                result += upCnt;
            } else if (ratings[i] == ratings[i - 1]) {
                upCnt = 1;
                downCnt = 0;
                peak = 0;
                result += 1;
            } else {
                downCnt++;
                upCnt = 1;
                result += downCnt;

                if (peak <= downCnt) {
                    result += 1;
                }
            }
        }
        return result;
    }

    public static void main(String[] args) {
        // Test code
        int[] ratings = {1, 2, 3};
        System.out.println(solution(ratings));

        ratings = new int[]{3, 2, 1};
        System.out.println(solution(ratings));

        ratings = new int[]{1, 0, 2};
        System.out.println(solution(ratings));

        ratings = new int[]{1, 2, 2};
        System.out.println(solution(ratings));

        ratings = new int[]{1, 3, 5, 3, 1, 3, 5, 7, 5, 3, 1, 0};
        System.out.println(solution(ratings));
    }
}

```
