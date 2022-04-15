# NetworkManagement-

[한국공학대학교 네트워크 매니지먼트 수업 이론 정리]()

## 📝

- Transport Layer
- Network Layer
- Data Link Layer

이 3개의 계층에 대해서 깊게 이론적인 지식과 실습 내용을 정리할 예정이다.

# LAN 과 WAN

```
LAN이란? Local Area Network로서, 학교 내 네트워크, 가정 집 등등 제한된 지역의 분산 네트워크라고 볼 수 있다. 이더넷 프로토콜을 사용하며 유 무선 사용이 가능하고 wifi 또한 LAN을 통해 이용할 수 있다.

WAN이란? Wide Area Network로서, LAN과 LAN 사이를 광범위한 지역 단위로 구성하는 네트워크로서 네트워크의 네트워크라고 볼 수 있다. 우리가 주로 알고 있는 KT, SKT, LG와 같은 통신사들이 Internet Service Provider(ISP)역할을 함으로서, 전 세계적으로 통신이 가능하도록 해준다.
```

## 📌 Ethernet 내부에서 가지고 있는 CSMA/CD 프로토콜

```
CSMA/CD (Carrier Sense Multiple Access/Collision Detection)

LAN의 통신 프로토콜의 종류중 하나이며, 이더넷 환경에서 사용한다.
용어
* Carrier Sense : 이더넷 환경에서 통신을 하고 싶은 PC나 서버는 네트워크 상에서 통신이 일어나는지 확인을 하게 되는데, 이것을 Carrier Sense라고 부른다.
* Carrier: 네트워크 상에 나타나는 신호를 의미한다.

네트워크를 아무도 사용하고 있지 않다면 성공적인 전송을 하게 된다. 하지만 동시에 네트워크를 PC들이 사용하게 된다면 Collision이 발생하게 될 것이다. 따라서 충돌을 방지하기 위해 어느정도 기다릴 수 있도록 해준다.

초기 방식 : 토큰링이라는 것이 있었는데, 토큰을 가진 PC만이 네트워크에 데이터를 실어보낼 수 있었다.
```

## 📌 UTP Straight - Through, CrossOver, Roll over

```
Straight-Through, 서로 다른 장비들끼리 통신을 하고자 할 때 연결 하는게 Straight-Through Cable이다.
Router - Switch
Switch - PC
Hub - PC
Switch - Server 등이 있다.

CrossOver, 서로 같은 장비들 끼리 통신하고자 할 때 연결하는게 Crossover Cable이다.
Switch - Swtich
Hub - Hub
Router - Router 등이 있다.

RollOver, 다이렉트와 유사하다고 보면 되는데 한 쪽은 다이렉트로 만들고 다른 한쪽은 다이렉트의 순서를 역순으로 배치하면 된다.
PC Com1
Com1은 Router/Switch, console port가 있다.
```

## 📌 MAC Address

```
Mac Address는 2계층에서 사용되는 주소로 물리적 주소, 이더넷 주소라고도 불린다.
Ipconfig/all 명령을 통해 맥어드레스를 추출할수도 있고, LAN카드에 고정되어 있다. Unique하다는 특징이 있다.


ARP(Address Resolution Protocol)
ARP Request를 통해 목적지를 찾아갈 수 있다. (BroadCast)방식으로.

예를들어, PC A가 다른 네트워크의 PC Z와 통신을 하고 싶어 ARP request를 하게 되면 다른 네트워크이기 때문에 ARP reply로 라우터의 Mac Address를 받게된다.


BroadCast의 개념
LAN상에 붙어 있는 모든 네트워크 장비들에게 데이터를 보내는 통신 host Address를 1로 채운다. 210.93.48.0, host 3에게 보낼때도 210.93.48.255로 보내는 것.

브로드캐스트를 자주 받게되면 인터럽트가 발생하기 때문에 CPU성능이 저하되는 원인이 되기도 한다.

멀티캐스트
보내고자 하는 그룹 멤버들에게 메시지를 보내는 방식
라우터나 스위치에서 기능을 지원해야 한다.
IP주소에서 D클래스를 사용함.
```

## 📌 LAN카드의 종류

```
데스크탑용 랜카드, 노트북용 랜카드 등등 초기에는 LAN의 설정 값을 직접 잡아주어야 했다.
```

## 📌 허브란?

- 멀티포트 리피터, 리피터는 데이터 전송시 전송거리의 제약이 있을 때 증폭기의 역할을 생각하면 되는데 멀리 떨어진 다른 곳으로 데이터의 전송이 가능하도록 하는 장비이다.

* 허브가 데이터를 전송할 때, 1번 보트가 데이터를 허브를 통해 전송한다고 하면 1번 포트를 제외하고 나머지 모든 포트로 데이터를 뿌려주게 된다.

* 랜카드는 MAC ADDRESS와 관련이 있기 때문에 나머지 포트들은 자신의 MAC과 비교하여 데이터를 무시하게 되고 자신의 MAC과 일치하는 경우에만 데이터를 처리할 것이다.

* 이 후, 자신에게 온 데이터라는 것을 알기 때문에 랜카드가 CPU에게 인터럽트를 걸어서 데이터를 처리해줄 것을 요청한다. (CSMA/CD 적용, 허브에 연결된 모든 PC들은 같은 콜리전 도메인에 있다❗️❗️)

* 📎 허브의 한계 -> 허브에 연결된 모든 PC는 하나의 콜리전 도메인에 속한다. 즉, 어느 한 순간에는 한 PC만이 데이터를 보내며 Shared 방식이다.

## 콜리전 도메인을 나누어줄 수 있는 장비 -> 스위치와 브릿지

- 스위치를 보통 스위치허브라 한다.
- 허브의 한계? 어느 한 순간에는 하나의 PC만이 데이터를 보내기 때문에 비효율적인 방식을 극복하기 위해 스위칭 허브를 사용, 각 포트별로 Collision Domain을 나누어 충돌을 방지시킨다.
- 스위칭 허브가 포트 별로 콜리전 도메인을 나누어서 사용하는 방식을 비동기적인 시선으로 바라보자❗️
- 브리지 또한 콜리전 도메인을 나누어 주는 역할을 수행한다.

## 📝 꼭 기억해야 할 것 Mac Address Table

- 콜리전 도메인을 나누어 주면서 Mac Address 테이블을 가지고 있다.

### 브리지와 스위치의 기능

- Learning : Mac Address table을 생성
- Flooding : 모르면 들어온 출발지 port를 제외하고 다른 모두에게 뿌려준다.
- Forwarding : Port 발견 시 보내준다.
- Filtering : 동일한 세그먼트 상에 있는 경우라면 가지 못하게 해준다. 세그먼트는 라우터, 허브 또는 스위치 등에 의해 묶여 있는 네트워크의 한 부분을 의미한다.
- Aging : 일정 시간이 지나다 보면 메모리 문제 때문에 지워진다. Mac Address Table에서 맥 어드레스를 저장하는 시간 주기 Default : 5 minutes

### 브리지와 스위치의 차이점

- 스위치는 처리 방식이 하드웨어 ASIC로 이루어지기 때문에 소프트웨어적으로 프레임을 처리하는 브리지에 비해 훨씬 빠르다.
- 브리지는 포트들이 같은 속도를 지원하는 반면 스위치는 서로 다른 속도를 연결해준다.
- 스위치는 브리지에 비해 제공하는 포트수가 많다.
- 스위치의 프레임 처리는 cut - through, store - and - forward방식을 사용
- 브리지의 프레임 처리는 store-and-forward만 사용

### ❗️ 스위치로 풀 수 없는 문제 -> 브로드캐스트

- 브로드캐스트 영역을 나눌 때, IP는 약 500개 노드
- 스위치로는 너무 제한적이다. 따라서 로드 분배가 필요하고 브로드캐스트를 나누어야 하기 때문에 라우터가 필요하다!
