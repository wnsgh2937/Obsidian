https://m.blog.naver.com/sampoo00/30190219050
https://stackoverflow.com/questions/24884827/possible-locations-for-sequence-picture-parameter-sets-for-h-264-stream/24890903#24890903

NAL ( 총 19 개)
- VLC (실제 압축된거)
	- IDR 5
- non-VLC(메타)
	- sps 7
	- pps 8
	- AUD 9



- **시퀀스 매개변수 세트(SPS).** 이 비 VCL NALU에는 프로필, 레벨, 해상도, 프레임 속도 등 디코더를 구성하는 데 필요한 정보가 포함되어 있습니다.
- **PPS(그림 매개변수 집합).** SPS와 유사하게 이 비 VCL에는 엔트로피 코딩 모드, 슬라이스 그룹, 모션 예측 및 디블로킹 필터에 대한 정보가 포함되어 있습니다.
- **즉각적인 디코더 새로 고침(IDR).** 이 VCL NALU는 자체 포함된 이미지 슬라이스입니다. 즉, 다른 NALU 저장 SPS 및 PPS를 참조하지 않고도 IDR을 디코딩하고 표시할 수 있습니다.
- **AUD(액세스 단위 구분 기호).** AUD는 기본 스트림에서 프레임을 구분하는 데 사용할 수 있는 선택적 NALU입니다. 이는 필요하지 않으며(TS와 같은 컨테이너/프로토콜에 의해 달리 명시되지 않는 한) 공간을 절약하기 위해 포함되지 않는 경우가 많지만 각 NALU를 완전히 구문 분석하지 않고도 프레임의 시작을 찾는 데 유용할 수 있습니다.

0110 0111 (뒤에 5개)
- forbidden_zero_bit : f(1) : [7] : 항상 0
- nal_ref_idc : u(2) : [6:5] : 00 :참조픽쳐에 사용되지 않음, 다른: 참조픽쳐 구성하는데 사용
- nal_unit_type : u(5) :[4:0] : Type정의 (책참조) -> 이게 19개 라는거