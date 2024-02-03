## 데크 (Deque)
- 양쪽에서 삽입과 삭제가 모두 가능한 자료구조
  - Deque: Doubly-ended Queue
  - Stack과 Queue를 합친 형태

</br>
  
## 데크 기본 구조
- 데크의 기본 구조는 양방향에서 삽입 삭제 가능한 구조
- 일부 기능을 제한하여 용도에 맞게 변형 가능


![](https://velog.velcdn.com/images/yezanee/post/16e58a1e-9553-4e26-ab4d-49abe8f1cbef/image.png)

</br>

## 입력제한 데크 (Scroll)
- 한 쪽의 입력을 제한한 데크

![](https://velog.velcdn.com/images/yezanee/post/66bbb019-4f57-4097-8a16-c690357ad661/image.png)

</br>

## 출력제한 데크 (Shelf)
- 한 쪽의 출력을 제한한 데크

![](https://velog.velcdn.com/images/yezanee/post/4cb8193a-b172-4496-a419-d6704890910e/image.png)

</br>

```java
// 선형 자료구조 - 데크


import java.util.ArrayDeque;
import java.util.Deque;

public class Main {
    public static void main(String[] args) {
        Deque deque = new ArrayDeque();

        // Front 부분 입력
        deque.addFirst(1);
        deque.addFirst(2);
        deque.addFirst(3);
        System.out.println(deque);


        // Rear 부분 입력
        deque.addLast(10);
        deque.addLast(20);
        deque.addLast(30);
        System.out.println(deque);


        // Front 부분 출력
        System.out.println(deque.removeFirst());
        System.out.println(deque);

        // Rear 부분 출력
        System.out.println(deque.removeLast());
        System.out.println(deque);

        System.out.println(deque.removeLast());
        System.out.println(deque.removeLast());
        System.out.println(deque.removeLast());
        System.out.println(deque.removeLast());
        System.out.println(deque);

        System.out.println(deque.pollLast()); // null 출력
        System.out.println(deque.removeLast()); // 오류


    }
}

```

```java
// Practice1
// ArrayList 를 이용한 데크 구현

import java.util.ArrayList;

class MyDeque1 {
    ArrayList list;

    MyDeque1() {
        this.list = new ArrayList();
    } // 생성자

    public boolean isEmpty() {
        if (this.list.size() == 0) {
            return true;
        } else {
            return false;
        }
    }

    public void addFirst(int data) {
        this.list.add(0,data); // 가장 앞쪽
    }

    public void addLast(int data) {
        this.list.add(data); // 바로 add 시켜주면 뒤쪽부터
    }

    public Integer removeFirst() {
        if (this.isEmpty()) {
            System.out.println("Deque is empty!");
            return null;
        }

        int data = (int)this.list.get(0); // 반환시킬 데이터 받아오기
        this.list.remove(0); // 제거
        return data; // 데이터 리턴
    }

    public Integer removeLast() {
        if (this.isEmpty()) {
            System.out.println("Deque is empty!");
            return null;
        }

        int data = (int)this.list.get(this.list.size() - 1);
        this.list.remove(this.list.size() - 1);
        return data;

    }

    public void printDeque() {
        System.out.println(this.list);
    }

}

public class Practice1 {
    public static void main(String[] args) {
        // Test code
        MyDeque1 myDeque = new MyDeque1();
        // Front 부분 입력
        myDeque.addFirst(1);
        myDeque.addFirst(2);
        myDeque.addFirst(3);
        myDeque.printDeque();    // 3 2 1

        // Rear 부분 입력
        myDeque.addLast(10);
        myDeque.addLast(20);
        myDeque.addLast(30);
        myDeque.printDeque();    // 3 2 1 10 20 30

        // Front 부분 출력
        System.out.println(myDeque.removeFirst());  // 3
        myDeque.printDeque();    // 2 1 10 20 30

        // Rear 부분 출력
        System.out.println(myDeque.removeLast());   // 30
        myDeque.printDeque();    // 2 1 10 20

        System.out.println(myDeque.removeLast());   // 20
        System.out.println(myDeque.removeLast());   // 10
        System.out.println(myDeque.removeLast());   // 1
        System.out.println(myDeque.removeLast());   // 2
        myDeque.printDeque();
    }
}

```

```java
// Practice2
// 배열을 이용한 기본 데크 직접 구현 (원형)

class MyDeque2 {
    int[] arr;
    int front = 0;
    int rear = 0;

    MyDeque2(int size) {
        this.arr = new int[size + 1]; // 원형으로 만들 건데, front는 가리키는 게 하나 없어서 사이즈를 하나 더 증가해서 만든다.
    }

    public boolean isEmpty() {
        return this.rear == this.front; // rear와 front가 같은 데이터를 가리키고 있는 상황이면 비어있는 상황
    }

    public boolean isFull() {
        return (this.rear + 1) % this.arr.length == this.front; // rear를 하나 증가시키고 나머지 연산을 한 결과가 front랑 같은 애면 꽉 차있는 상황
    }

    public void addFirst(int data) {
        if (this.isFull()) {
            System.out.println("Deque is Full!");
            return;
        }

        this.arr[this.front] = data; // front가 가리키고 있는 부분에다 data 추가
        this.front = (this.front - 1 + this.arr.length) % this.arr.length;
        // front - 1 + 배열의 길이 % 배열의 길이
    }

    public void addLast(int data) {
        if (this.isFull()) {
            System.out.println("Deque if Full!");
            return;
        }

        this.rear = (this.rear + 1) % this.arr.length;
        this.arr[this.rear] = data;

    }

    public Integer removeFirst() {
        if (this.isEmpty()) {
            System.out.println("Deque is empty!");
            return null;
        }

        this.front = (this.front + 1) % this.arr.length;
        return this.arr[this.front];
    }

    public Integer removeLast() {
        if (this.isEmpty()) {
            System.out.println("Deque is empty!");
            return null;
        }

        int data = this.arr[this.rear];
        this.rear = (this.rear - 1 + this.arr.length) % this.arr.length;
        return data;
    }

    public void printDeque() {
        int start = (this.front + 1) % this.arr.length;
        int end = (this.rear + 1) % this.arr.length;

        for (int i = start; i != end; i = (i + 1) % this.arr.length) {
            System.out.print(this.arr[i] + " ");
        }
        System.out.println();
    }

}

public class Practice2 {
    public static void main(String[] args) {
        // Test code
        MyDeque2 myDeque = new MyDeque2(5);
        // Front 부분 입력
        myDeque.addFirst(1);
        myDeque.addFirst(2);
        myDeque.addFirst(3);
        myDeque.printDeque();   // 3 2 1

        // Rear 부분 입력
        myDeque.addLast(10);
        myDeque.addLast(20);
        myDeque.addLast(30);    // Deque is full!
        myDeque.printDeque();        // 3 2 1 10 20

        // Front 부분 출력
        System.out.println(myDeque.removeFirst());  // 3
        myDeque.printDeque();   // 2 1 10 20

        // Rear 부분 출력
        System.out.println(myDeque.removeLast());   // 20
        myDeque.printDeque();    // 2 1 10

        System.out.println(myDeque.removeLast());   // 10
        System.out.println(myDeque.removeLast());   // 1
        System.out.println(myDeque.removeLast());   // 2
        System.out.println(myDeque.removeLast());   // Deque is empty!
    }
}

```

</br>

## Practice 1

> __데이터 재정렬__
D_0 -> D_1 -> ... -> D_n-1 -> D_n 순으로 되어 있는 데이터를
D_0 -> D_n -> D_1 -> D_n-1 -> ... 순이 되도록 재정렬 하시오. </br>
__입력 예시)__
입력 데이터: 1 -> 2 -> 3 -> 4 -> 5
출력 데이터: 1 -> 5 -> 2 -> 4 -> 3


```java
import java.util.ArrayDeque;
import java.util.ArrayList;
import java.util.Deque;
import java.util.stream.IntStream;

public class Practice1 {
    public static void reorderData(int[] arr) {
        Deque deque = new ArrayDeque();
        ArrayList result = new ArrayList();

        IntStream.of(arr).forEach(x -> deque.addLast(x));
        System.out.println(deque);

        while (!deque.isEmpty()) {
            result.add(deque.removeFirst());

            if(!deque.isEmpty()) {
                result.add(deque.removeLast());
            }
        }

        System.out.println("== 정렬 전 ==");
        printData(arr);
        System.out.println("== 정렬 후 ==");
        System.out.println(result.stream().mapToInt(x -> (int)x).toArray());
        // result를 stream 형태로 변환 후, 람다식으로 x에 대한 형태를 int 형태로 바꾸고 array 형태로 바뀐다.

    }

    public static void printData(int[] arr) {
        for (int i = 0; i < arr.length - 1; i++) {
            System.out.print(arr[i] + " -> ");
        }
        System.out.println(arr[arr.length - 1]);
    }

    public static void main(String[] args) {
        // Test code
        int[] arr = {1, 2, 3, 4, 5};
        reorderData(arr);   // 1 -> 5 -> 2 -> 4 -> 3

        int[] arr2 = {1, 2, 3, 4, 5, 6, 7};
        reorderData(arr2);  // 1 -> 7 -> 2 -> 6 -> 3 -> 5 -> 4
    }
}

```


</br>


## Practice 2

> __Palindrome 찾기__
Palindrome 이면 true, 아니면 false 를 반환하세요.
Palindrome: 앞으로 읽어도 거꾸로 읽어도 같은 문자열 </br>
__입출력 예시)__
입력: a
결과: true </br>
입력: madam
결과: true </br>
입력: abab
결과: false


```java
import java.util.ArrayDeque;
import java.util.ArrayList;
import java.util.Deque;

public class Practice2 {
    public static boolean checkPalindrome(String str) {

        Deque deque = new ArrayDeque();
        boolean isFront = true;
        boolean isPalindrome = true;

        for (String s: str.split("")) {
            deque.addFirst(s);

        }

        while (!deque.isEmpty()) {
            String s1 = (String)deque.pollFirst();
            String s2 = (String)deque.pollLast();

            if (s1 != null && s2 != null && !s1.equals(s2)) {
                isPalindrome = false;
                break;
            }
        }

        return isPalindrome;
    }

    public static void main(String[] args) {
        // Test code
        System.out.println(checkPalindrome("a"));       // true
        System.out.println(checkPalindrome("aba"));     // true
        System.out.println(checkPalindrome("abba"));    // true
        System.out.println(checkPalindrome("abab"));    // false
        System.out.println(checkPalindrome("abcba"));   // true
        System.out.println(checkPalindrome("abccba"));  // true
        System.out.println(checkPalindrome("madam"));  // true
    }
}

```

</br>

## Practice 3

> __데크 변형__
기본 데크 구조에서 중간에 데이터를 추가하는 기능을 구현하세요.
단, 추가적인 자료구조 생성하지 말고 구현 </br>
__입력 예시)__
초기 데크 상태 (size: 5)
-> 1, 2, 3, 4
중간 입력: 10
결과 데크
-> 1, 2, 10, 3, 4

```java
class MyDeque {
    int[] arr;
    int front = 0;
    int rear = 0;

    MyDeque(int size) {
        this.arr = new int[size + 1];
    }

    public boolean isEmpty() {
        return this.rear == this.front;
    }

    public boolean isFull() {
        return (this.rear + 1)  % this.arr.length == this.front;
    }

    public void addFirst(int data) {
        if (this.isFull()) {
            System.out.println("Deque is full!");
            return;
        }

        this.arr[front] = data;
        this.front = (this.front - 1 + this.arr.length) % this.arr.length;
    }

    public void addLast(int data) {
        if (this.isFull()) {
            System.out.println("Deque is full!");
            return;
        }

        this.rear = (this.rear + 1) % this.arr.length;
        this.arr[this.rear] = data;
    }

    public void addMiddle(int data) {
        if (this.isFull()) {
            System.out.println("Deque is full!");
            return;
        }

        int elements = this.rear - this.front;
        if (elements < 0) {
            elements = this.arr.length + elements;
        }

        int mid = (this.rear - elements / 2 + this.arr.length) % this.arr.length + 1;

        int start = (this.rear + 1) % this.arr.length;
        int end = (this.rear - elements / 2 + this.arr.length) % this.arr.length;
        for (int i = start; i != end ; i = (i - 1 + this.arr.length) % this.arr.length) {
            this.arr[i] = this.arr[(i - 1 + this.arr.length) % this.arr.length];

        }
        this.arr[mid] = data;
        this.rear = (this.rear + 1) % this.arr.length;
    }

    public Integer removeFirst() {
        if (this.isEmpty()) {
            System.out.println("Deque is empty!");
            return null;
        }

        this.front = (this.front + 1) % this.arr.length;
        return this.arr[this.front];
    }

    public Integer removeLast() {
        if (this.isEmpty()) {
            System.out.println("Deque is empty!");
            return null;
        }

        int data = this.arr[this.rear];
        this.rear = (this.rear - 1 + this.arr.length) % this.arr.length;
        return data;
    }

    public void printDeque() {
        int start = (this.front + 1) % this.arr.length;
        int end = (this.rear + 1) % this.arr.length;

        for (int i = start; i != end; i = (i + 1) % this.arr.length) {
            System.out.print(this.arr[i] + " ");
        }
        System.out.println();
    }
}

public class Practice3 {
    public static void main(String[] args) {
        // Test code
        MyDeque myDeque1 = new MyDeque(5);
        myDeque1.addLast(1);
        myDeque1.addLast(2);
        myDeque1.addLast(3);
        myDeque1.addLast(4);
        myDeque1.printDeque();

        myDeque1.addMiddle(10);
        myDeque1.printDeque();

        MyDeque myDeque2 = new MyDeque(5);
        myDeque2.addLast(10);
        myDeque2.addLast(10);
        myDeque2.addLast(10);
        myDeque2.addLast(10);
        myDeque2.addLast(10);
        myDeque2.removeFirst();
        myDeque2.removeFirst();
        myDeque2.removeFirst();
        myDeque2.removeFirst();
        myDeque2.addLast(11);
        myDeque2.addLast(12);
        myDeque2.addLast(13);
        myDeque2.printDeque();

        myDeque2.addMiddle(100);
        myDeque2.printDeque();
    }
}
```

</br>

## Practice 4

> __데크 리사이즈__
기본 데크 구조에서 데크 공간이 full 일 때 데이터를 추가하는 경우,
데크 공간을 2배 씩 늘려주는 코드를 작성하세요.


```java
class MyDeque2 {
    int[] arr;
    int front = 0;
    int rear = 0;

    MyDeque2(int size) {
        this.arr = new int[size + 1];
    }

    public boolean isEmpty() {
        return this.rear == this.front;
    }

    public boolean isFull() {
        return (this.rear + 1)  % this.arr.length == this.front;
    }

    public void increaseSize() {
        int[] arrTmp = this.arr.clone();
        this.arr = new int[this.arr.length * 2];

        int start = (this.front + 1) % arrTmp.length;
        int end = (this.rear + 1) % arrTmp.length;

        int idx = 1;
        for (int i = start; i != end; i = (i + 1) % arrTmp.length) {
            this.arr[idx++] = arrTmp[i];

        }

        this.front = 0;
        this.rear = idx - 1;

    }

    public void addFirst(int data) {
        if (this.isFull()) {
            increaseSize();
        }

        this.arr[front] = data;
        this.front = (this.front - 1 + this.arr.length) % this.arr.length;
    }

    public void addLast(int data) {
        if (this.isFull()) {
            increaseSize();
        }

        this.rear = (this.rear + 1) % this.arr.length;
        this.arr[this.rear] = data;
    }

    public Integer removeFirst() {
        if (this.isEmpty()) {
            System.out.println("Deque is empty!");
            return null;
        }

        this.front = (this.front + 1) % this.arr.length;
        return this.arr[this.front];
    }

    public Integer removeLast() {
        if (this.isEmpty()) {
            System.out.println("Deque is empty!");
            return null;
        }

        int data = this.arr[this.rear];
        this.rear = (this.rear - 1 + this.arr.length) % this.arr.length;
        return data;
    }

    public void printDeque() {
        int start = (this.front + 1) % this.arr.length;
        int end = (this.rear + 1) % this.arr.length;

        for (int i = start; i != end; i = (i + 1) % this.arr.length) {
            System.out.print(this.arr[i] + " ");
        }
        System.out.println();
    }
}

public class Practice4 {
    public static void main(String[] args) {
        // Test code
        MyDeque2 myDeque = new MyDeque2(5);

        myDeque.addLast(1);
        myDeque.addLast(2);
        myDeque.addLast(3);
        myDeque.addLast(4);
        myDeque.addLast(5);
        myDeque.printDeque();

        myDeque.addLast(6);
        myDeque.addLast(7);
        myDeque.addLast(8);
        myDeque.addLast(9);
        myDeque.addLast(10);
        myDeque.printDeque();

        myDeque.removeLast();
        myDeque.removeLast();
        myDeque.addFirst(100);
        myDeque.addFirst(200);
        myDeque.printDeque();

        myDeque.addFirst(300);
        myDeque.addFirst(400);
        myDeque.addFirst(500);
        myDeque.printDeque();
    }
}

```
