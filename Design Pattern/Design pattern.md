# Design pattern

1. ### Adapter Pattern

- 호출당하는 쪽의 메서드를 호출하는 쪽의 코드에 대응하도록 중간에 변환기를 통해 호출하는 패턴

2. ### Proxy Pattern

- 제어 흐름을 조정하기 위한 목적으로 중간에 대리자를 두는 패턴

3. ### Decorator Pattern

- 메서드 호출의 반환값에 변화를 주기 위해 중간에 장식자를 두는 패턴

4. ### Singleton Pattern

- 클래스의 인스턴스, 즉 객체를 하나만 만들어 사용하는 패턴
- 조건
  - new를 실행할 수 없도록 생성자에 private 접근 제어자를 지정한다.
  - 유일한 단일 객체를 반환할 수 있는 정적 메서드가 필요하다.
  - 유일한 단일 객체를 참조할 정적 참조 변수가 필요하다. 
  - 단일 객체는 쓰기 가능한 속성을 갖지 않는다.

5. #### Template Method Pattern

- 상위 클래스의 견본 메서드에서 하위 클래스가 오버라이딩한 메서드를 호출하는 패턴

6. ### Factory Pattern

- 오버라이드된 메서드가 객체를 반환하는 패턴

7. ### Strategy Pattern

- 클라이언트가 전략을 생성해 전략을 실행할 컨텍스트에 주입하는 패턴

8. ### Template Callback Pattern

- ​