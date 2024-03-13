아주 좋은 세션
https://tech.kakao.com/2023/12/22/techmeet-virtualthread/

![[Pasted image 20240121164953.png]]

Tomcat이던 뭐던 쓰레드 중심으로 작업이 하나씩 할당되는데, 걔를 Virtual Thread에 할당시킴

얘가 어떻게 동작하나면
![[Pasted image 20240121165034.png]]

Blocking IO가 발생할때, Carrier Thread에 다른 Virtual Thread를 매핑시킴.
자동으로..!

그런데 말입니다.
사용하는 코드 블록내에 syncronized가 있으면 Carrier Thread가 Block되므로 reentrant Lock( 가로채기가 가능한 잠금장치 ) 을 사용하길 권장한다.([동시성 관련 작성 글](obsidian://open?vault=LEO&file=%EC%A7%80%EC%8B%9D%2F%EC%9D%B4%EB%A1%A0%2F13.%20%EB%85%BC%EB%A6%AC%2F%EB%8F%99%EC%8B%9C%EC%84%B1%2F7%EA%B0%80%EC%A7%80%20%EB%8F%99%EC%8B%9C%EC%84%B1%20%EB%AA%A8%EB%8D%B8%2F2.%20%EC%8A%A4%EB%A0%88%EB%93%9C%EC%99%80%20%EC%9E%A0%EA%B8%88%EC%9E%A5%EC%B9%98))

그런데 말입니다.

외부 사용 라이브러리에 syncronized가 있다면?

꼭 써야하고 대안이 없다면?

[MYsql JDBC 드라이버가 그렇다고 한다](https://jaeyeong951.medium.com/virtual-thread-synchronized-x-6b19aaa09af1)
지금은 모르겠으나 무려 23년 11월 글.

그렇다면 전혀 사용할 이유가 없음. 그래서 도입을 면밀히 검토해야함.

그리고 얘를 도입하면 좋은게 딱 하나임.
- 기존 코드 거의 그대로 재활용
- 쓰레드처리량 증가(그니까 클라이언트 요청 엄청나게 많이 받을수 있음.)

처리량이 증가.. 좋지. 근데 이것으로 인해 뒷단의 자원이 부족해져서 터질 수 있음.
JDBC드라이버가 reentrant lock으로 바꿨다해도, DB 커넥션 풀이 부족해서 터지기는 매한가지임. 그 터질때를 위해서, 커넥션 풀을 엄청 늘려놔?

찾아보니,
virtual thread -> IO 블로킹 자주 있을때 좋음! ( = Network/DB 자주 쓸때)
근데 syncronized 있으면 안돼! ( = Network/DB drvier에 syncronized 있는게 있음.)
근데 syncronized없는것도 있어! ( = JDBC X , R2DBC O)
근데 R2DBC는 JPA 지원 안돼!

결론 : virtual Thread 도입하려면 JPA 지원 X
JDBC 지원 하던가

찾아본 결과 Oracle DB는 지원하는 것 같은데, 나머지는 아닌 것 같음. 
신규 기능이기도하고, 성숙하지도 않고, 코드 수정량도 어마어마해서 아직 ㄴㄴ인듯.

시기 상조임 ㅋ


