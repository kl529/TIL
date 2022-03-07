# Q. Graphql 과 rest api을 비교 설명하시오

## 나의 답변

### Graphql
- Graph Query Language 의 줄임말
- 편하게 정보를 수정할 수 있도록 하는 표준화된 Query language
- RESTful 은 각 Resource 종류 별로 요청을 해야하고, 따라서 요청 횟수가 필요한 Resource 의 종류에 비례한다. 반면 GraphQL 은 원하는 정보를 하나의 Query 에 모두 담아 요청하는 것이 가능하다.
- RESTful 은 응답의 형태가 정해져있고, 따라서 필요한 정보만 부분적으로 요청하는 것이 힘들다. 반면 GraphQL 은 원하는 대로 정보를 요청하는 것이 가능하다.

### Rest API
- REpresentational State Transfer의 줄임말
- 자원(resource)의 표현(representation)에 의한 상태 전달


### 비교
#### GraphQL
- 서로 다른 모양의 다양한 요청들에 대해 응답할 수 있어야 할 때
- 대부분의 요청이 CRUD(Create-Read-Update-Delete) 에 해당할 때

####RESTful
- HTTP 와 HTTPs 에 의한 Caching 을 잘 사용하고 싶을 때
- File 전송 등 단순한 Text 로 처리되지 않는 요청들이 있을 때
- 요청의 구조가 정해져 있을 때
