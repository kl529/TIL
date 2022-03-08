# Q. 3ways handshake의 과정을 설명하시오

## 나의 답변

### 3ways handshake
- TCP는 장치들 사이에 논리적인 접속을 성립(establish)하기 위하여 three-way handshake를 사용
- TCP/IP프로토콜을 이용해서 통신을 하는 응용프로그램이 데이터를 전송하기 전에 먼저 정확한 전송을 보장하기 위해 상대방 컴퓨터와 사전에 세션을 수립하는 과정을 의미

```
Client > Server : TCP SYN
Server > Client : TCP SYN ACK
Client > Server : TCP ACK
```

![image](https://user-images.githubusercontent.com/17926024/157181178-15041828-ba50-43dd-8d83-7dfa99c5bbcc.png)


### 과정
[STEP 1]   
A클라이언트는 B서버에 접속을 요청하는 SYN 패킷을 보낸다.   
이때 A클라이언트는 SYN 을 보내고 SYN/ACK 응답을 기다리는SYN_SENT 상태가 되는 것이다.

 

[STEP 2]    
B서버는 SYN요청을 받고 A클라이언트에게 요청을 수락한다는 ACK 와 SYN flag 가 설정된 패킷을 발송하고 A가 다시 ACK으로 응답하기를 기다린다.    
이때 B서버는 SYN_RECEIVED 상태가 된다.

 

[STEP 3]   
A클라이언트는 B서버에게 ACK을 보내고 이후로부터는 연결이 이루어지고 데이터가 오가게 되는것이다. 이때의 B서버 상태가 ESTABLISHED 이다.
위와 같은 방식으로 통신하는것이 신뢰성 있는 연결을 맺어 준다는 TCP의 3 Way handshake 방식이다.
