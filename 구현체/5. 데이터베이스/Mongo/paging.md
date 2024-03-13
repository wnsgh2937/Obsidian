https://medium.com/@davide.pedone/cursor-based-pagination-with-spring-boot-and-mongodb-bca6446f3b1f

인덱스 기반으로도 할 수 있고 커서 기반으로도 할 수 있음.

https://frankle97.tistory.com/45
https://stackoverflow.com/questions/50260384/what-is-the-best-way-for-pagination-on-mongodb-using-java
인덱스 기반 구현 방식은 두가지
- Skip, limit을 통한 구현
	- Skip은 맨 처음부터 탐색하므로, 인덱스가 커질수록 매우 비효율적
- 이전 마지막 Id로 찾고, limit 으로 탐색
	- Sort... 성능이...