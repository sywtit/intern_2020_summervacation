# intern_2020_summervacation

(주)텔러스 인턴 중 개발했던 PSAP simulator

### 기술 소개
-----

**e-call**

e-call이란 긴급 구난 통보 시스템을 의미하며, 차량 사고 발생시 수동 및 자동으로 이를 감지하여 사고 정보를 통제, 구관기관 요청이 가능한 센터(PSAP Simulator)에 연결함으로써 골든 타임을 확보해 사고에 대한 초기 대응을 도와주는 기술이다.

**처리 과정**

차량 사고 발생시, e-call 단말기에서 호 처리 기능의 call controller작동을 하고 사고 정보, 통신 데이터를 제어한다. call controller는 이후 VDCIApp를 통해 SIP signal, 미디어, NG eCall를 처리하여 PSAP Simulator에 해당 정보를 전송하고, 요청 받는다. 

### 개발 내용
-----

* Early-bird 사전 교육 과제로 SharpPcap를 이용해서 Wireshark와 같은 C# 패킷 캡쳐 프로그램을 구현
* 해당 프로그램은 PSAP Simulator가 단말기와 ftp, msrp등의 프로토콜을 통해 통신 및 정보 교환이 제대로 이뤄지고 있는지 확인하는 목적을 가지고 있다.
* 현재의 PSAP Simulator의 기능을 분석하고, 실제 사고가 발생했을 때의 여러 상황에 따라 테스트 시나리오를 제작해 프로그램의 개선사항과 오류를 모집해서 해당 프로그램을 개선한다

### 개발 결과
-----

**PSAP Simulator**

![image](https://user-images.githubusercontent.com/52434154/112965195-ff9aa400-9183-11eb-8c33-2722430d8f4b.png)

1. 기존 프로그램의 shutdown, thread, database등의 오류들을 고쳐 프로그램을 안정화
2. ftp 프로토콜을 통해 단말기로부터 사고 전 20초 영상을 받아 play를 해주고 사고 후 10초 영상을 여러 번 요청하여 받아 볼 수 있도록 기능을 추가
3. Emulator와 동시에 이용할 수 있는 test chart 기능을 추가해서 emulator혹은 단말기에게 받은 모든 정보들의 기록을 데이터베이스에 저장해서 시각적으로 표를 이용해서 확인가능
4. Call log기능을 제작해 단말기와의 전체 통신 기록 저장
5. 통신과 관련된 호 명령 및 event 처리 코드 개선
6. UI 개선

**Packet Capture Program**

![image](https://user-images.githubusercontent.com/52434154/112965493-45f00300-9184-11eb-842d-9f3bc6d50a50.png)

1. 주로 SharPcap를 이용하되, Interface이름은 friendly name를 가져오기 위해 WinPcap를 활용
2. Time, Source/Dest IP, Protocol, Length, Info등등 Wireshark와 비슷하게 기능을 보여줌

**Before/After**

1. 오류 발생 빈도수 0.1 → 0.02 → 0.005이하(네트워크 상태와 노트북 성능에 따라 오류발생률이 유동적이다)
2. 필요했던 기능들을 추가해서 기존의 PSAP Simulator 프로그램을 개선했다.


#### 사용한 오픈소스

Packer Capture Program : 
https://github.com/GhadeerElkhazragy/WiShark



