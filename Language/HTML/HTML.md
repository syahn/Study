# HTML

```html
<form action="FormEx" method="post">
```

- Servlet parameter
  - Form태그의 submit 버튼을 클릭하여 데이터를 서버로 전송하면, 해당파일(Servlet)에서는 HttpServletRequest객체를 이용하여 Parameter값을 얻을 수 있다. 
  - 관련 메소드
    - `getParameter(name)`
    - `getParameterValues(name)`
      - 여러 값을 가지는 태그들
    - `getParameterNames()`