# Q. tcp vs udp를 비교 설명하시오 (⭐)

## 나의 답변

### TCP (Transmission Control Protocol)
- 인터넷상에서 데이터를 메세지의 형태로 보내기 위해 IP와 함께 사용하는 프로토콜
- TCP는 연결형 서비스를 지원하는 프로토콜로 인터넷 환경에서 기본으로 사용
- 연결형 서비스로 가상 회선 방식을 제공한다.
- 3-way handshaking과정을 통해 연결을 설정하고 4-way handshaking을 통해 해제한다.
- 흐름 제어 및 혼잡 제어.
- 높은 신뢰성을 보장한다.
- UDP보다 속도가 느리다.
- 전이중(Full-Duplex), 점대점(Point to Point) 방식.
- 서버소켓은 연결만을 담당한다.
- 연결과정에서 반환된 클라이언트 소켓은 데이터의 송수신에 사용된다형 서비스로 가상 회선 방식을 제공한다.
- 서버와 클라이언트는 1대1로 연결된다.
- 스트림 전송으로 전송 데이터의 크기가 무제한이다.
- 패킷에 대한 응답을 해야하기 때문에(시간 지연, CPU 소모) 성능이 낮다.
- Streaming 서비스에 불리하다.(손실된 경우 재전송 요청을 하므로)

![image](https://user-images.githubusercontent.com/17926024/157352004-ff91bd2e-0da4-43e5-8b19-a4cef6c15440.png)
![image](https://user-images.githubusercontent.com/17926024/157352011-6ad694cc-eacd-4ea1-98da-114879a6a127.png)
![image](https://user-images.githubusercontent.com/17926024/157352026-04f4ab6c-a874-401e-be5b-0b4ec71be275.png)


### UDP (User Datagram Protocol)
- 데이터를 데이터그램 단위로 처리하는 프로토콜
- UDP는 비연결형 프로토콜입니다. 
- 연결을 위해 할당되는 논리적인 경로가 없는데, 그렇기 때문에 각각의 패킷은 다른 경로로 전송되고, 각각의 패킷은 독립적인 관계를 지니게 되는데 이렇게 데이터를 서로 다른 경로로 독립적으로 처리하게 되고, 이러한 프로토콜을 UDP비연결형 서비스로 데이터그램 방식을 제공한다
- 정보를 주고 받을 때 정보를 보내거나 받는다는 신호절차를 거치지 않는다.
- UDP헤더의 CheckSum 필드를 통해 최소한의 오류만 검출한다.
- 신뢰성이 낮다
- TCP보다 속도가 빠르다
- 신뢰성보다는 연속성이 중요한 서비스
- UDP에는 연결 자체가 없어서(connect 함수 불필요) 서버 소켓과 클라이언트 소켓의 구분이 없다.
- 소켓 대신 IP를 기반으로 데이터를 전송한다.
- 서버와 클라이언트는 1대1, 1대N, N대M 등으로 연결될 수 있다.
- 데이터그램(메세지) 단위로 전송되며 그 크기는 65535바이트로, 크기가 초과하면 잘라서 보낸다.
- 흐름제어(flow control)가 없어서 패킷이 제대로 전송되었는지, 오류가 없는지 확인할 수 없다.
- 파일 전송과 같은 신뢰성이 필요한 서비스보다 성능이 중요시 되는 경우에 사용된
![image](https://user-images.githubusercontent.com/17926024/157352036-878bba76-afe0-434d-9db7-5c93497ae11b.png)

### 비교 
![image](https://user-images.githubusercontent.com/17926024/157351507-0e5f95a9-81d8-4b96-ac4f-d74debe0145f.png)
