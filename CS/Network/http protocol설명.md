# Q. http protocol이 무엇인지 설명하시오 ( ⭐ )

## 나의 답변

### http protocol
- HTTP(Hypertext Transfer Protocol)는 인터넷상에서 데이터를 주고 받기 위한 서버/클라이언트 모델을 따르는 프로토콜
- TCP/IP 위에서 작동한다
- HTML문서, 이미지, 동영상, 오디오, 텍스트 문서 등 보낼 수 있음

###  작동방식
- HTTP는 서버/클라이언트 모델을 따른다. 
- 클라이언트에서 요청(request)를 보내면 서버는 요청을 처리해서 응답(response)한다.
![image](https://user-images.githubusercontent.com/17926024/157563594-ab7378b4-e0ca-4630-a801-b47399d8bdd8.png)

### 특징
- Connectionless 방식 / stateless
- 장점 : 불특정 다수를 대상으로 하는 서비스에 적합한 방식이다. / 수십만명이 웹 서비스를 사용하더라도 접속유지는 최소한으로 할 수 있기 때문에, 더 많은 유저의 요청을 처리할 수 있다.
- 단점 : 연결을 끊어버리기 때문에, 클라이언트의 이전 상태를 알 수가 없다. 
- 그래서 Cookie를 사용한다.

### URI
- HTTP는 전송 프로토콜이고, URI는 자원의 위치를 알려주기 위한 프로토콜이다.

### Method
- GET : 정보를 요청하기 위해서 사용한다. (SELECT)
- POST : 정보를 밀어넣기 위해서 사용한다. (INSERT)
- PUT : 정보를 업데이트하기 위해서 사용한다. (UPDATE)
- DELETE : 정보를 삭제하기 위해서 사용한다. (DELETE)
