# Stack
- LIFO의 특성을 가진 자료구조이다.

## 구현

### 1. Array 이용하기
- Array의 push()와 pop()을 이용해서 구현
- unshift()와 shift()를 이용해 구현할 수 있지만 효율성 문제가 있다.
- index가 굳이 필요없기 때문에 Linked List로 구현하면 효율성을 높일 수 있다. 
```javascript
let stack = [];
stack.push(3);
stack.push(2);
stack.push(1);

stack.pop(); // 1
stack.pop(); // 2
stack.pop(); // 3
```

### 2. Linked List 이용하기 

```javascript
class Node {
  constructor(value) {
    this.value = value;
    this.next = null;
  }
}

class Stack {
  constructor() {
    this.first = null;
    this.last = null;
    this.size = 0;
  }

  push(val) {
    let newNode = new Node(val);
    if(!this.first) {
      this.first = newNode;
      this.last = newNode;
    } else {
      let temp = this.first;
      this.first = newNode;
      this.fisrt.next = temp;
    }
    return ++this.size;
  }

  pop() {
    if(!this.first) return null;
    let temp = this.first;
    if(this.first == this.last) {
      this.last = null;
    }
    this.first = this.first.next;
    this.size--;
    return temp.value;
  }
}

let stack = new Stack();
stack.push('FIRST');
stack.push('SECOND');
stack.push('THIRD');
stack.push('FOURTH');
stack.pop(); // FOURTH
stack.pop(); // THIRD
stack.pop(); // SECOND
stack.pop(); // FIRST
stack.pop(); // null
```

## Stack의 Big O
- Insertion - O(1)
- Removal - O(1)
- Searching - O(N)
- Access - O(N)