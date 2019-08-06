# 19.8.6

자바스크립트는 단일 스레드 콜백큐 이벤트 시스템으로 이뤄어 짐.

엔진 중에 가장 유명하고 많이 쓰여지는건 구글의 V8엔진이다 크롬과 노드에서 사용되어 진다. 

자바스크립트 메모리힙과 콜스택 구조로 이뤄져 있다.


콜스택 - 단일 호출 한번에 한개의 태스크만 처리한다.

문제점.1 - 단일 스택이기 때문에 하나의 함수 처리가 너무 과하게 느리게 되면 다른 함수 실행이 같이 느려지는 문제가 있음.! 후속 작업 처리에 문제가 발생... 

해결책 - 비동기(프로미스 혹은 옵져버블 사용) - pull 방식이 아닌 push 방식의 실행구문을 갖는 비공기 콜백을 사용한다.
이런 비동기 함수들은 이벤트 시스템이라는 놈이 관리한다. 콜백큐에 함수실행 구분을 담아 이벤트루프가 가지고 있다가 노티를 주는 시점이 되면(처리되거나 트리거 된다면) 콜스택에 밀어넣어준다. (push)


v8엔진

가장큰 특징으로 코드를 바이트화 시키지 않고 바로 머신코드로 번역한다점 그래서 빠르다. 
프로파일러 스레드에서 한번 실행 후 어떤 메소드가 많은 시간을 쓰고 있는지 체크하여 메인스레드에 전달하고 메소드 최적화를 이뤄어 낸다. 2개의 컴파일러 풀코드젠과 크랭크샤프트가 있는데 복잡한 메소드의 최적화는 크랭크샤프트가 맞고 있다. 최적화 하는 방법으로는 메소드를 최적화 하는방법이다. 그리고 메소드를 시간과 연결성 등 중요도 순으로 정렬하고 데이터를 공유한다.