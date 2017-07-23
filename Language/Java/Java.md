# Java

### To Learn

- enum
- stream
- ​



### Basic

- Java에서는 자바 파일당 하나의 public class가 있다. 
  - 그 클래스는 파일과 이름이 같아야 한다. 
  - main() method는 이 public class내에 있다.


- Reference type vs Primitive type
  - primitive type은 기본적으로 8개
  - reference type은 데이터를 저장하는게 아니라 데이터에 대한 레퍼런스를 저장한다. 
- println() vs print() vs printf()
  - newline이 포함 / 미포함
  - printf는 format 

### Static

- 공유
- 유의할 점
  - ​
- static variable
  - class에 속한 변수
  - 다른 모든 instance에 공유되난 Single copy
  - 한번만 initialized 된다.
- Static method
  - static data에만 접근 가능하다
  - 오직 static method만 call할 수 있고, non-static method를 call할 수는 없다. 
  - this, super를 refer할 수 없다.

### Escape Sequence

- \

  - \"

- Flags

  - the width flag

    - used to specify total width

  - thousands seperator flag (,)

    ```java
    System.out.printf("%,.2f", 12345.56789);
    //12,345.57                  
    ```



### Accepting user Input

```Java
import java.util.Scanner;

Scanner reader = new Scanner(System.in);
```



### Try / Catch / Finally

- Exception method

  - getMessage()

    ```javascript
    e.getMessage()
    // 메세지를 볼 수 있음
    ```

- Specific Errors

  ```java
  import java.util.InputMismatchException;

  ArrayIndexOutOfBoundsException
  => 인덱스 벗어난 에러
  InputMismatchException
  => 자료형 불일치
    
  if (choice == 0) 
    throw new ArrayIndexOutOfBoundsException();

  ```



## OOP

- 모든 default는 package-private


- #### field

  - Class 내에 선언된 변수
  - Final 
    - 한번 선언되면 변경 불가
      1. class
         - 이 클래스는 상속을 허락하지 않는다.
      2. variable
         - 상수가 된다.
      3. method
         - 오버라이딩이 금지 된다.
  - Private 
    - 선언된 class 내에서만 사용
    - constructor에 선언되면 new로 object를 만들 수 없다.
  - public
    - 제한 없음
  - Protected 
    - 선언되었거나, 상속받거나, 같은 패키지거나

- #### getter / setter

  - 다른 클래스들이 private으로 선언된 필드 access할 때 사용

- #### Constructor

  - 클래스와 같은 이름을 가짐
  - 클래스의 필드를 initialize하기 위해 일반적으로 사용
  - void 쓸 필요없음

- #### Inheritance

  - 부모 클래스에서 public / protected / method를 상속한다.
    - Private 필드 역시 상속은 되지만 직접적으로 access할 수는 없다.
    - constructor, getter, setter를 통해서 접근가능하다
  - 우선 부모의 constructor부터 콜한다.

- ####Abstract Class

  - 다른 클래스들이 상속받기 위한 특별한 형태의 부모 클래스
  - 초기화될 수 없음
  - abstract method는 body가 없고, 상속받은 클래스에서만 사용해야 한다.
  - 하나 이상의 추상 매서드 포함

- #### Super

  - Overriding한 super class의 매서드를 호출할 수 있음
    - `super.func()`





## Collections

- object만 저장할 수 있음, primitive 저장 못함


- Autoboxing, unboxing

  - Wrapper class

    - Boolean, Character, Byte, Short, Integer, Long, Float, Double

  - ```java
    Integer intObject = new Integer(100);
    Integer intObject = 100; // autoboxing
    int m = intObject.intValue(); // 다시 primitive 값으로 돌아갈 때
    int m = intObject // unboxing
    ```

- Lists

  - ArrayList

    - array와 다르게 사이즈 조절 가능

    - ```java
      import java.util.ArrayList;
      ArrayList<type> name = new ArraryList<>()
      ```

    - method

      - add([pos], val)

      - set([pos], val)

      - remove(pos)

      - get(pos)

      - size()

      - contains()

      - indexOf()

      - toArray()

        - Object array로 나타내준다.

        - 만약 Object가 아닌, 다른 자료형으로 반환하고 싶다면,

          ```java
          Integer[] myIntArray = userAgeList.toArray(new Integer[0]);
          // 이렇게 나타낼 수 있다.
          ```

      - clear()

  - LinkedList

    - element를 빈번히 추가 삭제할 때 사용한다.

      - search에 약하고, 메모리를 많이 사용한다.

    - queue와 deque에 사용된다.

    - ```java
      LinkedList<Type> newList = new LinkedList<>();
      ```

    - 기본적으로 ArrayList가 제공하는 메서드 모두 제공 

    - 추가적으로

      - poll()
        - 첫 elem 반환 및 삭제
      - peek()
        - 첫 elem 확인
      - getFirst()
        - peek과 유사. 없으면 NoSuchElementException 오류 내뱉음
      - getLast()

### Generics

- Primitive type은 해당되지 않는다.

### FileReader

- import

  ```java
  import java.io.*;
  ```

- FileReader

  - char들의 스트림을 한 글자씩 읽어드린다.

  - 효율적으로 사용하기 위해서는 BufferedReader와 같이 사용한다.

  - ```java
    reader = new BufferedReader(new FileReader("myFile.txt"));
    ```

  - ```java

    package filehandlingdemo;
    import java.io.*;

    public class FileHandlingDemo {
        public static void main(String[] args) {
            String line;
            
            try (BufferedReader reader = new BufferedReader(new FileReader("myFile.txt"))){
                
                line = reader.readLine();
                while (line != null){
                    System.out.println(line);
                    line = reader.readLine();
                }
            }
            catch (IOException e) {
                System.out.println(e.getMessage());
            }

        }   
    }
    ```



### Interface

- interface는 오직 public abstract method 및 public static final variable(상수)만 가질 수 있다.

  - 따로 변수에 public static final, 매서드에 public abstract를 붙이지 않아도 자동으로 붙여준다.
  - private 변수는 가질 수 없다.
- object의 타입으로만 사용가능하다.


- #### Functional Interface
  - 하나의 abstract method밖에 없는 interface

  - ```java
    @FunctionalInterface
    interface MyNumber{
      double getValue();
    }
    ```

    ​



### This

- 객체 변수와 이름이 같은 지역 변수가 있는 경우 객체 변수를 사용하려면 this를 접두사로 사용
- 정적 변수와 이름이 같은 지역 변수가 있는 경우 정적 변수를 사용하려면 클래스명을 접두사로 사용


### Super

- 상위 클래스의 인스턴스를 지칭한다.




### String

- methods
  - concat
  - substring
  - length
  - toUpperCase
  - toLowerCase
  - charAt
  - indexOf
  - equals
  - trim
  - replace
  - replaceAll



### StringBuilder

- methods
  - append 
  - insert
  - delete
  - deleteCharAt



### Calendar API

### StringTokenizer

### HashMap

```java
HashMap<Integer, String> hashMap = new HashMap<Integer, String>();
```

- method

  - put
  - get
  - remove
  - clear

- Iterator

  - ```java
    Iterator<Integer> iterator = hashMap.keySet().iterator();
    while (iterator.hashNext()) {
      
    }
    ```

  - ​

### hashSet

- 객체 타입의 경우 주소값이 비교되기에 



### Synchronized

- 먼저 수행되는 스레드의 모든 작업이 끝날 때까지 다른 스레드는 기다려야 하는 방식


### OOP 설계 5원칙

1. SRP (Single Responsibility Principle): 단일 책임 원칙
   - 어떤 클래스를 변경해야 하는 이유는 오직 하나뿐이어야 한다.
2. OCP (Open Closed Principle): 개방 폐쇄 원칙
   - 소프트웨어 엔티티(클래스, 모듈, 함수 등)는 확장에 대해서는 열려 있어야 하지만 변경에 대해서는 닫혀 있어야 한다.
3. LSP (Liskov Substitution Principle): 리스코프 치환 원칙
   - subtype은 언제나 자신의 base type으로 교체할 수 있어야 한다.
4. ISP(Interface Segregation Principle): 인터페이스 분리 원칙
   - client는 자신이 사용하지 않는 method에 의존 관계를 맺으면 안된다.
5. DIP(Dependency Inversion Principle): 의존 역전 원칙
   - 고차원 모듈은 저차원 모듈에 의존하면 안된다. 이 두 모듈 모두 다른 추상화된 것에 의존해야 한다. 추상화된 것은 구체적인 것에 의존하면 안된다. 구체적인 것이 추상화된 것에 의존해야 한다. 자주 변경되는 구체 클레스에 의존하지 마라

- SoC (Seperation of Concern): 관심사의 분리
  - 하나의 속성, 하나의 매서드, 하나의 클래스, 하나의 모듈, 또는 하나의 패키지에는 하나의 관심사만 들어 있어야 한다.




### Thread




## Effective Java

1. Consider static factory methods instead of constructors

- Static factory method
  - A static method that returns an instance of the class. 
  - 장점 (constructor 대비)
    1. 이름이 있다.
       - 하나의 constructor에 오버로딩된 constructor를 두는 것은 나쁜 API설계이다. 이럴 경우, static factory method를 사용하라
    2. It's not required to create a new object each time they're invoked.
    3. It can return an object of any subtype of their return type.
    4. It reduce the verbosity of creating parameterized type instances.
       - *type inference*
  - 단점
    1. Classes without public or protected constructors cannot be subclassed.
    2. It's not readily distinguishable from other static methods.
  - Practice
    - **valueOf**—Returns an instance that has, loosely speaking, the same value as its parameters. Such static factories are effectively type-conversion methods.
    - **of**—A concise alternative to valueOf, popularized by EnumSet (Item 32).
    - **getInstance**—Returns an instance that is described by the parameters butcannot be said to have the same value. In the case of a singleton, getInstancetakes no parameters and returns the sole instance.
    - newInstance—Like getInstance, except that newInstance guarantees thateach instance returned is distinct from all others.
    - getType—Like getInstance, but used when the factory method is in a differ-ent class. Type indicates the type of object returned by the factory method.
    - newType—Like newInstance, but used when the factory method is in a differ-ent class. Type indicates the type of object returned by the factory method.