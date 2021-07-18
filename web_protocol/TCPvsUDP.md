# TCP와 UDP의 특징과 차이점
TCP와 UDP는 네트워크 계층중 전송계층에 해당하고, 전송계층은 송신자와 수신자를 연결하는 통신서비스를 제공하는 계층으로 쉽게 말해 데이터의 전달을 담당한다. 그리고 데이터를 전송하기 위해 사용하는 게 TCP UDP이다.



<br><br>

## 1. TCP(Transmission Control Protocol)

TCP는 인터넷상에서 테이터를 메세지의 형태로 보내기 위해 IP와 함께 사용하는 프로토콜이다.

일반적으로 TCP와 IP를 같이 사용하는데 IP가 데이터의 배달을 처리한다면 TCP는 패킥을 추적 및 관리를 하게 된다. TCP는 연결형 서비스를 지원하는 프로토콜로 인터넷 환경에서 기본으로 사용한다.

<br>

### TCP의 특징

 - 연결형 서비스로 가상회선 방식을 제공한다.
 - 3-way handshaking과정을 통해 연결을 설정하고 4-way handshaking을 통해 해제한다.
 - 흐름 제어 및 혼잠을 제어한다.
 - UDP보다 속도가 느리다.
 - 전이중(Full-Duplex), 점대점(Poing to Point)방식이다.

<br>

### TCP서버의 특징


<br><br>

## TCP vs UDP

TCP는 *Transmission Control Protocol*의 약자이고 UDP는 *User Datagram Protocol*의 약자이다. 두 프로토콜은 모두 패킷을 한 컴퓨터에서 다른 컴퓨터로 전달해주는 IP프로토콜을 기반으로 구현되어 있지만, 서로 다른 특징을 가지고 있다.


