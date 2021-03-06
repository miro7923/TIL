# 컴퓨터구조<br>
## 목차<br>
* [컴퓨터 네트워크 기초](#컴퓨터-네트워크-기초)
* [데이터 통신](#데이터-통신)
* [OSI 참조모델](#osi-참조모델)
* [인터넷 프로토콜](#인터넷-프로토콜)
* [Application](#application)
* [REST](#rest)
* [TCP와 UDP](#tcp와-udp)
* [Transmission Control Protocol](#transmission-control-protocol)
* [Congestion Control](#congestion-control)
* [출처](#출처)

# 컴퓨터 네트워크 기초
## 컴퓨터 네트워크
* 전송 매체를 통해 서로 연결되어 데이터를 공유, 교환하는 컴퓨터의 모음
* 예) 인터넷
* 네트워크는 크게 나누면 유선, 무선 두 종류로 나눌 수 있다.<br><br><br>

## 프로토콜(Protocol)
* 정보교환을 위해 필요한 통신 규약
* 사람들끼리 말을 할 때 맥락없이 얘기하지 않고 서로 합의된 맥락 안에서 얘기하듯 컴퓨터 간 통신을 할 때에도 맥락이 필요하다.
* 예) `HTTP`, `TCP`, `IP`<br><br><br>

## 컴퓨터 네트워킹이 필요한 이유
### 연결과 통신
* 멀리 떨어져 있는 사용자와도 효율적으로 정보를 교환하기 위해서

### 데이터 공유
* 컴퓨터 네트워크를 통해 쉽고 빠르게 데이터 공유
* 컴퓨터 네트워크를 사용하는 ❗️ 가장 중요한 이유 중의 하나라고 할 수 있다.

### 하드웨어 공유
* 사무실에 프린터는 한 대만 두고 사무실내의 컴퓨터들이 네트워크를 통해 프린터를 공유하는 것처럼 하드웨어 공유를 통해 경비를 절감할 수 있다.

### 데이터 보안과 관리
* 네트워크에 연결된 서버에 저장, 데이터 읽기/수정 관리

### 성능 개선
* 업무를 여러 컴퓨터에 분산시켜 동시에 처리<br><br><br>

## 기초 용어
* 노드(Node) : 컴퓨터 네트워크에 연결된 컴퓨터 또는 네트워크 장비를 일반화한 용어
* 호스트(Host) : 사용자의 요청을 처리하는 컴퓨터를 일반화한 용어
* 클라이언트(Client) : 서비스를 요청하는 호스트
* 서버(Server) : 서비스 요청을 받아 서비스를 제공하는 호스트
* 네트워크 인터페이스(Interface) : 호스트와 컴퓨터 네트워크의 연결 지점으로 네트워크 인터페이스 카드(NIC)라고 한다.
* 전송 매체(Transmission Medium)
    * 송신측 호스트와 수신측 호스트 사이를 상호 연결하는 물리적인 선로
    * 유선(Wired) 전송 매체와 무선(Wireless) 전송 매체로 구분
    * 링크(Link)라고도 한다.
* 채널(Channel)
    * 송신측에서 수신측으로 데이터를 전송하기 위해서 사용
    * 유선과 같은 전송매체 또는 무선(Radio) 채널과 같이 다중화(Multiplexing 여러 호스트가 하나의 채널을 공유하는 것) 된 매체에서 하나의 논리적 연결(Logical Connection)을 말함
    * 채널의 전송 용량은 `bps`(bit per second 초당 보내는 bit의 양) 단위의 전송률 또는 `Hz` 단위의 대역폭(Bandwidth)으로 표시<br><br><br>
    
## 컴퓨터 통신구조
* 서로 다른 시스템간의 통신을 하나의 모듈로 처리하기는 너무 복잡하기 때문에 기능별로 모듈을 세분화해서 구현할 필요가 있다. 
* 세분화된 모듈을 계층화 한 구조가 컴퓨터 통신 구조

### 계층화 하는 이유
* 복잡한 시스템의 각 부분을 식별하고 연계하는데 좋다.
* 모듈화는 시스템의 유지 및 개선을 용이하게 한다.
* 특정 모듈을 변경하더라도 다른 모듈에 영향을 주지 않는다.<br><br>

<p align="center"><img src="https://miro7923.github.io/assets/images/networkHierarchy.png" width="500px" height="550px"></p><br>

* 대표적으로 ISO OSI 7계층 통신구조와 인터넷 프로토콜 구조(5계층)이 있다.

### 인터넷 통신구조
* `응용(application)` : 응용 서비스 지원
    * `HTTP`, `FTP`, `SMTP`
* `트랜스포트(transport)` : 호스트간의 데이터 전송
    * `TCP`, `UDP`
* `네트워크(network)` : 라우팅
    * `IP`, `RIP`등
* `데이터링크(datalink)` : 네트워크 노드간의 데이터 전송
    * `Ethernet`
* `물리(physical)` : 물리적인 케이블<br>
* 각 계층은 하위계층을 반드시 이용해야 한다.
* 응용계층쪽으로 갈수록 사용자와 가깝고 물리계층으로 갈수록 하드웨어와 가깝다.<br><br><br>

## 표준화
* 정보통신 시스템 간의 프로토콜을 정립하는 활동
* 정보통신 표준 : 정보통신 시스템간의 미리 합의된 규약의 집합
* 정보통신 분야에 있어서 공통성, 통일성, 호환성, 등을 확보하기 위한 일반적 요구 사항

### 표준화 기구
* `ISO`(International Organization for Standards)
* `ITU-T`(International Telecommunication Union-Telecommunication)
* `ANSI`(American National Standards Institute)
* `EIA`(Electronic Industries Association)
* `TIA`(Telecommunications Industries Association)
* `IEEE`(Institute of Electrical and Electronics Engineers)
* `ETSI`(European Telecommunications Standards Institute)
* `IETF`(Internet Engineering Task Force) : 인터넷 표준규격 제정(`HTTP`, `FTP`), `IETF`에서 만든 표준은 `RFC`(Request For Comments)로 시작
***************************************

# 데이터 통신
## 전송 모드
### 병렬 전송(Parallel Transfer)
* 여러 전송라인을 통해 여러 비트들을 동시에 전송
* 두 장치들간의 거리가 짧은 경우에 일반적으로 사용
    * 예) PC에서 프린터로 전송하는 것
    * 예) 컴퓨터와 주변 장치들간의 연결
* 긴 거리를 병렬 전송으로 전송하면 비용이 많이 들어서 효율적이지 않다.

### 직렬 전송(Serial Transfer)
* 하나의 전송라인을 사용하여 하나씩 모든 비트를 보낸다.
* 긴 거리를 전송할 때 병렬 전송에 비해 적은 비용이 들고 신뢰성 증가
* 하지만 비트를 하나씩 보내는 만큼 병렬 전송에 비해 느리다.

### 비동기식 전송
* 한 번에 한 문자씩 보내거나 받는 방식
* 문자는 7~8 비트로 구성되며, 문자의 앞에 시작비트(Start bit)를, 끝에는 정지비트(Stop bit)를 첨가해서 보냄
* 송신측과 수신측 사이에 동기를 맞추기 위한 클럭 신호를 사용하지 않음
* 시작비트는 수신측에 문자에 해당하는 비트가 따라올 것이라는 것을 알려주는 역할
* 문자 비트들을 모두 수신하면 정지비트가 뒤따른다. 
* 키보드와 프린터 같이 느린 장치들을 위해 사용되며 높은 오버헤드를 가진다.

### 동기식 전송
* 정해진 수 만큼의 문자들을 하나의 그룹(프레임)으로 만들어서 일시에 전송하는 방법
* 일반적으로 비동기식 전송에 비해서 더 빠르다.
* 송신측과 수신측이 하나의 기준 클럭으로 동기신호를 맞추어 동작
* 동기화를 위한 클럭라인이 필요하다.
* 일반적으로 많이 사용하는 방식

#### 바이트기반 전송(Byte-Oriented Transmission)
* 각 프레임을 바이트(문자)의 연속으로 간주하는 방식
* STX(Start of Text), ETX(End of Text), DLE(Data-Link Escape)로 프레임의 시작과 끝을 구분
* 예) BISYNC, PPP, DDCMP 등

#### 비트기반 전송(Bit-Oriented Transmission)
* 일반적으로 많이 사용하는 방식
* 각 프레임을 비트의 연속으로 간주하는 방식
* 프레임의 시작과 끝을 알리기 위해 플래그(Flag)라고 하는 특수한 비트 패턴, "01111110"을 사용
* 예) 인터넷에서의 이더넷(Ethernet)과 HDLC(High-level Data Link Control) 등<br><br>

### 비트 스터핑(Bit Stuffing)
* 비트기반 전송에서 프레임의 시작과 끝이 아닌 데이터 필드에 프레임의 시작과 끝을 알리는 플래그가 포함될 수 있다. 그러면 전송이 아직 끝나지 않았는데 수신측에서는 전송이 끝난 것으로 간주하고 데이터 받기를 중단할 것이다.
* 그래서 이걸 해결하기 위해 사용하는 기법이 비트 스터핑 기법이다.

#### 비트 스터핑 방법
* 송신측 : 보낼 프레임의 데이터 필드에서 연속된 5개의 1을 발견하면 다섯 번째 1 뒤에 0을 추가함. 이렇게 하면 시작과 끝 부분 외에는 1이 연속해서 6개 위치하는 경우가 없어진다.
* 수신측 : 연속되는 5개의 1이 수신되고 나서 0이 수신되면 이 0은 비트 스터핑 된 것이라 간주하고 제거함<br><br><br>

### 단방향, 반이중, 전이중
#### 단방향(Simplex)
* 한 방향으로만 신호 전송이 가능한 형태
* 예) 공항 모니터, 프린터, TV 방송

#### 반이중(Half duplex)
* 양쪽 방향에서 보내고 받을 수 있지만 교대로 전송만 가능
* 예) 무전기

#### 전이중(Full duplex)
* 양쪽 호스트가 동시에 데이터전송 가능
* 예) 인터넷<br><br><br>

## 교환 기술
* N개의 통신 장비를 각각 직접 연결하면 필요한 연결선의 갯수가 너무 많아진다.
* 이것에 대한 해결방안으로 각각의 장비들은 통신망에 연결한 뒤 통신망을 이용해 서로 데이터를 주고 받는데 이걸 좀 더 효과적으로 운영하기 위해 교환 기술(Switching Technology)을 사용한다.

### 회선 교환(Circuit Switching)
* 공중 전화 망에서 사용
* 데이터 전송 과정 : 회선 설정 - 데이터 전송 - 회선 해제
* 단점 : 회선을 설정하고 해제할 때까지 채널의 대역폭을 독점하기 때문에 다른 회선을 동시에 사용할 수 없다.
* 장점 : 단점의 이유로 신뢰성 있는 데이터 전송이 가능하며 일정한 데이터 전송률로 데이터를 전송한다.
* 회선 설정(call setup) 시간이 필요하며 링크 및 스위칭 장비가 성능에 영향을 미친다.<br><br><br>

## 오류 검출과 교정기법
### 해밍코드(오류 교정 코드)
* N 비트의 데이터에 k개의 패리티 비트를 더하여 (n+k)비트의 코드워드(Codeword)를 생성
* 일종의 비트마스킹 기법으로 오류를 검출할 수 있다.
* N개의 비트를 사용해서 오류가 생긴 비트를 검출할 것이기 때문에 N 비트 데이터와 k개의 패리티 비트를 사용한다고 할 때 `2^k >= n + k + 1` 라는 수식이 성립해야 한다.(1을 더해주는 이유는 오류가 생기지 않는 경우도 표현하기 위해서)
* 수신측은 `XOR` 연산을 통해 syndrome을 계산해서 syndrome을 10진수로 바꾼 값이 오류발생 위치(syndrome의 모든 비트가 0이면 오류가 없음)
********************************************

# OSI 참조모델
* 예전엔 제조사별로 각자 통신 모델을 만들어 썼기 때문에 서로 호환이 되지 않아 통신이 되지 않는 경우가 많았다.
* 그래서 1970년대 후반에 국제 표준화 기구 ISO(Open System Interconnection)가 네트워크 설계의 호환성을 증진시키기 위해 개방시스템 상호접속 참조모델(OSI) 구조를 제안함
* `OSI`란 말은 타사의 시스템 간이라도 데이터를 교환하기 위한 표준을 가질 수 있다는 것을 의미함
* `OSI`는 `7계층`으로 이루어져 있다.

## 계층 구조의 장점
* 크고 복잡한 시스템을 기능별로 나누어 개발 과정을 단순화 하는데 매우 유용하게 사용(모듈화)
* 각 계층이 제공하는 서비스를 변경하기 쉬움(한 계층을 변경해도 나머지 계층에 영향을 주지 않아 유지 보수가 쉽다)

## OSI 참조모델의 계층
* N 계층의 프로토콜 모듈은 상대방의 동일 계층 프로토콜 모듈과 통신을 하며 동일 계층에 있는 N 계층 끼리의 통신 규약을 N 계층 프로토콜이라 함
* N 계층 프로토콜이 상대방의 동일 계층에 데이터를 직접 전달하는 것이 아니라 하위 계층(N - 1)으로 전달해서 맨 아래 계층인 물리 계층까지 도달하면 케이블을 통해 상대 호스트의 물리 계층으로 데이터를 전달한다.
* 상대 호스트는 물리 계층에서 받은 데이터를 하나씩 확인하며 상위 계층(N + 1)으로 올려 보낸다.
* 결과적으로, OSI 7계층 모델에서 상위 계층은 하위 계층의 서비스 사용자(Service User)가 되며, 하위 계층은 상위 계층의 서비스 제공자(Service Provider)가 된다.

## 서비스 프리미티브(Service Primitive)
* 동일 호스트상의 서비스 사용자(N + 1계층)와 서비스 제공자(N계층)간에 주고 받는 데이터
* N 계층의 서비스는 N 서비스 프리미티브와 이 프리미티브에 관련된 파라미터로 규정
* N 서비스 프리미티브는 요청(Request), 통지(Indicator), 응답(Response), 확인(Confirm)으로 구분
* 송신측에서 수신측으로 `Request`를 보내면 수신측의 하위 계층에서 `Indicator`를 발생시킨 뒤 송신측으로 `Response`를 보낸다. 송신측은 받은 데이터를 확인(`Confirm`)하며 하위계층에서 상위계층으로 올려보낸다.
* 송신측에서 데이터를 전송할 때 서비스 프리미티브를 사용하여 N + 1 계층의 송신 데이터(PDU : Protocol Data Unit)는 N 계층의 서비스 데이터 단위(SDU : Service Data Unit)로 N 계층에 넘겨진다.
* N 계층에서는 `PDU`에 프로토콜 제어 정보(PCI : Protocol Control Information)를 헤더로 붙여 N 계층 `PDU`로 만든 뒤 하위 계층으로 내려보내고 하위 계층에서도 이걸 반복한다.
* 이러한 계층간 데이터의 전달 과정을 캡슐화(Encapsulation)라고 한다.

## OSI 참조모델의 7계층
### 물리 계층(Physical Layer)
* 계층 1에 해당하며 전송매체에 대한 전기적, 기계적인 인터페이스를 다룸
* 전송하고자 하는 데이터를 전송매체에 적합한 전기적 신호로 바꾸는 기능
* 하드웨어로 구현되며 계층 2 이상은 대부분 소프트웨어로 구현된다.
* 물리 계층 관련 장치들
    * 리피터(Repeater), 허브(Hub), 케이블, 이더넷(Ethernet) 등과 같은 하드웨어 장치
    * LAN에서 사용하는 UTP(Unshieled Twisted Pair), STP(Shieled Twisted Pair)와 같은 케이블
    * LAN의 UTP 케이블에 연결하는 RJ-45 커넥터(흔히 사용하는 인터넷 랜선 커넥터)

### 데이터링크 계층(Datalink Layer)
* 물리 계층을 통해 전송되는 데이터의 오류 문제를 해결하여 신뢰성 있는 데이터 전송 기능을 제공하는데 `호스트 - 라우터 간 오류 문제만` 제어한다.
* 이를 통해 상위 계층인 네트워크 계층에게 오류 문제에 대한 부담을 줄임
* 데이터링크 계층에서 전송하는 데이터 단위를 `프레임(Frame)`이라 한다.
* 데이터링크 계층의 주요 기능
    * 순서 제어 : 데이터의 순차적 전송을 위해 프레임 번호 부여
    * 오류 제어 : 오류 검출과 교정 (가장 중요한 기능)
    * 흐름 제어 : 연속적인 프레임을 전송할 때 수신측이 수신이 가능한지 여부를 제어. 호스트 간 `CPU` 성능이 다를 때 느린 쪽이 빠른 쪽의 속도에 어느정도 맞춰 받을 수 있는지 서로 확인한 후 전송하는 등의 제어를 한다.
    * 프레임 동기화 : 데이터 전송시 프레임 단위로 전송
    
### 네트워크 계층(Network Layer)
* 네트워크 상에 존재하는 라우터와 같은 노드(Node)를 거칠 때마다 목적지로의 경로를 찾아주는 라우팅(Routing) 역할을 하는 계층
* 네트워크 계층의 데이터 전송 단위를 패킷(Packet)이라 부르며 패킷 내에는 송신 호스트의 주소와 목적지 호스트의 주소를 포함
* 라우터에 패킷이 도착하면 패킷의 목적지 주소에 따라 적합한 라우터로 중개하며 이러한 과정을 통해 목적지에 도착
* 라우터가 패킷을 중개할 때 자신이 관리하고 있는 라우팅 테이블(Routing Table)을 사용해서 패킷을 어디로 보낼지 결정한다.
* 네트워크 계층의 예
    * 인터넷의 `IP`(IP 주소가 이 계층에서 사용하는 주소)
    * `OSI`의 X.25

### 트랜스포트 계층(Transport Layer)
* 라우터와 같은 노드와는 상관없이 단대단(End-to-end) 신뢰성 있는 데이터 전송 기능을 제공
* 이를 위해 단대단 오류 복구, 흐름 제어 기능 등을 포함하는데 트랜스포트 계층에서의 제어 기능들은 `A 호스트에서 B 호스트까지 가는 모든 경로의 오류 및 흐름`을 제어한다.
* 트랜스포트 계층은 호스트 내에서 동작하는 `프로세스(Process)에서 프로세스`로 데이터를 전송한다.
    * 네트워크 계층은 `호스트에서 호스트`로의 데이터 전송에 관계함
    * 네트워크 계층에서 보내는 IP 주소 만으로는 상대 호스트의 어떤 프로세스에서 이 데이터를 보냈는지 알 수 없다. 그래서 각 프로세스별로 포트(Port) 번호를 사용해서 어떤 프로세스에서 보낸 데이터인지 구분한다.
    * 그래서 단대단 전송이라는 용어는 프로세스와 프로세스 간의 전송을 의미한다.
* 트랜스포트 계층의 데이터 전송 단위(PDU : Protocol Data Unit)에는 송신측 포트 번호와 수신측 포트 번호를 포함한다.
* 포트 번호는 특정 프로세스를 나타내기 위해 트랜스포트 계층에서 사용하는 주소라 할 수 있다.
* 인터넷 통신구조에서 `TCP`와 `UDP`가 트랜스포트 계층에 해당한다.

### 세션 계층(Session Layer)
* 양끝단에 있는 응용 프로세스간의 통신을 제어하는 기능 제공
* 응용 프로세스간 대화를 위해 세션을 설정하여 사용하는 기능 제공
* 제공 기능
    * 대화(Dialogue) 형태 : 단방향, 반이중, 전이중
    * 복구(Recovery) 기능 : 체크포인트(Checkpoint) 기능을 제공하여 체크포인트 사이에 오류가 있을 때 마지막 체크포인트 이후의 모든 데이터를 세션 계층이 재전송하는 기능

### 표현 계층(Presentation Layer)
* 호스트간에 교환되는 데이터의 표현방법(Syntax)과 의미(Semantic)를 다루는 계층
* 즉 양쪽 호스트의 데이터 표현 방식이 다를 때 송신 호스트는 양쪽 호스트가 이해할 수 있는 표준화 된 형식으로 인코딩(Encoding)하고, 수신 호스트는 표준화 된 형식을 수신측에 적합한 형식으로 디코딩(Decoding)하는 기능
* 이외에도 데이터의 안전하고 효율적인 전송을 위해 암호화(Encryption)하거나 압축(Compression)하는 기능 제공

### 응용 계층(Application Layer)
* `OSI 7계층` 중에서 최상위 계층에 있으며 사용자에게 필요한 응용 서비스를 제공하는 계층
* 응용 계층에 해당하는 프로토콜
    * FTAM(File Transfer Access and Management) : 파일 전송 프로토콜이며 인터넷의 FTP와 유사한 서비스
    * VT(Virtual Terminal) : 가상 단말 서비스 프로토콜이며 인터넷의 Telnet과 유사<br><br>
    
## SDU와 PDU의 차이
* SDU(Service Data Unit) : 상하위 계층간 데이터 전송을 위해 사용하는 데이터 단위
* PDU(Protocol Data Unit) : 상대방과의 통신을 위해 사용되는 데이터 단위
*****************************************

# 인터넷 프로토콜
## 구조
* 컴퓨터 상호간의 데이터 전달을 위한 통신구조로 현재 인터넷에서 사용하는 통신구조
* `TCP/IP(Transmission Control Protocol/Internet Protocol`라는 프로토콜을 사용하는데 이것은 인터넷과 연결된 컴퓨터들을 공용어라 할 수 있다.
* `OSI 참조모델`과 다르게 5계층으로 구성되어 있다.

### 1. 하드웨어 계층
* `OSI 참조모델`과 마찬가지로 물리적으로 연결하는 케이블 등 데이터 통신에 관련된 하드웨어로 구성되어 있다.

### 2. 네트워크 인터페이스 계층
* 네트워크 액세스 또는 데이터링크 계층이라고도 한다.
* 프레임(Frame)을 네트워크 전송매체로 전달하는 것과 네트워크 전송매체에서 프레임을 받아들이는 과정 담당
* `TCP/IP`는 네트워크 접근 방법, 프레임 포맷, 매체에 대해 독립적으로 동작하도록 설계
* `TCP/IP`는 서로 다른 네트워크 형태를 연결하는데 사용 가능
    * 네트워크 형태로는 이더넷(Ethernet), 토큰버스(Token Bus), 토큰링(Token Ring)과 같은 LAN 기술
    * X.25, 프레임 릴레이(Frame Relay)와 같은 WAN 기술을 포함
* 네트워크 인터페이스 계층은 `OSI 모델`에서 데이터 링크 계층에 해당

### 3. 인터넷 계층
* `OSI 모델`의 네트워크 계층에 해당하며 어드레싱(addressing - IP 주소를 만드는 것), 패키징(packaging - 데이터 전송 단위를 만드는 것), 라우팅(routing - 목적지까지 전송할 수 있도록 라우터에서 중개) 기능을 제공
* 핵심 프로토콜은 IP, ARP, ICMP, IGMP 등을 포함
    * `IP(Internet Protocol)` : IP 주소, 패킷의 라우팅을 책임지는 프로토콜
    * `ARP(Address Resolution Protocol)` : 인터넷 계층의 IP 주소를 네트워크 인터페이스 계층의 주소(MAC 주소 또는 물리적 하드웨어 주소)로 변환
    * `ICMP(Internet Control Message Protocol)` : IP 패킷의 전달에 따른 오류나 상태를 리포트하고 진단하는 기능
    * `IGMP(Internet Group Management Protocol)` : IP 멀티캐스트(multicast) 그룹의 관리

### 4. 트랜스포트 계층
* 두 호스트 간에 단대단(End-to-End) 통신을 제공
* 핵심 프로토콜은 `TCP`와 `UDP(User Datagram Protocol)`
* `TCP`
    * 1 대 1 연결 지향(전송 전 송-수신자간 논리적 연결을 먼저 함)
    * 신뢰성 있는 통신 서비스 제공
    * `TCP` 연결 설정과 보낸 패킷의 확인, 순서화, 전달 중 손상된 패킷을 복구하는 기능 제공
* `UDP`
    * 1 대 1, 1 대 다의 비연결 지향
    * 신뢰할 수 없는 통신 서비스 제공
    * 주로 전달해야 할 데이터의 크기가 작을 때나, `TCP` 연결 확립에 의한 부하를 피하려고 할 때 혹은 상위 프로토콜이 신뢰할 수 있는 전달을 책임지는 경우에 사용
    * 예) `DNS`: 전달해야 할 데이터가 상대적으로 적어서 빠른 응답을 위해 `UDP` 사용

### 5. 응용 계층
* 사용자와 가장 밀접한 관계를 가지고 있는 계층
* 여러 가지 응용 계층 프로토콜이 존재하며 지속적으로 새로운 프로토콜 개발
* 가장 많이 알려진 응용 계층 프로토콜로는
    * `HTTP(HyperText transfer Protocol)` : WWW의 `Web 페이지` 파일을 전송하는데 사용
    * `FTP(File transfer Protocol)` : 상호 `파일 전송`을 위해 사용
    * `SMTP(Simple Mail transfer Protocol)` : `메일 메시지`와 그에 추가된 첨부 파일을 전송하기 위해 사용
* `TCP/IP` 네트워크를 관리하거나 지원하는 응용 계층 프로토콜
    * `DNS(Domain Name System)` : 호스트 이름(예 : www.naver.com)을 숫자로 된 IP 주소로 변환하기 위해 사용
    * `RIP(Routing Information Protocol)` : IP 네트워크상에서 라우팅 정보를 교환하기 위해 라우터가 사용하는 프로토콜. 이를 이용해 최상의 라우팅 테이블을 유지하고 이 라우팅 테이블을 통해 가장 적합한 곳으로 패킷을 전송한다.
    * `SNMP(Simple Network Management Protocol)` : 네트워크 관리 콘솔과 네트워크 장비(라우터, 브리지, 지능형 허브)간에 네트워크 관리 정보를 수집, 교환하기 위해 사용. 네트워크 장비를 원격으로 관리할 수 있다.

## 인터넷 프로토콜 구현 환경
* 시스템 공간(계층 1 ~ 4) : `운영 체제`에서 동작(자동으로 설치됨)
* 사용자 공간(계층 5) : `사용자 프로그램`으로 동작

## 프로토콜 캡슐화(Encapsulation)
* 인터넷 프로토콜도 `OSI 참조모델`의 캡슐화 개념을 동일하게 사용한다.
* 그래서 하위 계층으로 내려보내서 물리 계층에 도착하면 상대편에게 보내고 상대편은 물리 계층부터 상위 계층으로 올라가서 사용자에게 최종적으로 메시지를 보여주는 형태와 똑같이 동작한다. 

### 🔸 수신측
* 응용 계층의 메시지(Message)는 트랜스포트 계층으로 전달되고, 트랜스포트 계층은 전달 받은 데이터 앞에 자신의 헤더를 추가한 후 세그먼트(Segment)를 만들어 네트워크 계층으로 전달
* 네트워크 계층은 전달 받은 데이터 앞에 자신의 헤더를 추가한 후 데이터그램(Datagram = Packet)을 만들어 링크 계층으로 전달
* 링크 계층은 전달 받은 데이터에 자신의 헤더를 추가하여 프레임(Frame)을 만든다.
* 마지막으로 프레임은 물리 계층에 해당하는 전송매체를 통해 상대방에게 전송

### 🔸 송신측
* 물리 계층에서 데이터를 수신하여 상위 계층으로 전달하는 과정 반복
* 각 계층은 자신의 데이터 단위가 도착하게 되면 프로토콜 동작 수행<br><br>

* 그래서 인터넷 프로토콜 또한 상위 계층은 하위 계층의 `서비스 사용자(Service user)`이고, 하위 계층은 `서비스 제공자(Service provider)`이다.
**********************************

# Application
* 응용프로그램이라고도 하며 사용자가 직접 다루는 프로그램을 의미한다.
* 그래서 네트워크 응용프로그램이라면 인터넷 상에서 통신을 할 때 사용자가 직접 다루게 되는 프로그램을 의미하게 된다.
* 종류에는 이메일, 크롬과 같은 웹 브라우저, P2P 파일 공유 프로그램, SNS, 카카오톡과 같은 메신저, 온라인 게임, 유튜브와 같은 비디오 스트리밍 서비스 등이 있다.<br><br>

## Application structures
### Client-sever model
* 최초로 사용되었던 방식으로 중앙에 서버 하나가 있고 클라이언트들이 그 하나의 서버에 접속해서 데이터를 받는 형태이다.
* 이 모델에서는 서버가 유일하게 데이터를 제공하는 장치이다. 
* 그래서 서버가 꺼져 있으면 데이터를 받을 수 없다. 그렇기 때문에 서버 컴퓨터는 항상 켜져 있어야 한다.
* 클라이언트는 서버에 접속해야만 데이터를 받을 수 있기 때문에 서버의 `IP 주소`는 항상 같아야 한다.
* 서버 하나에 너무 많은 클라이언트가 몰리면 서버의 성능이 떨어지기 때문에 부하를 분산하기 위해서 서버를 여러 개 둔다.
* 클라이언트가 다른 클라이언트와 통신하고 싶다면 서버를 거쳐야만 한다. 직접 통신 불가능

### Perr-to-peer (P2P) model
* 서버를 거치지 않고 각 컴퓨터들이 직접 연결되어 있는 형태로 네트워크에 참여하는 모든 컴퓨터들이 데이터 제공자이자 소비자가 된다. 특정한 하나의 서버가 없다.
* 그래서 모든 컴퓨터가 항상 켜져 있을 필요는 없다. 데이터를 주고받고자 할 때에만 켜도 된다.
* 부하가 분산되기 때문에 클라이언트가 많아져도 안정적이고 지속적인 서비스가 가능하다.
* 꼭 고정된 `IP 주소`를 가지지 않아도 된다.<br><br>

## Application Layer Protocol
* 인터넷 프로토콜은 5개의 층(layer)으로 이루어져 있는데 이 층 간에 통신을 할 때 필요한 규약이다.
* 우리가 서로 대화할 때 서로 이해 가능한 문법과 의미를 지켜서 얘기하는 것처럼 네트워크 응용프로그램도 서로 해석할 수 있는 프로토콜을 이용해 데이터를 주고받는다.

* `message syntax` : 요구하는 데이터가 무엇이고 이 데이터들을 어떻게 늘어놓을 것인지 
* `message semantics` : 이 데이터들을 어떻게 해석할 것인지
* `message pragmatics` : 어떤 순서로 어떻게 응답할 것인지

* 응용프로그램 프로토콜에는 `Open protocol`과 `Proprietary protocol`이 있는데 `Open protocol`은 전체 규칙이 표준화되어 공개되어 있어(`HTTP`, `SMTP`) 누구나 접근해 그 규격에 맞는 메시지를 만들어 통신할 수 있다.
* 반면에 `Proprietary protocol`은 기업에서 자체적으로 만들어 사용하는 고유한 프로토콜로 만든 곳에서 공개하지 않으면 알 수 없다.<br><br>

## Transport Layer Protocol
* 데이터를 전송할 때엔 데이터가 손실되지 않는지, 전송속도는 얼마나 나오는지 등 데이터가 제대로 전송될 수 있도록 신경써야 하는 부분이 있다. 그런데 이런 것들을 응용프로그래머가 일일이 다루기는 어렵다.
* 그래서 `Transport Layer`에서 이런 것들에 대한 요구사항을 만족시켜 준다.

### TCP
* 신뢰성 있는 전송
* `Error control` : 에러가 없을 때까지 재전송
* `Flow control` : 보내는 쪽은 받는 쪽이 받을 수 있을 만큼만 보낸다.
* `Congestion control` : 라우터나 스위치에 데이터가 쌓이지 않도록 제어
* 이메일, 웹, 파일 전송 등에서 사용

### UDP
* 신뢰성 없는 전송
* `TCP`가 제공하는 기능들을 제공하지 않는다. 
* 이렇게 보면 쓸모 없어보이지만 오디오/비디오와 같은 멀티미디어 데이터를 전송할 때 유용하게 사용될 수 있다.
* 받은 데이터에 손실이 있어도 수정하지 않고 그대로 보내기 때문에 유튜브처럼 데이터에 손실이 좀 생겨도 보는데에 지장이 없는 서비스에서는 빠르게 전송할 수 있다.
* 비디오 스트리밍 서비스나 통화 서비스 등에서 사용
********************************************

# REST?
* 서버가 클라이언트의 상태 정보를 가지고 있지 않는 것
* `HTTP`를 통한 서버 클라이언트 모델에서 서버가 클라이언트의 위치와 같은 현재 상태를 유지하는 정보를 가지고 있으면 오버헤드가 크다.
* 그래서 클라이언트의 상태 정보를 서버에 저장하지 않고 서버와 클라이언트 간에 주고받는 `HTTP` 메세지 안에 클라이언트의 상태 정보를 담고 그것을 해석할 수 있는 방법까지 담는다.
* 서버는 특정 클라이언트에 대한 정보를 저장하고 있지 않아도 `HTTP request` 메세지만 보고 클라이언트의 상태를 알 수 있고 클라이언트는 `HTTP response` 메세지를 받으면 어떤 방식으로 메세지를 가져와야 할 지 알 수 있다.
* 이런 아키텍처를 따르는 서비스를 `RESTful`이라 한다.<br><br>

## REST 요구사항
* `클라이언트-서버` 구조로 이루어져야 한다.
* `HTTP` 메세지 안에 모든 정보가 들어있어야 한다. (다른 데이터 스토리지 사용 X)
* 서버의 response가 클라이언트 쪽 또는 어떤 웹 캐시에 저장할 수 있어야 한다.
* 클라이언트가 웹 서버에 바로 연결되었든 다른 중간 지점을 거쳐서 연결이 되었든 클라이언트 입장에서는 서비스를 받는 데에 차이가 없어야 한다.
* 자바스크립트와 같이 어떤 코드가 클라이언트 기기에 다운로드 되었을 때 클라이언트 기기에 그 코드를 해석할 수 있는 방법이 없어도 그것을 실행할 수 있게 해 주는 응용프로그램을 전달해야 한다.
* 특정한 컴퓨터 아키텍처에 상관없이 어디서든 실행할 수 있어야 한다.
**********************************************

# TCP와 UDP
## Transport Layer
* 응용 계층 바로 아래에 있는 계층
* 대표적인 서비스는 프로세스들 간의 논리적 연결
* 하나의 컴퓨터 안에서는 여러 프로세스가 동시에 기동되고 있다.
* 전송 계층 바로 아래에 있는 네트워크 계층에서는 `IP`를 이용해 상대 호스트를 찾아가는데 이것 만으로는 상대방의 어떤 프로세스에게 전달해야 하는지 알 수 없다.
* 그래서 전송 계층에서 여러 프로세스들 중에서 어떤 프로세스에게 전달해야 할 지 알려주는 정보를 제공하는 것이다.
* 전송 계층의 보내는 쪽에서는 보내고자 하는 메세지(파일 등)를 분할한 다음에 세그먼트에 담아서 전송한다.
* 그러면 받는 쪽에서 분할되어 온 세그먼트들을 합친 후에 응용 계층으로 전달한다.
* 이때 사용하는 프로토콜은 `TCP`와 `UDP` 두 가지가 대표적으로 사용된다.<br><br>

## TCP
* 신뢰성 있는 전송
* 보낸 순서대로 전송이 되는데 사실 데이터가 도착하는 순서는 제각각이다. 그걸 순서대로 도착한 것처럼 보이게 만들어서 응용 계층으로 보내는 것이 `TCP`가 하는 일이다.
* 데이터를 주고받기 전에 먼저 `connection`을 설정한 뒤 둘 사이에 흐르는 데이터들의 에러나 속도를 제어해서 전체적으로 안정적인 서비스를 제공한다.<br><br>

## UDP
* 신뢰성 없는 전송
* `TCP`에서 제공하는 `connection`과 순서 보장 등을 제공하지 않고 전송 계층에서 제공해야 하는 가장 기본적인 서비스만 제공하고 나머지는 아래 계층에 넘기는 방식
* 그래서 `TCP`보다는 속도가 빠르다.
************************************************

# Transmission Control Protocol
* `TCP`에서 데이터 송수신 시 연결과 흐름 제어 동작을 수행하기 위해 사용되는 프로토콜
* `UDP`에 비해 긴 헤더로 구성되어 있으며 `Sequence number`와 `Acknowledgment number`를 이용해 데이터가 전송되었는지 확인하고 흐름을 제어한다.

## Sequence number
* 전송된 세그먼트의 순서로 전체 메세지에서 어느 부분에 해당하는지 구분하는 번호
* 1, 2, 3, ... 순서로 세그먼트가 전송된다고 하면 `Sequence number`를 통해 지금 받고 있는 부분이 어디쯤인지 알 수 있다.

## Acknowledgment number
* `receiver`가 다음에 받아야 하는 `Sequence number`
* `receiver`가 세그먼트를 받고 나서 다음에 몇 번 세그먼트를 받아야 하는지 `sender`에게 알려줄 때 사용하는 번호
* `sender`는 `receiver`로부터 온 `Acknowledgment number`를 보고 어떤 세그먼트를 보내야 하는지 알 수 있다.

* `TCP` 프로토콜에서 데이터의 송수신은 `sequence number`와 `ACK`의 확인으로 이루어지며 중간에 데이터가 누락되었다면 `ACK`를 통해 몇 번이 누락되었는지 확인하고 재전송 할 수 있다.

## flow control
* `receiver`가 수용할 수 있는 속도보다 훨씬 빠른 속도로 보내는 것을 막기 위해 사용된다.
* 데이터를 보낼 때 데이터를 받을 버퍼의 크기를 미리 제한한 뒤 그만큼씩 보내는 것이다.
*****************************************

# Congestion Control
* 트래픽의 양이 늘어나면 전송 가능한 양이 점점 줄어들어서 나중에는 하나도 보내지 못 하게 된다. 
* 그래서 지속 가능한 서비스를 할 수 있도록 네트워크 상에서 전송되는 데이터의 총량을 제한하는 것이다.
* `end-to-end`와 `network-assisted` 방식이 있는데 `end-to-end`의 대표적인 방식은 `TCP`가 있고 `network-assisted`에는 `ATM`이 있다.

## AIMD
* 혼잡이 생기면 `congestion window`의 크기를 갑자기 줄여서 혼잡을 해결한 후에 다시 크기를 서서히 증가시키는 것

## Congestion Window(cwnd)
* 네트워크가 `congestion`을 일으키지 않는 한도 내에서 `ACK`를 받지 않고 보낼 수 있는 데이터의 양
* `cwnd`의 크기는 네트워크 상황에 따라서 유동적으로 조절된다.<br><br>

# 한 번 더 비교해보는 TCP vs UDP
## TCP
* 데이터를 주고받을 당사자 간에 연결을 먼저 수립한 다음에 데이터의 송수신을 시작하고 데이터가 정확하게 도착하게 하기 위해서 흐름 제어 동작을 수행하기 때문에 `UDP`에 비해서는 느리다. 그만큼 데이터가 중간에 누락되지 않고 정확하게 도착하는 것을 보장할 수 있다.
* 데이터의 정확한 송수신을 요구하는 `Email`, `Web browsing`에서 주로 사용된다.

## UDP
* 연결과 흐름 제어를 위한 동작을 수행하지 않고 받은 대로 그냥 보내기 때문에 `TCP`에 비해서는 빠른 속도를 보여준다. 그만큼 데이터가 정확하게 도착한다는 보장이 없다.
* 중간에 데이터가 좀 누락되어도 괜찮고 속도가 빠른 것이 더 중시되는 실시간 스트리밍 서비스에서 주로 사용된다.
*****************************************

# 출처
* [데이터 통신과 컴퓨터 네트워크 - 동서대학교 KOCW 공개강의](http://www.kocw.net/home/cview.do?cid=5959f58996c6bd25)
* [컴퓨터 네트워킹 - 부산대학교 K-MOOC 공개강의](http://www.kmooc.kr/courses/course-v1:PNUk+CN_C01+2021_KM_013/video)
