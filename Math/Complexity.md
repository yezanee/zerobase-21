> 제로베이스 백엔드 스쿨 21기

</br>

# 복잡도 (Complexity)

- 알고리즘 성능을 나타내는 척도
- 시간 복잡도 (Time Complexity)
  - 알고리즘의 필요 연산 횟수
- 공간 복잡도 (Space Complexity)
  - 알고리즘의 필요 메모리
- 시간 복잡도와 공간 복잡도는 Trade-off 관계

## 시간 복잡도 (Time Complexity)

- 어떤 문제를 해결하기 위한 알고리즘의 필요 연산 횟수
- 빅오(Big-O) 표기법을 통해 나타냄

![](https://velog.velcdn.com/images/yezanee/post/398ef4a2-152a-4ada-9045-cef088befcd7/image.png)

## 공간 복잡도

- 어떤 문제를 해결하기 위한 알고리즘의 필요 메모리 사용량
- 빅오 표기법을 통해 나타냄
  - 일반적으로 메모리 사용량 기준은 MB 단위
  
![](https://velog.velcdn.com/images/yezanee/post/cd8de277-c895-441a-83c7-a7b69d4071c1/image.png)

</br>

> 시간 복잡도에 중점적으로 포커싱 하기

```java
// 기초 수학 - 알고리즘 복잡도

public class Main {
    static int fibonacci(int n) {
        if (n < 3) {
            return 1;
        }
        return fibonacci(n - 2) + fibonacci(n - 1);
    }

    static int factorial(int n) {
        if (n < 1) {
            return 1;
        }
        return n * factorial(n - 1);
    }

    public static void main(String[] args) {

//      1. 시간 복잡도
        System.out.println("== 시간 복잡도 ==");

//      O(1)
        System.out.println("== O(1) ==");
        System.out.println("hello");
        // 한번 연산 (출력 연산 한번)

//      O(logN)
        System.out.println("== O(logN) ==");
        for (int i = 1; i < 16; i*=2) {
            System.out.println("hello");
        }
        // 16에 대한 데이터를 처리할 때, 위의 출력은 4번만 이루어짐.

//      O(N)
        System.out.println("== O(N) ==");
        for (int i = 0; i < 2; i++) {
            System.out.println("hello");
        }
        // N번에 대해서 N번만큼 다 이루어짐

//      O(NlogN)
        System.out.println("== O(NlogN) ==");
        for (int i = 0; i < 2; i++) {
            for (int j = 1; j < 8; j*=2) {
                System.out.println("hello");
            }
        }
        // 바깥 for문 N번만큼 이루어짐
        // 안쪽 for문 logN번 만큼 이루어짐

//      O(N^2)
        System.out.println("== O(N^2) ==");
        for (int i = 0; i < 2; i++) {
            for (int j = 0; j < 2; j++) {
                System.out.print("hello ");
            }
            System.out.println();
        }
        // N번만큼 이루어지는 for문이 이중으로 있을 때

//      O(2^N)
        System.out.println("== O(2^N) ==");
//      피보나치 재귀
//      1, 1, 2, 3, 5, 8, 13, ...
        System.out.println(fibonacci(6));
        // WORST 케이스


//      2. 공간 복잡도
        System.out.println("== 공간 복잡도 ==");
//      O(N)
        System.out.println("== O(N) ==");
        int n = 3;
        System.out.println(factorial(n));
        // 재귀적으로 호출이 이루어지면 함수 콜 스택 정보가 스택이라는 공간에 메모리가 쌓임

//      O(1)
        System.out.println("== O(1) ==");
        int result = 1;
        for (int i = 1; i <= n; i++) {
            result *= i;
        }
        System.out.println(result);
    }
}
```
