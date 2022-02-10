## 트리 (Tree)
- 노드로 이루어진 자료구조
- 트리는 하나의 루트 노드를 갖는다.
- 루트 노드는 0개 이상의 자식 노드를 갖고 있다.
- 자식 노드 또한 0개 이상의 노드를 갖고 있고, 반복적으로 정의된다.

## 이진 트리 (Binary tree)
![image](https://user-images.githubusercontent.com/61968474/153439104-392ad90d-0a7a-414a-acc7-74c558a73995.png)

- 각각의 노드가 최대 두 개의 자식 노드를 가지는 트리 자료구조
- 자식 노드를 각각 왼쪽 자식 노드, 오른쪽 자식 노드라고 한다.

### 이진 탐색 트리 (Binary search tree)

- 모든 노드가 '모든 왼쪽 자식 < n <= 모든 오른쪽 자식' 속성에 대해 반드시 참이어야 한다. (중복된 값은 경우에 따
라 다를 수 있음)
<img width="200" alt="스크린샷 2022-02-11 오전 12 35 47" src="https://user-images.githubusercontent.com/61968474/153441457-6a1b5479-66d1-4452-b05d-6ee85d640b9e.png">

### 완전 이진 트리 (Complete binary tree)
- 모든 높이에서 노드가 꽉차 있는 이진 트리를 말한다.
- 마지막 단계에서는 꽉 차 있지 않아도 되지만, 노드가 왼쪽에서 오른쪽으로 채워져야 한다.

### 전 이진 트리 (Full binary tree)
- 모든 노드의 자식이 없거나 정확히 두 개 있는 경우
- 자식이 하나만 있는 노드가 존재해서는 않된다.

### 포화 이진 트리 (Perfect binary tree )
- 전 이진 트리이면서 완전 이진 트리인 경우
- 모든 말단 노드는 같은 높이에 있어야 하며, 마지막 단계에서 노드의 개수가 최대가 되어야 한다.
- k단계의 노드의 개수는 정확히 2^(k-1)개여야 한다.

## 균형 vs 비균형
**추가**
- 균형은 왼쪽과 오른쪽 부분 트리의 크기가 완전히 같다는 의미가 아니다.
- 균형잡힌 트리는 삽입, 탐색, 삭제가 O(logN) 정도의 시간복잡도를 가진다.

## 이진 트리 순회
### 중위 순회(in-order traversal)
- 왼쪽 가지, 현재 노드, 오른쪽 가지 순서대로 노드를 방문하는 방법
- 이진 탐색 트리를 중위 순회 방법으로 순회한다면 오름차순으로 방문하게 된다.
```java
void inOrderTraversal(TreeNode node) {
    if (node != null) {
        inOrderTraversal(node.left);
        visit(node);
        inOrderTraversal(node.right);
    }
}
```

### 전위 순회(pre-order traversal)
- 자식 노드보다 현재 노드를 먼저 방문하는 방법
- 전위 순회에서 가장 먼저 방문하는 노드는 항상 루트이다.

```java
void preOrderTraversal(TreeNode node) {
    if (node != null) {
        visit(node);
        preOrderTraversal(node.left);
        preOrderTraversal(node.right);
    }
}
```

### 후위 순회(post-order traversal) 
- 모든 자식 노드들을 먼저 방문한 뒤 마지막에 현재 노드를 망분하는 방법이다.
- 후위 순회에서 가장 마지막에 방문하는 노드는 항상 루트이다.

```java
void postOrderTraversal(TreeNode node) {
    if (node != null) {
        postOrderTraversal(node.left);
        postOrderTraversal(node.right);
        visit(node);
    }
}
```

<details>
<summary>참고</summary>

- 코딩인터뷰 완전 분석


</details>