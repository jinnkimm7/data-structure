# Binary Search Tree

## Tree
- 노드의 집합이다.
- 각 노드들 사이에 부모-자식의 관계를 가진다.
- Root - 트리에서 탑 노드를 가리킨다.
- Child - 루트에서 멀어지는 방향으로 연결된 노드
- Parent - 자식의 반대 개념이다.
- Siblings - 같은 부모를 갖는 노드
- Leaf - 자식이 없는 노드
- Edge - 노드 사이를 연결하는 선

## Tree vs List
- Tree - non linear
- List - linear

## 트리 사용 예시
- HTML DOM
- Network Routing

## Tree vs Binary Tree vs Binary Search Tree

- Tree 
  - 각 노드의 자식 노드의 개수가 정해지지 않음
- Binary Tree
  - 각 노드의 자식 노드의 개수는 최대 2개이다.
- Binary Search Tree
  - 노드 당 최대 두 개의 자식을 갖는다.
  - 특정한 방식으로 정렬 되어 있다.
    - 부모 노드의 왼쪽에 있는 모든 노드는 언제나 부모보다 작고, 부모 노드보다 오른쪽에 있는 모든 노드는 언제나 부모보다 크다. 

## 구현
```javascript
class Node {
  constructor(value) {
    this.value = value;
    this.left = null;
    this.right = null;
  }
}

class BinarySearchTree {
  constructor() {
    this.root = null;
  }

  insert(value) {
    let newNode = new Node(value);
    if (this.root === null) {
      this.root = newNode;
      return this;
    } else {
      let current = this.root;
      while (true) {
        if (value === current.value) return undefined;
        if (value < current.value) {
          if (current.left === null) {
            current.left = newNode;
            return this;
          } else {
            current = current.left;
          }
        } else if (value > current.value) {
          if (current.right === null) {
            current.right = newNode;
            return this;
          } else {
            current = current.right;
          }
        }
      }
    }
  }

  contains(value) {
    if (this.root === null) return false;
    let current = this.root;
    let found = false;
    while (current && !found) {
      if (value < current.value) {
        current = current.left;
      } else if (value > current.value) {
        current = current.right;
      } else {
        return true;
      }
    }
    return false;
  }
}
```

## Binary Search Tree의 Big O
- insertion - `O(log N)`
- searching - `O(log N)`

