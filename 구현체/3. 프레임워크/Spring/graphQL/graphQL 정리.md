체험 판으로 해당 [글](https://onethejay.tistory.com/117) 괜찮음.
[GitHub](https://github.com/onethejay/springboot-graphql/tree/master)

일단 기본 흐름이
1. resouce/graphql 폴더에 기본 명세 작성
2. 프론트에서 해당 명세를 요청한다.(http는 아닌 것 같고..; )
	1. postman에서 http://localhost:8080/graphql 같은 url로 명세를 받아볼 수 있다.
3. 프론트에서 원하는데로 골라서 쿼리요청을 보낸다.
![[Pasted image 20231210163731.png]]

그러면 이제 이거에 맞춰서 서버도 코드 짜면 되는 거임. 다만 복잡해질때는 어떻게 될지 잘 모르겠네.



[Graph Federation](https://blog.doctor-cha.com/integrating-graphql-services-with-graphql-federation#graphql-federationyi-mogjeog) 직역하면 그래프 연합인데, 이게 뭐냐면

마이크로 서비스를 구축할 경우에, 모든 서버는 각 서버의 명세를 가지고 있을거고, 프론트는 각 서버별 명세를 다 가져와서 각각 쿼리해야하는 문제점이 있음.

이러면 graphql의 장점이 사라짐.

해결방법은 단순함. 명세를 합치는 라우터를 놓으면 된다. ㅇㅇ 단순함.


일단 내 graphql 찍먹 느낌은

서버 프론트 모두 변경에 대한 유연성을 가지고, 쿼리 자유성이 높아지는 장점이 있음.

단점,, 아마 명세가 복잡해지고 여러 서비스로직이 들어가면 여러 해결하기 어려운 애로사항이 생길 것 같음. 또 정보도 적어서 트러블 슈팅하기 좀 어려울 것 같음.

