
- [ffmpeg-cli-wrapper](https://github.com/bramp/ffmpeg-cli-wrapper/tree/master/src/main/java/net/bramp/ffmpeg)
- 를 내 코드 수정해서 gradle 프로젝트에 포함 시켜야함

- 방법 1
	- ffmpeg-cli-wrapper를 gradle 프로젝트로 전환
	- https://www.lesstif.com/spring/maven-gradle-129007766.html 참조
	- gradle init + gradle build
- 방법 2
	- maven 프로젝트로 빌드후, maven repo에 올리고 참조
- 방법 3
	- maven 프로젝트로 빌드후, jar 파일 import