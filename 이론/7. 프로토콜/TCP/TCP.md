- 연결이란
[참고 동영상](https://www.youtube.com/watch?v=DC9FfKSgisg)

![[Pasted image 20231227102655.png]]

일단 MAC/IP 계층에 적힌 정보를 통해 목적 단말까지는 도착했다. 

그러면 다음과 같은 기능이 제공되어야함.
1. 신뢰성 있는 데이터 전달
2. 올바른 어플리케이션(프로세스)에 데이터 전달

- 신뢰성 있는 데이터 전달
	- 그니까 데이터가 누락되어도 재전송을 한다는 말임.
	- Seq Number와 Ack Num을 통해서 이를 식별할 수 있음.
	- Seq Num은 내가 00번 세그먼트 보내고 있어
	- Ack Num은 00번 받았고, 01번 줘 와 같은 의미
- 올바른 프로세스에 데이터 전달
	- [참고 SOF](https://stackoverflow.com/questions/11129212/tcp-can-two-different-sockets-share-a-port?noredirect=1&lq=1)
	- 일단 세그먼트의 식별자는 총 5개
		- Source IP / Port
		- Dest IP / Port
		- Protocol
	- 근데 뭐, IP는 이미 쓰였고, Protocol은 TCP이므로 사실상 
		- Source Port
		- Dest Port
	- 두가지 밖에 식별할 수 있는게 없다.
	- 한 크롬 탭에서 naver로 요청을 보낸다고 해보자.
	- HTTP 이므로,
		- Source Port = 80 (크롬에서 바인딩된 포트)
		- Dest Port = 80 (네이버 웹서버 포트)
	- 라고 생각할 수 있다.
	- 이렇게 생각하면, 내가 네이버로 여러 다른 API요청을 보냈다고 했을때 해당 API요청들을 구분할 수 가 없다. (다 80 포트이므로)
	- 실제 TCP 요청은 이렇게 들어간다.
		- [커널이 로컬 포트를 선택하는 과정](https://brunch.co.kr/@alden/19)
		- Source Port = 23155 (임의의 미사용 포트)
		- Dest Port = 80
	- 아니 그러면 방화벽은요?
		- Source Port는 막지 않음.


부가적으로, 3-way handshake에 대해서도 알아보자.
3-way handshake란 클라이언트와 서버 간 서로의 sequence 번호를 교환하는 행위이다. 이 과정에서 겸사겸사 MSS(Maximum Segment Size)와 혼잡 제어 방법(최근 대부분 SACK)도 교환한다.

ㅇㅇ




