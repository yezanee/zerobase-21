## 집합 (Set)

- 특정 조건에 맞는 원소들의 모임
- 집합 표현 방법
  - 원소나열법
  A = {1, 2, 3, 4, 5}, B = {2, 4, 6, 8, 10}
  - 조건제시법
  A = {A | A는 정수, 1<=A<=5}
  - 벤 다이어그램
  ![](https://velog.velcdn.com/images/yezanee/post/e3c4ea60-d6fd-469f-bbf5-923cdc4cd9d8/image.png)

</br>


### 교집합
- 두 집합이 공통으로 포함하는 원소로 이루어진 집합

</br>

### 합집합
- 어느 하나에라도 속하는 원소들을 모두 모은 집합

</br>

### 차집합
- A(or B)에만 속하는 원소들의 집합

</br>

### 여집합
- 전체집합 중 A의 원소가 아닌 것들의 집합

</br>

// 기초 수학 - 집합

import java.util.ArrayList;
import java.util.Arrays;
import java.util.HashSet;

public class Main {
    public static void main(String[] args) {

//      1. 자바에서 집합 사용 - HashSet
        System.out.println("== HashSet ==");
        HashSet set1 = new HashSet();
        set1.add(1);
        set1.add(1);
        set1.add(1);
        System.out.println("set1 = " + set1); // 1 하나만 출력 (중복 삭제)
        set1.add(2);
        set1.add(3);
        System.out.println("set1 = " + set1);
        set1.remove(1);
        System.out.println("set1 = " + set1);
        System.out.println(set1.size());
        System.out.println(set1.contains(2)); // 집합 데이터에 '2'가 들어가는 지 확인
        

//      2. 집합 연산
        System.out.println("== 집합 연산 ==");

//      2-1. 교집합
        HashSet a = new HashSet(Arrays.asList(1, 2, 3, 4, 5));
        HashSet b = new HashSet(Arrays.asList(2, 4, 6, 8, 10));
        a.retainAll(b); // 교집합 계산되어 a에는 교집합의 원소만 남는다.
        System.out.println("교집합: " + a);

//      2-2. 합집합
        a.addAll(b); // 합집합 게산되어 a에는 합집합의 원소만 남는다.
        System.out.println("합집합: " + a);


//      2-3. 차집합
        a.removeAll(b); // 차집합 계산되어 a에는 차집합의 원소만 남는다.
        System.out.println("차집합: " + a);

    }

}

</br>

```java
// Practice
// ArrayList를 사용한 집합 구현 실습 (집합 관련 연산 사용 X)

import java.util.ArrayList;

class MySet {
// ArrayList
    ArrayList<Integer> list;

// 생성자1 (생략 가능한 생성자)
    MySet() {
        this.list = new ArrayList<Integer>();
    }

// 생성자 2
    MySet(int[] arr) {
        this.list = new ArrayList<Integer>();

        for(int item: arr) {
            this.list.add(item);
        }
    }

// 원소 추가 (중복 X)
    public void add(int x) {
        for (int item : this.list) {
            if (item == x) {
                return;
            }
        }
        this.list.add(x);
    }

// 교집합
    public MySet retainAll(MySet b) {
        MySet result = new MySet();

        for (int itemA: this.list) {
            for (int itemB: b.list) {
                if (itemA == itemB) {
                    result.add(itemA);
                }
            }
        }
        return result;
    }


// 합집합
    public MySet addAll(MySet b) {
        MySet result = new MySet();

        for (int itemA: this.list) {
            result.add(itemA);
        }

        for (int itemB: b.list) {
            result.add(itemB);
        }
        return result;
    }

// 차집합
    public MySet removeAll(MySet b) {
        MySet result = new MySet();

        for (int itemA: this.list) {
            boolean containFlag = false;

            for(int itemB: b.list) {
                if (itemA == itemB) {
                    containFlag = true;
                    break;
                }
            }

            if (!containFlag) {
                result.add(itemA);
            }
        }

        return result;
    }

}

public class Practice {
    public static void main(String[] args) {

//      Test code
        MySet a = new MySet();

        a.add(1);
        a.add(1);
        a.add(1);
        System.out.println(a.list);
        a.add(2);
        a.add(3);
        System.out.println(a.list);

        a = new MySet(new int[]{1, 2, 3, 4, 5});
        MySet b = new MySet(new int[]{2, 4, 6, 8, 10});
        System.out.println("a: " + a.list);
        System.out.println("b: " + b.list);

        MySet result = a.retainAll(b);
        System.out.println("교집합: " + result.list);

        result = a.addAll(b);
        System.out.println("합집합: " + result.list);

        result = a.removeAll(b);
        System.out.println("차집합: " + result.list);
    }
}
```
