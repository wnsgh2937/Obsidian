파이썬에서 ffmpeg을 실행시킬때 stdout을 받아서 파싱해서 뭔가를 하는 작업을 한다. 

계속 이런 데이터 흐름에 대해서 궁금증을 가지고 있었고, 여러 자료중 [위키피디아 자료](https://ko.wikipedia.org/wiki/%ED%91%9C%EC%A4%80_%EC%8A%A4%ED%8A%B8%EB%A6%BC)가 가장 괜찮았 던 것 같음.

<iframe src="https://ko.wikipedia.org/wiki/%ED%91%9C%EC%A4%80_%EC%8A%A4%ED%8A%B8%EB%A6%BC" width="100%" height="1080px"></iframe>

핵심은,
- unix 기반의 모든 프로그램에는 3가지 표준 입출력 스트림을 상속 받는데, 그것이 각각 stdin, stdout, stderr 이다.

프로그램간에 pipe ( ex. ps -ef | grep java ) 와 같은 리다이렉트 기능으로 표준 스트림들을 연결 시킬 수 있다는 것.

파이썬에서 ffmpeg을 돌리는것 을 생각해보았을때,
- ffmpeg에 stdin 으로 명령어 입력
- ffmpeg stdout으로 나오는 데이터를 파이프를 이용해 python의 stdin 으로 리다이렉트
와 같은 데이터 흐름이라고 생각할 수 있다.

[참고자료](https://eteo.tistory.com/343)
stdout과 stderr는 둘다 그냥 출력한다는 점에서 동일해보이지만 조금의 차이점이 있다.
- stdout
	- 버퍼를 사용
	- 개행문자가 나와야 출력
- stderr
	- 버퍼를 사용하지 않음.
	- 버퍼링 없이 바로 출력