## 알고리즘

올바른 값을 도출은 했지만, 정해진 시간 내에 동작을 하지 않아 실제 코딩 테스트에서 fail이 나는 경우가 있다. 우리는 이러한 문제를 해결 하기 위해 시간 복잡도 등을 고려하여 알고리즘을 설계해 조금 더 효율적으로 코딩을 할 수 있다.

</br>

### 알고리즘이란?
> 어떤 문제를 해결하기 위한 **절차**나 **방법**.
따라서 각각의 알고리즘에는 정형화 된 flow가 있다.

</br>

### 알고리즘의 조건
- 입력: 입력 값이 정의 되어 있어야 어떤 동작을 할 지가 정해진다.
- 출력: 각 입력에 맞는 올바른 출력이 되어야 한다.
- 명확성: 알고리즘이 무슨 동작을 해야 되는가 명확하게 정해져야 한다.
- 유한성: 정해진 시간 내에 알고리즘이 올바르게 작동되어야 한다.
- 효율성: 시간 복잡도, 공간 복잡도 등이 최대한 효율성 있게 짜여져야 된다.

</br>

> **실생활의 예를 들어 위의 알고리즘 조건이 필요한 이유를 더 명확하게 이해보도록 하자.** </br>
- 우리가 아이스크림 가게를 운영한다고 하자. 아이스크림 기계에는 여러가지 맛의 버튼들이 있다. **그 버튼들이 입력**이 될 것이다.
- 우리가 초코맛 버튼을 눌렀는데 바닐라맛 아이스크림이 추출된다면 문제가 될 것이다. 따라서, 각 **입력에 맞는 올바른 출력**이 되어야 한다.
- 명확성이라고 함은 동작 방식이다. 우리가 버튼을 한번 눌렀을 때, 일정량의 아이스크림이 나오거나 버튼을 계속 누르고 있는 동안에만 아이스크림이 나오는 등 **동작에 대한 flow가 명확**해야 한다.
- 또한, 아이스크림을 한번 뽑아내는 데에 10분 이상이 걸린다면 장사를 할 수 없을 것이다. 10초 이내로 아이스크림을 뽑아내는 등 **유한성 내에 출력**이 되도록 한다.
- 위의 조건들을 모두 만족하면 동작은 제대로 되겠지만, 아이스크림이 하나에 천원인데 아이스크림을 한번 뽑아내는 데에 전력이 900원 정도가 든다면 이윤을 내기 힘들 것이다. **효율성은 이러한 전력을 줄여주는** 거라고 보면 된다.

</br>

### 좋은 알고리즘
- 정확성
- 시간 복잡도
- 공간 복잡도

</br>

### 알고리즘  SUMMARY
- 정렬
- 이진 탐색 / 투 포인터
- 그리디 알고리즘
- 분할 정복 / 다이나믹 프로그래밍
- 백 트래킹
- 최단 경로
- 최소 신장 트리