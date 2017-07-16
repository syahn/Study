# HTTP Status Codes

| Status Code | Description   |
| ----------- | ------------- |
| 1xx         | Informational |
| 2xx         | Success       |
| 3xx         | Redirection   |
| 4xx         | Client Error  |
| 5xx         | Server Error  |



### HTTP Status Code 2xx

| Status Code    | Description                              |
| -------------- | ---------------------------------------- |
| 200 ok         | request 성공                               |
| 201 Created    | Request가 충족되어서 새로운 리소스가 생성됨              |
| 204 No Content | 서버가 request를 충족시켰으나 entity-body를 반환할 필요가 없으며, 업데이트된 meta정보를 반환하고 싶을지도 모른다. |



### HTTP Status Code 3xx

| Status Code            | Description                              |
| ---------------------- | ---------------------------------------- |
| 300 Moved Permanently  | 요청된 리소스에 새로운 permanent URI가 할당되고, 후에 이 리소스를 참조하려면 반드시 반환된 URI를 사용해야 함 |
| 304 Not Modified       | 클라이언트가 conditional GET request를 하고 접근이 허용되었으나 document가 변화되지 않았다. 서버는 반드시 이 상태코드로 응답해야 한다. |
| 307 Temporary Redirect | 리퀘스트가 또다른 URI로 반복되어야 한다. 그러나 미래의 리퀘스트는 여전히 original URI를 사용할 수 있다. |



### HTTP Status Code 4xx

| Status Code      | Description                              |
| ---------------- | ---------------------------------------- |
| 400 Bad Request  | 요청된 리소스에 새로운 permanent URI가 할당되고, 후에 이 리소스를 참조하려면 반드시 반환된 URI를 사용해야 함 |
| 401 Unauthorized | 403과 비슷하지만 specifically authentication이 가능하지만 실패하거나 제공되지 않을 때 사용 |
| 403 Forbidden    | 리퀘스트는 합당한 요구지만, respond할 수 없다. 401과 다르게 authenticating will make no place. |
| 404 Not Found    | 요청된 리소스를 찾을 수 없어 나중에도 가능하지 않음. Subsequent requests by the client are permissible. |







### HTTP Status Code 5xx

| Status Code               | Description                              |
| ------------------------- | ---------------------------------------- |
| 500 Internal Server Error | 서버가 request를 충족시키지 못하는  조건               |
| 502 Bad gatewat           | 게이트웨이나 프록시로 기능하는 서버가 유효하지 않은 응답으러=상위 업스트림 |

