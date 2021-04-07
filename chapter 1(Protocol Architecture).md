# Data Communication
---
## Protocol Architecture
- Layered Architecture
  - 복잡한 내용을 분할 정복해서 계층별로 정렬한 것이다.
  - 각 Layer는 바로 아래의 Layer만 이용 가능하고, 바로 위의 Layer에게 정보를 제공해준다.
  - 한 Layer의 변경이 반드시 다른 Layer의 변경을 유도하진 않는다.

![Layer](https://user-images.githubusercontent.com/80378041/113821626-4e18f580-97b7-11eb-93ed-860cd6e8d232.PNG)

- Layered Protocol Architecture
  - 상대(peer Layer)와 통신하기 위한 약속(Protocol)이 필요하다.
- Protocol의 key Elements
  - __Syntax__ : 데이터 블럭의 형태
  - __Sementics__ : 데이터의 처리 방법, 에러 해결 방법 등
  - __Timing__ : 서로간의 (시간 등)동기화
- __PDU, SDU, PCI__
	- __PDU(Protocol Data Unit)__ : PCI + SDU, 프로토콜 실행을 위해 주고받는 단위 유닛
	- __SDU(Service Data Unit)__ : 프로토콜의 서비스 유닛(자신이 서비스 받고싶은 유닛)
	- __PCI(Protocol Control Information)__ : 프로토콜 기능 실현을 위한 제어정보, Protocol Header
![PDU](https://user-images.githubusercontent.com/80378041/113822889-f5e2f300-97b8-11eb-9953-3e63e9b8d788.PNG)>Layered Protocol Architecture Example

![LP](https://user-images.githubusercontent.com/80378041/113823314-79044900-97b9-11eb-976c-9dcd1f82b5bc.PNG)>peer 사이의 통신 시에 물리적으로는 계층구조를 통하지만, 논리적으로는 peer 사이가 직접 연결 된 것 처럼 인식한다
## Standard Protocol Architecture
- __OSI Reference model__ : De Jure Standard(법률적인 표준)
	- ISO에서 정한 표준
	- 7개의 계층이 있음
- __TCP/IP protocol suite__ : De Facto Standard(사실상의, 마켓을 장악한 표준)
	- 현재 가장 널리 쓰이고 있음
#### OSI 7계층
- Physical : 신호를 처리해서 bit stream을 보내느 역할(전기, 기능, 기계적 신호)
- DataLink : bit stream의 신호를 이용해서 frame 을 주고 받을 수 있게 함
- Network : 하나 이상의 Link를 이용해서 다수의 장치들이 효과적으로 통신할 수 있게 함
- Transport : end system 사이의 데이터 교환(오류 검사 등)
- Session : Applications 사이의 Dialogues 
- Presentation : 데이터의 압축, 포맷 등을 담당
- Application : User interface
![ISO](https://user-images.githubusercontent.com/80378041/113824391-b0bfc080-97ba-11eb-93dc-5b9004ceb97e.PNG)
#### TCP/IP Protocol
- 세계 인터넷에서 쓰임
- 뚜렷한 model이 없음
- 분산적인 구조가 특징

OSI vs TCP/IP
![TCP](https://user-images.githubusercontent.com/80378041/113824744-1744de80-97bb-11eb-911b-58ea6e958984.PNG)
