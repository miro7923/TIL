# 운영체제<br>
## 목차<br>
* [운영체제란?](#운영체제란)
* [컴퓨터 시스템 구조](#컴퓨터-시스템-구조)
* [프로세스](#프로세스)
* [스케줄러 (Scheduler)](#스케줄러-scheduler)
* [스레드 (Thread)](#스레드-thread)
* [Process Management](#process-management)
* [CPU Scheduling](#cpu-scheduling)
* [Process Synchronization](#process-synchronization)
* [Deadlocks](#deadlocks)
* [출처](#출처)

# 운영체제란?
* Operating System, OS
* 컴퓨터 하드웨어 바로 위에 설치되어 사용자 및 다른 모든 소프트웨어와 하드웨어를 연결하는 소프트웨어 계층<br><br>
![os](../img/os.png)<br><br>

* 좁은 의미의 운영체제(커널)
    * 운영체제의 핵심 부분으로 메모리에 상주하는 부분
    * 전공자 입장에서는 운영체제 하면 커널만을 이야기한다.
    
* 넓은 의미의 운영체제
    * 커널 뿐 아니라 메모리에 상주하지 않는 각종 주변 시스템 유틸리티를 포함한 개념<br><br>
    
## 🔸 운영체제의 목적<br>
1. 컴퓨터 시스템을 편라하게 사용할 수 있는 환경 제공
2. 컴퓨터 시스템의 **자원을 효율적으로 관리**
    * 하드웨어 자원인 프로세서, 기억장치, 입출력 장치들의 관리와
    * 소프트웨어 자원인 프로세스, 파일, 메시지 등 모든 것을 관리한다.
    * 사용자간의 형평성 있는 자원 분배가 가능해야 하고 **주어진 자원으로 최대한의 성능**을 낼 수 있어야 한다.
    * 실행 중인 프로그램들은 CPU를 번갈아가며 차지하며 동작을 하게 되는데 이 때 운영체제는 한 프로그램이 CPU를 너무 오랫동안 쓰지 않고 짧은 시간동안 번갈아 쓰도록 할당해 주어야 한다.
    * 또한 실행 중인 프로그램들에게 메모리 공간을 적절히 분배해 주어야 한다.<br><br>
    
## 🔸 운영체제의 분류
* 동시 작업 가능 여부
* 사용자의 수
* 처리 방식<br><br>
* 위 세 가지에 따라 분류할 수 있는데 현대 운영체제는 동시 작업이 가능하고 다중 사용자를 지원하며 시분할이 가능하다고 정리할 수 있다.

### ☑️ 동시 작업 가능 여부
#### 단일 작업(single tasking)
* 한 번에 하나의 작업만을 처리한다.
* 예) MS-DOS 프롬프트 상에서는 한 명령의 수행을 끝내기 전에 다른 명령을 수행시킬 수 없음
* 과거에 MS-DOS에서 주로 사용되던 방식으로 현대 컴퓨터에선 쓰이지 않지만 엘리베이터처럼 기능이 단순하거나 특수 목적을 수행하는 기계에는 지금도 사용되고 있다.
    
#### 다중 작업(multi tasking)
* 동시에 두 개 이상의 작업 처리
* 예) UNIX, MS Windows 등에서는 한 명령의 수행이 끝나기 전에 다른 명령이나 프로그램을 수행할 수 있음
* 스마트폰을 포함한 현대의 대부분의 하드웨어에서 사용되는 운영체제이다.<br><br>
    
### ☑️ 사용자의 수
#### 단일 사용자(single user)
* 예) MS-DOS, MS Windows
    
#### 다중 사용자(multi user)
* 예) UNIX, NT server
* 사용자가 많아지면 파일에 대한 접근 권한이나 사용자간 자원 분배를 형평성 있게 해 줄 수 있어야 한다.<br><br>
    
### ☑️ 처리 방식
#### 일괄 처리(batch processing)
* Interactive 하지 않은 방식
* 작업 요청을 일정량 모아서 한꺼번에 처리
* 작업이 완전 종료될 때까지 기다려야 함(하루 이상 걸림)
* 에) 초기 Punch Card 처리 시스템
    
#### 시분할(time sharing)
* Interactive한 방식
* 현대에 주로 사용하는 운영체제로 일반적인 범용 컴퓨터에서 사용
* 여러 작업을 수행할 때 컴퓨터 처리 능력을 일정한 시간 단위로 분할해서 사용
* 일괄 처리 시스템에 비해 짧은 응답 시간을 가짐(UNIX)
* 하지만 응답 시간이 항상 고정된 것은 아니며 사용자가 많아지면 느려질 수 있다. 
* 사람이 빠르다고 느끼면서 주어진 자원과 시간을 최대한 활용하는 것이 목적이다.
    
#### 실시간(Realtime OS)
* 정해진 시간 안에 어떠한 일이 반드시 종료됨이 보장되어야 하는 실시간시스템을 위한 OS
* 원자로/공장 제어, 미사일 제어, 반도체 장비, 로보트 제어 등 특수 목적을 가진 시스템에서 사용된다.

##### ▪️ 실시간 시스템의 개념 확장
* Hard realtime system(경성 실시간 시스템)
    * 데드라인을 지키지 않으면 큰일나는 시스템
    * 예) 반도체, 미사일 등
    
* Soft realtime system(연성 실시간 시스템)
    * 데드라인을 좀 못 지켜도 괜찮은 시스템
    * 예) OTT<br><br>
    
## 🔸 비슷한 의미로 사용되지만 약간 다른 용어들
* `Multitasking` : 하나의 프로그램이 끝나기 전에 다른 프로그램 작업이 가능한 것
* `Multiprogramming` : 여러 프로그램이 메모리에 올라가 있는 것을 강조
* `Time sharing` : `CPU`의 시간을 분할하여 나누어 쓴다는 것을 강조
* `Multiprocess` : 여러 프로그램이 동시에 실행된다.
* => 모두 컴퓨터에서 여러 작업을 동시에 수행한다는 것을 뜻하지만 어디에 더 초점을 맞추느냐에 따라 다르게 사용된다.

### ☑️ Multiprocessor
* 하나의 컴퓨터에 `CPU(processor)`가 여러 개 붙어 있음을 의미
* `CPU`가 하나임을 전제로 하는 위의 네 가지 용어들과는 하드웨어적으로 다르다.<br><br>

## 🔸 운영체제의 예
### ☑️ 유닉스(UNIX)
* 멀티태스킹 가능
* 다중 사용자용
* 대형 서버용
* 코드의 대부분을 C언어로 작성 - 기계어 사용에 어려움이 많아서 유닉스 개발용으로 C언어를 만들었다.
* 높은 이식성 - 다른 기계어 집합을 사용하는 컴퓨터에 이식이 쉽다.
* 최소한의 커널 구조
* 복잡한 시스템에 맞게 확장 용이
* 소스 코드 공개 - 학술적으로 사용하기 좋다.
* 프로그램 개발에 용이
* 다양한 버전
    * System V, FeeBSD, SunOS, Solaris - 유로. 소스 코드 비공개
    * Linux - 무료. 소스 코드 공개. 유닉스보다는 규모가 작은 환경이나 개인용 컴퓨터에 사용된다.
    
### ☑️ DOS(Disk Operating System)
* MS사에서 1981년 IBM-PC를 위해 개발
* 단일 사용자용 운영체제
* 싱글태스크
* 메모리 관리 능력의 한계(주 기억 장치 최대 용량 : 640KB)

### ☑️ MS Windows
* MS사의 다중 작업용 GUI 기반 운영체제
* Plug and Play, 네트워크 환경 강화
* DOS용 응용 프로그램과 호환성 제공
* 불안정성(초창기 윈도우즈)
* 풍부한 지원 소프트웨어

### ☑️ Handheld device를 위한 OS
* PalmOS, Pocket PC(WinCE), Tiny OS<br><br>

## 🔸 운영체제의 구조
* 크게 `CPU` - `memory` - `Disk` - `I/O device` 구조

### ☑️ CPU
* `CPU 스케줄링`을 통해 실행중인 프로그램들에게 `CPU`를 효율적으로 할당해야 함
* `CPU`에게는 선착순 처리가 효율적이지 않기 때문에 프로그램마다 걸리는 작업 시간에 따라 처리하도록 스케줄링한다.

### ☑️ memory
* 프로그램을 실행하려면 `memory`에 올려야 하는데 `memory`는 한정되어 있기 때문에 적당히 잘 쪼개어 써야 한다.
* 최근에 많이 사용된 데이터는 오래 보관하고 그렇지 않으면 쫓아내는 방식으로 관리

### ☑️ Disk
* `Disk`에는 헤드가 있고 그 헤드를 움직이면서 일정 위치에 파일을 기록하기 때문에 I/O 요청이 들어왔을 때 헤드를 최대한 적게 움직이면서 최대한 빠르게 많이 처리할 수 있도록 처리 순서를 스케줄링 해야 한다.

### ☑️ I/O device
* 지금까지 나온 장치들 중에선 가장 느리다.
* 때문에 `인터럽트` 기반으로 관리되며 `CPU`는 평소에는 자기 할 일을 하고 있다가 `I/O` 장치에서 `인터럽트` 요청이 들어오면 입출력을 수행하는 방식으로 진행된다.

### ☑️ 프로세스 관리
* 프로세스의 생성과 삭제
* 자원 할당 및 반환
* 프로세스 간 협력

### ☑️ 그 외
* 보호 시스템
* 네트워킹
* 명령어 해석기(command line interpreter)
*******************************

# 컴퓨터 시스템 구조<br>

![systemStructure](../img/systemStructure.png)<br><br>

* `CPU`는 매 시간마다 `Memory`에서 기계어 `Instruction`을 읽어서 실행하게 된다.
* 따라서 `Memory`는 `CPU`의 작업공간이라 할 수 있다.
* `Disk`가 `I/O` 장치인 이유는 데이터를 `Memory`에서 읽어들이기도 하고 처리된 데이터를 가져와서 저장하기도 하기 때문이다.<br><br>

* `device controller`는 각 `I/O device`를 전담하는 작은 `CPU` 역할을 한다.
* `I/O device`가 `CPU`에 비해 많이 느려서 `CPU`가 `I/O` 작업 처리가 끝나는 것을 마냥 기다릴 수는 없기 때문에 중간에 `controller`를 둬서 `I/O` 작업이 끝나면 `CPU`에게 알려준다.
* `local buffer`는 각 `I/O device controller`의 작업공간이다. 
* 입력받은 내용이나 출력할 내용을 여기에 저장해뒀다가 `device controller`가 사용자 프로그램으로 전달하거나 화면에 출력하는 등의 작업을 한다.<br><br>

## Mode bit
* 사용자 프로그램의 잘못된 수행으로 다른 프로그램 및 운영체제에 피해가 가지 않도록 하기 위한 보호 장치가 필요해서 사용한다.
* 현재 수행중인 `Instruction`이 운영체제인지 사용자 프로그램인지 구분하기 위한 것
* `0`과 `1`이라는 두 가지 `operation`을 사용해 `모니터 모드`와 `사용자 모드`를 구분한다.
    * `1` 사용자 모드 : 사용자 프로그램 수행
    * `0` 모니터 모드(= 커널 모드, 시스템 모드) : `OS` 코드 수행
    
* 보안을 해칠 수 있는 중요한 명령어는 모니터 모드에서만 수행 가능한 `특권명령`으로 규정한다.
* `Interrupt`나 `Exception` 발생시 `하드웨어`가 `mode bit`을 0으로 바꾼다.
* 사용자 프로그램에게 `CPU`를 넘기기 전에 `mode bit`을 1로 세팅<br><br>

## Timer
* `CPU`를 특정 프로그램이 독점하는 것으로부터 보호하기 위해서 사용한다.
    * 정해진 시간이 흐른 뒤 운영체제에게 제어권이 넘어가도록 `Interrupt`를 발생시킨다.
    * `Timer`는 매 클럭 틱 때마다 1씩 감소한다.
    * `Timer` 값이 0이 되면 `Timer Interrupt` 발생<br><br>
    
* `time sharing`을 구현하기 위해 널리 이용된다.
* 현재 시간을 계산하기 위해서도 사용된다.<br><br>

## Device Controller
* 해당 `I/O` 장치유형을 관리하는 일종의 작은 `CPU`
* 제어 정보를 위해 `control register`, `status register`를 가진다.
    * `CPU`는 `device controller`를 통해 일을 시키는데 이 때 `control register`와 `status register`를 사용한다.
* `local buffer`를 가진다.(일종의 `data register`)<br><br>

* `I/O`는 실제 `device`와 `local buffer` 사이에서 일어난다.
* `device controller`는 `I/O`가 끝났을 경우 `Interrupt`로 `CPU`에 그 사실을 알린다.<br><br>

### ☑️ device driver(장치구동기)
* `OS` 코드 중 각 장치별 처리루틴 ➡️ `software`
    * ex) 새 프린터를 사면 설치하는 프린터용 드라이버
    
### ☑️ device controller(장치제어기)
* 각 장치를 통제하는 일종의 작은 `CPU` ➡️ `hardware`<br><br>

## 입출력(I/O)의 수행
* 모든 입출력 명령은 `특권명령`이다.

### ☑️ 사용자 프로그램의 `I/O` 방법
* 시스템콜(`system call`)
    * 사용자 프로그램은 운영체제에게 `I/O` 요청
* `trap`을 사용하여 인터럽트 벡터의 특정 위치로 이동
* 제어권이 인터럽트 벡터가 가리키는 인터럽트 서비스 루틴으로 이동
* 올바른 `I/O` 요청인지 확인 후 `I/O` 수행
* `I/O` 완료 시 제어권을 `system call` 다음 명령으로 옮김<br><br>

## 인터럽트(Interrupt)
* 인터럽트 당한 시점의 레지스터와 `program counter`를 저장한 후 `CPU`의 제어를 인터럽트 처리 루틴에 넘긴다.

### ☑️ 넓은 의미의 인터럽트
* `Interrupt` (하드웨어 인터럽트) : 하드웨어가 발생시킨 인터럽트로 일반적인 의미의 인터럽트
* `Trap` (소프트웨어 인터럽트)
    * `Exception` : 프로그램이 오류를 범한 경우(프로그램 강제종료 등으로 대응)
    * `System call` : 프로그램이 커널 함수를 호출하는 경우
* 일반적으로 인터럽트 하면 하드웨어적인 인터럽트를 의미하고 소프트웨어적인 인터럽트는 `Trap`이라고 따로 지칭한다.

### ☑️ 인터럽트 관련 용어
* 인터럽트 벡터 
    * 해당 인터럽트의 처리 루틴 주소(처리 위치)를 가지고 있다.
* 인터럽트 처리 루틴(= `Interrupt Service Routine`, 인터럽트 핸들러)
    * 해당 인터럽트를 처리하는 커널 함수
    
### 🔸 현대의 운영체제는 인터럽트에 의해 구동된다.
* 만약 인터럽트가 없으면 `CPU`는 항상 사용자 프로그램이 쓰고 있게 될 것이다.<br><br>

## 시스템콜(System Call)
* 사용자 프로그램이 운영체제의 서비스를 받기 위해 `커널 함수`를 호출하는 것
* 사용자 프로그램이 `I/O` 등의 작업을 수행해야 할 때 `시스템콜`을 통해 운영체제에게 `CPU`를 넘겨줌으로서 필요한 서비스를 받을 수 있게 된다.<br><br>

## 동기식 입출력과 비동기식 입출력
### ☑️ 동기식 입출력 (Synchronous I/O)
* `I/O` 요청 후 입출력 작업이 완료된 후에야 제어가 사용자 프로그램에게 넘어간다.<br><br>

* 구현 방법 1 (잘 안 씀)
    * 하나의 `I/O`가 끝날 때까지 그거 하나만 한다.
    * `I/O`가 끝날 때까지 `CPU`를 낭비시킴
    * 매시점 하나의 `I/O`만 일어날 수 있음<br><br>
    
* 구현 방법 2 (보통 이렇게 구현함)
    * `I/O`가 완료될 때까지 해당 프로그램에게서 `CPU`를 빼앗음
    * `I/O` 처리를 기다리는 줄에 그 프로그램을 줄 세움
    * 다른 프로그램에게 `CPU`를 줌
    * 이 프로그램의 `I/O` 작업이 끝나면 다시 `CPU`를 준다.
    
### ☑️ 비동기식 입출력 (Asynchronous I/O)
* `I/O`가 시작된 후 입출력 작업이 끝나기를 기다리지 않고 제어가 사용자 프로그램에게 즉시 넘어간다.

### 🔸 두 경우 모두 `I/O`의 완료는 인터럽트로 알려준다.

## DMA(Direct Memory Access)
* 입출력 장치를 메모리에 가까운 속도로 처리하기 위해 사용한다.
* `CPU`의 중재 없이 `device controller`가 `device`의 `buffer storage`의 내용을 메모리에 `block` 단위로 직접 전송
* `byte` 단위가 아니라 `block` 단위로 인터럽트를 발생시킴<br><br>

## 서로 다른 입출력 명령어<br>

![ioInstruction](../img/ioInstruction.png)<br><br>

* 일반적인 `I/O` 방식은 메모리를 관리하는 주소와 디바이스를 관리하는 주소를 따로 관리한다.
* `Memory Mapped` 방식은 디바이스를 관리하는 주소도 메모리 영역에서 함께 관리한다.<br><br>

## 저장장치 계층 구조<br>

<img src="../img/storageHierarchy.png" width="450" height="500"><br><br>

* 위로 갈수록 `Speed` ⬆️  `Cost` ⬆️(단위공간당 용량이 적어진다)  `Volatility` ⭕️ (`휘발성` - 전원을 끄면 데이터가 사라진다)
    * `CPU`에서 직접 접근 가능(`byte` 단위 접근 가능)
* 아래로 갈수록 `Speed` ⬇️  `Cost` ⬇️(단위공간당 용량이 커진다)  `Volatility` ❌ (`비휘발성` - 전원을 꺼도 데이터가 사라지지 않는다)
    * `CPU` 직접 접근 불가(`byte` 단위 접근이 불가능하며 `섹터` 단위 접근 가능)
    
### ☑️ Caching
* 메인 메모리에 있는 내용 중 당장 필요한 것만 캐시 메모리에 올려 쓰는 것으로 재사용을 빠르게 하기 위한 목적<br><br>

## 프로그램의 실행(메모리 load)<br>

![memoryLoad](../img/memoryLoad.png)<br><br>

## 커널 주소 공간의 내용<br>

![kernalAddress](../img/kernalAddress.png)<br><br>

## 사용자 프로그램이 사용하는 함수
* 모든 프로그램은 함수 구조로 짜여 있다. (기계어 레벨에서도 함수의 시작과 끝이 표시됨)<br><br>

* 사용자 정의 함수
    * 자신의 프로그램에서 정의한 함수<br><br>
    
* 라이브러리 함수
    * 자신의 프로그램에서 정의하지 않고 만들어져 있는 것을 가져다 쓴 함수
    * 자신의 프로그램의 실행 파일에 포함되어 있다.

### ☑️ 이 두 가지는 자신의 프로그램의 코드 영역에 포함되어 있어서 가상 메모리 안에서 자유롭게 점프가 가능하다.<br><br>

* 커널 함수
    * 운영체제 프로그램의 함수
    * 커널 함수의 호출 = 시스템 콜

### ☑️ 커널 함수는 커널의 코드 영역에 포함되어 있기 때문에 사용자 프로그램에서 자유로운 점프를 할 수 없다. ➡️ `System call`을 통해 운영체제에게 `CPU` 제어권을 넘기게 된다.<br><br>

## 프로그램의 실행<br>

![programCycle](../img/programCycle.png)
*************************************

# 프로세스
* 프로세스란 실행 중인 프로그램을 말한다.

## 프로세스의 문맥(context)
* 현대 프로세스는 멀티태스킹 환경이기 때문에 이 작업 저 작업 왔다갔다 하면서 실행하려면 프로세스가 어디까지 실행했었는지를 알 수 있는 문맥 정보가 필요하다.<br><br>

* `CPU` 수행 상태를 나타내는 하드웨어 문맥
    * Program Counter
    * 각종 register<br><br>
    
* 프로세스의 주소 공간
    * code, data, stack<br><br>
    
* 프로세스 관련 커널 자료 구조
    * PCB (Process Control Block) : 프로세스가 실행될 때마다 하나씩 만들어서 프로세스에 `CPU`, `메모리`를 얼마나 줘야 할 지, 어디까지 실행했는지 이상 행동을 하지는 않는지 관리하기 위한 자료구조
    * Kernal stack : 프로세스마다 별도로 둔다.

## 프로세스의 상태 (Process State)
* `CPU`가 하나라고 가정했을 때 프로세스는 상태가 변경되며 수행된다.

### Running
* `CPU`를 잡고 `instruction`을 수행중인 상태
* `Time interrupt`, `System call`이 생기게 되면 `CPU`를 다시 내어주게 된다.

### Ready
* `CPU`를 기다리는 상태(메모리 등 `CPU`를 얻기 위한 다른 조건을 모두 만족하고)
* `CPU`를 얻기 위한 `Ready queue`에서 기다리고 있다.

### Blocked (wait, sleep)
* `CPU`를 주어도 당장 `instruction`을 수행할 수 없는 상태
* `Process` 자신이 요청한 event(ex. I/O)가 즉시 만족되지 않아 이를 기다리는 상태
    * 예) 디스크에서 파일을 읽어와야 하는 경우
    
### New
* 프로세스가 생성중인 상태

### Terminated
* 수행(execution)이 끝난 상태인데 작업이 완전히 끝난 것은 아니고 정리할 것이 남아있는 상태이다.<br><br>


## PCB (Process Control Block)
* 운영체제가 각 프로세스를 관리하기 위해 프로세스당 유지하는 정보
* 다음의 구성 요소를 가진다(구조체로 유지).
1) `OS`가 관리상 사용하는 정보
- Process state, Process ID
- scheduling information, priority<br><br>

2) `CPU` 수행 관련 하드웨어 값
- Program counter, registers<br><br>

3) 메모리 관련
- Code, data, stack의 위치 정보<br><br>

4) 파일 관련
- Open file descriptors...<br><br>


## 문맥 교환 (Context Switch)
* `CPU`를 한 프로세스에서 다른 프로세스로 넘겨주는 과정
* `CPU`가 다른 프로세스에게 넘어갈 때 운영체제는 다음을 수행한다.
    * `CPU`를 내어주는 프로세스의 상태를 그 프로세스의 `PCB`에 저장
    * `CPU`를 새롭게 얻는 프로세스의 상태를 `PCB`에서 읽어옴<br><br>
    
❗️ `System call`이나 `Interrupt` 발생시 반드시 `Context switch`가 일어나는 것은 아니다.<br>
`System call`이나 `Interrupt` 발생 후 다른 프로세스에게 `CPU`를 넘겨줬을 때 `Context switch`가 일어나는 것이지 같은 프로세스에게 다시 `CPU`를 줬을 때엔 `Context switch`가 일어난 것이 아니다.<br><br>

* `Context switch`가 일어나면 `cache memory`를 비워야 하는데 이거 자체가 상당한 오버헤드를 일으킨다.<br><br>

## 프로세스를 스케줄링하기 위한 큐
### Job queue
* 현재 시스템 내에 있는 모든 프로세스의 집합

### Ready queue
* 현재 메모리 내에 있으면서 `CPU`를 잡아서 실행되기를 기다리는 프로세스의 집합

### Device queues
* `I/O device`의 처리를 기다리는 프로세스의 집합<br><br>

🔸 프로세스들은 각 큐들을 오가며 수행된다.<br><br>

# 스케줄러 (Scheduler)
## Long-term scheduler (장기 스케줄러 or job scheduler)
* 시작 프로세스 중 어떤 것들을 `ready queue`로 보낼지 결정
* 프로세스에 `memory(및 각종 자원)`을 주는 문제 결정
* `degree of Multiprogramming`(메모리에 올라가 있는 프로세스의 수) 제어
* 하지만 `time sharing system`에는 보통 장기 스케줄러가 없다(무조건 `ready`)

## Short-term scheduler (단기 스케줄러 or CPU scheduler)
* 어떤 프로세스를 다음번에 `running` 시킬지 결정
* 프로세스에 `CPU`를 주는 문제 결정
* 충분히 빨라야 함 (millisecond 단위)

## Medium-term scheduler (중기 스케줄러 or Swapper)
* `time sharing system`에서는 중기 스케줄러를 사용한다.
* 여유 공간 마련을 위해 일부 프로세스를 통째로 메모리에서 디스크로 쫓아낸다.
* 프로세스에게서 `memory`를 뺏는 문제 결정
* `degree of Multiprogramming` 제어

## 중기 스케줄러를 사용하면서 바뀌는 프로세스의 상태
### Running
* `CPU`를 잡고 `instruction`을 수행중인 상태
* `Time interrupt`, `System call`이 생기게 되면 `CPU`를 다시 내어주게 된다.

### Ready
* `CPU`를 기다리는 상태(메모리 등 `CPU`를 얻기 위한 다른 조건을 모두 만족하고)
* `CPU`를 얻기 위한 `Ready queue`에서 기다리고 있다.

### Blocked (wait, sleep)
* `I/O`등의 `event`를 (스스로) 기다리는 상태
    * 예) 디스크에서 파일을 읽어와야 하는 경우
* 자신이 요청한 `event`가 만족되면 `Ready` 상태가 된다.

### Suspended (stopped)
* 외부적인 이유로 프로세스의 수행이 정지된 상태
* 프로세스는 통째로 디스크에 `swap out` 된다.
    * 예) 사용자가 프로그램을 일시 정지시킨 경우 (break key)
    * 시스템이 여러 이유로 프로그램을 잠시 중단시킴(메모리에 너무 많은 프로세스가 올라와 있을 때)
* 외부에서 `resume` 해 주어야 `Active` 상태가 된다.
**************************************************

# 스레드 (Thread)
* 프로세스 하나에 `CPU` 수행단위(`Program Counter`)만 여러개 두고 있는 것
* 스레드를 사용하는 이유는 메모리 절약과 수행속도를 높이기 위해서라고 볼 수 있다. 
* 만약 같은 프로세스를 여러개 실행시키고 싶을 때 프로세스를 여러개 만들면 그만큼 메모리 공간을 할당해야 하니까 메모리 낭비가 커진다. 그리고 그 프로세스들 간에 문맥 교환이 일어난다면 오버헤드도 클 것이다. 
* 하지만 프로세스의 주소공간(메모리)은 함께 쓰면서 각 프로그램마다 `PCB`에 코드를 어디까지 실행했는지만 저장해 놓고 코드 영역에서 각자 다른 부분의 코드만 실행하면 메모리를 아낄 수 있다(그 프로그램에 저장된 데이터와 코드가 바뀌는 것이 아니니까). 즉, 프로세스의 `Code`와 `Data` 영역만 함께 쓰는 것이다. 
* 하지만 각 스레드별로 함수를 어디까지 실행했는지 등의 정보는 각자 알고 있어야 하기 때문에 함수 실행과 관련된 정보를 저장하는 `Stack`영역은 따로 사용해야 한다. 
* 그래서 하나의 프로세스를 만들고 스레드를 생성하면 `code`와 `data` 영역은 공유하고 각 스레드의 `stack` 영역이 여러개 만들어진다.<br><br> 

## 스레드 사용의 장점
### 응답성 - 사용자 입장에서 빠르게 느껴진다
* 만약 웹페이지를 로드한다고 했을 때 이미지와 텍스트를 불러오는 작업은 상당히 시간이 걸리는 작업인데 스레드를 하나만 써서 웹페이지가 완전히 완성될 때까지 기다렸다가 사용자에게 보여주면 웹페이지를 표시하기 위한 작업이 끝날 때까지 사용자는 빈 화면만 보고 있을 것이다. 이것은 굉장히 답답하게 느껴진다.
* 이 때 멀티 스레드를 사용해 작업을 하면 한 스레드가 이미지를 불러오는 동안 다른 스레드는 일찍 로드된 텍스트를 사용자에게 먼저 보여주고 있는다든지 하는 일을 수행할 수 있게 된다. 그러면 답답함을 많이 줄일 수 있다.

### 자원 공유
* 위에서 서술했듯이 프로세스는 하나만 두고 `PC`랑 `register`만 따로 사용해서 프로세스를 실행하면 자원을 효율적으로 쓸 수 있다. 

### 경제성
* 실행 속도 측면에서도 프로세스를 추가하는 것 보다는 스레드를 추가하는 것이 훨씬 빠르다. 
* 문맥 교환이 일어났을 때에도 스레드 간에 하는 것이 오버헤드가 훨씬 적다.

### 병렬성
* `CPU`가 여러개인 환경에서 각각의 스레드가 병렬적으로 작업을 할 수 있어 동시에 처리할 수 있는 작업이 늘어난다.<br><br>

## 스레드의 구현 스타일
* 스레드를 구현하는 스타일이 다 같지 않다. 

### Kernel Threads
* 운영체제의 지원을 받아 관리되는 스레드
* 그래서 `OS`가 스레드의 존재를 알고 있다.
* 예) `Windows 95/98/NT`, `Solaris`, `Digital UNIX`, `Mach`

### User Threads
* 사용자 레벨에서 라이브러리의 지원을 받아 관리되는 스레드
* 그래서 `OS`는 스레드의 존재를 알 수 없다. `OS` 입장에서 보면 프로세스 하나가 실행되고 있는 것이다.
* 사용자 프로세스 스스로가 스레드를 관리한다. 
* 예) `POSIX Pthreads`, `Mach C-threads`, `Solaris threads`<br><br>

그리고 `real-time`으로 관리되는 스레드가 있는데 그냥 이런게 있구나 정도로 알고 있으면 된다고 한다.
*****************************************

# Process Management
## 프로세스 생성 (Process Creation)
* 부모 프로세스(Parent process)가 자식 프로세스(Child process) 생성. 복제 생성 하는 것으로 부모 프로세스의 문맥(코드, 데이터, 스택 등)을 모두 복사한다.
* 복제된 자식 프로세스가 부모 프로세스의 하위 노드로 위치하고 그 자식이 또 자식을 복제하면 또 하위 노드로 위치하고... 를 반복하면서 프로세스의 트리(계층 구조)를 형성한다.
* 프로세스 혼자서 자식을 생성할 수는 없고 시스템 콜을 통해 운영체제의 서비스를 받아야만 자식 생성이 가능하다.
* 프로세스는 자원을 필요로 하기 때문에 운영체제로부터 받거나 부모와 공유한다. 기본적으로는 자식이 복제되는 순간 별도의 프로세스가 되기 때문에 그 순간부터 부모와 자원을 얻기 위해 경쟁하는 관계가 된다.

### 자원의 공유
* 부모와 자식이 모든 자원을 공유하는 모델
* 일부를 공유하는 모델
* 전혀 공유하지 않는 모델 (일반적)

### 수행 (Execution)
* 부모와 자식은 공존하며 수행되는 모델
* 자식이 종료(terminate)될 때까지 부모가 기다리는(wait) 모델

### 주소 공간 (Address space)
* 자식은 부모의 공간을 복사함 (binary and OS data)
* 자식은 그 공간에 새로운 프로그램을 올린다.(덮어씌움)

#### 유닉스의 예
* `fork()` 시스템 콜이 새로운 프로세스를 생성
    * 부모를 그대로 복사 후 주소 공간 할당
* `fork` 다음에 이어지는 `exec()` 시스템 콜을 통해 새로운 프로그램을 메모리에 올림 (덮어씌우는 단계)
* `fork`와 `exec`은 독립적으로 이루어지기 때문에 둘 중 하나만 실행될 수 있다.<br><br><br>

## 프로세스 종료 (Process Termination)
* 운영체제는 부모 프로세스가 종료하는 경우 자식이 더 이상 수행되도록 두지 않는다.
* 그래서 단계적인 종료를 통해 모든 자식 프로세스가 먼저 종료된 후 부모가 종료되어야 한다.

### System call을 통해 자발적으로 종료되는 경우
* 프로세스가 마지막 명령을 수행한 후 이를 운영체제에게 알려준다.(`exit`)
* 자식이 부모에게 output data를 보냄 (via `wait`)
* 프로세스의 각종 자원들이 운영체제에게 반납됨

### 비자발적으로 종료되는 경우
* 부모 프로세스가 자식 프로세스의 수행을 강제로 종료시킨다.(`abort`)
* 자식이 할당 자원의 한계치를 넘어선 경우
* 자식에게 할당된 태스크가 더 이상 필요하지 않은 경우
* 부모가 종료(exit)하는 경우<br><br><br>

## fork() 시스템 콜

```c
int main()
{
    int pid; // 부모와 자식을 구분하기 위한 값
    pid = fork(); // 새로운 자식 프로세스가 생성되면 여기 다음 줄부터 실행한다.(부모의 문맥을 복사하기 때문)
    if (0 == pid)   // this is a child
        printf("\n Hello, I am a child!\n");
    else if (0 < pid)   // this is a parent
        printf("\n Hello, I am a parent!\n");
}
```

* 자식 프로세스를 생성하기 위한 시스템 콜로 부모와 자식을 구분하기 위해 부모의 `pid`는 0보다 큰 값을 가지고 자식의 `pid`는 0을 가진다.<br><br><br>

## exec() 시스템 콜

```c
int main()
{
    int pid;
    pid = fork();
    if (0 == pid)   // this is a child
    {
        printf("\n Hello, I am a child! Now I'll run date \n");
        execlp("/bin/date", "/bin/date", (char *)0);
    }
    else if (0 < pid)   // this is a parent
        printf("\n Hello, I am a parent!\n");
}
```

* 어떤 프로그램을 새로운 프로세스로 바꿔주기 때문에 `execlp()`가 호출되는 순간 이후의 코드들은 실행되지 않는다.<br><br><br>

## wait() 시스템 콜

```c
int main()
{
    int childPID;
    S1;
    
    childPID = fork();
    
    if (0 == childPID)
        // child 프로세스 코드 실행
    else 
        wait();
        
    S2;
}
```

* 프로세스 A가 `wait()` 시스템 콜을 호출하면 커널은 `child`가 종료될 때까지 프로세스 A를 `sleep`시킨다.(block 상태)
* 자식 프로세스가 종료되면 커널은 프로세스 A를 깨운다.(ready 상태)<br><br><br>

## exit() 시스템 콜
### 프로세스의 자발적 종료
* 마지막 statement 수행 후 `exit()` 시스템 콜을 통해 종료
* 프로그램에 명시적으로 적어주지 않아도 main 함수가 리턴되는 위치에 컴파일러가 넣어줌

### 프로세스의 비자발적 종료
* 부모 프로세스가 자식 프로세스를 강제 종료시킴
    * 자식 프로세스가 한계치를 넘어서는 자원 요청시
    * 자식에게 할당된 태스크가 더 이상 필요하지 않을 때
* 키보드로 `kill`, `break`등을 친 경우
* 부모가 종료하는 경우 부모 프로세스가 종료되기 전 자식 프로세스들이 먼저 종료된다.<br><br><br>

## 프로세스 간 협력
### 독립적 프로세스 (Independent process)
* 프로세스는 각자의 주소 공간을 가지고 수행되므로 원칙적으로 하나의 프로세스는 다른 프로세스의 수행에 영향을 미치지 못한다.

### 협력 프로세스 (Cooperating process)
* 프로세스 협력 메커니즘을 통해 하나의 프로세스가 다른 프로세스의 수행에 영향을 미칠 수 있다.

### 프로세스 간 협력 메커니즘 (`IPC`: Interprocess Communication)
#### 🔸 메시지를 전달하는 방법
* `message passing` : 커널을 통해 메시지 전달

##### 🔸 주소 공간을 공유하는 방법
* `shared memory` : 서로 다른 프로세스 간에도 일부 주소 공간을 공유하게 하는 shared memory 메커니즘이 있음
* 물리적 메모리에 매핑할 때 일부 주소공간을 공유하도록 매핑한다.(사전에 시스템 콜을 통해 운영체제에게 보고되어야 한다)

##### 🔸 thread
* `thread`는 사실상 하나의 프로세스이므로 프로세스 간 협력으로 보기는 어렵지만 동일한 프로세스를 구성하는 스레드들 간에는 주소 공간을 공유하기 때문에 협력이 가능하다. <br><br><br>

## Message Passing
* 사용자 프로그램끼리는 메시지를 주고받는 것이 불가능하기 때문에 운영체제 커널을 통해서 메시지를 주고받는다.

### Message system
* 프로세스 사이에 공유 변수(shared variable)를 일체 사용하지 않고 통신하는 시스템

### Direct Communication
* 통신하려는 프로세스의 이름을 명시적으로 표시해서 메시지를 주고받는 것

### Indirect Communication
* mailbox(또는 port)를 통해 메시지를 간접 전달하는 방식
***********************************

# CPU Scheduling
## CPU-Burst time
* 프로세스의 실행은 `CPU`를 얻어서 작업을 수행하는 것과 `I/O` 작업을 수행하는 것으로 나눌 수 있다.
* 이 때 `CPU`만 쓰면서 `Instruction`을 실행하는 단계는 `CPU burst`라 하고 `I/O`만 실행하는 단계는 `I/O burst`라 한다.
* 현재 프로세스가 `CPU`를 사용중이라면 다른 프로세스는 사용이 끝날 때까지 기다려야 하겠지만 `I/O` 작업중이라면 다른 프로세스가 `CPU`를 쓸 수 있다.
* 프로세스의 종류는 여러 가지가 있기 때문에 시스템 자원을 효율적으로 쓸 수 있도록 `CPU 스케줄링`이 필요하다.<br><br><br>

## 프로세스의 특성 분류
### I/O-bound process
* `CPU`를 잡고 계산하는 시간보다 `I/O`에 많은 시간이 필요한 job (CPU burst가 아주 짧다)
* 주로 사람과 Interactive하는 job

### CPU-bound process
* 계산 위주의 job (CPU burst가 아주 길다)<br><br><br>

## CPU Scheduler
* `Ready` 상태의 프로세스 중에서 이번에 CPU를 줄 프로세스를 고른다.

### Dispatcher
* CPU의 제어권을 CPU Scheduler에 의해 선택된 프로세스에게 넘긴다.
* 이 과정을 context switch(문맥 교환)라 한다.

### CPU 스케줄링이 필요한 경우
* Running -> Blocked (예: I/O 요청하는 시스템 콜)
* Running -> Ready (예: 할당시간 만료로 timer interrupt)
* Blocked -> Ready (얘: I/O 완료 후 인터럽트)
* Terminate<br><br>

* 스케줄링에는 강제로 빼앗지 않고 자진 반납하는 `non-preemptive`와 강제로 빼앗는 `preemptive`가 있다.
* 현대 대부분의 프로세서는 `preemptive`를 사용한다.<br><br><br>

## 스케줄링 성능 척도
* CPU utilization(이용률) : `CPU`가 얼마나 쉼 없이 일하는지
* Throughput(처리량) : 단위 시간동안 처리하는 작업의 양이 얼마나 많은지
* Turnaround time(소요시간, 반환시간) : 프로세스가 CPU를 얻어서 작업을 시작하고 끝날 때까지 걸린 총 시간(대기시간 포함)
* Waiting time(대기 시간) : Ready queue에서 CPU를 얻을 때까지 기다린 시간. 작업 시간은 제외하고 순수하게 기다린 시간만 본다.
* Response tiem(응답 시간) : (time-sharing 시스템에서) 처음으로 CPU를 얻어서 작업을 시작하기까지 걸린 시간<br><br><br>

## 스케줄링 알고리즘
### FCFS (First-Come First-Serve)
* 선착순 방식으로 먼저 온 순서대로 CPU를 얻어서 작업을 시작하고 나중에 온 프로세스들은 이전 작업이 끝날 때까지 기다린다.
* 오래 걸리는 작업이 먼저 와서 계속 수행되고 시간이 짧은 작업들이 뒤에서 기다리고 있는 경우에는 효율적이지 않다. 이런 경우엔 평균 대기 시간이 길어짐
* 짧은 작업이 먼저 와서 처리된 후 오래 걸리는 작업을 처리하게 되면 평균 대기 시간이 짧아지지만 늘 이렇게 프로세스가 도착하지는 않을 것이니까 일반적으로는 효율적이지 않은 방식이라고 할 수 있다. 
* `Convoy effect` : 수행 시간이 긴 작업이 먼저 와서 처리되는 동안 짧은 작업들은 수행되지 못하고 기다리고 있는 현상

### SJF (Shortest-Job-First)
* 도착하는 프로세스마다 CPU burst time을 예측해서 CPU burst time이 가장 짧은 프로세스를 제일 먼저 스케줄한다. 그래서 평균 대기시간이 가장 짧다.
* 두 가지 방식이 있다.
    * `Non-preemptive` : 일단 CPU를 잡으면 다음 작업이 지금 수행 중인 작업보다 실행 시간이 더 짧아도 지금 작업이 완료되기 전 까지는 CPU를 넘겨주지 않는다.
    * `Preemptive` : 현재 수행 중인 프로세스 다음에 온 프로세스의 수행 시간이 더 짧으면 CPU를 뺏어서 시간이 더 짧은 프로세스에게 넘긴다. 근데 이러다보면 수행 시간이 긴 프로세스는 평생 CPU를 얻지 못 할 수도 있어서(`starvation` 기아 현상) 아주 좋은 방법은 아니다.
    
#### 다음 CPU Burst time 예측 방법
* 완벽하게 계산하기 보다는 과거 데이터로부터 추정(estimate)하는 방식을 사용한다.
* n번째 프로세스의 실제 CPU 사용 시간과 n번째 프로세스의 CPU 사용 시간을 예측했던 값들을 일정 비율씩 곱해서 더해주는 방식으로 n + 1번째 프로세스의 CPU burst time을 예측한다.

### Priority Scheduling
* 우선순위 스케줄링이라 하며 프로세스에게 부여된 우선순위가 높은 순서대로 CPU를 할당한다.
* 이것 또한 나중에 도착했지만 우선순위가 더 높은 프로세스에 대해 `Preemptive`와 `Non-preemptive` 방식으로 나뉜다.
* 우선순위 스케줄링의 문제점 또한 우선순위가 낮은 프로세스는 평생 CPU를 얻지 못하는 `Starvation` 현상이 생길 수 있다는 것이다. 
* 그래서 `Aging` 기법을 통해 우선순위가 낮아도 오래 기다렸으면 우선순위를 높여주는 방식을 쓴다.

### Round Robin (RR)
* 대부분의 운영체제에서 사용하는 방식으로 각 프로세스는 동일한 크기의 `CPU 할당 시간(time quantum)`을 가지고 할당된 시간이 끝나면 `CPU`를 다음 프로세스에게 넘겨주고 `Ready queue`의 맨 뒤에 가서 다시 줄을 서는 방식이다.
* 그래서 모든 프로세스는 `Ready queue`의 크기만큼 기다리게 되는데 수행 시간이 짧은 프로세스는 그만큼 빨리 `CPU`를 쓰고 `Ready queue`에서 빠져나가기 때문에 각 프로세스의 대기 시간은 본인의 `CPU` 사용 시간에 비례하게 된다.
* 할당 시간이 너무 크면 `FCFS`와 다를 바가 없고 너무 작으면 `context switch`가 자주 일어나 오버헤드가 커지기 때문에 적절한 중간값을 찾는 것이 좋다.

### Multilevel Queue
* `Ready queue`를 작업의 종류에 따라 여러 개로 분할해서 각 큐마다 다른 스케줄링 알고리즘을 적용한다.
* 예를 들어 `interactive`한 작업들이 담긴 큐라면 `RR` 스케줄링을 적용하고 `CPU burst` 작업들이 담긴 큐라면 `FCFS` 스케줄링을 적용하는 것이다.
* 이 때 `Starvation`을 방지하기 위해서 각 큐에 `CPU time`을 적절한 비율로 할당한다.
    * 예) `RR` 스케줄링 큐에는 80%를 할당하고 `FCFS` 스케줄링 큐에는 20% 할당
    
### Multilevel Feedback Queue
* `Multilevel Queue`에서는 한 번 큐가 결정되면 다른 큐로 이동할 수 없어서 나중에 프로세스의 `burst time`이 바뀌게 되어도 계속 맞지 않는 큐에 있어야 할 수 있다.
* 이것을 보완한 것이 `Multilevel Feedback Queue`인데 프로세스가 다른 큐로 이동이 가능하다.
* `Aging`을 이런 방식으로 구현할 수 있다.
* `Multilevel Feedback Queue scheduler`를 정의하는 파라미터들
    * `Queue`에 있는 작업의 수 : 작업의 수가 적은 큐에 먼저 할당
    * 각 큐의 스케줄링 알고리즘
    * 프로세스를 상위 큐로 보내는 기준 (예: `CPU` 사용시간이 짧을 수록)
    * 프로세스를 하위 큐로 보내는 기준 (예: `CPU` 사용시간이 길수록)
    * 프로세스가 `CPU` 서비스를 받으려 할 때 들어갈 큐를 결정하는 기준

### Multiple-Processor Schduling
* `CPU`가 여러 개인 경우 스케줄링이 더욱 복잡해진다.
* `Homogeneous processor`(동종)인 경우
    * 큐에 한 줄로 세워서 각 프로세서가 알아서 꺼내가게 할 수 있다.
    * 반드시 특정 프로세서에서 수행되어야 하는 프로세스가 있는 경우에는 더 복잡해짐
* `Load sharing`
    * 일부 프로세서에 job이 몰리지 않도록 부하를 적절히 공유하는 메커니즘 필요
    * 별개의 큐를 두는 방법 vs. 공동 큐를 사용하는 방법
* `Symmetric Multiprocessing (SMP)`
    * 각 프로세서가 각자 알아서 스케줄링 결정
* `Asymmetric multiprocessing`
    * 하나의 프로세서가 시스템 데이터의 접근과 공유를 책임지고 나머지 프로세서는 거기에 따름
    
### Real-Time Scheduling
* 데드 라인이 있는 작업들에 적용되는 스케줄링
* `Hard real-time systems` : 반드시 정해진 시간 안에 끝내도록 스케줄링
* `Soft real-time computing` : 데드 라인을 조금 어겨도 괜찮기 때문에 `Soft real-time task`는 일반 프로세스에 비해 높은 우선순위를 갖게 한다.

### Thread Scheduling
* `Local Scheduling` : `User level thread`일 경우 사용자 수준의 스레드 라이브러리에 의해 어떤 스레드를 스케줄 할 지 결정
* `Global Scheduling` : `Kernal level thread`인 경우 일반 프로세스와 마찬가지로 커널의 단기 스케줄러가 어떤 스레드를 스케줄 할 지 결정

### 스케줄링 알고리즘 평가
* `Queueing models`
    * `확률 분포`로 주어지는 `arrival rate`와 `service rate` 등을 통해 각종 `performance index` 값을 계산하는데 요즘은 잘 안 쓴다.
* `Implementation (구현) & Measurement (성능 측정)`
    * `실제 시스템`에 알고리즘을 `구현`하여 실제 작업(`workload`)에 대해서 성능을 `측정` 비교하는 방식으로 많이 쓰는 방식
* `Simulation (모의 실험)`
    * 알고리즘을 `모의 프로그램`으로 작성 후 `trace`를 입력으로 하여 결과 비교
*************************************
# Process Synchronization
## Process Synchronization 문제
* 컴퓨터에 저장되어 있는 어떤 데이터를 변경하려면 그 데이터에 접근해서 변경하는 연산을 한 뒤 연산 결과를 다시 그 데이터가 있는 자리에 갱신시켜줘야 한다.
* 그런데 이 때 하나의 프로세스만 접근해서 작업을 하면 문제가 없지만 컴퓨터에는 수많은 프로세스가 있고 하나의 데이터에 여러 프로세스가 접근하는 상황이 생길 수 있다.
* 이 때 아무런 제어 없이 여러 프로세스가 접근해서 하나의 데이터를 변경시키면 서로 다른 시점에 데이터를 변경하게 될 수 있고 그러다보면 데이터가 사용자의 의도와 다르게 변경될 수 있다(데이터 불일치 문제). 그래서 이걸 막고 데이터의 일관성 유지를 위해서 공유 데이터에 접근할 때 협력 프로세스 간의 실행 순서를 정해주어야 한다.

### 🔸 Race condition
* 여러 프로세스들이 동시에 공유 데이터에 접근하는 상황
* 데이터의 최종 연산 결과는 마지막에 그 데이터를 다룬 프로세스에 따라 달라짐
* `Race condition`을 막기 위해 `concurrent process(동시 접근)`는 `동기화(synchronize)`되어야 한다.<br><br><br>

## Race Condition이 발생하는 상황
### 1. 커널 수행 중 인터럽트 발생 시
* 커널 데이터를 처리하는 도중에 `인터럽트`가 생긴 경우
* 해결책 : 먼저 작업 중이던 커널 코드의 작업이 끝나기 전 까지는 `인터럽트`를 받지 않는다.

### 2. 프로세스가 시스템 콜을 하여 커널 모드로 수행 중인데 context switch가 일어나는 경우
* A 프로세스가 `PC`를 증가시키는 도중에 다른 커널 코드 B에게 `CPU`를 뺏겼다가 뺏어간 쪽의 작업이 끝난 후 다시 돌려 받으면 A는 B가 증가시키기 전의 `PC` 정보를 가지고 있기 때문에 A가 증가시키는 `PC`는 정확한 값으로 증가되지 않는다.
* 해결책 : 커널 모드에서 수행 중일 때는 `CPU`를 `preempt`하지 않고 커널 모드에서 사용자 모드로 돌아갈 때 `preempt`한다.

### 3. Multiprocessor에서 shared memory 내의 커널 데이터
* 위 경우들은 같은 `CPU` 내에서만 할 수 있는 동작들이기 때문에 멀티 프로세서 환경에서는 적용이 어렵다. 
* 여러 프로세스들이 하나의 공유 메모리에 접근해야 할 때 각각의 `CPU`에서 동시에 접근해서 데이터를 변경할 수 있다.
* 해결책 1 : 한 번에 하나의 `CPU`만이 커널에 들어갈 수 있게 하는 방법
* 해결책 2 : 커널 내부에 있는 각 공유 데이터에 접근할 때마다 그 데이터에 대한 `lock/unlock`을 하는 방법<br><br><br>

## The Critical-Section Problem
* n개의 프로세스가 공유 데이터를 동시에 사용하기를 원하는 경우
* 각 프로세스의 `code segment`에는 공유 데이터를 접근하는 코드인 `critical section`이 존재
* 하나의 프로세스가 `critical section`에 있을 때 다른 모든 프로세스는 `critical section`에 들어갈 수 없어야 한다.

### 프로그램적 해결법의 충족 조건
* `Mutual Exclusion(상호 배제/배타적 접근)`
    * 프로세스 Pirk `critical section` 부분을 수행 중이면 다른 모든 프로세스들은 그들의 `critical section`에 들어가면 안 된다.
* `Progress(진행)`
    * 아무도 `critical section`에 있지 않은 상태에서 `critical section`에 들어가고자 하는 프로세스가 있으면 `critical section`에 들어가게 해 주어야 한다.
* `Bounded Waiting(유한 대기)`
    * 프로세스가 `critical section`에 들어가려고 요청한 후부터 그 요청이 허용될 때까지 다른 프로세스들이 `critical section`에 들어가는 횟수에 한계가 있어야 한다.
    * 무한대로 기다리지 않게 해서 `starvation`을 방지<br>

* 가정
    * 모든 프로세스의 수행 속도는 0보다 크다.
    * 프로세스들 간의 상대적인 수행 속도는 가정하지 않는다.

### 기본적인 해결 방법
* 두 개의 프로세스 `P0`, `P1`이 있다고 가정했을 때 

```c
do {
    entry section   /* lock */
    critical section
    exti section    /* unlock */
    remainder section
} while(1);
```

* 프로세스들은 수행의 동기화를 위해 몇몇 변수를 공유할 수 있다. - `Synchronization variable`

#### Algorithm 1

```c
int turn;   /* 누구 차례인지 표시할 변수.  Synchronization variable */
initially turn = 0;

do {
    while (turn != 0);  /* 내 턴이 아닌 동안 대기 */
    critical section
    turn = 1;   /* 상대편으로 턴 넘김 */
    remainder section
} while (1);
```

* 위 코드대로만 진행되면 문제가 없어 보이지만 반드시 상대 프로세스가 들어와서 `turn`을 바꿔 주어야만 다른 프로세스가 `critical section`에 들어갈 수 있기 때문에 만약 A 프로세스가 더 빈번하게 `critical section`에 들어가야 하는 경우 B 프로세스는 상대적으로 덜 들어가기 때문에 `turn`이 바뀌지 않아 A 프로세스가 들어갈 수 없는 상황이 생긴다.

#### Algorithm 2

```c
boolean flag[2];    /* critical section에 들어가고자 하는 의중을 표시하는 flag */
initially flag[모두] = false; /* 처음엔 critical section에 아무도 없음 */

do {
    flag[i] = true;     /* 진입 표시 */
    while (flag[j]);    /* 상대 프로세스도 진입해 있으면 대기 */
    critical section
    flag[i] = false;    /* 나왔다고 표시 */
    remainder section
} while (1);
```

* 위 코드에서는 만약 A 프로세스가 첫번째 줄만 실행하고 `CPU`를 뺏긴 경우 상대 프로세스도 첫번째 줄을 실행하고 두번째 줄에서 대기하게 될 것이다. 즉 둘 다 무한히 대기하게 된다.

#### Algorithm 3 (Peterson's Algorithm)

```c
do {
    flag[i] = true;     /* 진입 표시 */
    turn = j;           /* 상대편으로 턴 변경 */
    while (flag[j] && turn == j);   /* 들어가고자 하는 프로세스와 턴 모두 확인 */
    critical section
    flag[i] = false;
    remainder section
} while (1);
```

* 알고리즘 1과 2를 합친 방법으로 앞선 두 가지 방법에서 있었던 문제들을 모두 해결할 수 있다.
* `Busy Waiting(= spin lock)`
    * 하지만 `critical section`에 프로세스가 이미 있어서 못 들어가는 것이 확실한 상황에서도 계속 `CPU`를 얻어서 `while`문 조건을 확인해야 하기 때문에 지속적으로 `CPU`와 `memory`를 소모하게 된다.

#### 하드웨어적으로 해결하기
* `Instruction` 하나로 `Synchronization variable` 읽기와 쓰기를 동시에 실행하면 위의 알고리즘으로 해결하고자 했던 문제들을 간단히 해결할 수 있다. 

```c
boolean lock = false;

do {
    while (Test_and_set(lock); /* lock이 걸려있다면 lock을 걸고 기다릴 것이고 걸려있지 않다면 lock을 걸고 들어갈 것임 */
    critical section
    lock = false;
    remainder section
} while (1);
```
<br><br>

### Semaphores
* 프로그래머가 매번 앞의 작업들을 하려면 귀찮으니까 그 작업들을 추상화시킨 것
* `integer variable` 형태로 자원의 갯수를 가지고 있다.
* 아래의 두 가지 `atomic` 연산에 의해서만 접근할 수 있다.

```c
/* P(S) : 공유 데이터를 획득하는 연산 */
while (S <= 0) do wait; /* 사용할 수 있는 자원이 없으면 대기 */
S--;

/* V(S) : 공유 데이터를 사용 후 반납 */
S++;
```

#### 세마포어를 이용한 코드 - Busy-wait

```c
semaphore mutex;    /* initially 1 : 1개가 critical section에 들어갈 수 있다 */

do {
    P(mutex);   /* 자원이 남아 있으면 하나 감소시키고 입장 */
    critical section
    V(mutex);   /* 자원 반납 및 증가 */
    remainder section
} while (1);
```

* 대기하는 프로세스가 있으면 자원이 생겼는지 계속 확인해야 하기 때문에 `busy-wait`하게 된다.

#### 세마포어를 이용한 코드 - Block & wekeup
* 세마포어를 다음과 같이 정의한다.

```c
typedef struct
{
    int value;          /* semaphore */
    struct process *L;  /* 프로세스 대기열 */
} semaphore;
```

* `block`과 `wakeup`을 다음과 같이 가정한다.
    * `block` : 커널은 `block`을 호출한 프로세스를 `suspend` 시킨 후 이 프로세스의 `PCB`를 세마포어에 대한 대기열에 넣음
    * `wakeup` : `block`된 프로세스를 `wakeup` 시킨 후 이 프로세스의 `PCB`를 `ready queue`로 옮김

* 세마포어 연산 정의

```c
/* P(S) */
S.value--;  /* 입장 전에 자원의 수를 감소시킴 */
if (S.value < 0)    /* 현재 쓸 수 있는 자원이 없으면 대기시킨다 */
{
    add this process to S.L;
    block();
}

/* V(S) */
S.value++;
if (S.value <= 0)   /* P 연산에서 자원을 미리 감소시키고 들어가기 때문에 자원을 반납했는데도 갯수가 0 이하라면 기다리고 있는 프로세스가 있는 것 */
{
    remove a process P from S.L;
    wakeup(P);
}
```

#### 👀 Busy-wait vs. Block/wakeup
* `critical section`의 길이가 긴 경우 `Block/wakeup`이 적당
* `critical section`의 길이가 매우 짧은 경우 `Block/wakeup` 오버헤드가 `Busy-wait` 오버헤드보다 더 커질 수 있다.
* 일반적으로는 `Block/wakeup` 방식이 좋다.<br><br>

### 세마포어의 두 종류
* `Counting semaphore`
    * 도메인이 0 이상인 임의의 정수값
    * 주로 리소스의 갯수를 세는 데 사용한다.
    
* `Binary semaphore`
    * 0 또는 1 값만 가질 수 있는 세마포어
    * 주로 `mutual exclusion (lock/unlock)`에 사용

### Deadlock and Starvation
#### Deadlock
* 둘 이상의 프로세스가 서로 상대방에 의해 충족될 수 있는 event를 무한히 기다리는 현상
* 1과 2 두 개의 자원을 얻어야 하는 A 프로세스가 있을 때 만약 A 프로세스가 1번 자원만 얻고 B 프로세스에게 `CPU`를 뺏긴 후 B 프로세스가 2번 자원을 얻으면 A 프로세스는 `CPU`를 다시 돌려받아도 2번 자원을 얻지 못해서 다음으로 진행할 수 없다. B 프로세스 또한 1번 자원이 필요하다면 영원히 기다리게 된다.
* 이러한 현상을 해결하기 위해서 자원을 획득하는 순서를 정해줘서 1번 자원을 먼저 얻어야만 2번 자원을 얻을 수 있게 하는 방식을 사용할 수 있다.

#### Starvation
* `indefinite blocking`
* 프로세스가 `suspend`된 이유에 해당하는 세마포어 큐에서 빠져나갈 수 없는 현상<br><br><br>

## Classical Problems of Synchronization
### 🔸 Bounded buffer problem
* `Producer-Consumer Problem`이라고도 하며 데이터 입력을 위한 버퍼를 생성하는 생산자와 그 버퍼를 읽어서 수정된 데이터를 반영할 소비자로 나누는 개념이다. 
* 생산자는 빈 버퍼가 있는지 확인 후(없으면 기다림) 공유데이터에 lock을 걸고 버퍼에 데이터를 입력한 다음 lock을 풀고 든 버퍼를 하나 증가시킨다.
* 소비자는 든 버퍼가 있는지 확인 후(없으면 기다림) 공유데이터에 lock을 걸고 버퍼에서 데이터를 꺼낸 뒤 lock을 풀고 빈 버퍼를 하나 증가시킨다.

#### 공유 데이터
* 버퍼 및 버퍼 조작 변수(empty/full buffer의 시작 위치)

#### 동기화 변수
* mutual exclusion : 공유데이터의 mutual exclusion을 위해 필요
* resource count : 남은 empty/full buffer의 수를 표시하기 위해 필요

```c
/* Producer */
do {
    produce an item in x
    ...
    P(empty);
    P(mutex);
    ...
    add x to buffer
    ...
    V(mutex);
    V(full);
} while (1);

/* Consumer */
do {
    P(full);
    P(mutex);
    ...
    remove an item from buffer to y
    ...
    V(mutex);
    V(empty);
    ...
    consume the item in y
    ...
} while (1);
```

### 🔸 Readers-Writers Problem
* 한 프로세스가 `DB`에 `write` 중일 때 다른 프로세스가 접근하면 안 됨
* `read`는 동시에 여럿이 해도 됨
* solution
    * `Writer`가 `DB`에 접근 허가를 아직 얻지 못한 상태에서는 모든 대기 중인 `Reader`들을 다 `DB`에 접근하게 해준다.
    * `Writer`는 대기 중인 `Reader`가 하나도 없을 때 `DB` 접근이 허용된다.
    * 일단 `Writer`가 `DB`에 접근 중이면 `Reader`들은 접근이 금지된다.
    * `Writer`가 `DB`에서 빠져 나가야만 `Reader`의 접근이 허용된다.

#### 공유 데이터
* `DB` 자체
* `readcount` : 현재 `DB`에 접근 중인 `Reader`의 수

#### 동기화 변수
* `mutex` : 공유 변수 `readcount`를 접근하는 코드(critical section)의 `mutual exclusion` 보장을 위해 사용
* `db` : `Reader`와 `Writer`가 공유 `DB` 자체를 올바르게 접근하는 역할

```c
int readcount = 0;
DB 자체;
semaphore mutex = 1, db = 1;

/* Writer */
P(db);
...
writing DB ...
...
V(db);

/* Reader */
P(mutex);
readcount++;
if (readcount == 1) P(db);  /* Writer 대기시킴 */
V(mutex);
...
reading DB ...
...
P(mutex);
readcount--;
if (readcount == 0) V(db);  /* Writer 입장 가능 */
V(mutex);
```

* 하지만 위 코드대로만 하면 `Reader`가 계속 들어와서 `Writer`가 영원히 기다리게 될 수 있기 때문에(starvation) `Writer`의 우선순위를 높여줘서 너무 오래 기다리지 않게 한다.

### 🔸 Dining-Philosophers Problem
* 다섯 명의 철학자가 원형 테이블에 앉아서 생각과 식사를 반복하는데 젓가락이 5개(2개 세트 아님)밖에 없음
* 철학자는 내 양 옆에 있는 젓가락을 옆에 있는 철학자들이 쓰고 있지 않아야 젓가락을 사용해 밥을 먹을 수 있다.
* 이 때 어떤 철학자의 양 옆에 있는 철학자들이 계속 밥을 먹어서 어떤 철학자가 젓가락을 영원히 쓰지 못하면 굶어 죽는다는.. 그런 문제이다.
* 해결 방안
    * 4명의 철학자만 테이블에 동시에 앉을 수 있도록 한다.
    * 젓가락을 두 개 모두 집을 수 있을 때에만 젓가락을 집을 수 있게 한다.
    * 비대칭 : 짝수(홀수) 철학자는 왼쪽(오른쪽) 젓가락부터 집도록 한다.<br><br><br>
    
## Monitor
### 세마포어의 문제점
* 코딩하기 힘들다. - 문제가 생겼을 때 버그 잡기 힘듦
* 정확성(correctness)의 입증이 어렵다.
* 자발적 협력(voluntary cooperation)이 필요하다.
* 한 번의 실수가 모든 시스템이 치명적인 영향을 끼친다.

#### 예

```
V(mutex)
critical section
P(mutex)
```
* `Mutual exclusion`이 깨짐<br>

```
P(mutex)
critical section
P(mutex)
```
* `Deadlock`<br>

* 위 경우들처럼 순서가 바뀌거나 같은 연산을 두 번 쓰는 실수가 생기면 오작동이 생긴다.

### Monitor
* 동시 수행 중인 프로세스 사이에서 `abstract data type`의 안전한 공유를 보장하기 위한 `high-level synchronization construct`
* 객체 지향 프로그래밍에서 `class`에 멤버 변수와 함수를 담아서 사용하듯이 공유 데이터를 모니터 안에 선언하고 공유 데이터에 접근하려면 모니터 내부의 함수를 통해서만 하도록 하는 방법
* 모니터 내의 함수는 한 번에 하나만 실행할 수 있기 때문에 `lock`을 걸 필요가 없다. 그래서 프로그래머 입장에서는 좀 더 간편하게 프로그램을 짤 수 있다.
*************************************

# Deadlocks
* 일련의 프로세스들이 서로가 가진 자원을 기다리며 `block`된 상태

## Resource(자원)
* 하드웨어, 소프트웨어 등을 포함하는 개념
* 예) `I/O device`, `CPU cycle`, `memory space`, `semaphore` 등
* 프로세스가 자원을 사용하는 절차
    * `Request` -> `Allocate` -> `Use` -> `Release`

## 데드락이 발생하는 예
* 시스템에 2개의 `tape drive`가 있고 프로세스 `P1`, `P2` 각각이 하나의 `tape drive`를 보유한 채 다른 하나를 기다리고 있는 경우<br><br>

```c
P0          P1
P(A);       P(B);
P(B);       P(A);
```

* 두 세마포어가 필요한 자원을 서로 자원을 하나씩 가진 상태에서 상대가 내놓기를 기다리는 경우

## 데드락 발생의 4가지 조건
### Mutual exclusion (상호 배제)
* 매 순간 하나의 프로세스만이 자원을 사용할 수 있음

### No preemption (비선점)
* 프로세스는 자원을 스스로 내어놓을 뿐 강제로 빼앗기지 않음

### Hold and wait (보유 대기)
* 자원을 가진 프로세스가 다른 자원을 기다릴 때 보유 자원을 놓지 않고 계속 가지고 있음

### Circular wait (순환 대기)
* 자원을 기다리는 프로세스간에 사이클이 형성되어야 함
* 프로세스 `1, 2, 3, 4`가 있을 때
    * `1`은 `2`가 가진 자원을 기다림
    * `2`는 `3`이 가진 자원을 기다림
    * `3`은 `4`가 가진 자원을 기다림
    * `4`는 `1`이 가진 자원을 기다림<br><br>

## 데드락 처리 방법
### Deadlock Prevention
* 자원 할당 시 `데드락`의 4가지 필요 조건 중 어느 하나가 만족되지 않도록 하는 것

### Deadlock Avoidance
* 자원 요청에 대한 부가적인 정보를 이용해서 `데드락`의 가능성이 없는 경우에만 자원 할당
* 시스템 `state`가 원래 `state`로 돌아올 수 있는 경우에만 자원 할당

### Deadlock Detection and recovery
* `데드락` 발생은 허용하되 그에 대한 `detection` 루틴을 두어 `데드락` 발견시 `recover`

### Deadlock Ingorance
* `데드락`을 시스템이 책임지지 않음
* `UNIX`를 포함한 대부분의 `OS`가 채택
* `데드락` 자체가 자주 발생하는 일이 아니기 때문에 `데드락`에 대비한다고 시스템의 자원 분배를 조절하는 것은 비효율적이기 때문에 사용자가 알아서 처리하도록 한다.<br><br>

## 데드락 방지
### Mutual exclusion
* 공유해서는 안 되는 자원의 경우 반드시 성립해야 함
* 즉 이 조건이 반드시 성립한다면 데드락이 발생할 수 없다.

### Hold and Wait
* 프로세스가 자원을 요청할 때 다른 어떤 자원도 가지고 있지 않아야 한다.
* 방법 1 : 프로세스 시작 시 모든 필요한 자원을 할당받게 하는 방법
* 방법 2 : 자원이 필요할 경우 보유 자원을 모두 놓고 다시 요청

### No Preemption
* 프로세스가 자원을 기다려야 하는 경우 이미 보유한 자원이 선점됨
* 모든 필요한 자원을 얻을 수 있을 때 그 프로세스는 다시 시작됨
* 즉 자원을 선점할 수 있게 하는 것
* `state`를 쉽게 `save`하고 `restore`할 수 있는 자원에서 주로 사용 (예: `CPU`, `memory`)

### Circular Wait
* 모든 자원 유형에 할당 순서를 정하여 정해진 순서대로만 자원 할당
* 예를 들어 순서가 3인 자원을 보유 중인 프로세스가 순서가 1인 자원을 할당받기 위해서는 우선 순서 3을 `release`해야 한다.
* 자원 요청 사이클이 생성되지 않게 하는 것<br>

* 하지만 위 기법들을 적용하면 `Utilization(이용률)` 저하, `Throughput(성능)` 감소, `Starvation` 문제가 생겨서 굉장히 비효율적이다.<br><br>

## Deadlock Avoidance
* 자원 요청에 대한 부가정보를 이용해서 자원 할당이 데드락으로부터 안전한지 동적으로 조사해서 안전한 경우에만 할당
* 가장 단순하고 일반적인 모델은 프로세스들이 필요로 하는 각 자원별 최대 사용량을 미리 선언하도록 하는 방법

### Resource Allocation Graph algorithm
* 자원당 하나의 인스턴스만 있을 때 사용하는 방법
* 자원들과 프로세스들 간을 실선과 점선으로 잇는 그래프를 그려 할당과 요청된 자원은 실선으로 표시하고 어떤 프로세스가 미래에 한 번은 사용할 수 있는 자원은 점선으로 표시하는 것이다. 
* 새로운 자원 요청이 들어오면 실선을 점선으로 바꿨을 때 사이클이 생기지 않을 때에만 요청 자원을 할당한다.
* 사이클 생성 여부 조사시 프로세스의 수가 `n`일 때 `O(n^2)` 시간이 걸린다.

### Banker's Algorithm
* 가정
    * 모든 프로세스는 자원의 최대 사용량을 미리 명시
    * 프로세스가 요청 자원을 모두 할당받은 경우 유한 시간 안에 이들 자원을 다시 반납한다.
    
* 방법
    * 기본 개념 : 자원 요청 시 `safe` 상태를 유지할 경우에만 할당
    * 총 요청 자원의 수가 가용 자원의 수보다 적은 프로세스를 선택 (그런 프로세스가 없으면 `unsafe` 상태)
    * 위의 경우에 부합하는 프로세스가 있으면 그 프로세스에게 자원 할당
    * 할당받은 프로세스가 종료되면 모든 자원 반납
    * 모든 프로세스가 종료될 때까지 이러한 과정 반복

## Deadlock Detection and Recovery
### Detection
* `Banker's Algorithm`과 유사한 방법으로 사이클의 존재 여부를 주기적으로 검사하여 자원을 할당하는 방법이 있다.

### Recovery
#### Process termination
* 데드락 된 모든 프로세스 종료
* 데드락이 해결될 때 까지 데드락에 갇혀 있는 프로세스를 하나씩 종료

#### Resource preemption
* 비용을 최소화 할 `victim` 선정
* `safe state`로 `rollback`하여 프로세스 재시작
* `Starvation` 문제
    * 동일한 프로세스가 계속해서 `victim`으로 선정되는 경우
    * `cost factor`에 `rollback` 횟수도 같이 고려<br><br>
    
## Deadlock Ignorance
* 데드락이 일어나지 않는다고 생각하고 아무런 조치도 취하지 않음
* 데드락은 매우 드물게 발생하므로 데드락에 대한 조치 자체가 더 큰 오버헤드일 수 있다.
* 만약, 시스템에 데드락이 발생한 경우 시스템이 비정상적으로 작동하는 것을 사람이 느낀 후 직접 프로세스를 죽이는 등의 방법으로 대처
* `UNIX`, `Windows` 등 대부분의 범용 `OS`가 채택
**********************************************

# 출처
* [운영체제 - 이화여자대학교 KOCW 공개강의](http://www.kocw.net/home/search/kemView.do?kemId=1046323)

