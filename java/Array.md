# Array(배열)

## Array(배열)이란?
- 데이터가 많아지면 `그룹관리`의 필요성이 생기게 된다.
- 이럴 때 사용하는 것이 `배열`이다.

> 여러 데이터를 하나의 이름으로 그룹핑해서 관리하기 위한 데이터 스트럭쳐

- 배열을 생성하면 element(index, value)가 생성된다.

## 배열의 생성 (Create)

```java
int[] numbers1 = new int[5];
String[] strings = new String[5];
```
- element의 타입을 지정해주고, []로 배열임을 표시한다.
- new를 통해 배열을 생성하고, (new라는 키워드를 통해 배열도 객체의 일종임을 알 수 있다.) 배열의 크기를 설정한다.  

- 배열에 값 넣기
  ```java
  numbers[0] = 10;
  numbers[1] = 20;
  numbers[2] = 30;
  ```

- 배열 생성과 동시에 값 넣기
```java
int[] numbers2 = {10, 20, 30, 40};
int[] numbers3 = new int[]{10, 20, 30, 40};
```

## 배열의 값 가져오기 (Get)
```java
System.out.println(numbers1[0]);
```

## 배열의 크기 (Size)
```java
System.out.println(numbers.length);
```

## 배열의 반복 (Iteration)
```java
int i = 0;
while(numbers1.length > i) {
  System.out.println(numbers1[i]);
  i++;
}
```

```java
for(int i = 0; i < numbers1.length; i++) {
  System.out.println(numbers1[0]);
}
```

## 배열의 단점
1. 배열의 크기가 정해져 있다.
  - 크기보다 더 많은 정보를 추가하려고하면, 에러가 발생한다.
2. 기능이 없다.
  - 데이터를 추가하고, 삭제하고, 이동시키는 것과 같은 기능이 전혀 없다.

## 배열의 장점
1. 배열의 크기가 정해져 있다.
  - 작고, 가볍다. (메모리를 적게 사용한다.)
2. 기능이 없다. 
  - 단순하다.