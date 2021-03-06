# TCP와 UDP의 특징과 차이점
TCP와 UDP는 OSI 표존모델과 TCP/IP모델의 전송계층에 사용되는 프로토콜이고, 전송계층은 송신자와 수신자를 연결하는 통신서비스를 제공하는 계층으로 쉽게 말해 데이터의 전달을 담당한다. 그리고 데이터를 전송하기 위해 사용하는 게 TCP와 UDP이다.

<br><br>

## 1. TCP(Transmission Control Protocol)

TCP는 인터넷상에서 테이터를 메세지의 형태로 보내기 위해 IP와 함께 사용하는 프로토콜이다.

일반적으로 TCP와 IP를 같이 사용하는데 IP가 데이터의 배달을 처리한다면 TCP는 패킥을 추적 및 관리를 하게 된다. TCP는 연결형 서비스를 지원하는 프로토콜로 인터넷 환경에서 기본으로 사용한다.

<div align = "center">
    <img src = "../img/TCP-packet_change.png" width = "70%">
</div>

<br>

### TCP의 특징

 - 연결형 서비스로 가상회선 방식을 제공한다.
 - 데이터의 경계를 구분하지 않는다.(바이트 스트림 서비스)
 - 데이터의 전송 순서를 보장한다.(데이터의 순서 유지를 위해 각 바이트마다 번호를 부여)
 - 3-way handshaking과정을 통해 연결을 설정하고 4-way handshaking을 통해 해제한다.
 - 데이터 흐름 제어 및 혼잡을 제어한다.
 - UDP보다 속도가 느리다.
 - 전이중(Full-Duplex), 점대점(Poing to Point)서비스

<br>

### TCP의 단점
 - 데이터를 보내기 전에 반드시 연결이 형성되어야한다.
 - 1:1 통신만 가능하다
 - 고정된 통신 선로가 최단선(네트워크 길이)이 아닐경우 상대적으로 UDP보다 데이터 전송속도가 느리다.

<br>

### TCP서버의 특징
 - 서버소켓은 연결만 담당한다.
 - 연결과정에서 반환된 클라이언트 소켓은 데이터의 송수신에 사용된다
 - 서버와 클라이언트는 1대로 연결된다.
 - 스트림 전송으로 전송 데이터의 크리가 무제한이다.
 - 패킷에 대한 응답을 해야하기 때문데(시간지연, CPU소모) 성능이 낮다.
 - Streaming서비스에 불리하다(손실된 경우 재전송 요청을 하므로).

<br>

### TCP의 헤더 정보

| 필드 | 크기 | 내용 |
| :---: |:---:|:---:|
| `송신자의 포트 번호` | 16 | TCP로 연결되는 가상 회선 양단의 송수신 프로세스에 할당되는 포트 주소 |
| `시퀀스 번호(Sequence Number)` | 32 | 송신자가 지정하는 순서 번호, 전송되는 바이트 수를 기준으로 증가 SYN = 1 : 초기 시퀀스 번호가 된다. ACK 번호는 이 값에 1을 더한값 SYN = 0 : 현재 세션의 이 세그먼트 데이터의 최초 바이트 값의 누적 시퀀스 번호|
| `응답 번호 (ACK Number)`      | 32 | 수신 프로세스가 제대로 수신한 바이트 수를 응답하기 위해 사용|
| `데이터 오프셋 (Data Offset)`  | 4 | TCP 세그먼트의 시작 위치를 기준으로 데이터의 시작 위치를 표현(TCP 헤더의 크기) |
| `예약필드(Reserved)` | 6 | 사용을 하지 않지만 나중을 위한 예약필드이며 )으로 채워져야 한다. |
| `제어 비트(Flag Bit)` | 6 | SYN, ACK, FIN등의 제어 번호 |
| `윈도우 크기` | 16 | 수신 윈도우의 버퍼 크기를 지정할 때 사용, 0 이면 송신 프로세스의 전송 중지 |
| `체크섬(Checksum)` | 16 | TCP 세그먼트에 포함되는 프로토콜 헤더와 데이터에 대한 오류 검출 용도 | 
| `긴급 위치(Urgent Point)` | 16 | 긴급 데이터를 처리하기 위함, URG 플래그 비트가 지정된 경우에만 유효 |


<br><br>

## 2. UDP(User Datagram Protocol)

UDP는 데이트를 데이터그램 단위로 처리하는 프로토콜이다. 여기서 데이터그램이란 독림적인 관계를 지니는 패킷이라는 뜻으로, UDP의 동작방식은 TCP와 달리 UDP는 비연결성 프로토콜이다. 즉 연결을 위해 할당되는 논리적인 경로가 없다. 그래서 각각의 패킷은 다른 경로로 전송되고, 각각의 패킷은 독립적인 관계를 지니게 되는데 이렇게 데이터를 서로 다른 경로로 독립적으로 처리하는게 UDP이다.



<div align = "center">
    <img src = "../img/UDP-packet_change.png" width = "70%">
</div>

<br>

### UDP의 특징
 - 비연결형 서비스로 연결 없이 통신이 가능하며 데이터그램 방식을 제공한다.
 - 데이터 경계를 구분한다.(데이터그램 서비스)
 - 정보를 주고 받을때 정보를 보내거나 받는다는 신호절차를 거치지 않는다.
 - 신회성 없는 데이터를 전송한다.(데이터 재전송과 데이터 순서 유지를 위한 작업을 하지 않는다)
 - 패킷관리가 필요하다.
 - 패킷 오버헤드가 적어 네트워크 부하가 감소되는 장점이 있다.
 - 상대적으로 TCP보다 전송속도가 빠르다.

<br>

### UDP의 단점
 - 데이터의 신뢰성이 업다.
 - 의미있는 서버를 구축하기 위해서 일일이 패킷을 관리해주어야 한다.

<br>

### UDP의 헤더 정보


| 필드 | 크기 | 내용 |
| :---: |:---:|:---:|
| `송신자의 포트 번호` | 16 | 데이터를 보내는 어플리케이션의 포트 번호|
| `수신자의 포트 번호` | 16 | 데이터를 받을 어플리케이션의 포트 번호|
| `데이터의 길이`      | 16 | UDP 헤더와 데이터의 총 길이|
| `체크섬(Checksum)`  | 16 | 데이터 오류 검사에 사용|



<br><br>

## TCP / UDP 간략비교

<br>

### 공통점

| TCP와 UDP의 공통점 |
| :---: |
| 포트번호를 이용하여 주소를 지정 | 
| 데이터 오류 검사를 위한 체크섬 존재 | 

<br>

### 차이점

|       |  TCP  |  UDP  |
| :--- | :--- | :--- |
| `연결방식` | 연결형 서비스 | 비 연결형 서비스 |
| `패킷 교환 방식` | 가상 회선 방식 | 테이터그램 방식|
| `전송 순서` | 전송 순서 보장 | 전송 순서가 바뀔 수 있음 | 
| `수신 여부 확인` | 수신 여부를 확인함 | 수신 여부를 확인하지 않음 | 
| `통신 방식` | 1:1 통신만 가능 | 1:1 / 1:N / N:N 통신 모두 가능 |
| `신뢰성` | 높음 | 낮음 | 
| `속도` | 느림 | 빠름 |


