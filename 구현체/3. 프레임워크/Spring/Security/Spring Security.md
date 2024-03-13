https://spring.io/projects/spring-security

Spring Security는 강력하고 사용자 정의가 가능한 인증 및 액세스 제어 프레임워크입니다. 이는 Spring 기반 애플리케이션 보안을 위한 사실상의 표준입니다.

Spring Security는 Java 애플리케이션에 인증과 권한 부여를 모두 제공하는 데 중점을 둔 프레임워크입니다. 모든 Spring 프로젝트와 마찬가지로 Spring Security의 진정한 힘은 사용자 정의 요구 사항을 충족하기 위해 얼마나 쉽게 확장할 수 있는지에 있습니다.

feature
- Authentication ( 인증 )
	- 비밀번호 저장
	- https://docs.spring.io/spring-security/reference/features/authentication/password-storage.html
- Authorization ( 권한 )
	- 요청 기반 승인
	- 방법 기반 승인

servlet Application 에서의 적용



![[Pasted image 20240207095052.png]]

서블렛 필터 체인 기반으로 동작함.

그냥 붙일 수도 있긴한데

따로 프록시로 빼서 관리하고, url 별로 필터를 따로 먹이는 등, 다양한 작업이 가능함.

- 예외 처리
https://docs.spring.io/spring-security/reference/servlet/architecture.html#servlet-exceptiontranslationfilter

![[Pasted image 20240207095226.png]]


- 인증 메커니즘
- [사용자 이름 및 비밀번호](https://docs.spring.io/spring-security/reference/servlet/authentication/passwords/index.html#servlet-authentication-unpwd) - 사용자 이름/비밀번호로 인증하는 방법
- [OAuth 2.0 로그인](https://docs.spring.io/spring-security/reference/servlet/oauth2/login/index.html#oauth2login) - OpenID Connect 및 비표준 OAuth 2.0 로그인(예: GitHub)을 사용한 OAuth 2.0 로그인
- [SAML 2.0 로그인](https://docs.spring.io/spring-security/reference/servlet/saml2/index.html#servlet-saml2) - SAML 2.0 로그인 ( ss0 )
- [중앙 인증 서버(CAS)](https://docs.spring.io/spring-security/reference/servlet/authentication/cas.html#servlet-cas) - 중앙 인증 서버(CAS) 지원 (sso )
    
- [Remember Me](https://docs.spring.io/spring-security/reference/servlet/authentication/rememberme.html#servlet-rememberme) - 세션 만료 이후의 사용자를 기억하는 방법
    
- [JAAS 인증](https://docs.spring.io/spring-security/reference/servlet/authentication/jaas.html#servlet-jaas) - JAAS로 인증 ( jaas는 자바의 보안 프레임워크. 느낌이 레거시임.)
    
- [사전 인증 시나리오 -](https://docs.spring.io/spring-security/reference/servlet/authentication/preauth.html#servlet-preauth) [SiteMinder](https://www.siteminder.com/) 또는 Java EE 보안 과 같은 외부 메커니즘으로 인증 하지만 일반적인 악용에 대한 인증 및 보호를 위해 여전히 Spring Security를 ​​사용합니다.
    
- [X509 인증](https://docs.spring.io/spring-security/reference/servlet/authentication/x509.html#servlet-x509) - X509 인증 (ssl 인증서)



- 느낌이..
	- 토큰 발급 : OAuth2 Authroization Server
	- 토큰 인증 : OAuth2 Resource Server
	- 권한 : Spring Security..인데 ㅋㅋ ㅋㅋ ㅋㅋ ㅋ ㅋㅋ ㅋ ㅋ ㅋ ㅋ



- 사실 JWT랑 SPring Security는 별개임.

JWT만 구현해도 되는데

