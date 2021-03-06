## OSI 7계층

<img src="http://www.netcrew.co.kr/files/2016/01/01/e5043fd276f8e8a924a6c703fcd1b4af162424.jpg" width=550px />

전송 데이터는 송신 호스트의 응용 계층에서 시작해 하위 계층으로 순차적으로 전달되어, 최종적으로 물리 계층에서 수신 호스트에 전달된다.

데이터가 **하위 계층**으로 이동할 때는 각 계층의 프로토콜에서 정의한 헤더 정보가 **추가**된다. 수신 호스트에서는 반대로 **상위 계층**으로 이동하며 순차적으로 헤더 정보를 **제거**하고 해석한다.



#### 물리계층

- 하드웨어 시스템으로 구현
- 데이터 전송속도, 송수신 호스트 사이의 클록 동기화 방법, 물리적 연결 형태 등을 다룬다.



#### 데이터 링크 계층

- 물리 계층을 통해 전송되는 데이터의 물리적 전송 오류를 감지해 송수신 호스트가 인지할 수 있게 한다.
- 상위 네트워크 계층에 신뢰성 있는 패킷 전송을 보장
- 전송 경로 문제를 해결할 수 없으므로, 두 호스트가 1:1로 직접 연결된 환경에서 데이터 전송 기능을 지원.
- 데이터 링크 계층을 이용해 전송되는 데이터를 **프레임**이라 부른다. 프레임 헤더에 표시되는 송수신 호스트 정보에는 LAN 카드에 내장된 송수신 호수트의 ==*MAC 주소*==가 기록된다.
- 흐름 제어 기능 지원



#### 네트워크 계층

- 데이터가 올바른 경로를 선택할 수 있도록 지원
- 중개 시스템의 기능은 일반적으로 **라우터**가 수행
- 전송 데이터를 **패킷**이라 부른다.
- 중개 과정에서 경로 선택의 기준이 되는 호스트 주소가 필요... 인터넷에서는 IP프로토콜
- 혼잡 제어(Congestion Control)



#### 전송 계층

- 송신 프로세스와 수신 프로세스를 직접 연결하는 **단대단(End-to-End)** 통신 기능을 제공
- 컴퓨터 내부에서 논리적으로 구축되는 통신 당사자 사이의 통신 문제를 다룬다.
- 전송 오류율, 전송 속도, 흐름 제어



#### 세션 계층

- 전송계층과 유사하지만 *사용자에게 원격 파일 전송이나 원격 로그인 같은 세션 기능을 제공*한다는 점이 다르다.
- 송수신 호스트 사이의 대화 제어, 토큰 제어, 일시적인 전송 장애를 해결하기 위한 동기화 기능



#### 표현계층

- 데이터의 의미와 표현방법 처리. 통신 양단에서 서로 이해할 수 있는 표준 방식으로 데이터를 코딩
- 데이터표현 방법이 서로 다른 호스트 사이에서 데이터 변환, 데이터 암호화, 압축



#### 응용계층

- 다양하게 존재하는 응용 환경에서 공통적으로 필요한 기능을 다룬다.

- 인터넷에서 많이 사용하는 서비스는 FTP





## 게이트웨이

네트워크르 연결을 수행하는 시스템을 Gateway라고 부른다.

- 리피터

  물리 계층의 기능을 지원.

  물리적 신호는 전송 거리가 멀면 감쇄되기 때문에 중간에 이를 보완해준다.

  입력된 신호를 물리적으로 증폭하여 다른쪽으로 중개하는 역할



- 브리지

  리피터 기능에 데이터 링크 계층의 기능이 추가된 게이트웨이



- 라우터

  물리계층, 데이터링크 계층, 네트워크 계층의 기능을 지원

  네트워크 계층은 경로 선택 기능을 제공해야 하므로 임의의 네트워크에서 들어온 데이터의 경로를 판단한다.

  라우터는 자신과 연결된 네트워크와 호스트 정보를 유지/관리 —> 라우팅 테이블 이용









## TCP/IP 모델

인터넷은 데이터 중개 기능을 담당하는 네트워크 계층으로 IP프로토콜을 사용하는 네트워크다.

따라서 인터넷에 연결하고자 하는 호스트는 반드시 IP프로토콜을 지원해야 하며, 전송 계층은 TCP나 UDP를 사용한다.

현재 인터넷에서 사용하는 IP프로토콜은 IPv4다.



#### ARP / RARP

TCP/IP 모델에서 사용하는 주소는 데이터 링크 계층의 MAC 주소, 네트워크 계층의 IP 주소, 전송 계층의 포트번호다.

* ARP : IP -> MAC
* RARB : MAC -> IP



#### ICMP(Internet Control Message Protocol)

IP 프로토콜을 이용해 데이터를 전송하는 과정에서 오류가 발생하면 ICMP를 사용해 관련 제어 데이터를 처리한다.





## LAN(Local Area Network)

단일 건물이나 학교 같은 소규모 지역에 위치하는 호스트로 구성된 네트워크

호스트간의 간격이 가깝이 때문에 브로드캐스팅(Broadcasting)방식으로 전송

![LAN ë²ì¤íì ëí ì´ë¯¸ì§ ê²ìê²°ê³¼](http://cfile217.uf.daum.net/image/036D593F50F76F6E2B0C6E)



- 버스형

  - 한 호스트가 전송한 데이터를 네트워크에 연결된 모든 호스트에 전송 -> 브로드캐스트 방식

  - 버스형에서는 전송데이터가 모든 호스트에 전송되므로 라우팅 기능이 따로 필요없다.

  - 둘 이상의 호스트에서 데이터를 동시에 전송 -> 충돌(Collision) 발생

- 링형

  - 데이터는 시계나 반시계 방향으로 전송

  - 특정 호스트에서 전송한 데이터는 반드시 링을 한바퀴 돌아 송신 호스트로 되돌아온다.

  - 브로드캐스팅방식 지원

  - 충돌 발생 -> 토큰(Token)을 사용해 충돌 가능성 차단

    데이터를 전송할 호스트는 사전에 전송용 토큰을 확보해야 한다. 토큰은 하나밖에 없다.



## WAN(Wide Area Network)

점대점(Point-to-Point)연결. 스타형, 트리형, 완전형, 불규칙 형 등 다양한 구조





## 데이터 전송 

- 점대점 방식

  1:1 , 다른 호스트에는 데이터 전달 x

  WAN환경에서 주로 사용

  스타형, 링형, 완전형(mesh), 불규칙형



- 브로드캐스팅 방식

  공유 전송 매체 하나에 여러 호스트를 연결하기 때문에 네트워크에 연결된 모든 호스트에 데이터가 전송된다.

  수신데이터를 바을지, 폐기할지는 수신호스트가 결정

  LAN
  버스형, 링형(자신이 수신 호스트가 아니면 데이터를 수신하지 않고 그냥 통과시킨다.)



* 유니캐스팅(1:1)
* 멀티캐스팅(N:N)







- 프레임





## MAC 계층

- IEEE 802
- 
- 
- 
- 
- 
- 이더넷
- 토큰 버스
- 토큰 링



## 이더넷



#### CSMA/CD

- CSMA 방식은 둘 이상의 호스트에서 동시에 채널의 유휴 상태를 확인할 가능성이 있다. 따라서 여러 호스트가 동시에 채널을 사용할 가능성 -> 충돌 가능성이 커진다.
- 호스트가 충돌을 감지하면 진행 중인 프레임의 전송을 중지한다.





## 데이터 링크 계층

- 프로토콜
- 슬라이딩 윈도우 프로토콜
- HDLC 프로토콜



## IP 프로토콜

- 서비스의 종류
- 라우팅
- 혼잡제어
- IP프로토콜



## ipconfig

Internet Protocol Configuration

![ipconfigì ëí ì´ë¯¸ì§ ê²ìê²°ê³¼](https://i.imgur.com/NvgGVgR.jpg)

1. IP Address

   192.168.65.1

   원래는 32bit. 이 주소를 8bit section으로 나누어 각 section을 십진수로 변환한 것.



 - 네트워크 주소 : 192.168.65.x
 - 호스트 주소 : x.x.x.1

네트워크 주소는 호스트별로 사용할 수 있는 네트워크의 범위를 나타내고,

호스트 주소는 네트워크 범위 내에서 각 호스트를 구분하기 위한 주소.



2. Subnet Mask

   서브, 메인이 아닌 어떤 가공으 통한 네트워크를 만들기 위해 씌우는 마스크

   주어진 IP주소를 네트워크 환경에 맞게 나누어 주기 위해서 씌워주는 이진수의 조합

3. Default Gateway

   내부 네트워크에서는 라우터 없이도 통신이 가능

   통신 시 목적지를 찾기 위해 내부 네트워크에서 먼저 찾음

   없을 경우, 기본 게이트웨이를 통해 외부 네트워크에서 목적지를 찾음



## DHCP(Dynamic Host Configuration Protocol)

IP주소, 서브넷마스크, 디폴트게이트웨이 IP주소, DNS 서버 주소 등 다양한 네트워크 정보럴 DHCP가 PC와 같은 이용자단말에 동적으로 할당해주는 프로토콜

IP주소를 효율적으로 낭비 없이 사용하고, 충돌을 막는데 효과적.

​	

## 네트워크 계층 프로토콜

- IPv6

  서브넷팅과 DHCP등으로 열심히 개선했지만, 그래도 감당이 안되어 등장한 것

- 터널링

- ARP

- ICMP

- IGMP



## TCP



## UDP



## 세션계층



## 표현계층



## 응용계층



## 암호화

- DES
- RSA
- 전자서명



## 웹(WWW)

- 클라이언트-서버 모델
- HTML
- HTTP



## DNS



## FTP



