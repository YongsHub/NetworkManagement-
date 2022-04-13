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
