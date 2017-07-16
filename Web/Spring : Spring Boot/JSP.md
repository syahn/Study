# JSP

1. ### JSP 태그 개념

Servlet은 Java언어를 이용하여 문서를 작성하고, 출력객체를 이용하여 HTML코드를 삽입한다. JSP는 Servlet과 반대로 HTML코드에 JAVA언어를 삽입하여 동적 문서를 만든다. HTML코드 안에 JAVA 코드를 삽입하기 위해서는 태그를 이용해야 한다.

- 종류
  - 지시자: `<%@	%>`
    - 페이지 속성
    - import도 이 태그 이용
  - 주석: `<%— —%>`
    - HTML 주석은 브라우져에서 볼 수 있지만, JSP는 볼 수 없다. (서버에서 실행되기 때문에)
  - 선언: `<%!     %> `
    - 변수, 메소드 선언
  - 표현식 : `<%=     %>`
    - 결과값 출력
  - 스크립트릿: `<%      %>`
    - 자바 코드
  - 액션 태그: `<jsp:action> </jsp:action>`
    - 자바빈 연결

### 2. 동작 원리

클라이언트가 웹브라우저로 helloWorld.jsp를 요청하게 되면 JSP컨테이너가 JSP파일을 Servlet파일(.java)로 변환합니다. 그리고 Servlet파일(.java)은 컴파일 된 후, 클래스 파일(.class)로 변환되고, 요청한 클라이언트한테 html파일 형태로 응답됩니다.   



### 3. JSP 내부 객체

개발자가 객체를 생성하지 않고 바로 사용할 수 있는 객체 => 내부 객체. JSP에서 제공되는 내부객체는 JSP컨테이너에 의해 Servlet으로 변화될 때 자동으로 객체가 생성 됩니다. 

- 종류
  - 입출력객체: request, response, out
  - servlet객체: page, config
  - 세션 객체: session
  - 예외 객체: exception



### 4. 스크립트릿, 선언, 표현식

JSP 문서 안에 JAVA언어를 넣기 위한 방식들이다. 

- scriptlet: <% %>

- Declaration: `<%! %>`
  - JSP페이지 내에서 사용되는 변수 또는 메소드를 선언할 때 사용합니다. 여기서 선언된 변수 및 메소드는 전역의 의미로 사용됩니다.  

- expression(표현식): `<%=   %>`
  - JSP페이지 내에서 사용되는 변수의 값 또는 메소드 호출 결과값을 출력하기 위해 사용된다. 결과값은 String타입이며, 

- 지시자

  - 전체적인 속성을 지정할 때 사용한다. 

  - page, include, taglib이 있으며, `<%@ 속성 %>` 

    - page: 해당 페이지의 전체적인 속성 지정

      - import할 때 사용

    - Include: 별도의 페이지를 현재 페이지에 삽입

      ```jsp
      <%@ include file="include01.jsp" %>
      ```

      ​

    - taglib: 태그 라이브러리의 태그 사용

      - 사용자가 만든 tag들을 태그라이브러리라고 합니다. 이러한 태그 라이브러리를 사용하기 위해 taglib지시자를 사용합니다. uri 및 prefix 속성이 있으며, uri는 태그 라이브러리의 위치값을 가지며, prefix는 태그를 가리키는 이름값을 가진다.  

### Request 객체의 이해

- 메소드
  - `getContextPath()`: 웹어플리케이션의 컨텍스트 패스를 얻는다.
  - `getServerName()`: 
  - `getMethod()`: get방식과 post방식을 구분할 수 있습니다. 
  - `getSession()`: 세션 객체를 얻습니다. 
  - `getRequestURL()`: 요청 URL을 얻습니다. 
  - `getRequestURI()`: 요청 URI를 얻습니다. 
  - `getQueryString()`: 쿼리스트링을 얻습니다. 
- Parameter 메소드
  - JSP 페이지를 제작하는 목적이 데이터 값을 전송하기 위함
  - `getParameter(String name)`: name에 해당하는 파라미터 값을 구함
  - `getParameterNames()`: 모든 파라미터 이름을 구함
  - `getParameterValues(String name)`: name에 해당하는 파라미터값을 구함.

### Response 객체의 이해

- 메소드
  - `getCharacterEncoding()`: 응답할 때 문자의 인코딩 형태를 구합니다. 
  - `addCookie(Cookie)`: 쿠키를 지정합니다.
  - `sendRedirect(URL)`: 지정한 URL로 이동합니다. 



### 액션태그

JSP페이지 내에서 어떤 동작을 하도록 지시하는 태그. 예를 들어 페이지 이동, 페이지 include 등등이다. 

- forward

  - 현재의 페이지에서 다른 특정 페이지로 전환할 때 사용. 사용법이 간단하며 예제를 통해 쉽게 이해.

  - ```jsp
    <jsp:forward page="sub.jsp" />
    ```

  - url과 현재 페이지가 다름

- include

- param

  - Forward 및 include 태그에 데이터 전달을 목적으로 사용되는 태그. 이름과 값으로 이루어져 있음

    ​