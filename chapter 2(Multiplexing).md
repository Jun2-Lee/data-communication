# Multiplexing
---
## Link Layer - Multiplexing
__전송매체의 분류__
- Wired(유선) : 점대점 매체로, 양끝의 두 장치만 매체를 사용한다(Point to Point 방식) 
  - 전송매체 : Twisted Pair, Coaxial Cable...
- Wireless(무선) : 공유매체로, 여러 장치가 매체를 함께 사용한다(Multi-Point/Shared Media)
  - 전송매체 : Air, Sea Water...

__통신의 종류__
- Simplex(단방향 통신) : 한쪽은 송신, 한쪽은 수신만 가능 ex)Tv
- Half Duplex(반 쌍방향 통신) : 양방향 통신이 가능하나, 동시에는 불가능 ex) police Radio
- Duplex(쌍방향 통신) : 양방향 통신 ex)cell phone
### Multiplexing
__Multiplexing__
> 점대점 매체의 공유 <-> MAC(Medium Access Control : 방송매체의 공유)

__Multiplexing Type__
- FDM(_Frequency Division Multiplexing_) : 주파수 분할 다중화
- TDM(_Time Division Multiplexing_) : 시간 분할 다중화
- CDM(_Code Division Multiplexing_) : 코드 분할 다중화
#### FDM(Frequency Division Multiplexing)
- analog signal을 사용 가능
- 전송할 Data가 있던 없던 채널을 할당하는 단점이 존재 -> 자원 낭비
- 반송파(carrier frequencies)가 주파수를 겹치지 않게, _Guard Bands_ 를 포함해서 분리해줌
![FDM](https://user-images.githubusercontent.com/80378041/113839815-ff755680-97ca-11eb-84b3-0723a48216e3.PNG)

__Baseband Signal & Modulation__
- Baseband Signal : modulation이 되기 전의 신호(우리가 보내고자 하는 신호)
- modulation : BaseBand에 반송파(carrier frequencies)를 씌우는 것.
- Passband Signal : Molulation을 거친 후의 신호
![BB](https://user-images.githubusercontent.com/80378041/113840442-a5c15c00-97cb-11eb-84f7-3f9fb2c32cbb.PNG)
>            Modulation 식. 이때 X = f_c+f_m, Y = f_c-f_m

__Filter & Demodulation__
- Filter : 내가 받고자 하는 주파수의 영역대를 걸러주는 것.
- Demodulation : Passband Signal을 받아서 다시 Baseband Signal로 바꿔주는 것.
![asdf](https://user-images.githubusercontent.com/80378041/113841227-76f7b580-97cc-11eb-8285-3f8d0e489065.PNG)
![zxcv](https://user-images.githubusercontent.com/80378041/113841301-87a82b80-97cc-11eb-9fd1-bab3c6eef9d9.PNG)
>            Demodulation 식. 이때 X = 2f_c+f_m, Y = f_m
__FDM Example__

![zxcvsd](https://user-images.githubusercontent.com/80378041/113841659-e8cfff00-97cc-11eb-8f11-885e8cb8a68c.PNG)
> 이때의 carrier signal은 각각 위에서부터 20, 24, 28이다.
### WDM(Wavelength Division Multiplexing)
- 각기 다른 주파수의 빛들이 광섬유 안으로 지나다니는 방식
- WDM은 FDM과 비슷하며 Multiplexing과 Demultiplexing을 통해 light signals로 정보를 전달함.
- 현재의 초고속 인터넷을 가능하게 한 기술이다.
- Wavelength(파장) ~ 1/Frequency
### Synchronous TDM(Time Division Multiplexing)
- digital&analog signal을 시간으로 분리된 digital data로 전송한다.
- Time slot을 block단위로 자른다.
- FDM과 비슷하게 전송할 데이터가 없어도 Time slot이 할당되는 낭비가 있다.
- digital화 된 voice stream을 multiplexing할 때 많이 사용된다.

__Synchronous TDM의 구조__
![xzcvw](https://user-images.githubusercontent.com/80378041/113843551-a14a7280-97ce-11eb-8d72-974b3d08797c.PNG)
- 위의 사진에서, 각각의 input connection들의 data rate을 1kbps라고 하자. 만약 한번에 1비트가 multiplexed된다고 가정할 때, 
- (a) : 각각의 input slot의 duration은? --> 1ms(1/1000s)
- (b) : 각각의 output slot의 duration은? --> 1/3ms(1/3000s)
- (c) : 각각의 frame의 duration은? --> 1ms(1/1000s)
__Digital Carrier Systems__
- 통신 사업자들이 디지털 기간 망 구축에 사용한 TDM 체계
![ds](https://user-images.githubusercontent.com/80378041/113847701-af9a8d80-97d2-11eb-86a9-be4d13d3c26d.PNG)

### Statistical/Asynchronous TDM
- Synchronous TDM에서는 보낼 Data가 없어도 Time slot을 낭비한다.
- 이 낭비를 줄이기 위해서 Time slot에 헤더를 붙여서 도착지를 지정해준다.
- Time slot하나의 길이는 더 길어지지만, Synchronous TDM보다 line을 적게 쓰기때문에 얻는 Gain이 더 크다.

## Queueing Models
- __Input Rate__(넣는 데이터) : lambda, __Output Data Rate__(처리할 수 있는 데이터) : mu
  - Average of lambda < Average of mu(capacity)여야 한다 --> lambda > mu이면 큐에 무한하게 item들이 쌓이게 되고,
    lambda = mu이면 무한 loop가 돌게 된다.
![q](https://user-images.githubusercontent.com/80378041/113850207-2d5f9880-97d5-11eb-9a19-c1e633e77412.PNG)
__Basic Queueing Parameters__
- lambda : Arrival Rate(input Rate)
- T_s : Service time
- T_w : Waiting time
- T_r : T_s+T_w, residence time
- R : system안에 있는 item들의 수
- W : Queue안에 대기하고 있는 item의 수
- rho : 서버가 얼마나 바쁜지 = lambda/mu
 
__Example of Queueing model__

![s](https://user-images.githubusercontent.com/80378041/113851090-166d7600-97d6-11eb-98e6-237091625171.PNG)
>        Input = 10 sources, 1000 bps/source; average input rate = 50% of maximum
- Backlog : Input으로 들어온 값을 capacity만큼 계산해서 output으로 내보낸 뒤 남은 값.
- Limited Buffer/Queueu Length : 한계 Backlog 값. 이것을 넘어가면 packet drop이 발생하고 overflow가 된다.

__Some Basic Queuing Relationships__

![b](https://user-images.githubusercontent.com/80378041/113852615-b546a200-97d7-11eb-9f8a-0e3c9e196fe9.PNG)

__Kendal's Notation__
- Arrival process / Service time / Servers / Max Occupancy(없을수도 있음) 형식으로 쓴다
- Arrival process, Service time에 대해서
  - M : 포아송 process(Input rate - lambda 값)
  - G : General Distribution
  - D : Dererministic Distribution

__Exponential Service (M/M(포아송으로 값이 바뀜)/1)__

![we](https://user-images.githubusercontent.com/80378041/113853552-bf1cd500-97d8-11eb-9d18-f4032d0f32f5.PNG)

__Constant Service Time (M/D(값이 정해짐)/1)__

![wr](https://user-images.githubusercontent.com/80378041/113853634-d65bc280-97d8-11eb-9185-b2b7d468eacb.PNG)

### Poisson Random Variable

![p](https://user-images.githubusercontent.com/80378041/113853935-3e120d80-97d9-11eb-8b27-a54d16dc7968.PNG)
>   k : 어떤 사건의 발생 횟수. 
>   
>   lambda : 이 사건의 평균 발생 확률(이것을 알고 있어야 한다). 
>   
>   모든 사건은 독립적으로 일어나야 한다.

__The relation between Poisson and Exponential__

- 둘 다 평균 발생횟수 lambda는 바뀌지 않으며, 각 사건들은 독립적이어야 한다는 공통점이 있다.
- 포아송은 이산적인 사건에 대해서, time에 대한 사건 발생에 중점을 두고, Exponential은 연속적인 사건이 일어나는 시간을 중점으로 둔다. 







