# Queue
- 먼저 들어온 데이터가 먼저 나가는 형식의 자료구조이다.
  - FIFO(First In First Out)
- 입구와 출구가 모두 뚫려 있는 터널과 같은 형태로 시각화 할 수 있다. 
- LinkedList 클래스를 이용해 Queue를 구현한다.
  - ```java
    Queue<Integer> queue = new LinkedList<>();
    ```
- 참고: 큐는 어디에 많이 쓰일까?
  - 멀티 태스킹을 위한 프로세스 스케쥴링 방식을 구현하기 위해 많이 사용된다.(운영체제 참조)
  - 큐의 경우에는 장단점 보다는, 큐의 활용 예로 프로세스 스케쥴링 방식을 함께 이해해두는 것이 좋다.

## 주요 메서드
- add(), offer()
- remove(), poll()
- peek()
- isEmpty()

## 구현
```java
import java.util.NoSuchElementException;

class Queue<T> {
  class Node<T> {
    private T data;
    private N

    public Node(T data) {
      this.data = data;
    }
  }

  private Node<T> first;
  private Node<T> last;

  public void add(T item) {
    Node<T> t = new Node<T>(item);

    if(last != null) {
      last.next = t;
    }
    last = t;

    if(first == null) {
      first = last;
    }
  }

  public void T remove() {
    if(first == null) {
      throw new NoSuchElementException();
    }

    T data = first.data;
    first = first.next;

    if(first == null) {
      last = null;
    }
    return data;
  }

  public T peek() {
    if (first == null) {
      throw new NoSuchElementException();
    }
    return first.data;
  }

  public boolean isEmpty() {
    return first == null;
  }

  }
  public class Test {
    public static void main(String[] args) {
      Queue<Integer> q = new Queue<Integer>();
      q.add(1);
      q.add(2);
      q.add(3);
      q.add(4);
      System.out.println(q.remove());
      System.out.println(q.remove());
      System.out.println(q.peek());
      System.out.println(q.remove());
      System.out.println(q.isEmpty());
      System.out.println(q.remove());
      System.out.println(q.isEmpty());
    }
}
```

```
1
2
3
3
false
4
true
```