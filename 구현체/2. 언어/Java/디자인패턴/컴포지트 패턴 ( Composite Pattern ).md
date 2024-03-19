- 객체를 트리구조로 구성해서, 단일 객체로 다룰 수 있도록 하는 패턴
- Component -> interface Shape draw()
- Leaf -> Circle : Shape-> draw() 구현
- Leaf -> Rectangle : Shape-> draw() 구현
- Composite -> ShapeGroup : Shape -> draw() 구현
	- 내부에 Shape 리스트 관리

<iframe src="https://sjh9708.tistory.com/139" width="100%" height="1080px"></iframe>

