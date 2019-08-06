# 19.8.5
이벤트 pull 방식과 push 방식의 차이

함수는 pull
프로미스 는 push
제너레이터는 pull
옵져버블은 push

데이터가 전달되어지는 방식의 차이다
함수와 제너레이터는 호출되어지는 순간 데이터가 전달된다.

프로미스와 옵져버블은 구독하는 시점 부터 데이터를 받을 준비를 하고 데이터를 이어 받는다.

가장 큰 차이는 pull은 데이터를 보장 받지 못할 수도 있다는 것이다. 호출하는 시점에 데이터가 없다면 받을 수 없다는 것이다. 하지만 push는 데이터가 작업하기 때라 다르겠지만 데이터가 준비된 시점에 밀어넣어 주기 때문에 데이터를 보장 받는다.

그렇다면 제너레이터와 함수의 차이는 데이터의 복수성에 있다. 여러개의 데이터를 pull형식으로 핸들링 하려면 제너레이터를 사용해야 한다.

프로미스와 옵져버블의 차이도 이와같다. 프로미스는 하나의 데이터밖에 핸들링 하지 못하고 연속적이지 않고 데이터가 받아지면 끝난다. 또한 중간에 취소하거나 시간을 유연하게 늘리지 못한다. 비동기 처리를 할때 이런 특성에 의거해서 옵져버블을 사용하는게 어떤 이로움이 있는지 파악 할 수 있다.

옵져버블에서 많이 나오는 계념

핫과 콜드

가장 큰 차이는 구독을 필요로 한다는것에 차이가 있다.
구독을 해야지만 하는게 콜드
구독을 하지 않아도 발생하는게 핫

- 핫의 예( UI 이벤트, subject)
- 콜드의 예( Io.observer 생성 후 구독 )

핫은 여러게의 구독자가 있을 수 있고 없어도 구동되고 있지만 콜드는 한개의 구독자라도 있어야 하고 구독하는 시점에서 실행되기에 1개의 구독자만을 위한 작동이다.

subject가 있으면 여러개의 콜드 옵져버가 생성될 수 있다. 구독자에 맞춤형.

아주 단적인 예가 이벤트에 사용자 정의 옵져버를 달아서 관찰하며 데이터를 핸들링 하는것.
