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
  - 만약 충돌이 발생한다면, random delay 이후에 다시 보낸다(이전에 충돌 했던것들 간의 충돌을 막기 위해)
  - 최대 효율이 18%이다.

![f](https://user-images.githubusercontent.com/80378041/113896491-f0ab9580-9804-11eb-80ab-82ddcc33c7a8.PNG)

- __Slotted ALOHA__
  - 데이터가 들어와도 slot의 시작 시점에만 데이터를 전송한다.
  - Node들이 central clock으로 동기화 되어있어야 한다.
  - 충돌이 일어나면 프레임이 사라지거나 전체가 겹쳐진다
  - 최대 효율이 37%이다.

![wqe](https://user-images.githubusercontent.com/80378041/113952487-b9fb6c80-9850-11eb-9912-86042d251efc.PNG)

##### Performance Analysis of Pure ALOHA protocol
- Slot length를 1, 평균 도착 Frame을 Poisson 도착 비율 lambda라고 가정하자.
- __Throughput__ = Arrival Rate * Pr(Success) = lambda * Pr(success)
  - Pr(success) = Pr(No collision)
  - Packet Arrival during the interval (𝑡−1,𝑡+1)
   
    ![x](https://user-images.githubusercontent.com/80378041/113952897-938a0100-9851-11eb-9f5a-ab5eea1ba015.PNG)
    >m = (t+1 - (t-1)) * lambda
  
  - Pr(No Collision) →Pr(No Packet Arrival) : P_x(0)(충돌이 발생하지 않을 경우는 t-1부터 t+1까지 프레임이 전송되지 않을 확률과 같다.)
  - Throughput : lambda * P_x(0)
  - When does the throughput have the maximum : Throughput을 미분했을 때 0이 되는 lambda값이 maximum이다. 따라서 이 문제의 경우에는 lmabda = 1/2일 때이다.

##### Performance Analysis of Slotted ALOHA protocol
- 기본적인 동작은 Pure ALOHA와 동일하다.
- 하지만 충돌이 발생하는 범위가 t-1~t이다.
#### CSMA(Carrier Sense Multiple Access)
- 데이터를 전송하기 전에 내가 사용할 carrier주파수가 사용중인지 탐색한다
- 만약 사용중이 아니면, 전송을 시작한다.
- 사용 중일때는 다음 3가지 중에 1가지 방법을 사용한다
  - 채널이 idle 해 질때까지 기다렸다가 전송 -> 1 Persistent-CSMA
  - 채널이 idle 해 질때까지 기다린 후 p의 확률에 인해 전송 -> p Persistant-CSMA 
    - 어떤 1개가 p의 확률로 1개만 전송될 확률은 np(1-p)^n-1이다
  - 채널이 사용중이면, random delay이후에 다시 사용중인지 검사 -> NP-CSMA


__Persistand__ : channel이 busy하면 idle해 질때까지 기다리는 것

![xc](https://user-images.githubusercontent.com/80378041/113953860-b0bfcf00-9853-11eb-83bf-faa725d3445a.PNG)

##### CSMA collisions
- 기본적으로 충돌이 없을 것 같지만, 전파지연(Propagation Delay) 때문에 충돌이 발생함.

![xcva](https://user-images.githubusercontent.com/80378041/113953966-ebc20280-9853-11eb-9b53-98496528361e.PNG)
> t1이 검사를 했을때는 channel이 idle 했었다.

###### Network Delay
- Transmission Delay(전송 지연) : 데이터의 양 / Data Rate in bps
  - 데이터의 양에 따라 결정됨. 
  - ex) 우리가 큰 용량의 사진을 보내면 다운받는데 오래걸리는 것
- Propagation Delay(전파 지연) : 링크의 길이 / 신호의 속도(Maybe 빛의 속도)
  - 링크의 길이에 따라 결정됨.

![v](https://user-images.githubusercontent.com/80378041/113954699-4e67ce00-9855-11eb-84b9-a52d7279add4.PNG)

#### CSMA/CD(COllision Detection)
- CSMA를 사용하면, 충돌이 일어났을 때 충돌의 피해가 큼 -> 충돌의 피해를 감소시키기 위해 CSMA/CD를 도입(충돌 자체를 막는 것은 아니다)
- 충돌이 발생한 것을 감지한다 -> 전송을 중단한다 -> 채널이 낭비되는 것을 줄일 수 있다.
- 작동 구조는 다음과 같다
  - 채널이 idle하면, 전송을 시작한다. 아니면, 다음으로 넘어간다.
  - 채널이 busy하면, idle 해질 때까지 기다린 후, 전송을 시작한다(여기까지는 CSMA와 동일)
  - 충돌이 감지되면, 전송을 중지한다
  - 걸림(jam)이 끝난 후, random 시간을 기다린 후에 1번부터 다시 시작한다.
 
![erw](https://user-images.githubusercontent.com/80378041/113955283-61c76900-9856-11eb-80a9-f242477b145e.PNG)

![we](https://user-images.githubusercontent.com/80378041/113955323-773c9300-9856-11eb-9128-2ebbf7031b97.PNG)
> 보낸 신호와 검사한 신호가 같지 않으면, 충돌이 일어난 것이다.

##### 2 Observation on CSMA/CD
- transmitter가 전송/수신을 동시에 할 수 있어야 한다.
- 송신 신호 세기(Tx)와 수신 신호 세기(Rx)가 비슷해야 감지가 가능하다.
- 
__이러한 이유들로 인해서 무선에서는 사용하기가 어렵다__

![x](https://user-images.githubusercontent.com/80378041/114340035-9fe3c600-9b91-11eb-87f5-da731e9653bc.PNG)
> A에서 봤을 때, C의 신호가 도달한다고 하더라도, 신호의 세기가 너무 차이나서 detect하기가 매우 힘들다 (Near-Far effect). --> 이러한 이유로 Rx, Tx를 동시에 하기가 힘들다.

##### HTP(Hide Terminal Problem)

![HTP](https://user-images.githubusercontent.com/80378041/114340545-c22a1380-9b92-11eb-9c54-f7fc92412f7e.PNG)
> A가 carrier sense를 함 -> 하지만 C의 신호가 SINR threshold(수신민감도) 아래이기 때문에 A에서는 C의 신호를 감지를 하지 못함 -> channel이 Idle하다고 판단해서 신호를 보냄 -> B에서 충돌이 발생. ==> 이 경우에 A의 입장에서는 C가 숨겨져 있다(C is hidden terminal to A)라고 한다.

##### ETP(Exposed Terminal Problem)

![etp](https://user-images.githubusercontent.com/80378041/114341002-bc80fd80-9b93-11eb-9321-0e7cfb1fbdee.PNG)
> X는 Y에게 신호를 보내고 싶음 -> carrier sense를 했는데, A가 전송중이라 전송을 하지 않음 -> 하지만, Y는 A의 범위 밖이라서 충돌이 일어나지 않음.
> 반대로,A도 X가 전송중이라 전송을 하지 않았는데,X와 B도 충돌이 일어나지 않음. ==> 두가지 경우에 손해가 일어났다.(성능 저하) 
> 여기서 충돌이란 reciever 입장에서 판단해야 한다는 것을 알 수 있다.

#### Taking Turns Mac Protocols
- Polling
  - master node가 node들의 turn을 지정해주는 방식이다.
  - polling overhead, 지연, master node가 고장나면 시스템이 고장난다는 문제점이 있다.
- Token Passing
  - Token이 존재하고, token을 가지고 있는 node의 turn이 되는 방식.
  - token overhead, 지연, token이 없어지면 안된다는 문제점이 있다.








