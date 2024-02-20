# 트리 (Tree)
- 노드와 링크로 구성된 자료구조 (그래프의 일종, Cycle 없음)
- 계층적 구조를 나타낼 때 사용
  - 폴더 구조 (디렉토리, 서브 디렉토리)
  - 조직도, 가계도, ...

</br>

## 트리의 구조
![](https://velog.velcdn.com/images/yezanee/post/48fc0891-e0f0-427e-b51b-03b9ae5179ef/image.png)

- 노드(Node): 트리 구조의 자료 값을 담고 있는 단위
- 엣지(Edge): 노드 간의 연결선(=link, branch)
- 루트 노드(Root): 부모가 없는 노드, 가장 위의 노드
- 잎새 노드(Leaf): 자식이 없는 노드 (=단말)
- 내부 노드(Internal): 잎새 노드를 제외한 모든 노드
- 부모(Parent): 연결된 두 노드 중 상위의 노드
- 자식(Child): 연결된 두 노드 중 하위의 노드
- 형제(Sibling): 같은 부모는 가지는 노드
- 깊이(Depth): 루트에서 어떤 노드까지의 간선의 수
- 레벨(Level): 트리의 특정 깊이를 가지는 노드 집합
- 높이(Height): 트리에서 가장 큰 레벨 값
- 크기(Size): 자신을 포함한 자식 노드의 개수
- 차수(Degreee): 각 노드가 지닌 가지의 슈ㅜ
- 트리의 차수: 트리의 최대 차수

</br>

## 트리의 특징
- 하나의 노드에서 다른 노드로 이동하는 경로는 유일
- 노드가 N개인 트리의 Edge의 수는 N-1개
- Acyclic (Cycle이 존재하지 않음)
- 모든 노드는 서로 연결되어 있음
- 하나의 Edge를 끊으면 2개의 Sub-Tree로 분리됨

</br>

# 이진 트리 (Binary Tree)
- 각 노드는 최대 2개의 자식을 가질 수 있음
- 자식 노드는 좌우를 구분함
  - 왼쪽 자식: 부모 노드의 왼쪽 아래
  - 오른쪽 자식: 부모 노드의 오른쪽 아래

![](https://velog.velcdn.com/images/yezanee/post/7f013288-27b4-499a-9950-70a101ab726b/image.png)

</br>

## 이진 트리 종류 (1)
- 포화 이진 트리 (Perfect Binary Tree)
  - 모든 레벨에서 노드들이 꽉 채워져 있는 트리
  
- 완전 이진 트리 (Complete Binary Tree)
  - 마지막 레벨을 제외하고 노드들이 모두 채워져 있는 트리
  
![](https://velog.velcdn.com/images/yezanee/post/521af489-86a3-4d35-84c1-2a5a584f2f45/image.png)

</br>


## 이진 트리 종류 (2)
- 정 이진 트리 (Full Binary Tree)
  - 모든 노드가 0개 또는 2개의 자식 노드를 갖는 트리
- 편향 트리 (Skewed Binary Tree) = 사향 트리
  - 한쪽으로 기울어진 트리
  
![](https://velog.velcdn.com/images/yezanee/post/eb38998f-d9ef-4a86-be33-b311bc5f9664/image.png)

</br>

## 이진 트리 종류 (3)
- 균형 이진 트리 (Balanced Binary Tree)
  - 모든 노드의 좌우 서브 트리 높이가 1이상 차이 나지 않는 트리

![](https://velog.velcdn.com/images/yezanee/post/b1a75103-1f57-4e47-b047-0e72353d3403/image.png)

</br>

## 이진 트리 특징
- 포화 이진 트리의 높이가 h일 때, 노드의 수는 2^h+1 - 1개
- 포화(or 완전) 이진 트리의 노드가 N개 일 때, 높이는 logN
- 이진 트리의 노드가 N개 일 때, 최대 가능 높이는 N

</br>

## 이진 트리의 순회 (Traversal)
- 모든 노드를 빠뜨리거나 중복하지 않고 방문하는 연산
- 순회 종류는 4가지
  - 전위 순회, 중위 순회, 후위 순회,
  - 레벨 순회
  
</br>

## 이진 트리의 순회 - 전위 순회
- Preorder Traversal
- 방문 순서: 현재 노드 → 왼쪽 노드 → 오른쪽 노드

![](https://velog.velcdn.com/images/yezanee/post/4ec78fb8-f8ad-458d-8b0a-0a099c57454d/image.png)

</br>

## 이진 트리의 순회 - 중위 순회
- Inorder Traversal
- 방문 순서: 왼쪽 노드 → 현재 노드 → 오른쪽 노드

![](https://velog.velcdn.com/images/yezanee/post/b1154fb7-942d-4c54-b0bf-d46453c3f0b3/image.png)

</br>

## 이진 트리의 순회 - 후위 순회
- Postorder Traversal
- 방문 순서: 왼쪽 노드 → 오른쪽 노드 → 현재 노드

![](https://velog.velcdn.com/images/yezanee/post/67e1df5a-941b-45f5-aa8a-1d71ded33e7e/image.png)

</br>

## 이진 트리의 순회 - 레벨 순회
- Levelorder Traversal
- 방문 순서: 위쪽 레벨부터 왼쪽 노드 → 오른쪽 노드

![](https://velog.velcdn.com/images/yezanee/post/e493baa4-c05b-4c7f-afa2-ba3c57a2473f/image.png)

</br>

## 이진 트리 구현
- 배열
  - 레벨 순회 순으로 배열에 구성
  
![](https://velog.velcdn.com/images/yezanee/post/c9c53b50-ab4c-4e00-8f95-291129a45ea5/image.png)

- 연결 리스트
  - 값과 간선을 관리하기 위한 노드로 연결리스트 구성
  
```java
// Practice1
// 배열을 이용한 이진 트리 구성, 순회

class BinaryTree {
    char[] arr;

    BinaryTree(char[] data) {
        this.arr = data.clone();
    }
    // 받아온 데이터를 클론해주는 형태

    public void preOrder(int idx) {
        System.out.print(this.arr[idx] + " ");
        // 처음에 들어온 인덱스에 해당하는 데이터 출력 (현재)

        int left = 2 * idx + 1;
        int right = 2 * idx + 2;
        if (left < this.arr.length) { // 왼쪽의 인덱스가 배열 범위 안에 들어 있으면 (왼쪽)
            this.preOrder(left); // 재귀 함수 형태로 (왼쪽이 출력)
        }
        if (right < this.arr.length) { // 오른쪽 인덱스가 뱌열 범위 안에 들어 있으면 (오른쪽)
            this.preOrder(right); // 재귀 함수 형태로 (오른쪽이 출력)
        }
    }

    public void inOrder(int idx) {
        int left = 2 * idx + 1; // 왼쪽 자식 인덱스
        int right = 2 * idx + 2; // 오른쪽 자식 인덱스

        if (left < this.arr.length) {
            this.inOrder(left); // 왼쪽으로 먼저 쭉 내려간 다음 (재귀)
        }

        System.out.print(this.arr[idx] + " "); // 현재 출력

        if (right < this.arr.length) {
            this.inOrder(right); // 오른쪽으로 쭉 내려감 (재귀)
        }
    }

    public void postOrder(int idx) {
        int left = 2 * idx + 1;
        int right = 2 * idx + 2;

        if (left < this.arr.length) {
            this.postOrder(left); // 왼쪽으로 먼저 쭉 내려간 다음 (재귀)
        }

        if (right < this.arr.length) {
            this.postOrder(right); // 오른쪽으로 쭉 내려감 (재귀)
        }

        System.out.print(this.arr[idx] + " "); // 현재 출력
    }

    public void levelOrder(int idx) {
        for (int i = idx; i < this.arr.length; i++) {
            System.out.print(this.arr[i] + " ");
        }
        System.out.println();
    }
}

public class Practice1 {
    public static void main(String[] args) {
        // Test code
        char[] arr = new char[10];
        for (int i = 0; i < arr.length; i++) {
            arr[i] = (char)('A' + i);
        }

        BinaryTree bt = new BinaryTree(arr);

        System.out.println("== Preorder ==");
        bt.preOrder(0);
        System.out.println();

        System.out.println("== Inorder ==");
        bt.inOrder(0);
        System.out.println();

        System.out.println("== Postorder ==");
        bt.postOrder(0);
        System.out.println();

        System.out.println("== Levelorder ==");
        bt.levelOrder(0);
        System.out.println();
    }
}
```

<실행 결과>

```
== Preorder ==
A B D H I E J C F G 
== Inorder ==
H D I B J E A F C G 
== Postorder ==
H I D J E B F G C A 
== Levelorder ==
A B C D E F G H I J 
```

</br>

```java
// Practice2
// 연결 리스트를 이용한 이진 트리 구성, 순회

import java.util.LinkedList;
import java.util.Queue;

class Node {
    char data;
    Node left;
    Node right;

    Node(char data, Node left, Node right) {
        this.data = data;
        this.left = left;
        this.right = right;
    }
}

class BinaryTree2 {
    Node head;

    BinaryTree2() {}
    BinaryTree2(char[] arr) { // 연결 작업 하는 부분 (기본 트리 구조)
        Node[] nodes = new Node[arr.length]; // char[] arr 배열을 노드 형태의 배열로 만들어 준다.
        for (int i = 0; i < arr.length; i++) {
            nodes[i] = new Node(arr[i], null, null);
        }

        for (int i = 0; i < arr.length; i++) { // 현재 노드에 대해서 자식 노드들을 찾아준다.
            int left = 2 * i + 1;
            int right = 2 * i + 2;

            if (left < arr.length) { // 왼쪽 범위 체크
                nodes[i].left = nodes[left]; // 노드 연결
            }

            if (right < arr.length) { // 오른쪽 범위 체크
                nodes[i].right = nodes[right]; // 노드 연결
            }

        }
        this.head = nodes[0]; // 루트 노드에 대한 연결 부분
    }

    public void preOrder(Node node) { // 전위 순회
        if (node == null) { // 노드가 비어 있으면 (재귀함수 탈출 조건)
            return;
        }

        System.out.print(node.data + " "); // 현재
        preOrder(node.left); // 왼쪽
        preOrder(node.right); // 오른쪽
    }

    public void inOrder(Node node) { // 중위 순회
        if (node == null) { // 노드가 비어 있으면 (재귀함수 탈출 조건)
            return;
        }

        inOrder(node.left); // 왼쪽
        System.out.print(node.data + " "); // 현재
        inOrder(node.right); // 오른쪽
    }

    public void postOrder(Node node) { // 후위 순회
        if (node == null) { // 노드가 비어 있으면 (재귀함수 탈출 조건)
            return;
        }

        postOrder(node.left); // 왼쪽
        postOrder(node.right); // 오른쪽
        System.out.print(node.data + " "); // 현재
    }

    public void levelOrder(Node node) { // 레벨 순회 (재귀 함수로 이용하면 오히려 불편이요)
        // 큐에다 A 넣고 pop하고 링크 검사(B와 C), B pop하고 링크 검사(D와 E), C pop하고 링크 검사(F와 G) D pop 하고 링크 검사 (없음) ...
        Queue<Node> queue = new LinkedList<>(); // 큐 이용!
        queue.add(node); // 현재 노드부터 추가
        while (!queue.isEmpty()) { // 큐가 비어 있지 않는 동안 순회
            Node cur = queue.poll(); // 큐에서 하나 꺼냄

            System.out.print(cur.data + " "); // 출력
            if (cur.left != null) { // 링크 검사
                queue.offer(cur.left); // 자식 노드가 있으면 큐에다가 다시 넣어줌
            }

            if (cur.right != null) { // 링크 검사
                queue.offer(cur.right); // 자식 노드가 있으면 큐에다가 다시 넣어줌
            }
        }
    }
}


public class Practice2 {
    public static void main(String[] args) {
        // Test code
        char[] arr = new char[10];
        for (int i = 0; i < arr.length; i++) {
            arr[i] = (char)('A' + i);
        }

        BinaryTree2 bt = new BinaryTree2(arr);

        System.out.println("== Preorder ==");
        bt.preOrder(bt.head);
        System.out.println();

        System.out.println("== Inorder ==");
        bt.inOrder(bt.head);
        System.out.println();

        System.out.println("== Postorder ==");
        bt.postOrder(bt.head);
        System.out.println();

        System.out.println("== Levelorder ==");
        bt.levelOrder(bt.head);
        System.out.println();
    }
}
```

<실행 결과>

```
== Preorder ==
A B D H I E J C F G 
== Inorder ==
H D I B J E A F C G 
== Postorder ==
H I D J E B F G C A 
== Levelorder ==
A B C D E F G H I J 
```

</br>

```java
// Practice3
// 트리 구조 복습 / 구현

import java.util.LinkedList;
import java.util.Queue;

class Node2 {
    char data; // 데이터 값
    Node2 left; // 왼쪽 자식 노드
    Node2 right; // 오른쪽 자식 노드
    Node2 parent; // 부모 노드

    public Node2(char data, Node2 left, Node2 right, Node2 parent) { // 생성자
        this.data = data;
        this.left = left;
        this.right = right;
        this.parent = parent;
    }
}

class BinaryTree3 {
    Node2 head; // 헤드

    BinaryTree3(char[] arr) { // 생성자
        Node2[] nodes = new Node2[arr.length];
        for (int i = 0; i < arr.length; i++) {
            nodes[i] = new Node2(arr[i], null, null, null);
        } // 각각의 노드들 초기화 시켜 놓가

        for (int i = 0; i < arr.length; i++) { // 자식 노드에 대한 인덱스 찾기
            int left = 2 * i + 1;
            int right = 2 * i + 2;

            if (left < arr.length) { // 범위 비교
                nodes[i].left = nodes[left];
                nodes[left].parent = nodes[i]; // 부모쪽도 연결!
            }

            if (right < arr.length) { // 범위 비교
                nodes[i].right = nodes[right];
                nodes[right].parent = nodes[i]; // 부모 쪽도 연결!
            }

        }
        this.head = nodes[0]; // 헤드에다 루트 노드
    }

    public Node2 searchNode(char data) {
        Queue<Node2> queue = new LinkedList(); // 큐를 만듬
        queue.add(this.head); // 탐색 시점은 헤드로부터 출발
        while (!queue.isEmpty()) { // 큐가 비어있지 않을 때까지 반복
            Node2 cur = queue.poll(); // 큐에 데이터 꺼내기
            if (cur.data == data) { // 찾고자 하는 데이터이면
                return cur; // 현재 위치의 노드 반환
            }

            if (cur.left != null) {
                queue.offer(cur.left);
            }

            if (cur.right != null) {
                queue.offer(cur.right);
            }
        }
        return null;
    }

    public Integer checkSize(char data) { // 데이터가 해당하는 노드로부터의 사이즈를 체크해서 반환
        Node2 node = this.searchNode(data); // 해당 노드를 먼저 찾아줌

        Queue<Node2> queue = new LinkedList(); // 큐 구조 이용
        queue.add(node);
        int size = 0;
        while (!queue.isEmpty()) { // 큐가 빌 때까지
            Node2 cur = queue.poll(); // 큐에서 데이터를 꺼낸다.

            if (cur.left != null) { // 왼쪽이 비어있지 않으면
                queue.offer(cur.left); // 큐에다 넣어줌
                size++; // 순회 가능할 때마다 사이즈 늘어남
            }

            if (cur.right != null) { // 오른쪽이 비어있지 않으면
                queue.offer(cur.right); // 큐에다 넣어줌
                size++; // 순회 가능할 때마다 사이즈 늫어남
            }
        }
        return size + 1;
    }
}

public class Practice3 {

    public static void main(String[] args) {
        char[] arr = new char[10];
        for (int i = 0; i < arr.length; i++) {
            arr[i] = (char)('A' + i);
        }

        BinaryTree3 bt = new BinaryTree3(arr);

        // Root node
        System.out.println("Root: " + bt.head.data); // 루트 노드 출력


        // B's child node
        Node2 B = bt.searchNode('B');
        if (B.left != null) { // 왼쪽 자식 노드가 비어있지 않으면
            System.out.println("B -> left child: " + B.left.data); // 출력
        }
        if (B.right != null) { // 오른쪽 자식 노드가 비어있지 않으면
            System.out.println("B -> right child: " + B.right.data); // 출력
        }


        // F's parent node
        Node2 F = bt.searchNode('F');
        System.out.println("F -> parent: " + F.parent.data);


        // Leaf node
        System.out.print("Leaf node: "); // 자식 노드가 없는 노드들
        for (int i = 0; i < arr.length; i++) {
            Node2 cur = bt.searchNode((char)('A' + i)); // 각각의 노드들을 찾는다.

            if (cur.left == null && cur.right == null) { // 찾은 각각의 노드들에 대한 자식노드들을 찾는다. (리프노드 찾기)
                System.out.print(cur.data + " "); // 출력
            }
        }
        System.out.println();


        // E's Depth
        Node2 E = bt.searchNode('E'); // 루트노드부터 E라는 노드까지의 간선 (몇번 거침?)
        Node2 cur = E;
        int cnt = 0;
        while (cur.parent != null) { // 부모가 비어있지 않을 때까지
            cur = cur.parent; // 부모로 이동!
            cnt++; // 개수 +1 (간선의 길이)
        }
        System.out.println("E depth: " + cnt);


        // Level2 Node
        System.out.print("Level2 Node: ");
        for (int i = 0; i < arr.length; i++) {
            Node2 target = bt.searchNode((char)('A' + i)); // 각각의 노드들을 찾아준다.
            cur = target;
            cnt = 0;
            while (cur.parent != null) { // 리프노드까지
                cur = cur.parent; // 부모 노드로 이동
                cnt++; // 개수 +1 (간선의 길이)
            }

            if (cnt == 2) { // 레벨 2에 해당하는 노드들
                System.out.print(target.data + " ");
            }
        }
        System.out.println();


        // Height
        int maxCnt = Integer.MIN_VALUE; // 최대 깊이를 찾기 위해 최솟값을 넣어준다.
        for (int i = 0; i < arr.length; i++) {
            Node2 target = bt.searchNode((char)('A' + i)); // 각각의 노드들을 찾아준다.
            cur = target;
            cnt = 0;
            while (cur.parent != null) {
                cur = cur.parent;
                cnt++;
            }

            if (maxCnt < cnt) { // maxCnt와 비교해준다.
                maxCnt = cnt; // 가장 큰 depthr값이 들어간다.
            }
        }
        System.out.println("Height: " + maxCnt);


        // B's Size
        int size = bt.checkSize('B');
        System.out.println("B size = " + size);

    }
}
```

<실행 결과>

```
Root: A
B -> left child: D
B -> right child: E
F -> parent: C
Leaf node: F G H I J 
E depth: 2
Level2 Node: D E F G 
Height: 3
B size = 6
```

</br>

```java
// Practice1 (난이도 하)
// 종이 접기
// 종이를 반으로 접었을 때, 안으로 파인 부분은 0, 볼록 튀어나온 부분은 1이라고 하자.
// 종이를 접을 때는 오른쪽에서 왼쪽으로 접는다.
// 종이를 N번 접었을 때의 접힌 상태(0 또는 1)를 출력하는 문제를 작성하세요.

// 입출력 예시
// 입력: 1
// 출력: 0

// 입력: 2
// 출력: 0, 0, 1

// 입력: 3
// 출력: 0, 0, 1, 0, 0, 1, 1


public class Practice1 {
    public static void solution(int n) {
        int[] binaryTree = new int[(int)Math.pow(2, n)];

        binaryTree[0] = 0;
        for (int i = 0; i < (int) Math.pow(2, n - 1) - 1; i++) {
            binaryTree[i * 2 + 1] = 0;
            binaryTree[i * 2 + 2] = 1;
        }

        inOrder(binaryTree, 0);
        System.out.println();
    }

    public static void inOrder(int[] arr, int idx) {
        int left = 2 * idx + 1;
        int right = 2 * idx + 2;

        if (left < arr.length - 1) {
            inOrder(arr, left);
        }

        System.out.print(arr[idx] + " ");

        if (right < arr.length - 1) {
            inOrder(arr, right);
        }
    }

    public static void main(String[] args) {
        // Test code
        solution(1);
        solution(2);
        solution(3);
    }
}
```

</br>

```java
// Practice2
// 각각의 에지에 가중치가 있는 포화 이진 트리가 있다.
// 루트에서 각 리프까지의 경로 길이를 모두 같게 설정하고,
// 이 때, 모든 가중치들의 총합이 최소가 되도록 하는 프로그램을 작성하세요.

class BinaryTree {
    int h;
    int[] arr;
    int res;

    public BinaryTree(int h, int[] w) {
        this.h = h;
        // 이렇게 만들고 0번 위치 인덱스는 사용 X
        arr = new int[(int)Math.pow(2, h + 1)];
        res = 0;

        // 포화 이진 트리의 간선의 수는 노드 수 - 1로 2부터 저장
        for (int i = 2; i < (int)Math.pow(2, h + 1); i++) {
            arr[i] = w[i - 2];
        }
    }

    // 하단 부터 형제 노드의 간선을 맞춰 나가면서 진행
    public int dfs(int idx, int h) {
        if(this.h == h) {
            res += arr[idx];
            return arr[idx];
        }

        int left =  dfs(idx * 2, h + 1);
        int right = dfs(idx * 2 + 1, h + 1);
        res += arr[idx] + Math.abs(left - right);
        return arr[idx] + Math.max(left, right);
    }
}

public class Practice2 {
    public static void solution(int h, int[] w) {
        BinaryTree bt = new BinaryTree(h, w);
        bt.dfs(1, 0);
        System.out.println(bt.res);
    }

    public static void main(String[] args) {
        // Test code
        int h = 2;
        int[] w = {2, 2, 2, 1, 1, 3};
        solution(h, w);
        System.out.println();

        h = 3;
        w = new int[]{1, 2, 1, 3, 2, 4, 1, 1, 1, 1, 1, 1, 1, 1};
        solution(h, w);
    }
}
```
