# [Spring Boot] Fundamental



## Java Bean

- @Component
- @Controller
- @Service 
  - `@Service("userDefService")`처럼 이름을 정해줄 수도 있다
- @Repository
- @Bean



## Dependency Injection

### Bean Configurations

- XML
- Annotations
- Java Bean Configuration
- Grooby Bean Configuration



### Bean Scope

- singleton(default Value)
- prototype
  - 요청받을 때마다 새로운 instance 생성
- request
  - HTTP 리퀘스트받을 때마다 새로운 instance 생성
- session
- globalSession



- @Scope("session")



### Property Based Injection

```java
@RestController
public class PageController {
  @Autowired
  private NotificationService notificationService;
}
```

- `@Autowired`

  - spring에게 이 property는 dependency니까 알아서 관리해줘라고 말하는 것과 같다.
  - 단점: 테스트를 어렵게 한다.




### Setter Based Injection

```java
@RestController
public class PageController {
  
  private NotificationService notificationService;
  
  @Autowired
  public void setNotificationService(NotificationService notificationService) {
   	this.notificationService = notificationService; 
  }
}
```



### Constructor Based Injection

```java
@RestController
public class PageController {
  
  private NotificationService notificationService;
  
  @Autowired
  public  PageController(NotificationService notificationService) {
   	this.notificationService = notificationService; 
  }
}
```

