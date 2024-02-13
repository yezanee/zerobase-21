> 제로베이스 백엔드 스쿨 21기

</br>

### 순열 (Permutation)

- 순서를 정해서 나열
- 서로 다른 n개 중에 r개를 선택하는 경우의 수 (순서 O, 중복 X)
   - 예시) 5명을 3줄로 세우는 방법
   - 예시) 서로 다른 4명 중 반장, 부반장을 뽑는 방법

</br>

### 중복 순열
- 서로 다른 n개 중에 r개를 선택하는 경우의 수 (순서 O, 중복 O)
  - 예시) 서로 다른 4개의 수 중 2개를 뽑는 방법 (중복 허용)
  - 예시) 후보 2명, 유권자 3명일 때 기명 투표 방법
  
  
</br>

### 원 순열
- 원 모양의 테이블에 n개의 원소를 나열하는 경우의 수
  - 예시) 원 모양의 테이블에 3명을 앉히는 경우
  
</br>

```java
// 기초 수학 - 순열

import java.util.stream.IntStream;

public class Main {
    public static void main(String[] args) {

//      1. 팩토리얼
        System.out.println("== 팩토리얼 ==");
//      5!
        int n = 5;
        int result = 1;
        for (int i = 1; i <= n; i++) {
            result *= i;
        }
        System.out.println("result = " + result);

        System.out.println(IntStream.range(2, 6).reduce(1, (x, y) -> x * y));
        // 초깃값은 1로, 그리고 두 수를 잘 곱하기 ..


//      2. 순열
        System.out.println("== 순열 ==");
//      5명을 3줄로 세우는 경우의 수
        n = 5;
        int r = 3;
        result = 1;

        for (int i = n; i >= n - r + 1; i--) {
            result *= i;
        }
        System.out.println("result = " + result);


//      3. 중복 순열
        System.out.println("== 중복 순열 ==");
//      서로 다른 4개의 수 중 2개를 뽑는 경우의 수 (중복 허용)
        n = 4;
        r = 2;
        result = 1;

        for (int i = 0; i < r; i++) {
            result *= n; // n의 r승
        }
        System.out.println("result = " + result);
        System.out.println(Math.pow(n, r));


//      4. 원 순열
        System.out.println("== 원 순열 ==");
//      원 모양의 테이블에 3명을 앉히는 경우의 수
        n = 3;
        result = 1;

        for (int i = 1; i < n; i++) {
            result *= i;
        }
        System.out.println("result = " + result);
    }
}
```

</br>

```java
// Practice1
// 1, 2, 3, 4 를 이용하여 세자리 자연수를 만드는 방법 (순서 O, 중복 x)의 각 결과를 출력하시오
// 방법 1

public class Practice1 {
    void permutation(int[] arr, int depth, int n, int r) {
        if (depth == r) {
            for (int i = 0; i < r; i++) {
                System.out.print(arr[i] + " ");
            }
            System.out.println();
            return;
        }

        for (int i = depth; i < n; i++) {
            swap(arr, depth, i); // 재귀함수 호출 전 자리 바꿔줌
            permutation(arr, depth + 1, n, r); // 재귀함수 형태, 호출
            swap(arr, depth, i); // 다시 원래대로 자리 바꿔줌
        }
    }

    void swap(int[] arr, int depth, int idx) {
        int tmp = arr[depth];
        arr[depth] = arr[idx];
        arr[idx] = tmp;
    }

    public static void main(String[] args) {
//      Test code
        int[] arr = {1, 2, 3, 4};

        Practice1 p = new Practice1();
        p.permutation(arr, 0, 4, 3);
    }
}

/*
arr = 1234
depth = 0  ->  1  ->  2  ->  3
i = 0  ->  1  ->  2
*/
```

</br>

```java
// Practice2
// 1, 2, 3, 4 를 이용하여 세자리 자연수를 만드는 방법 (순서 O, 중복 x)의 각 결과를 출력하시오
// 방법 2

import java.util.Arrays;

public class Practice2 {
    void permutation(int[] arr, int depth, int n, int r, boolean[] visited, int[] out) {
        if (depth == r) {
            System.out.println(Arrays.toString(out));
            return;
        }

        for (int i = 0; i < n; i++) {
            if (visited[i] != true) {
                visited[i] = true; // 방문 했음을 표시
                out[depth] = arr[i];
                permutation(arr, depth + 1, n, r, visited, out); // 재귀 이용
                visited[i] = false; // 1을 다시 0으로 바꿔줌
            }
        }

    }

    public static void main(String[] args) {
//      Test code
        int[] arr = {1, 2, 3, 4};
        boolean[] visited = new boolean[4];
        int[] out = new int[3];

        Practice2 p = new Practice2();
        p.permutation(arr, 0, 4, 3, visited, out);
    }
}
```
