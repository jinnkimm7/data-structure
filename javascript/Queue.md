# Queue
- FIFO의 특성을 가진 자료구조이다.

## 구현

### 1. Array 이용하기

- push(), shift()
- re indexing을 피할 수 없다.
```javascript
let queue = [];

queue.push('FIRST');
queue.push('SECOND');
queue.push('THIRD');
queue.shift(); // FIRST
queue.shift(); // SECOND
queue.shift(); // THIRD
```

### 2. Linked List 이용하기
```javascript
class Node {
  constructor(value) {
    this.value = value;
    this.next = null;
  }
}

class Queue {
  constructor {
    this.first = null;
    this.last = null;
    this.size = 0;
  }

  enqueue(value) {
    const newNode = new Node(value);
    
    if(!this.first) {
      this.first = newNode;
      this.last = newNode;
    } else {
      this.last.next = newNode;
      this.last = newNode;
    }
    return ++this.size;
  }

  dequeue() {
    if(!this.first) return null;

    let temp = this.first;
    if(this.first === this.last) {
      this.last = null;
    }
    this.first = currentFirst.next;
    this.size--;
    return temp.value;
  }
}
```

## Queue의 Big O
- Insertion - O(1)
- Removal - O(1)
- Searching - O(N)
- Access - O(N)