### Error Detection
- Error in communication : 보낸 정보과 받은 정보가 다른 것.
- 2 different Binaty Channel Models
  - Binary Channel이란 1과 0두가지 Symbol만을 전송하는 채널이다.

![er](https://user-images.githubusercontent.com/80378041/114344571-0ae5ca80-9b9b-11eb-949d-012e467cde4f.PNG)
> BSC(Binary Symmetric Channel) : 보낸 값이 바뀜  BEC(Binary Erasure Channel) : 보낸 값이 사라짐.

#### Error in computer Network
- Bit level error -> BSC 모델
  - Link나 channel단위에서 발생(외부 Noise등에 의해서)
- Packet level error -> BEC 모델
  - 너무 많은 Bit error가 발생해서 패킷을 복원하기 어려운 경우 하위계층에서 packet을 버림
  - Network 계층에서 스위치가 수신한 Packet을 처리하지 못하여 Drop시키기도 함(ex_ Queue가 가득차서 Packet을 Drop하는 경우)

![fweq](https://user-images.githubusercontent.com/80378041/114345023-e6d6b900-9b9b-11eb-88e1-6a0ad751c11a.PNG)

#### Error Detection & Recovery
- Error Detection
  - Bit level error : Error detecting code를 이용해서 탐지한다(Parity bit, CRC등)
  - packet level error : Loss, Out of Order, Duplicate
- Error Recovery
  - Retransmission : 데이터를 받은 수신자 측에서 송신자 측으로 feedback을 보내고, 이를 기반으로 문제가 된 데이터를 재전송 해주는 방법.

![r](https://user-images.githubusercontent.com/80378041/114345336-78462b00-9b9c-11eb-963c-d7cc38d2daf9.PNG)
  - FEC(Forward Error Correction) : 송신자가 데이터 외에 추가정보(Redundancy)를 보내 에러 발생시 정보 재전송 없이 추가 정보만으로 수신자가 자체 복구하는 방법. 
delay없이 복구 가능하다는 장점이 있지만, error가 없는 경우에도 Redundancy overhead가 붙ㅇ고, 모든 error가 복구 가능한 것도 아니다.

![f](https://user-images.githubusercontent.com/80378041/114345505-d246f080-9b9c-11eb-8531-964db7d32b16.PNG)

#### Type of Errors
- single bit error : 에러가 가끔 하나씩 발생하는 경우
- bust errors : 에러가 한번에 많이 발생하는 경우 -> 이 경우에 복구가 더 어렵다.

![v](https://user-images.githubusercontent.com/80378041/114345649-1639f580-9b9d-11eb-82d6-80d2145ad190.PNG)

#### Error Detection
- n bit codeword(k bit data(보내고 싶은 데이터) + (n-k)bit codebits(에러를 찾기 위한 추가 데이터)) : 이것을 사용해서 에러를 찾아 낼 수 있다
  - code rate = data / codeword = k/n
- Legal codewords와 Illegal codewords가 있다(ex_parity bit에서의 even parity example이 Legal codewords면, 1이 홀수개인 것들이 Illegal codewords이다)
  - no error : Legal codewords -> Legal codewords
  - Error
    - Legal codewords -> Legal codewords지만, 보내는 값과는 다른 경우(Undetectable Error)
    - Legal codewords -> Illegal codewords(Detectable Error)

![b](https://user-images.githubusercontent.com/80378041/114346179-fc4ce280-9b9d-11eb-858a-fff1f910deaa.PNG)
> 이 경우 B와 C가 Error이다, B는 Legal codewords -> Illegal codewords, C는 Legal codewords -> Legal codewords지만, 보내는 값과는 다른 경우이다. 
