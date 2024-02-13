> 제로베이스 백엔드 스쿨 21기

</br>

# 제곱, 제곱근, 지수

## 제곱
- 같은 수를 두번 곱합
- 거듭 제곱: 같은 수를 거듭하여 곱합

## 제곱근 (=root)
- a를 제곱하여 b가 될 때 a를 b의 제곱근이라고 함

![](https://velog.velcdn.com/images/yezanee/post/508e5432-41e6-42d1-a594-c290463279b7/image.png)

</br>

# 로그
- a가 b가 되기 위해 제곱해야 하는 수

![](https://velog.velcdn.com/images/yezanee/post/7165be21-f3c1-4c0f-b0e6-153d66bb780d/image.png)

</br>

```java
// 기초 수학 - 지수와 로그

public class Main {

    public static void main(String[] args) {

//      1. 제곱, 제곱근, 지수
        System.out.println("== 제곱 ==");
        System.out.println(Math.pow(2, 3));
        System.out.println(Math.pow(2, -3));
        System.out.println(Math.pow(-2, -3));

        System.out.println(Math.pow(2, 30));
        System.out.printf("%.0f\n", Math.pow(2, 30));

        System.out.println("== 제곱근 ==");
        System.out.println(Math.sqrt(16));
        System.out.println(Math.pow(16, 1.0/2));
        System.out.println(Math.pow(16, 1.0/4));

//      참고) 절대 값
        System.out.println("== 절대 값 ==");
        System.out.println(Math.abs(5));
        System.out.println(Math.abs(-5));


//      2. 로그
        System.out.println("== 로그 ==");
        System.out.println(Math.log(2.7182818284590452353602874713527));
        System.out.println(Math.log10(1000));
        System.out.println(Math.log(4) / Math.log(2));

    }
}
```

</br>

```java
// Practice
// 제곱과 제곱근을 Math 없이 구현하기

public class Practice {
    static double pow(int a, double b) {
        double result = 1;
        boolean isMinus = false;

        if (b == 0) { // 지수 0
            return 1;
        } else if (b < 0) { // 지수가 음수
            b *= -1;
            isMinus = true;
        }

        for (int i = 0; i < b; i++) {
            result *= a;
        }

        return isMinus ? 1 / result : result; // 지수가 음수인지 여부
    }

    static double sqrt(int a) {
        double result = 1;
        for (int i = 0; i < 10; i++) {
            result = (result + (a / result)) / 2;
        } // 많이 할수록 근사값에 가까워짐

        return result;
    }

    public static void main(String[] args) {

//      Test code
        System.out.println("== Math pow ==");
        System.out.println(Math.pow(2, 3));
        System.out.println(Math.pow(2, -3));
        System.out.println(Math.pow(-2, -3));

        System.out.println("== My pow ==");
        System.out.println(pow(2, 3));
        System.out.println(pow(2, -3));
        System.out.println(pow(-2, -3));

        System.out.println("== Math sqrt ==");
        System.out.println(Math.sqrt(16));
        System.out.println(Math.sqrt(8));

        System.out.println("== My sqrt ==");
        System.out.println(sqrt(16));
        System.out.println(sqrt(8));

    }
}
```
