# Servlet

- Servlet

  - Java를 사용해서 웹프로그램을 제작하는 것

  - HttpServlet class를 상속받는다.

  - HttpServlet => GenericServlet(abstract) => Servlet(Interface)

  - ```java
    response.setContentType("text/html");
    PrintWriter writer = response.getWriter();
    ```

  - 컴텍스트 패스(Context Path)

    - WAS(Web Application Server)에서 웹 어플리케이션을 구분하기 위한 path입니다. 이클립스에서 프로젝트를 생성하면, 자동으로 server.xml에 추가됩니다.

- 작동순서

  - 클라이언트에서 servlet요청이 들어오면 서버에서는 servlet컨테이너를 만들고, 요청이 있을 때마다 스레드가 생성된다.
  - 웹브라우저 => 웹서버 => 웹어플리케이션 서버(WAS) => Servlet 컨테이너 (스레드, Servlet객체 생성)

- 라이프사이클

  - 사용도가 높은 이유: 빠른 응답 속도
  - 최초 요청 시 객체가 만들어져 메모리에 로딩되고, 이후 요청시에는 기존의 객체를 재활용하게 됩니다. => 동작 속도가 빠름
    1. Servlet 객체 생성(최초한번)
    2. Init() 호출(최초 한번)
    3. service(), doGet(), doPost() 호출 (매번 호출.)
    4. destroy()

- 선처리, 후처리

  - Init 전에 @PostConstruct
  - destroy 뒤에 @PreDestroy

- 한글처리

  - Tomcat 서버의 기본 문자 처리 방식은 IOS-8859-1방식입니다. 따라서 개발자가 별도의 한글 인코딩을 하지 않으면 한글이 깨져 보이는 현상이 있습니다. Get방식과 Post방식에 따라서 한글처리 방식에 차이가 있다.

    1. Get방식 요청 => <server.xml> 수정

       ```html
       <Connecter URIEncoding="EUC-KR" port="8181" ...></Connecter>
       ```

       ​

    2. Post방식 요청 =>
       <request.setCharacterEncoding() 메소드 이용>

       ```java
       request.setCharacterEncoding("EUC-KR");
       ```

- 서블릿 초기화 파라미터: ServletConfig

  - 특적 Servlet이 생성될 때 초기에 필요한 데이터들이 있습니다. 예를 들어 특정 결로 및 아이디 정보 등입니다. 이러한 데이터들을 초기화 파라미터라고 하며, web.xml에 기술하고 Servlet파일에서는 ServletConfig 클래스를 이용해서 접근(사용)합니다. 또한 초기화 파라미터를 web.xml이 아닌 Servlet파일에 직접 기술하는 방법도 살펴봅시다. 

  - Web.xml파일에 초기화 파라미터(Initialization Parameter) 기술

    - Servlet 클래스 제작 => web.xml파일에 초기화 파라미터 기술 => ServletConfig 메소드 이용해서 데이터 불러오기

    ```jsp
     <servlet>
      	<servlet-name>ServletInitParam</servlet-name>
      	<servlet-class>com.javalec.ex.ServletInitParam</servlet-class>
      	
      	<init-param>
      		<param-name>id</param-name>
      		<param-value>abcdef</param-value>
      	</init-param>
      	<init-param>
      		<param-name>pw</param-name>
      		<param-value>1234</param-value>
      	</init-param>
      	<init-param>
      		<param-name>path</param-name>
      		<param-value>C:\\javalec\\workspace</param-value>
      	</init-param>
      	
      </servlet>
    ```

  - Servlet파일에 초기화 파라미터 기술

    - Servlet 클래스 제작 => @webInitParam에 초기화 파라미터 기술 => ServletConfig 메소드 이용해서 데이터 불러오기

- 데이터 공유: ServletContext

  - 여러 Servlet에서 특정 데이터를 공유해야 할 경우 context parameter를 이용해서 web.xml에 데이터를 기술하고 Servlet에서 공유하면서 사용할 수 있다.

- 웹어플리케이션 감시: ServletContextListner

  - 웹앱의 라이프사이클을 감시하는 listener가 있다. 리스너의 해당 메소드가 웹앱의 시작과 종료 시에 호출된다. `contextInitialized()`, `contextDestroyed()`

 