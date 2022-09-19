# ArrayList

- List라는 완제품 안에 Array라는 부품을 사용
- 데이터를 추가(Add)하고 삭제(Remove)할 때 느리다. 하지만 index값으로 데이터를 조회(Get)할 때 빠르다.

---

## 1. 기능
### 생성 (Create)
```java
import java.util.ArrayList;

ArrayList<Integer> numbers = new ArrayList<>();
```

### 추가 (Insert)
```java
numbers.add(10);
numbers.add(20);
numbers.add(30);
numbers.add(40);
// [10, 20, 30, 40]
numbers.add(1, 50);
// [10, 50, 20, 30, 40]
```

### 삭제 (Remove)
```java
numbers.remove(2);
// [10, 50, 30, 40]
```

### 가져오기 (Get)
```java
numbers.get(2)
```

### 크기 (Size)
```java
numbers.size();
```

### 반복 (Iteration)
```java
Iterator it = numbers.iterator();

while(it.hasNext()) {
  int value = (int)it.next();
  System.out.println(value);
}
```

```java
for(int value : numbers) {
  System.out.println(value);
}
```

```java
for(int i = 0; i < numbers.size(); i++) {
  System.out.println(numbers.get(i));
}
```

---

## 2. ArrayList 구현하기

### 객체 생성하기
```java
package list.arraylist.implementation;

pulbic class Main {
  public static void main(String[] args) {
    ArrayList numbers = new ArrayList();
    numbers.addLast(10);
    numbers.addLast(20);
    numbers.addLast(30);
    numbers.addLast(40);
    numbers.add(1, 15);
    numbers.addFirst(5);
    System.out.println(numbers.toString());
  }
}
```
### 구현하기

```java
class ArrayList {
  private int size = 0;
  // 실제 자바의 Collections의 ArrayList는 데이터가 아무리 많이 추가되도 자동으로 커진다.
  private Object[] elementData = new Object[100]; 

// 추가(addFirst)
  public boolean addFirst(Object element) {
      return add(0, element);
  }

// 추가(add)
  public boolean add(int index, Object element) {
    for(int i = size() - 1; i >= index; i--) {
      elementData[i + 1] = elementDate[i];
    }
    elementData[index] = element;
    size++;
    return true;
  }

// 추가(addLast)
  public boolean addLast(Object element) {
    elementData[size] = element;
    size++;
    return true;
  }

// toString
  public String toString() {
    String str = "[";
    for(int i = 0; i < size; i++) {
      str += elementData[i];
      if(i < size - 1){
        str += ",";
      }
    }
    return str + "]";
  }

// remove
  public Object remove(int index) {
    Object removed = elementData[index];
    for(int i = index + 1; i <= size - 1; i++) {
      elementData[i - 1] = elementData[i];
    }
    size--;
    elementData[size] = null;
    return removed;
  }

// removeFirst
  public Object removeFirst() {
    return remove(0);
  }

// removeLast
  public Object removeLast() {
    return remove(elementData(size - 1));
  }

// get -> index로 접근해 특정 데이터를 빠르게 가져올 수 있다 ! -> ArrayList를 사용하는 이유 
  public Object get(int index) {
    return elementData[index];
  }
 
// size
  public int size() {
    return size;
  }

// indexOf
  public int indexOf(Object o) {
    for(int i = 0; i < size; i++) {
      if(o.equals(elementData[i])) {
        return i;
      }
    }
    return -1;
  }
}
```