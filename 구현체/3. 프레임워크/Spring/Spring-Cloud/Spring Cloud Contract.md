https://spring.io/projects/spring-cloud-contract/
Spring Cloud Contract는 사용자가 소비자 중심 계약 접근 방식을 성공적으로 구현하는 데 도움이 되는 솔루션을 보유한 포괄적인 프로젝트입니다. 현재 Spring Cloud Contract는 Spring Cloud Contract Verifier 프로젝트로 구성되어 있습니다.

Spring Cloud Contract Verifier는 JVM 기반 애플리케이션의 CDC(Consumer Driven Contract) 개발을 가능하게 하는 도구입니다. Groovy 또는 YAML로 작성된 DSL(계약 정의 언어)과 함께 제공됩니다. 계약 정의는 다음 리소스를 생성하는 데 사용됩니다.
https://docs.spring.io/spring-cloud-contract/reference/getting-started/introducing-spring-cloud-contract.html

https://clack2933.tistory.com/51

단순 외부 모킹 테스트 -> 각 이해관계간 규격 동기화 기능 제공


- 기본적으로 클라이언트 코드에 대한 통합 테스트(클라이언트 테스트)를 수행할 때 WireMock(HTTP 서버 스텁)에서 사용되는 JSON 스텁 정의입니다. 테스트 코드는 여전히 직접 작성해야 하며 테스트 데이터는 Spring Cloud Contract Verifier에서 생성됩니다.
    
- 메시징 경로(사용 중인 경우) 우리는 Spring Integration, Spring Cloud Stream 및 Apache Camel과 통합하고 있습니다. 그러나 원하는 경우 자체 통합을 설정할 수 있습니다.
    
- API의 서버측 구현이 계약을 준수하는지 확인하는 데 사용되는 승인 테스트(기본적으로 JUnit 또는 Spock)(서버 테스트). 전체 테스트는 Spring Cloud Contract Verifier에 의해 생성됩니다.
