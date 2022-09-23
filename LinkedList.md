# LinkedList

- Element대신에 Node라는 용어를 사용한다.
- Node에는 데이터와 다음 노드가 무엇인지를 저장한다.
- 첫번째 노드가 무엇인지를 알려주는 Head가 있다.

## ArrayList vs LinkedList
ArrayList : 조회가 빠르지만, 삭제, 추가가 느리다./ 배열리스트의 크기가 정해져있다.  
LinkedList : 삭제, 추가는 빠르지만, 조회가 느리다. / 리스트의 크기가 확정적이지 않다.

---
## 1. 구현
```java
package list.linkedlist.implementation;

public class Main {
  public static void main(String[] args) {
    LinkedList numbers = new LinkedList();
  }
}
```

```java
package list.linkedlist.implementation;

public class LinkedList {
  private Node head;
  private Node tail;
  private int size = 0;
  private class Node{
    private Object data;
    private Node next;
    public Node(Object input) {
      this.data = input;
      this.next = null;
    }
    public String toString() {
      return String.valueOf(this.data);
    }

    // addFirst
    public void addFirst(Object input) {
      Node newNode = new Node(input);
      newNode.next = head;
      head = newNode;
      size++;
      if(head.next == null) {
        tail = head;
      }
    }

    // addLast
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
  }
```