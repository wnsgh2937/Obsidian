https://d2.naver.com/helloworld/294797
https://bcho.tistory.com/1016

  

분산 시스템을 설계 하다보면, 가장 문제점 중의 하나가 분산된 시스템간의 정보를 어떻게 공유할것이고, 클러스터에 있는 서버들의 상태를 체크할 필요가 있으며 또한, 분산된 서버들간에 동기화를 위한 락(lock)을 처리하는 것들이 문제로 부딪힌다.

**ZooKeeper 활용 시나리오**
- 큐 : Watcher와 Sequence node를 이용하면, 큐를 구현할 수 있는데, Queue 라는 Node를 만든 후에, 이 노드의 Child node를 sequence node로 구성하면, 새롭게 생성되는 메세지들은 이 sequence node로 순차적으로 생성된다. 이 큐를 읽는 클라이언트가 이 큐 node를 watch 하도록 설정하면, 이 클라이언트는 새로운 메세지가 들어올 때 마다 call back을 받아서, 마치 메세지 Queue의 pub/sub 과 같은 형태의 효과를 낼 수 있다. 대용량 메세지나 애플리케이션 성격상의 메세지는 일반적인 큐 솔루션인 Rabbit MQ등을 활용하고, ZooKeeper는 클러스터간 통신용 큐로 활용하는 것을 고려해볼 수 있다.
    
- 서버 설정 정보 : 가장 일반적인 용도로는 클러스터 내의 각 서버들의 설정 정보(Configuration)를 저장하는 저장소로 쓸 수 있다. 정보가 안정적으로 저장이 될 뿐 아니라. Watch 기능을 이용하면, 설정 정보가 저장될 경우, 각 서버로 알려서 바로 반영을 할 수 있다.
    
- 클러스터 정보 : 현재 클러스터에서 기동중인 서버 목록을 유지할 수 있다. Ephemeral Node는 Zookeeper 클라이언트가 살아 있을 경우에만 유효하기 때문에, 클러스터내의 각 서버가 Ephemeral Node를 등록하도록 하면, 해당 서버가 죽으면 Ephemeral Node 가 삭제 되기 때문에 클러스터 내의 살아 있는 Node 리스트만 유지할 수 있다. 조금 더 발전하면, 클러스터가 master/slave 구조일때, master 서버가 죽었을 때, 다른 master 서버를 선출하는 election logic 도 구현이 가능하다. (https://zookeeper.apache.org/doc/r3.4.6/recipes.html#sc_recipes_Queues 참고)
    
- 글로벌 락 : Zookeeper를 이용하여 많이 사용되는 시나리오 중의 하나인데, 여러개의 서버로 구성된 분산 서버가 공유 자원을 접근하려고 했을때, 동시에 하나의 작업만이 발생해야 한다고 할때, 그 작업에 Lock을 걸고 작업을 할 수 있는 기능을 구현할때 사용한다. 자바 멀티 쓰레드 프로그램에서 synchronized를 생각하면 쉽게 이해가 가능할 것이다.
    

출처: [https://bcho.tistory.com/1016](https://bcho.tistory.com/1016) [조대협의 블로그:티스토리]