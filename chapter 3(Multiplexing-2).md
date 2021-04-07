# Multiplexing
---
### Spread Spectrum
- 무선 통신을 위한 Encoding 기술이다.
- jamming과 signal interception을 당하지 않기 위해서 signal을 넓은 bandwidth에 퍼뜨려서 보내는 기술이다.
- __FHSS, DSSS__ 2가지 방식이 있다.
#### General Model of Spread Spectrum System
![a](https://user-images.githubusercontent.com/80378041/113864980-871c8e80-97e6-11eb-9fd2-739ee1a90767.PNG)
### FHSS(Frequency Hopping Spread Spectrum)
- 주파수를 Hopping하면서 signal을 spread하는 것.
- hopping 순서는 pseudo Random으로 결정한다.
- ex) Bluetooth(대표적인 frequency spread spectrum) 
    - 2.4G의 대역폭을 사용하며, 80개의 채널을 Hopping한다.
    - ISM band(License Free Band)이다.

![FSSS](https://user-images.githubusercontent.com/80378041/113865559-2fcaee00-97e7-11eb-9570-cbb92be76229.PNG)

### DSSS(Direct Sequence Spread Spectrum)
- signal에 pseudo Noise code를 Xor해서 전송하는 방식.
- 다시 해독할때도 같은 pseudo Noise code를 Xor해서 해독한다.

![DSSS](https://user-images.githubusercontent.com/80378041/113868940-29d70c00-97eb-11eb-908f-0775bea41b9a.PNG)
 
### Spread Spectrum Gains
- noise, 신호왜곡에 강한 특성을 가진다.
- 보안정이 강화된다.
- 적은 간섭으로 같은 주파수를 공유 할 수 있게 되었다.
  - CDM(Code division muliplexing), Cellular telephones, CDMA(Code division multiple access)
  
### CDM(Code Division Multiplexing)
- DSSS 기술을 기초로 한다

![zx](https://user-images.githubusercontent.com/80378041/113869839-242df600-97ec-11eb-9a52-2caf3a3f2777.PNG)

- spread spectrum과 CDM
  - CDM은 Spread Spectrum에 기초하고 있지만 두 기술의 목표는 다르다.
  - CDM ->자원 공유, Spread Spectrum -> 통신보안, 간섭 및 잡음에 대한 강인성을 각각 목표로 한다.
###### CDM Example

![exx](https://user-images.githubusercontent.com/80378041/113870177-8555c980-97ec-11eb-9fc1-3ebc8774399b.PNG)

![ec](https://user-images.githubusercontent.com/80378041/113870310-ac140000-97ec-11eb-9196-3114dec2bbb2.PNG)

> 2개 이상의 신호를 한 주파수로 보낼 때 곱하는 code는 orthogonal code(둘이 곱했을때 0이 되는)여야 한다.

###### WH(Walsh-Hadamard) Matrix
- orthogonal code를 쉽게 구하기 위해 고안된 Matrix

![WH](https://user-images.githubusercontent.com/80378041/113870895-4a07ca80-97ed-11eb-8604-4f711fbc63a4.PNG)
> 이러한 형태로 생겼고, H_2는 2명까지 사용 가능, H_4는 4명, 이런식으로 늘어나서 120명이 사용하기 위해서는 H_128이 필요하다.
> 각각의 column, row가 모두 othogonal code이다.
### SDM(spatial Division Multiplexing)
- 동일한 시간에 동일한 주파수라도 공간이 다르다면 사용할 수 있다
- ex)

![e](https://user-images.githubusercontent.com/80378041/113872765-22196680-97ef-11eb-9580-645107a888a7.PNG)

#### MIMO(Multi-Input Multi-Output) / Beamforming
- 다중 안테나와 진보적인 신호 처리 기술로 다양한 경로로 전달되는 공간의 무선 스트림들응ㄹ 개별적으러 처리 가능해짐
- 다중 안테나로 출력 -> 다중 안테나로 입력을 받는 스마트 안테나 시스템
- 무선통신의 용량을 늘리기 위해 사용.

![x](https://user-images.githubusercontent.com/80378041/113884948-62caad00-97fa-11eb-9f3e-9dbcc6673e48.PNG)

- beamforming : 특정 신호를 증폭시켜 하나의 단말기로 집중시키는 것

![b](https://user-images.githubusercontent.com/80378041/113885138-8db50100-97fa-11eb-8c63-05206887d4b6.PNG)

###### MIMO Principles:2 transmission schemes
- Spatial Diversity : 전송 안정성을 높이기 위한 방법. 각자 신호에 원하는 Data를 강한 신호로 줌.
- Spatial Multiplexing : 전송 용량을 높이기 위한 방법. 각자 신호에 원하는 신호만 실어서 보냄

#### MU-MIMO(Multi-user MIMO)
- Mimo를 다중 사용자에게 적용시킨 것.
- Wi-Fi, 4G/5G에도 사용되고 있다.
