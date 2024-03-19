https://flutter-ko.dev/get-started/install/macos
에서 SDK 압축 풀고 환경변수 등록하고 설치 
( Brew ㄴㄴ )

Settings - Language&Framework - Flutter 에 해당 폴더 등록

IOS 시뮬레이터 안열릴텐데 App Store에서 XCode 설치

flutter doctor 해보면 IOS 시물레이터 연결 안되어있다고 뜰텐데
sudo xcode-select --switch /Applications/Xcode.app/Contents/Developer
sudo xcodebuild -runFirstLaunch

맥OS면 루비 쓸 수 있음. 루비 패키지 관리자인 gem을 이용해 cocoapods를 설치해준다.
gem install cocoapods

난 뭐 버전 낮다고 해서
gem install drb -v 2.0.6
gem install activesupport -v 6.1.7.7





