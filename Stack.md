# Stack
- Stack => 쌓아 올리다.
- LIFO(Last In First Out), 나중에 저장한 데이터가 먼저 나오는 구조이다.
- `입구와 출구가 동일한 형태`로 스택을 시각화할 수 있다.

## 주요 메서드
- push()
- pop()
- peak()
- isEmpty()

## 구현
```java
import java.util.EmptyException;

class Stack<T> {
  class Node<T> {
    private T data;
    private Node<T> next;

    public Node(T data) {
      this.data = data;
    }

    private Node<T> top;

    public T pop() {
      if(top == null) {
        throw new EmptyStackException();
      }
      
      T item = top.data;
      top = top.next;
      return item;
    }

    public void push(T item) {
      Node<T> t = new Node<T>(item);
      t.next = top;
      top = t;
    }
  }

  public T peak() {
    if (top == null) {
      throw new EmptyStackException();
    }
    return top.data;
  }

  public boolean isEmpty() {
    return top == null;
  }

  public class Test {
    public static void main(String[] args) {
      Stack<Integer> s = new Stack<>();
      s.push(1);
      s.push(2);
      s.push(3);
      s.push(4);

      System.out.println(s.pop());
      System.out.println(s.pop());
      System.out.println(s.peak());
      System.out.println(s.pop());
      System.out.println(s.isEmpty());
      System.out.println(s.pop());
      System.out.println(s.isEmpty());
    }
  }
}
```

```
4
3
2
2
fasle
1
true
```