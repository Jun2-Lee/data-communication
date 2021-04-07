# Multiple Access & Mac
---
### Multiplexing and Multiple Access
- TDD(Time Division Duplex : 시간을 다르게 해서 양방향 통신을 함), FDD(Frequency Division Duplex : 주파수를 다르게 해서 양방향 통신을 함)로 양방향 통신을 한다
### Multiple Access Protocols
- Single shared broadcast channel
  - broadcast channel은 하나인데 node들이 여러개이다.
  - 동시에 하나 이상으로부터 정보를 전송받으면, 충돌이 일어나서 전송이 제대로 되지 않을 수 있음
- Multiple Access Protocols
  - 노드들이 어떤 방법으로 broadcast를 나누어 쓰는지 정하는 것이다.
  - in-band communication : separate control channel을 보유하지 않은 경우(Bandwidth내에 있는 특정 채널을 사용)
  - out-band communication : separate control channel을 보유한 경우(외부의 채널을 사용)
#### Ideal multiple Access Protocol
- broadcast channel이 R bps라고 했을 때, node가 1개면 R의 속도로 전송.
- node가 m개면 R/M의 속도로 전송.
- no special node : 다른 node들을 관리하는 special node가 없다.
- 시간이나, slot에 대해 동기화가 필요 없다.
- 간단해야 한다.

위의 것들을 만족하는 것이 Ideal multiple Access Protocol이다.

#### MAP Taxonomy
- Channel Partitioning
  - 채널을 구분하는 것.
  - 채널을 작은 조각으로 나누어서 사용. ex) FDMA, CDMA, TDMA등
- Taking Turns
  - 토큰을 획득해서 노드를 사용하는 것.
- Random Access
  - 채널이 분리되지 않았고, 충돌이 발생 가능하다.
  - 충돌에 대한 복구가 있어야 한다.
##### Random Access Protocols
- 임의로 공유된 채널에 접속
- Random(or contention(경쟁) based) Access Protocol
- 미리 어떤 노드가 사용할지 미리 정하지 않기 때문에 충돌이 발생할 수 있다.
- LAN(Local Area Network)에서 많이 쓰임
  - WAN(Wide) -> MAN(Metro) -> LAN(Local) -> PAN(Personal) -> BAN(Body)
- 충돌을 어떻게 감지할 것인지, 충돌을 어떻게 복구할 것인지 고려해야 함.
__Type of Contention based MAC Protocol__
  - ALOHA(Pure ALOHA), slotted ALOHA
  - CSMA(carrier sense multiple access)
  - CSMA/CD(Carrier Sense Multiple Access/Collision Detection) - Ethernet(wired) -> IEEE 802.3
  - CSMA/CA(Carrier Sense Multiple Access/Collision Avoidance) - Wireless LAN(WIFI) -> IEEE 802.11
#### ALOHA
- 1970년에 하와이 주립대에서 만듬.
- __Pure ALOHA__
  - 데이터가 들어오면 바로 전송
  - 만약 충돌이 발생한다면, random delay 이후에 다시 보낸다
  - 최대 효율이 18%

![f](https://user-images.githubusercontent.com/80378041/113896491-f0ab9580-9804-11eb-80ab-82ddcc33c7a8.PNG)

- __Slotted ALOHA__
  -










