- Widevine 시스템 구성도
	- ![[Pasted image 20231018103858.png]]
- CDM
	- Client 단 Content Decryption Module
	- 복호화를 위한 키 획득과 화면 송출을 위한 아웃풋 담당
	- CDM 사용은 EME Layer를 통해 노출되어 있음.
	- CMD은 Widevine HAL (OEM Crypto 하드웨어) 와 일함.
- OEM Crypto
	- 하드웨어 추상화 라이브러리
	- 클라와 서버간 메세지를 서명한다.
	- 키 복호화 및 핸들링
	- 키별 정책을 적용함
	- 오디오 및 비디오 스트림 복호화
- 클라단 보안 레벨
	- L1
		- 복호화 정보가 절대 CPU에 노출되지 않음.
			- 하드웨어 및 보안 프로세서만이 복호화 작업을 한다.
		- OEM Crypto의 키박스 공장 초기화가 필요함.
		- 보안 부트 로더가 필요함(?)
		- ![[스크린샷 2023-10-18 오전 10.31.05.png]]
	- L2
		- L1과 비슷하나, 디코딩된 비디오 스트림이 메모리에 쌓이게된다.
		- ![[Pasted image 20231018103225.png]]
	- L3
		- NO HARDWARE
		- ![[Pasted image 20231018103353.png]]
		- 키박스의 Device Key는 먼데?
- Device 인증 시스템
	- ![[Pasted image 20231018103949.png]]
- 통합 테스트 사이트  https://integration.widevine.com

License Proxy
- 유저 요청을 비즈니스 로직에 따라 인증
- 라이센스 요청을 구글에 요청 및 수신
- ![[Pasted image 20231018105236.png]]


아키텍처 9요소
- Common Encryption
- EME (Encrypted Media Extensions)
	- 보안 통신을 위한 프로토콜
- MSE ( Media Source Extensions)
- ABR
- Widevine Liscense Server
- Player
- CDM ( Content Decryption Module )
	- 기기 스펙 기술
- OEM Crypto Module
	- 하드웨어 복호화 기술

