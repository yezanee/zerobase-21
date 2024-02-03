> 제로베이스 백엔드 스쿨 21기

## 스택 (Stack)

- 후입선출 (Last In First Out; LIFO) 자료구조
  : 마지막에 들어온 데이터가 먼저 나가는 구조
  
  
## 스택 기본 구조

- 후입 선출 구조
- 기본적으로 데이터 추가, 꺼내기, 스택 공간 확인 동작으로 이루어짐

![](https://velog.velcdn.com/images/yezanee/post/d37b5e7a-66a9-43f9-b7bd-fb6a0ea8b8b7/image.png)

## 스택 기본 연산

- 데이터 추가 (Push)
: 스택의 가장 마지막 위치에 데이터 추가

![](https://velog.velcdn.com/images/yezanee/post/9cbe6aa9-0387-4ede-bca8-b42ce8873157/image.png)

- 데이터 꺼내기 (Pop)
: 스택의 가장 마지막 위치에서 데이터 꺼냄

![](https://velog.velcdn.com/images/yezanee/post/8f34fa4f-e61d-4a28-b0c0-328c7b481040/image.png)


```java
// 선형 자료구조 - 스택

import java.util.Stack;

public class Main {
    public static void main(String[] args) {
        Stack stack = new Stack();

        stack.push(1);
        stack.push(2);
        stack.push(3);
        stack.push(4);
        stack.push(5);
        System.out.println(stack);

        System.out.println(stack.pop());
        System.out.println(stack);

        System.out.println(stack.pop());
        System.out.println(stack);

        System.out.println(stack.peek()); // 스택에서 가장 마지막으로 들어갔던 데이터 반환만
        System.out.println(stack);

        System.out.println(stack.contains(1));
        System.out.println(stack.size());
        System.out.println(stack.empty());

        stack.clear();
        System.out.println(stack);
        stack.pop();
    }

}
```

</br>

```java
// Practice1
// ArrayList 를 이용한 스택 구현

import java.util.ArrayList;

class MyStack1 {
    ArrayList list;

    MyStack1() {
        this.list = new ArrayList();
    }

    public boolean isEmpty() {
        if (this.list.size() == 0) {
            return true;
        } else {
            return false;
        }
    }

    public void push(int data) {
        this.list.add(data);
    }

    public Integer pop() {
        if (this.isEmpty()) {
            System.out.println("Stack is empty!");
            return null;
        }

        int data = (int)this.list.get(this.list.size() - 1);
        this.list.remove(this.list.size() - 1);
        return data;
    }

    public Integer peek() {
        if (this.isEmpty()) {
            System.out.println("Stack is empty!");
            return null;
        }

        int data = (int)this.list.get(this.list.size() - 1);
        return data;
    }

    public void printStack() {
        System.out.println(this.list);
    }
}

public class Practice1 {
    public static void main(String[] args) {
        // Test code
        MyStack1 myStack = new MyStack1();
        System.out.println(myStack.isEmpty());
        myStack.push(1);
        myStack.push(2);
        myStack.push(3);
        myStack.push(4);
        myStack.push(5);
        myStack.printStack();               // 1, 2, 3, 4, 5

        System.out.println(myStack.peek()); // 5
        myStack.printStack();               // 1, 2, 3, 4, 5

        System.out.println(myStack.pop());  // 5
        System.out.println(myStack.pop());  // 4
        myStack.printStack();               // 1, 2, 3

        System.out.println(myStack.pop());  // 3
        System.out.println(myStack.pop());  // 2
        System.out.println(myStack.pop());  // 1
        myStack.printStack();
    }
}
```

</br>

```java
// Practice2
// 배열을 이용한 기본 스택 직접 구현

class MyStack2 {
    int[] arr;
    int top = -1;

    MyStack2(int size) {
        arr = new int[size];
    }

    public boolean isEmpty() {
        if(this.top == -1) {
            return true;
        } else {
            return false;
        }

    }

    public boolean isFull() {
        if (this.top == this.arr.length - 1) {
            return true;
        } else {
            return false;
        }
    }

    public void push(int data) {
        if (this.isFull()) {
            System.out.println("Stak is full!");
            return;
        }

        this.top += 1;
        this.arr[this.top] = data;
    }

    public Integer pop() {
        if (this.isEmpty()) {
            System.out.println("Stack is empty!");
            return null;
        }

        int data = this.arr[this.top];
        this.top -= 1;
        return data;
    }

    public Integer peek() {
        if (this.isEmpty()) {
            System.out.println("Stack is empty!");
            return null;
        }

        return this.arr[this.top];
    }

    public void printStack() {
        for (int i = 0; i < this.top + 1; i++) {
            System.out.print(this.arr[i] + " ");
        }
        System.out.println();
    }
}

public class Practice2 {
    public static void main(String[] args) {
        // Test code
        MyStack2 myStack = new MyStack2(5);
        System.out.println(myStack.isEmpty());
        myStack.push(1);
        myStack.push(2);
        myStack.push(3);
        myStack.push(4);
        myStack.push(5);
        myStack.push(6);
        myStack.printStack();               // 1, 2, 3, 4, 5

        System.out.println(myStack.peek()); // 5
        myStack.printStack();               // 1, 2, 3, 4, 5

        System.out.println(myStack.pop());  // 5
        System.out.println(myStack.pop());  // 4
        myStack.printStack();               // 1, 2, 3

        System.out.println(myStack.pop());  // 3
        System.out.println(myStack.pop());  // 2
        System.out.println(myStack.pop());  // 1
        myStack.printStack();
    }
}
```

</br>

**Practice 1**

>**문자열 뒤집기** </br>
입출력 예시)
입력: "Hello"
출력: "OlleH" </br>
입력: 1 3 5 7 9
출력: 9 7 5 3 1


```java
import java.util.Stack;

public class Practice1 {
    public static String reverseString(String str) {
        Stack stack = new Stack();
        String result = ""; // 반환에 사용할 변수

        for(String s: str.split("")) { // 스택이 비어있지 않을 경우 반복문 돌려주기
            stack.push(s);
        }

        while (!stack.isEmpty()) {
            result = result + stack.pop();
        }

        return result;
    }

    public static void main(String[] args) {
        // Test code
        String result = reverseString("Hello");
        System.out.println("result = " + result);

        result = reverseString("1 3 5 7 9");
        System.out.println("result = " + result);
    }
}

```

</br>

**Practice 2**
>**괄호 짝 검사** </br>
입출력 예시)
입력: "("
출력: Fail </br>
입력: ")"
출력: Fail </br>
입력: "()"
출력: Pass


```java
import java.util.Stack;

public class Practice2 {
    public static void checkParenthesis(String str) {
        Stack stack = new Stack();
        boolean checkFlag = true;

        for(String s: str.split("")) {
            if (s.equals("(")) { // s가 '('애 해당한다면
                stack.push(s);
            } else {
                if (stack.isEmpty()) { // 만약 스택이 비어있다면
                    checkFlag = false;
                    break;
                } else { // 비어있지 않다면
                    stack.pop();
                }
            }
        }

        if (checkFlag && stack.isEmpty()) { // checkFlag가 참이고, 스택이 다 비어있으면
            System.out.println("PASS!");
        } else {
            System.out.println("FAIL!");
        }
    }

    public static void main(String[] args) {
        // Test code
        checkParenthesis("(");          // FAIL!
        checkParenthesis(")");          // FAIL!
        checkParenthesis("()");         // PASS!
        checkParenthesis("()()()");     // PASS!
        checkParenthesis("(())()");     // PASS!
        checkParenthesis("(((()))");    // FAIL!
    }
}
```

**Practice 3**
>**후위표기법 연산**</br>
입출력 예시)
입력: "2 2 +"
출력: 4 </br>
입력: "2 2 -"
출력: 0


```java

import java.util.Stack;

public class Practice3 {
    public static double calculate(String string) {
        Stack<Double> stack = new Stack();

        for (String s: string.split(" ")) { // 공백 기준으로 나누어라.
            if(s.equals("+")) {
                stack.push(stack.pop() + stack.pop());
            } else if(s.equals("-")) {
                stack.push(- stack.pop() + stack.pop()); // 나오는 순서 주의하기!
            } else if(s.equals("*")) {
                    stack.push(stack.pop() * stack.pop());
            } else if(s.equals("/")) {
                    stack.push(1 / stack.pop() * stack.pop());
            } else {
                stack.push(Double.parseDouble(s));
            }
        }

        return stack.pop();
    }

    public static void main(String[] args) {
        // Test code
        System.out.println(calculate("2 2 +"));    // 4
        System.out.println(calculate("2 2 -"));    // 0
        System.out.println(calculate("2 2 *"));    // 4
        System.out.println(calculate("2 2 /"));    // 1

        System.out.println(calculate("1 1 + 2 * 3 * 2 / 5 -"));    // 1
        System.out.println(calculate("5 2 * 3 - 8 * 4 /"));        // 14

    }
}

```

</br>

**Practice 4**

>**두 문자열 비교**
단, #은 backspace 로 바로 이전의 문자를 삭제하는 기능이라고 가정 </br>
입출력 예시
입력: s1 = "tree", s2 = "th#ree"
출력: true </br>
입력: s1 = "ab#a", s2 = "aab#"
출력: true </br>
입력: s1 = "wo#w", s2 = "ww#o"
출력: false


```java
import java.util.Stack;

public class Practice4 {

    public static boolean stringCompare(String s1, String s2) {
        String s1After = doBackspace(s1);
        String s2After = doBackspace(s2);
        return s1After.equals(s2After);
    }

    public static String doBackspace(String s) {
        Stack stack = new Stack();
        for (char c: s.toCharArray()) {
            if (c == '#' && !stack.empty()) {
                stack.pop();
            } else {
                stack.push(c);
            }
        }
        return String.valueOf(stack); // 어떤 값이라도 string 문자열로 바꿔줌
    }

    public static void main(String[] args) {
        // Test code
        String s1 = "tree";
        String s2 = "th#ree";
        System.out.println(stringCompare(s1, s2));

        s1 = "ab#a";
        s2 = "aab#";
        System.out.println(stringCompare(s1, s2));

        s1 = "wo#w";
        s2 = "ww#o";
        System.out.println(stringCompare(s1, s2));
    }
}

```
