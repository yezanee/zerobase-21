> 제로베이스 백엔드 스쿨 21기

</br>

# 점화식 (Recurrence)

- 어떤 수열의 일반항을 그 이전의 항들을 이용하여 정의한 식
  - 예시) 피보나치 수열

![](https://velog.velcdn.com/images/yezanee/post/54b1049e-7de6-4673-9d17-b31bf73337b4/image.png)

> 1 + 1 = 2
> 1 + 2 = 3
> 2 + 3 = 5
> ...

</br>

# 재귀함수

- 어떤 함수가 자신을 다시 호출하여 작업을 수행하는 방식
- 종료 조건 반드시 있어야 한다!

![](https://velog.velcdn.com/images/yezanee/post/5b7bc7fb-68a5-4a07-bc39-65cb172ae8c7/image.png)

</br>

```java

// 기초 수학 - 점화식과 재귀함수

public class Main {
    static int recursion1(int n) {
        if (n == 1) {
            return 1;
        }
        return 3 * recursion1(n - 1);
    }

    /*
        3 * recursion1(3)
            3 * recursion1(2)
                3 * recursion1(1)
                    1
    */


    static int recursion2(int n) {
        if (n == 1) {
            return 1;
        }
        return n + recursion2(n - 1);
    }

    /*
        5 + recursion(4)
                4 + recursion(3)
                        3 + recursion(2)
                                2 + recursion(1)
                                        1
    */

    static int recursion3(int n) {
        if (n < 3) {
            return 1;
        }
        return recursion3(n - 2) + recursion3(n -1);
    }

    /*
        n = 6
               recursion3(4)                      +                    recursion(5)
        recursion(2)    +   recursion(3)                 recursion(3)        +    recursion(4)
              1      recursion(1) + recursion(2)  recursion(1) + recursion(2)  recursion(2) + recursion(3)
                            1           1               1           1               1               ...
    */

    public static void main(String[] args) {
        
//      점화식 -> 반복문, 재귀함수
        System.out.println("== 점화식/재귀함수 연습1 ==");
//      1, 3, 9, 27, ... 의 n번째 수
        int n = 4;
        int result = 1;
        for (int i = 0; i < n; i++) {
            if (i == 0) {
                result = 1;
            } else {
                result *= 3;
            }
        }
        System.out.println(result);
        System.out.println(recursion1(n));


        System.out.println("== 점화식/재귀함수 연습2 ==");
//      1, 2, 3, 4, 5, 6, ... 의 n번째 까지의 합
        n = 5;
        result = 0;
        for (int i = 1; i < n + 1; i++) {
            result += i;
        }
        System.out.println(result);
        System.out.println(recursion2(n));


        System.out.println("== 점화식/재귀함수 연습3 ==");
//      1, 1, 2, 3, 5, 8, 13, ...의 n번 째 수 (피보나치 수열)
        n = 6;
        result = 0;
        int a1 = 1;
        int a2 = 1;

        if (n < 3) {
            result = 1;
        } else {
            for (int i = 2; i < n; i++) {
                result = a1 + a2;
                a1 = a2;
                a2 = result;
            }
        }
        System.out.println(result);
        System.out.println(recursion3(n));

    }
}

```

</br>

```java
// Practice1
// 팩토리얼을 재귀함수로 구현하시오.

public class Practice1 {
    static int factorial(int n) {
        if (n == 1) {
            return 1;
        }
        return n * factorial(n - 1);
    }

    public static void main(String[] args) {
//      Test code
        System.out.println(factorial(1));
        System.out.println(factorial(2));
        System.out.println(factorial(3));
        System.out.println(factorial(4));
        System.out.println(factorial(5));
    }
}
```

</br>

```java
// Practice2
// 최대공약수를 재귀함수로 구현하시오.

public class Practice2 {
    static int gcd(int a, int b) {
        if (a % b == 0) {
            return b;
        }
        return gcd(b, a % b);
    }

    /* 3을 5로 나눈 나머지는 0이 되지 않음 (조건문 건너뜀)
       gcd(5, 3)
       gcd(3, 2)
       gcd(2, 1)
       return 1
    */

    /*
        8 % 12 = 8
        12 % 8 = 4
        8 % 4 = 0
        -> 따라서 4!
    */

    public static void main(String[] args) {
//      Test code
        System.out.println(gcd(3, 5));
        System.out.println(gcd(2, 6));
        System.out.println(gcd(8, 12));
    }
}
```
