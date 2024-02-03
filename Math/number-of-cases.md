### 경우의 수
- 어떤 사건에서 일어날 수 있는 경우의 가짓수
  - 예시 1) 동전을 던지는 사건: 경우의 수 2
  - 예시 2) 주사위를 던지는 사건: 경우의 수 6
  
  > 사건 A가 일어날 경우의 수 : n(A)

</br>

### 합의 법칙
- 사건A 또는 사건B가 일어날 경우의 수

</br>

### 차의 법칙
- 사건A와 사건B가 동시에 일어날 경우의 수

</br>

```java
// 기초 수학 - 경우의 수

import java.util.ArrayList;
import java.util.Arrays;
import java.util.HashSet;

public class Main {
    public static void main(String[] args) {

//      1. 합의 법칙
        System.out.println("== 합의 법칙 ==");
//      두 개의 주사를 던졌을 때 합이 3 또는 4의 배수일 경우의 수

        int[] dice1 = {1, 2, 3, 4, 5, 6};
        int[] dice2 = {1, 2, 3, 4, 5, 6};

        int nA = 0;
        int nB = 0;
        int nAandB = 0;
        
        // 기본 풀이
        for (int item1: dice1) {
            for (int item2: dice2) {
                if ((item1 + item2) % 3 == 0) {
                    nA += 1;
                }

                if ((item1 + item2) % 4 == 0) {
                    nB += 2;
                }

                if ((item1 + item2) % 12 == 0) {
                    nAandB += 1;
                }
            }
        }
        System.out.println("결과: " + (nA + nB - nAandB));


        // HashSet 이용
        HashSet<ArrayList> allCase = new HashSet<>();
        for (int item1: dice1) {
            for (int item2: dice2) {
                if ((item1 + item2) % 3 == 0 || (item1 + item2) % 4 == 0) {
                    ArrayList list = new ArrayList(Arrays.asList(item1, item2));
                    allCase.add(list);
                }
            }
        }
        System.out.println("결과: " + allCase.size());



//      2. 곱의 법칙
        System.out.println("== 곱의 법칙 ==");
//      두 개의 주사위 a, b를 던졌을 때 a는 3의 배수, b는 4의 배수인 경우의 수
        nA = 0;
        nB = 0;

        for (int item1: dice1) {
            if (item1 % 3 == 0) {
                nA++;
            }
        }

        for (int item1: dice2) {
            if (item1 % 4 == 0) {
                nB++;
            }
        }

        System.out.println("결과: " + (nA * nB));


    }
}
```

</br>

```java
// Practice
// 약수 구하기, 두 수의 최대공약수와 최소공배수 구하기
// 활용) 1~10의 수 중 A의 약수 또는 B의 약수인 경우의 수
// 활용) 1~10의 수 중 A의 약수이면서 B의 약수인 경우의 수

import java.util.ArrayList;

public class Practice {
    
//  약수
    public ArrayList getDivisor(int num) {
        ArrayList result = new ArrayList();

        for (int i = 1; i <= (int)num/2; i++) {
            if (num % i == 0) {
                result.add(i);
            }
        }
        result.add(num);

        return result;
    }

//  최대 공약수
//  GCD: the Greatest Common Denominator
    public int getGCD(int numA, int numB) {
        int gcd = -1;

        ArrayList divisorA = this.getDivisor(numA);
        ArrayList divisorB = this.getDivisor(numB);

        for (int itemA: (ArrayList<Integer>)divisorA) {
            for (int itemB : (ArrayList<Integer>)divisorB) {
                if (itemA == itemB) {
                    if (itemA > gcd) {
                        gcd = itemA;
                    }
                }
            }
        }

        return gcd;
    }

//  최소 공배수
//  LCM: the Lowest Common Multiple
    public int getLCM(int numA, int numB) {
        int lcm = -1;

        int gcd = this.getGCD(numA, numB);

        if (gcd != -1) {
            lcm = numA * numB / gcd;
        }

        return lcm;
    }

    public static void main(String[] args) {

//      Test code
        int number1 = 10;
        int number2 = 6;

        Practice p = new Practice();
        ArrayList l1 = p.getDivisor(number1);   // 10: 1, 2, 5, 10
        ArrayList l2 = p.getDivisor(number2);   // 6: 1, 2, 3, 6
        System.out.println("l1 = " + l1);
        System.out.println("l2 = " + l2);

        System.out.println("최대 공약수: " + p.getGCD(number1, number2));
        System.out.println("최대 공배수: " + p.getLCM(number1, number2));
    }
}
```number of cases
