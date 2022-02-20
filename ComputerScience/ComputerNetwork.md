# 컴퓨터구조<br>
## 목차<br>
* [컴퓨터 네트워크 기초](#컴퓨터-네트워크-기초)
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
* `IETF`(Internet Engineering Task Force) : 인터넷 표준규격 제정(`HTTP`, `FTP`), `IETF`에서 만든 표준은 `RFC`(Request For Comments)로 시작<br><br><br>

# 출처
* [KOCW 동서대학교 임효택 교수님 공개강의](http://www.kocw.net/home/search/kemView.do?kemId=1357811&ar=relateCourse)
