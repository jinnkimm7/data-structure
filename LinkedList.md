# LinkedList

- Element대신에 Node라는 용어를 사용한다.
- Node에는 `데이터`와 다음 노드의 주소값을 저장하고 있는 `포인터`가 있다.
- 첫번째 노드가 무엇인지를 알려주는 Head가 있다.

## ArrayList vs LinkedList
ArrayList : 조회가 빠르지만, 삭제, 추가가 느리다./ 배열리스트의 크기가 정해져있다.  
LinkedList : 삭제, 추가는 빠르지만, 조회가 느리다. / 리스트의 크기가 확정적이지 않다. 데이터 공간을 미리 할당하지 않아도 된다.

---
## 구현
```java
public class LinkedList {
  private Node head;
  private Node tail;
  private int size = 0;

  public class Node {
    private Object data;
    private Node next;
    public Node(Object input) {
      this.data = input;
      this.next = null;
    }
    public String toString() {
      return String.valueOf(this.data);
    }
  }

  // addFirst 구현
  public void addFirst(Object input) {
    Node newNode = new Node(input);
    newNode.next = head;
    head = newNode;
    size++;
    
    if(head.next == null) {
      tail = head;
    }
  }

  // addLast 구현
  public void addLast(Object input) {
    Node newNode = new Node(input);
    if(size == 0) {
      addFirst(input);
    } else {
      tail.next = newNode;
      tail = newNode;
      size++;
    }
  }

  // node 구현
  Node node(int index) {
    Node x = head;
    for(int i = 0; i < index; i++) {
      x = x.next;
    }
    return x;
  }

  // add 구현
  public void add(int k, Object input) {
    if(k == 0) {
      addFirst(input);
    } else {
      Node temp1 = node(k-1);
      Node temp2 = temp1.next;
      Node newNode = new Node(input);
      
      temp1.next = newNode;
      newNode.next = temp2;
      size++;
      if(newNode.next == null) {
        tail == newNode;
      }
    }
  }

  // toString 구현
  public String toString() {
    if(head == null) {
      return "[]";
    } 

    Node temp = head;
    String str = "[";

    while(temp.next != null) {
      str += temp.data;
      temp = temp.next;
    }
    str += temp.data;
    return str + "]";
  }
}
```

```java
public class Main {
  public static void main(String[] args) {
    LinkedList numbers = new LinkedList();
  } 
}
```