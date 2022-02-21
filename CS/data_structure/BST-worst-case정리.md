# Q. BST의 worst case 시간복잡도는  O(n)입니다. 어떠한 경우에 worst case가 발생하나요? 해결방법은 무엇인가요?  (⭐)

## 나의 답변

### BST worst case 발생 경우
- Binary Search Tree(이진 탐색 트리)는 부모노드의 왼쪽에는 작은 값이, 오른쪽에는 큰 값이 들어간다.
- heap을 이용해서 구현 가능하다.
- worstcase가 발생하는 경우는, 모두 확인해야되는 경우로, 오름차순으로 값이 들어올 경우입니다.
- 그래서 한쪽으로 치우쳐진 트리모양을 할때 worst case

### 해결방법
- 균형이진트리로 만들어야함
- AVL 트리, Red-Black 트리 등이 있다.
