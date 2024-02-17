# 연결 리스트 (Linked List)

- 데이터를 링크로 연결해서 관리하는 구조
- 자료의 순서는 정해져 있지만, 메모리상 연속상이 보장되지는 않음

</br>

## 연결 리스트의 장점
- 데이터 공간을 미리 할당할 필요 없음
- 즉, 리스트의 길이가 가변적이라 데이터 추가/삭제 용이

## 연결 리스트의 단점
- 연결 구조를 위한 별도 데이터 공간 필요
- 연결 정보를 찾는 시간이 필요 (접근 속도가 상대적으로 느림)
- 데이터 추가, 삭제 시 앞뒤 데이터의 연결을 재구성하는 작업 필요

## 연결리스트 기본 구조

### 노드 (Node)
- 데이터 저장 단위로, 값과 포인터로 구성
  - 포인터 : 다음 노드나 이전 노드의 연결 정보

![](https://velog.velcdn.com/images/yezanee/post/7aa90660-cd7d-4644-966b-596163da06c6/image.png)

## 연결 리스트 기본 연산

### 데이터 추가
- 데이터 추가 위치 (head, 중간, tail)에 따른 연결 작업 필요

![](https://velog.velcdn.com/images/yezanee/post/5dfaae71-c4cf-4ccc-b35f-8c2eccf36a4a/image.png)

1. 추가할 데이터를 담을 노드 생성
2. 링크 연결 작업
3. head 이전 작업

![](https://velog.velcdn.com/images/yezanee/post/94de3143-bbcb-4a50-a9cd-f9ee6f6bbe29/image.png)

1. 추가할 데이터를 담을 노드 생성
2. head로부터 끝 노드까지 순회
3. 링크 연결 작업

![](https://velog.velcdn.com/images/yezanee/post/04200806-b50c-4797-9915-522198dd6675/image.png)

1. 추가할 데이터를 담을 노드 생성
2. head로부터 데이터 추가 위치 직전 노드까지 순회
3. 링크 연결 작업

### 데이터 삭제
- 데이터 삭제 위치(head, 중간, tail)에 따른 연결 작업 필요

![](https://velog.velcdn.com/images/yezanee/post/08512f9b-1182-472f-b035-b711dd02c2b2/image.png)

1. 삭제 대상 노드 지정 (delete_node)
2. head 이전 작업
3. delte_node 삭제

![](https://velog.velcdn.com/images/yezanee/post/429adf2e-896f-4a73-afce-6cef882b92ee/image.png)

1. head로부터 가장 끝까지 순회
2. 끝 노드 삭제
3. 삭제 이전 노드의 링크 처리

![](https://velog.velcdn.com/images/yezanee/post/4bb06770-e3c6-494f-9b49-581a3c2022c1/image.png)

1. head로부터 삭제 대상 노드까지 순회 및 해당 노드 지정 (delete_node)
2. 삭제 대상 이전/이후 노드의 링크 연결 작업
3. delete_node 삭제

</br>

```java
// 선형 자료구조 - 연결 리스트
// 단순 연결 리스트 (simple ver.) 기본 구조 구현

// 노드
class Node {
    int data; // 값
    Node next; // 링크 (자기 자신의 클래스를 가리킬 노드 자료형, 여러 노드들이 있을 때 다음 노드를 가리키는 역할)

    Node() {} // 생성자
    Node(int data, Node next) {
        this.data = data;
        this.next = next;
    }
}

class LinkedList {
    Node head; // 헤드 역할

    LinkedList() {}
    LinkedList(Node node) {
        this.head = node;
    }

    //  연결 리스트 비어있는지 확인
    public boolean isEmpty() {
        if (this.head == null) {
            return true;
        }
        return false;
    }

    //  연결 리스트의 맨 뒤에 데이터 추가
    public void addData(int data) {
        if (this.head == null) { // 노드가 전부 비어있음!
            this.head = new Node(data, null);
        } else {
            Node cur = this.head; // 새로운 변수 잡아서 헤드를 가리키도록
            while (cur.next != null) { // 다음이 없을 때까지 계속 뒤로 이동
                cur = cur.next;
            }
            cur.next = new Node(data, null); // 비어있는 부분에 새로운 노드와 데이터 추가
        }
    }

    //  연결 리스트의 맨 뒤의 데이터 삭제
    public void removeData() {
        if (this.isEmpty()) { // 노드가 텅 비어있으면
            System.out.println("List is empty");
            return;
        }

        Node cur = this.head; // 새로운 변수 잡아서 헤드를 가리키도록
        Node prev = cur; // 쫓아 다니도록, null로 만들기 위해

        while (cur.next != null) {
            prev = cur; // cur 보다 하나 이전!
            cur = cur.next;
        }

        if (cur == this.head) { // 뒤에 아무것도 없는 상태
            this.head = null;
        } else {
            prev.next = null;
        }
    }

    //  연결 리스트에서 데이터 찾기
    public void findData(int data) {
        if (this.isEmpty()) {
            System.out.println("List is empty");
            return;
        }

        Node cur = this.head;
        while (cur != null) { // 데이터가 있다면
            if (cur.data == data) { // cur가 찾고자 하는 데아터와 같은 지 확인
                System.out.println("Data exist!");
                return;
            }
            cur = cur.next; // cur 다음으로
        }
        System.out.println("Data not found!"); // 모두 다 돌았는데도 없다
    }

    //  연결 리스트의 모든 데이터 출력
    public void showData() {
        if (this.isEmpty()) {
            System.out.println("List is empty!");
            return;
        }

        Node cur = this.head; 
        while (cur != null) { // 데이터가 없을때까지 반복
            System.out.print(cur.data + " ");
            cur = cur.next; // 다음으로
        }
        System.out.println();
    }
}


public class Main {

    public static void main(String[] args) {

//      Test Code
        LinkedList myList = new LinkedList(new Node(1, null));
        myList.showData();      // 1

        myList.addData(2);
        myList.addData(3);
        myList.addData(4);
        myList.addData(5);
        myList.showData();      // 1 2 3 4 5

        myList.findData(3);     // Data exist!
        myList.findData(100);   // Data not found!

        myList.removeData();
        myList.removeData();
        myList.removeData();
        myList.showData();      // 1 2

        myList.removeData();
        myList.removeData();
        myList.removeData();    // List is empty

    }

}
```

</br>

```java
// Practice1
// 단순 연결 리스트 구현 완성

class LinkedList2 extends LinkedList {

    LinkedList2(Node node) {
        this.head = node;
    }

    // 연결 리스트에 데이터 추가
    // before_data 가 null 인 경우, 가장 뒤에 추가
    // before_data 에 값이 있는 경우, 해당 값을 가진 노드 앞에 추가
    public void addData(int data, Integer beforeData) {
        if (this.head == null) { // head 에 아무것도 없는 경우
            this.head = new Node(data, null); // 노드를 새로 만들어서 해당 값을 노드에다가 할당
        } else if (beforeData == null) { // 가장 뒤에다가 추가
            Node cur = this.head;
            while (cur.next != null) { // cur 다음이 없을 때까지
                cur = cur.next; // 다음으로
            }
            cur.next = new Node(data, null); // 맨 끝에다가 data 추가
        } else { // 해당 값을 가진 노드 앞에 추가
            Node cur = this.head;
            Node pre = cur; // cur 하나 앞에서 쫓아다닐 변수
            while (cur != null) { // cur의 값이 없을 때까지
                if (cur.data == beforeData) { // 값이 같을 경우
                    if (cur == this.head) { // 노드가 제일 앞에 있다.
                        this.head = new Node(data, this.head); // 앞에다 새로운 노드를 만들고 데이터를 할당
                    } else {
                        pre.next = new Node(data, cur); // 해당 값 한 칸 앞에다 새로운 노드를 만들고 데이터를 할당
                    }
                    break;
                }
                pre = cur;
                cur = cur.next;
            }
        }
    }

    //  연결 리스트에서 특정 값을 가진 노드 삭제
    public void removeData(int data) { // 데이터에 해당하는 노드를 지운다.
        if (this.isEmpty()) {
            System.out.println("List is empty");
            return;
        }

        Node cur = this.head;
        Node pre = cur;
        while (cur != null) {
            if (cur.data == data) { // 지우고자 하는 데이터와 같은 지
                if (cur == this.head) { // 제일 앞이였으면
                    this.head = cur.next; // cur의 다음으로 가리킨다.
                } else {
                    pre.next = cur.next; // pre가 cur의 다음으로 가리킨다.( cur의 값이 없어진다. )
                }
                break;
            }

            pre = cur;
            cur = cur.next;
        }
    }
}

public class Practice1 {
    public static void main(String[] args) {

//      Test code
        LinkedList2 myList = new LinkedList2(new Node(1, null));
        myList.showData();         // 1

        myList.addData(2);
        myList.addData(3);
        myList.addData(4);
        myList.addData(5);
        myList.showData();         // 1 2 3 4 5

        myList.addData(100, 1);
        myList.addData(200, 2);
        myList.addData(300, 3);
        myList.addData(400, 4);
        myList.addData(500, 5);
        myList.showData();         // 100 1 200 2 300 3 400 4 500 5

        myList.removeData(300);
        myList.removeData(100);
        myList.removeData(500);
        myList.removeData(200);
        myList.removeData(400);
        myList.showData();         // 1 2 3 4 5

        myList.removeData(3);
        myList.removeData(1);
        myList.removeData(5);
        myList.removeData(2);
        myList.removeData(4);
        myList.showData();         // List is empty!
    }
}
```

```java
// Practice1
// 단순 연결 리스트 구현 완성

class LinkedList2 extends LinkedList {

    LinkedList2(Node node) {
        this.head = node;
    }

    // 연결 리스트에 데이터 추가
    // before_data 가 null 인 경우, 가장 뒤에 추가
    // before_data 에 값이 있는 경우, 해당 값을 가진 노드 앞에 추가
    public void addData(int data, Integer beforeData) {
        if (this.head == null) { // head 에 아무것도 없는 경우
            this.head = new Node(data, null); // 노드를 새로 만들어서 해당 값을 노드에다가 할당
        } else if (beforeData == null) { // 가장 뒤에다가 추가
            Node cur = this.head;
            while (cur.next != null) { // cur 다음이 없을 때까지
                cur = cur.next; // 다음으로
            }
            cur.next = new Node(data, null); // 맨 끝에다가 data 추가
        } else { // 해당 값을 가진 노드 앞에 추가
            Node cur = this.head;
            Node pre = cur; // cur 하나 앞에서 쫓아다닐 변수
            while (cur != null) { // cur의 값이 없을 때까지
                if (cur.data == beforeData) { // 값이 같을 경우
                    if (cur == this.head) { // 노드가 제일 앞에 있다.
                        this.head = new Node(data, this.head); // 앞에다 새로운 노드를 만들고 데이터를 할당
                    } else {
                        pre.next = new Node(data, cur); // 해당 값 한 칸 앞에다 새로운 노드를 만들고 데이터를 할당
                    }
                    break;
                }
                pre = cur;
                cur = cur.next;
            }
        }
    }

    //  연결 리스트에서 특정 값을 가진 노드 삭제
    public void removeData(int data) { // 데이터에 해당하는 노드를 지운다.
        if (this.isEmpty()) {
            System.out.println("List is empty");
            return;
        }

        Node cur = this.head;
        Node pre = cur;
        while (cur != null) {
            if (cur.data == data) { // 지우고자 하는 데이터와 같은 지
                if (cur == this.head) { // 제일 앞이였으면
                    this.head = cur.next; // cur의 다음으로 가리킨다.
                } else {
                    pre.next = cur.next; // pre가 cur의 다음으로 가리킨다.( cur의 값이 없어진다. )
                }
                break;
            }

            pre = cur;
            cur = cur.next;
        }
    }
}

public class Practice1 {
    public static void main(String[] args) {

//      Test code
        LinkedList2 myList = new LinkedList2(new Node(1, null));
        myList.showData();         // 1

        myList.addData(2);
        myList.addData(3);
        myList.addData(4);
        myList.addData(5);
        myList.showData();         // 1 2 3 4 5

        myList.addData(100, 1);
        myList.addData(200, 2);
        myList.addData(300, 3);
        myList.addData(400, 4);
        myList.addData(500, 5);
        myList.showData();         // 100 1 200 2 300 3 400 4 500 5

        myList.removeData(300);
        myList.removeData(100);
        myList.removeData(500);
        myList.removeData(200);
        myList.removeData(400);
        myList.showData();         // 1 2 3 4 5

        myList.removeData(3);
        myList.removeData(1);
        myList.removeData(5);
        myList.removeData(2);
        myList.removeData(4);
        myList.showData();         // List is empty!
    }
}
```

</br>

```java
// Practice2
// 양방향 연결 리스트 (Doubly Linked List) 구현

class NodeBi {
    int data;
    NodeBi next;
    NodeBi prev;

    NodeBi(int data, NodeBi next, NodeBi prev) {
        this.data = data;
        this.next = next;
        this.prev = prev;
    }
}

class DoublyLinkedList extends LinkedList { // 양방향 LinkedList
    NodeBi head;
    NodeBi tail;

    DoublyLinkedList(NodeBi node) { // 처음에는 head와 tail이 같은 곳 가리키도록
        this.head = node;
        this.tail = node;
    }

    //  연결 리스트 비어있는지 확인
    public boolean isEmpty() {
        if (this.head == null) {
            return true;
        }
        return false;
    }

    // 연결 리스트에 데이터 추가
    // before_data 가 null 인 경우, 가장 뒤에 추가
    // before_data 에 값이 있는 경우, 해당 값을 가진 노드 앞에 추가
    public void addData(int data, Integer beforeData) {
        if (this.head == null) { // head가 비어있다면
            this.head = new NodeBi(data, null, null); // 새로운 노드를 만들어서 값을 할당
            this.tail = this.head; // tail도 같은 노드를 기리킬 수 있도록 할당
        } else if (beforeData == null) { // 가장 끝에 추가하는 경우
            this.tail.next = new NodeBi(data, null, this.tail); // tail을 관리하므로(기존 노드의 끝), 바로 추가 가능
            this.tail = this.tail.next; // tail이 원래 tail이 가리키던 노드의 다음 노드를 가리킴
        } else {
            NodeBi cur = this.head; // 찾을 대상
            NodeBi pre = cur;
            while (cur != null) {
                if (cur.data == beforeData) {
                    if (cur == this.head) { // 찾은 노드가 맨 처음인 head
                        this.head = new NodeBi(data, this.head, null);
                        this.head.next.prev = this.head; // prev를 바뀐 head로 바리킴
                    } else { // head가 아닐 때
                        pre.next = new NodeBi(data, cur, pre);
                        cur.prev = pre.next;
                    }
                    break;
                }
                pre = cur;
                cur = cur.next;
            }
        }
    }

    //  연결 리스트에서 특정 값을 가진 노드 삭제
    public void removeData(int data) {
        if (this.isEmpty()) {
            System.out.println("List is empty");
            return;
        }

        NodeBi cur = this.head;
        NodeBi pre = cur;

        while (cur != null) {
            if (cur.data == data) {
                if (cur == this.head && cur == this.tail) { // 노드가 1개인 케이스
                    this.head = null; // 해당 노드가 삭제되면 head든, tail이든
                    this.tail = null; // 텅 비어있게 된다.
                } else if (cur == this.head) { // 노드가 1개는 아닌 상황
                    this.head = cur.next; // head를 다음으로 가리킨다.
                    this.head.prev = null; // 이전 노드를 없앤다.
                } else if (cur == this.tail) { // 찾은 노드가 가장 끝인 경우
                    this.tail = this.tail.prev; // tail을 기존 tail의 이전으로
                    this.tail.next = null; // 기존의 노드 삭제
                } else { // 중간 노드 삭제
                    pre.next = cur.next; // pre의 다음이 cur의 다음이 오도록
                    cur.next.prev = pre; // cur의 다음의 prev를 원래의 pre가 되도록.
                }
                break;
            }

            pre = cur;
            cur = cur.next;
        }
    }

    //  연결 리스트의 모든 데이터 출력
    public void showData() {
        if (this.isEmpty()) {
            System.out.println("List is empty!");
            return;
        }

        NodeBi cur = this.head;
        while (cur != null) {
            System.out.print(cur.data + " ");
            cur = cur.next;
        }
        System.out.println();
    }

    //  연결 리스트의 모든 데이터 출력 (tail 부터)
    public void showDataFromTail() {
        if (this.isEmpty()) {
            System.out.println("List is empty");
            return;
        }

        NodeBi cur = this.tail;
        while (cur != null) {
            System.out.print(cur.data + " ");
            cur = cur.prev;
        }
        System.out.println();
    }

}

public class Practice2 {
    public static void main(String[] args) {

//      Test code
        DoublyLinkedList myList = new DoublyLinkedList(new NodeBi(1, null, null));
        myList.showData();          // 1

        myList.addData(2, null);
        myList.addData(3, null);
        myList.addData(4, null);
        myList.addData(5, null);
        myList.showData();          // 1 2 3 4 5
        myList.showDataFromTail();  // 5 4 3 2 1

        myList.addData(100, 1);
        myList.addData(200, 2);
        myList.addData(300, 3);
        myList.addData(400, 4);
        myList.addData(500, 5);
        myList.showData();          // 100 1 200 2 300 3 400 4 500 5
        myList.showDataFromTail();  // 5 500 4 400 3 300 2 200 1 100

        myList.removeData(300);
        myList.removeData(100);
        myList.removeData(500);
        myList.removeData(200);
        myList.removeData(400);
        myList.showData();          // 1 2 3 4 5
        myList.showDataFromTail();  // 5 4 3 2 1

        myList.removeData(3);
        myList.removeData(1);
        myList.removeData(5);
        myList.removeData(2);
        myList.removeData(4);
        myList.showData();          // List is empty!
        myList.showDataFromTail();  // List is empty!
    }
}
```

</br>

```java
// Practice3
// 원형 연결 리스트 (Circular Linked List) 구현

class CircularLinkedList {
    NodeBi head;
    NodeBi tail;

    CircularLinkedList(NodeBi node) {
        this.head = node;
        this.tail = node;
        node.next = this.head; // 자기자신으로 다시 순환할 수 있도록
        node.prev = this.head; // 원형 형태로 구현한다.
    }

    public boolean isEmpty() {
        if (this.head == null) {
            return true;
        }
        return false;
    }

    // 연결 리스트에 데이터 추가
    // before_data 가 null 인 경우, 가장 뒤에 추가
    // before_data 에 값이 있는 경우, 해당 값을 가진 노드 앞에 추가
    public void addData(int data, Integer beforeData) {
        if (this.head == null) {
            NodeBi newNodeBi = new NodeBi(data, null, null);
            this.head = newNodeBi;
            this.tail = newNodeBi;
            newNodeBi.next = newNodeBi;
            newNodeBi.prev = newNodeBi;
        } else if (beforeData == null) { // 가장 뒤에 추가
            NodeBi newNodeBi = new NodeBi(data, this.head, this.tail);
            this.tail.next= newNodeBi;
            this.head.prev = newNodeBi;
            this.tail = newNodeBi; // 가장 뒤에 값 추가
        } else {
            NodeBi cur = this.head;
            NodeBi pre = cur;
            do {
                if (cur.data == beforeData) {
                    if (cur == this.head) {
                        NodeBi newNodeBi = new NodeBi(data, this.head, this.tail);
                        this.tail.next = newNodeBi;
                        this.head.prev = newNodeBi;
                        this.head = newNodeBi;
                    } else { // 노드가 중간에 추가
                        NodeBi newNodeBi = new NodeBi(data, cur, pre);
                        pre.next = newNodeBi;
                        cur.prev = newNodeBi;
                    }
                    break;
                }
                pre = cur;
                cur = cur.next;
            } while (cur != this.head);
        }
    }

    //  연결 리스트에서 특정 값을 가진 노드 삭제
    public void removeData(int data) {
        if (this.isEmpty()) {
            System.out.println("List is empty");
            return;
        }

        NodeBi cur = this.head;
        NodeBi pre = cur;
        while (cur != null) {
            if (cur.data == data) { // 삭제하려고 하는 데이터의 노드를 찾았을 때
                if (cur == this.head && cur == this.tail) { // 노드가 하나 뿐일때
                    this.head = null;
                    this.tail = null;
                } else if (cur == this.head) { // head 일때
                    cur.next.prev = this.head.prev;
                    this.head = cur.next;
                    this.tail.next = this.head;
                } else if (cur == this.tail) { // tail 일때
                    pre.next = this.tail.next;
                    this.tail = pre;
                    this.head.prev = this.tail;
                } else { // 중간 일때
                    pre.next = cur.next;
                    cur.next.prev = pre;
                }
                break;
            }

            pre = cur;
            cur = cur.next;
        }
    }

    public void showData() {
        if (this.isEmpty()) {
            System.out.println("List is empty!");
            return;
        }

        NodeBi cur = this.head;
        while (cur.next != this.head) {
            System.out.print(cur.data + " ");
            cur = cur.next;
        }
        System.out.println(cur.data);
    }
}

public class Practice3 {
    public static void main(String[] args) {
        // Test code
        CircularLinkedList myList = new CircularLinkedList(new NodeBi(1, null, null));
        myList.addData(2, null);
        myList.addData(3, null);
        myList.addData(4, null);
        myList.addData(5, null);
        myList.showData();  // 1 2 3 4 5

        myList.addData(100, 1);
        myList.addData(200, 2);
        myList.addData(300, 3);
        myList.addData(400, 4);
        myList.addData(500, 5);
        myList.showData();  // 100 1 200 2 300 3 400 4 500 5

        myList.removeData(300);
        myList.removeData(100);
        myList.removeData(500);
        myList.removeData(200);
        myList.removeData(400);
        myList.showData();          // 1 2 3 4 5

        myList.removeData(3);
        myList.removeData(1);
        myList.removeData(5);
        myList.removeData(2);
        myList.removeData(4);
        myList.showData();          // List is empty!
    }
}
```
