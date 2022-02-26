# 컴퓨터구조<br>
## 목차<br>
* [컴퓨터의 발전](#컴퓨터의-발전)
* [컴퓨터의 종류](#컴퓨터의-종류)
* [데이터의 단위](#데이터의-단위)
* [미래의 컴퓨터](#미래의-컴퓨터)
* [컴퓨터의 성능](#컴퓨터의-성능)
* [컴퓨터 구조](#컴퓨터-구조)
* [Levels of Program Code](#levels-of-program-code)
* [컴퓨터의 구성요소](#컴퓨터의-구성요소)
* [CPU 구성요소](#CPU-구성요소)
* [추상화](#추상화)
* [메모리 종류](#메모리-종류)
* [반도체 기술](#반도체-기술)
* [Performance](#performance)
* [CPU Time](#cpu-time)
* [Instruction Count & CPI](#instruction-count--cpi)
* [성능에 영향을 미치는 요소](#성능에-영향을-미치는-요소)
* [Clock period](#clock-period)
* [Power wall](#power-wall)
* [Multiprocessors](#multiprocessors)
* [CPU 성능 측정](#cpu-성능-측정)
* [Amdahl's Law](#amdahls-law)
* [대기 중 전력소모](#대기-중-전력소모)
* [Instruction Set](#instruction-set)
* [Design Principle](#design-principle)
* [Operations of the Computer Hardware](#operations-of-the-computer-hardware)
* [Logical Operations](#logical-operations)
* [명령 실행 단계](#명령-실행-단계)
* [코드가 실행되는 과정](#코드가-실행되는-과정)
* [출처](#출처)

# 컴퓨터의 발전
* `무어의 법칙` 덕분에 숱한 기술의 발전이 가능했다.
* 중요하니까 외우자.<br><br>

## 👀 무어의 법칙
* 싱글 칩의 트랜지스터 수가 2년마다 2배로 증가한다는 법칙(실제로는 2배보다 더 많이 증가)
* 성능의 급격한 발전으로 인해 과거에 비해 더 싼 가격에 더 좋은 성능을 발휘할 수 있게 되었다.<br><br><br>

# 컴퓨터의 종류
## 개인 컴퓨터
* 일반적으로 사용하는 컴퓨터
* 비교적 저렴하고 저성능<br><br>

## 서버 컴퓨터
* 네트워크 통신이 주 목적
* 고가, 대용량, 고성능<br><br>

## 수퍼 컴퓨터
* 군사용, 기상청 날씨 예측용 등 특수 목적으로 사용되는 컴퓨터<br><br>

## 임베디드 컴퓨터
* 큰 시스템에 컴퓨터가 하나의 컴포넌트로 구성된 것
* 적은 전력소모, 저성능, 저가
* ex) 스마트폰, 태블릿 PC<br><br><br>

# 데이터의 단위
* `bit` - `byte` - `Kilobyte` - `Megabyte` - `Gigabyte` - `Terabyte` - `Petabyte` - `Exabyte`<br><br>

* `Byte` : 8`bit`
* `Kilobyte` : 2^10 or 1,024 `bytes`
* `Megabyte` : 2^20 or 1,048,576 `bytes`
* `Gigabyte` : 2^30 or 1,073,741,824 `bytes`
* `Terabyte` : 2^40 or 1,099,511,627,776 `bytes`
* `Petabyte` : 2^50 or 1024 `terabytes`
* `Exabyte` : 2^60 ir 1024 `petabytes`<br><br><br>

# 미래의 컴퓨터
## Personal Mobile Device (PMD)
* 스마트폰, 태블릿 PC, 전자안경 등
* 배터리로 작동되며 인터넷에 연결해서 사용<br><br>

## Cloud computing
* Warehouse Scale Computers (WSC) : 특정한 데이터를 서버에서 처리하고 필요할 때 서버에서 다운받아서 사용
* Software as a Service (SaaS) : 필요한 소프트웨어를 서비스 형태로 제공받는다.
* 복잡한 연산은 `Cloud`에서 처리하고 `PMD`에서는 간단한 `UI` 같은 것만 보여주는 것
* 아마존과 구글의 클라우드 서비스<br><br><br>

# 컴퓨터의 성능
## 알고리즘 측면
* 실행되는 `operation`의 수가 적을수록 성능이 높다.<br><br>

## 프로그래밍 언어, 컴파일러, 구조
* `operation`당 실행되는 `instruction`의 수가 많을수록 성능이 높다.<br><br>

## 프로세서와 메모리
* 단위시간당 `instruction`을 얼마나 빨리 실행하는지<br><br>

## 입출력 시스템
* 단위시간당 `I/O operation`을 얼마나 많이 실행하는지에 따라 결정된다.<br><br><br>

# 컴퓨터 구조
## Application software
* 일반적으로 사용자가 사용하는 프로그램
* 고급언어로 작성된 프로그램<br><br>

## System software
* `Compiler` : 고급언어를 기계어로 번역하는 것
* `Operating System` : 운영체제. 입출력, 메모리 관리, 자원 스케줄링 등을 한다.<br><br>

## Hardware
* `Processor`, `memory`, `I/O controllers`<br><br><br>

# Levels of Program Code
## High-level language
* `C`언어 같이 우리가 알아보기 쉬운 언어로 작성한 코드
* 컴파일러를 거쳐 어셈블리어로 번역된다.<br><br>

## Assembly language
* 고급언어보다는 알아보기 어렵지만 그래도 사람이 알아볼 수는 있는 정도의 단어들로 작성된 코드
* 어셈블러(Assembler)를 거쳐 기계어로 번역된다.<br><br>

## Hardware representation
* 0과 1로 이루어진 코드(Binary digits, bits)
* 비주얼 스튜디오 같은 `IDE`엔 컴파일러와 어셈블러가 함께 들어있어서 일반적으로는 함께 실행되지만 단계를 나눠서 실행도 가능하다.<br><br><br>

# 컴퓨터의 구성요소
* 컴퓨터의 종류는 여러개여도 구성요소는 다 비슷하다.
* `User-interface divices` : display, keyboard, mouse
* `Storage devices` : hard disk, CD/DVD, flash
* `Network adapters` : 다른 컴퓨터와 소통하기 위한 수단<br><br><br>

# CPU 구성요소
* `Datapath` : 데이터가 어떻게 연산되어 흘러가는지
* `Control` : 프로세서의 컴포넌트 컨트롤
* `Cache memory` : 작고 빠른 `SRAM`이 있어서 `SRAM`에 자주 사용하는 데이터를 저장해 놓는다.<br><br><br>

# 추상화(Abstractions)
* 복잡한 문제를 단순화해서 쉽게 풀 수 있도록 하는 것<br><br><br>

# 메모리 종류
## 휘발성 메모리 (Volatile main memory)
* 전원을 끄면 데이터가 날아가는 메모리<br><br>

## 비휘발성 메모리 (Non-volatile secondary memory)
* 전원을 꺼도 데이터가 날아가지 않는 메모리
* 마그네틱 디스크, 플래시 메모리, CD/DVD 등<br><br><br>

# 반도체 기술
* 실리콘에 기판을 새겨넣는 것이 반도체 칩을 만드는 과정
* `conductors`(도체), `insulators`(부도체), `switch`들이 잘 동작되게 하는 것<br><br><br>

# Performance
* `throughput`과 `response time`로 정의된다.<br>

## Response time
* `operation` 하나를 처리하는 데 걸리는 시간
* 짧을수록 성능이 좋다.<br>

## Throughput
* 단위시간 당 얼마나 많은 일을 할 수 있는지 나타낸 것
* 높을수록 성능이 좋다.<br>

* ❗️ `response time`은 `throughput`에 영향을 주지만 `throughput`은 `response time`에 영향을 주지 않는다. 그래서 성능은 `response time`으로 표현할 수 있다.<br>

## Execution time
* 짧을수록 성능이 좋다.

```
Performance X / Performance Y = Execution time Y / Execution time X = n
```

* `Performance`와 `Execution time`은 반비례 관계이다.(기억하기❗️)<br>

## Elapsed time
* 총 걸린 시간
* 프로세싱, 입출력, `OS` 오버헤드, 대기시간 등 컴퓨터가 실행되는 동안 모든 것을 처리하는 데 걸린 시간
* 그 시스템 전체의 성능을 정의하게 된다.<br>

## CPU time
* 어떤 일을 처리할 때 `CPU`에서 걸리는 시간
* 그래서 입출력, 다른 작업을 처리하는 데 드는 시간 등은 제외하고 계산된다.
* `user CPU time`과 `system CPU time`으로 나눌 수 있으며 프로그램마다 `CPU`와 시스템 성능에 다르게 영향 받는다.<br><br><br>

# CPU Clocking
* `CPU`의 처리 속도
* `CPU`의 각 부품들은 일정한 시간마다 동작한다. `Clock cycle`이라 함
* `Clock period` : `Clock cycle`의 길이
* `Clock frequency (rate)` : 초당 존재하는 `Clock cycle`의 개수

## 👀 시간 단위
`second, s` > `millisecond, ms` 10^-3 > `microsecond, μs` 10^-6 > `nanosecond, ns` 10^-9 > `picosecond, ps` 10^-12<br>

* ❗️ `Clock cycle time`과 `Clock rate`는 반비례 관계이다.<br><br><br>

# CPU Time
* 한 컴퓨터 프로그램이 `CPU`를 차지하여 일을 한 시간의 양
* 컴퓨터의 성능을 측정하기 위해 사용된다.
* `CPU Time`이 적을수록 성능이 좋다고 할 수 있다.
* `clock cycle`을 줄이거나 `clock rate`가 올라가면 성능이 향상된다.<br><br><br>

# Instruction Count & CPI
## Instruction Count
* 명령어의 수

## CPI
* Cycles per Instructions
* `Instruction`의 실행주기<br><br><br>

# 성능에 영향을 미치는 요소
* 알고리즘 : `IC`, `CPI`
* 프로그래밍 언어 : `IC`, `CPI`
* 컴파일러 : `IC`, `CPI`
* ISA(명령어셋) : `IC`, `CPI`, `T`<br><br><br>

# Clock period
* Duration of a clock cycle
* 하나의 `clock cycle`이 걸리는 시간
* `1/clock rate`로 나타낼 수 있다.<br><br><br>

# Power wall
* `clock rate`는 매년 꾸준히 늘다가 2004년을 기점으로 늘지 않고 있다.
* 왜냐면 전력소모가 많이 줄었기 때문
* 전력소모량은 `Capacitive load`x`Voltage^2`x`Frequency`로 구할 수 있는데 `Voltage`가 많이 줄었기 때문에 `Frequency`가 많이 늘어났음에도 전력소모량은 크게 늘지 않았다.
* 그런데 `Voltage`가 높을수록 전력소모와 열 발생이 많은데 `Voltage`를 더이상 줄일 수가 없게 되었기 때문에 기존에 `clock rate`을 증가시키는 방법으로는 성능 향상을 꾀하기가 어려워졌다.
* 2004년 이후로 `clock rate`을 증가시키지 못한 이유가 `CPU`에서 발생하는 열을 해결하지 못해서였다.
* 그래서 `clock rate`을 올리지 않고 성능을 향상시키기 위한 방법으로 `Multi-core`가 등장하게 된다.<br><br><br>

# Multiprocessors
* `Multicore microprocessors` : 하나의 칩 안에 프로세서가 여러 개 있는 것
* `Parallel programming`이 필요하다. 
    * 하드웨어가 여러 명령을 동시에 실행할 수 있지만 그만큼 프로그래밍이 어렵다.<br><br><br>
    
# CPU 성능 측정
* `SPEC CPU Benchmark`로 측정하거나 `MIPS`(Millions of Instructions per Second : 시간당 몇백만개의 명령을 실행하는가)를 이용해 측정할 수 있는데 `SPEC CPU Benchmark`가 더 정확하다고 할 수 있다.
* `SPEC CPU Benchmark`는 여러 파트에서 측정한 시간값을 바탕으로 총점을 매기는데 `MIPS`는 `IC`와 `Exectution time`을 이용해 계산하기 때문에 컴퓨터마다 `ISA`(명령어셋)가 다르고 또 명령어마다 필요한 `CPI`값이 다를 수 있기 때문에 객관적이라 하기 어렵다.<br><br><br>

# Amdahl's Law
* 컴퓨터의 어느 한 부분의 성능을 향상시키면 전체 성능의 향상은 그 부분이 컴퓨터에서 차지하는 비율만큼 향상된다는 법칙
* `Corollary : make the common case fast`
* 따라서 전체 시스템에서 차지하는 비율이 높은 부분의 성능을 향상시키는 것이 전체 성능 향상에 도움이 된다.<br><br><br>

# 대기 중 전력소모
* `CPU`를 거의 사용하지 않는 상황에서도 생각보다 전력소모가 크다.
    * 예를 들어 `CPU`가 10%만 사용중인데 전력은 전체의 47%를 사용한다는 등
* 그래서 프로세서를 만들 때 전력소모의 비율이 `CPU` 사용량에 비례되게 설계할 필요가 있는데 쉽지 않다.
***********************************

# Instruction Set
* 프로세서에서 지원하는 명령어들의 집합
* 다른 컴퓨터는 다른 명령어셋을 가지고 있지만 기본적으로는 비슷하다. 
* 현대 컴퓨터는 대부분 간단한 명령어셋(`MIPS` - `RISK` 방식)을 가지고 있다.

## Instruction Set Architecture (ISA)
* 하드웨어와 낮은 레벨의 소프트웨어를 연결하는 인터페이스로 시스템 소프트웨어(운영체제)라 할 수 있다.
* `ISA`가 같으면 같은 소프트웨어를 여러 개의 `CPU`에서 실행할 수 있다.

## ABI
* `ISA`와 운영체제 인터페이스를 합친 것
* `ABI`만 같으면 같은 프로그램이 어디에서든 실행될 수 있다.
* 윈도우 운영체제를 쓰는 컴퓨터들은 어떤 컴퓨터를 쓰든 같은 프로그램을 실행할 수 있는 것<br><br><br>

# Design Principle
## 1. 정규화(규칙화)해서 간단하게 만들기
* 간단할수록 저비용으로 고성능을 만들기가 쉽다.

## 2. 메모리 용량이 작은 것이 빠르다
* 메모리 용량을 작은 레지스터를 최대한 활용하는 것이 성능 향상에 도움이 된다.

## 3. 공통 케이스는 빠르게 만들기
* 자주 사용하고 비중이 높은 연산은 빠르게 처리하도록 만드는 것이 성능 향상에 좋다.

## 4. 좋은 디자인을 위해 최대한 통일하기
* 명령어의 포맷 가짓수는 최대한 줄이고 통일하는 것이 좋다. 
* 포맷이 다르면 디코딩 하는 데 복잡해지고 이것은 성능 하락으로 이어지기 때문이다. <br><br><br>

# Operations of the Computer Hardware
## Arithmetic Operations (산술연산)
* `register` 간 연산으로 `RISK` 프로세서 방식
* `add`와 `subtract`, 더하기와 빼기로 이루어져 있으며 피연산자 3개가 필요하다.

```
add a, b, c
```

* 위와 같이 쓰면 `b`와 `c`를 더한 값을 `a`에 저장해라는 의미<br><br><br>

# Operands of the Computer Hardware
## Register Operands
* 자주 사용하는 데이터에 빠르게 접근하기 위해서 레지스터를 사용한다.
* 32개의 `bit`로 이루어져 있으며 `word`라 부른다.
* `MIPS`는 32개의 `32bit` 레지스터 파일을 가지고 있다.

## Byte Addresses
* 대부분의 아키텍처는 `byte` 단위로 메모리를 관리한다.
* `word`는 `4bytes`로 이루어져 있으며 이것은 하나의 명령어 단위가 된다.
* 레지스터에 있는 데이터를 메모리에 저장할 때 자리수가 큰 게 최하위 비트(LSB)에 오면 `Big Endian`, 자리수가 제일 작은 것이 최하위 비트에 오면 `Little Endian`이라 한다.

## Memory Operands
* 메인 메모리는 자료의 집합을 이용한다.
* 산술 연산을 하기 위해서 메모리에 접근할 수 있는 명령어가 지정되어 있다.(`Load/Store`)
* 메모리는 `8bit` 크기의 주소로 이루어져 있다.
* 모든 명령어의 크기는 `4bytes`이기 때문에 메모리 주소 또한 `4bytes` 간격으로 나열되어 있다.
* `MIPS`는 빅 엔디안 방식을 사용한다.

## Registers vs. Memory
* 레지스터가 메모리에 접근하는 것 보다 훨씬 빠르다.
* 그래서 메모리 접근을 최대한 줄이고 레지스터에서 연산하는 것이 성능 향상에 좋은데 그렇다고 너무 레지스터만 써도 성능이 떨어지니까 자주 쓰지 않는 데이터는 메모리로 내려주는 것이 좋다.
* 한 주소는 `32bit`로 이루어져 있는데 레지스터 하나는 `5bit` 크기이기 때문에 메모리에 접근하는 것 보다는 레지스터를 최대한 사용하는 것이 한 번에 처리할 수 있는 코드가 많아진다.

## Immediate Operands
* 피연산자 중에 하나가 상수일 때 사용하는 명령어

```
addi $s3 , $s3, 4 // 동작은 add와 같음
addi $s2, $s1, -1 // 뺄셈은 -1 사용
```

* 상수를 레지스터에서 만들어 쓰지 않으면 메모리에 접근해서 가져와야 하는데 이러면 느리다.
* 그래서 0 같이 자주 사용되는 상수는 메모리에 접근할 필요 없이 레지스터에서 바로 연산하면 훨씬 빠르다.

## Constant Zero
* `$zero`라고 표시하며 `read only`로만 사용할 수 있다.
* 주로 레지스터간 `move`연산을 할 때 사용하는데 

```
add $t1, $s1, $zero
```

* `move`와 같은 명령어를 따로 만들어서 사용하는 것 보다 `add`연산을 하는데 나머지 연산자를 0으로 만들어서 사용하면 `move/copy`와 같은 효과를 낼 수 있어서 명령어를 따로 만들지 않고 이렇게 쓴다.
* 왜냐면 명령어 셋은 최대한 간단한 것이 성능 향상에 좋기 때문이다.
* 어떤 특정 연산 처리만을 위한 명령어를 많이 만들어 쓰다 보면 구현 자체도 쉽지 않지만 구현해도 그 명령어를 처리하는 시간이 다른 쉬운 명령어보다 늘어나는데, 그 늘어난 시간은 다른 간단한 명령어의 실행 시간에도 영향을 미쳐서 다 같이 느려진다.<br><br><br>

# Logical Operations
## 시프트 연산자
* 왼쪽 시프트
    * 시프트하면서 생기는 빈 비트는 0으로 채운다.
    * 원래 값에 2^i 을 곱한 효과(음수, 양수 둘 다 적용)
* 오른쪽 시프트
    * 시프트하면서 생기는 빈 비트는 0으로 채운다.
    * 원래 값을 2^i 만큼 나눈 효과(양수에만 적용됨)
    
## 비트 연산자
* `and`, `or`, `nor` 연산자를 사용한다.
* `MIPS`에는 NOT 연산자가 없기 때문에 대신 `nor` 연산자(a도 아니고 b도 아니다)를 사용해서 NOT 연산자와 같은 효과를 낸다.<br><br><br>

# Instructinos for Making Decisions
## Conditional Operations
* 어떤 조건이 `true`인 경우에 이름지어져 있는 명령어로 분기를 나누고 `false`라면 다음 명령어를 계속 실행하는 것 (if ~ else문)

```
beq rs, rt, L1 // rs와 rt가 같으면 L1에 있는 명령어 실행
bne rs, rt, L2 // rs와 rt가 같지 않으면 L1에 있는 명령어 실행
j L1 // 무조건 L1으로 Jump하는 것
```
* 어떤 수들의 대소관계 비교도 전용 명령어를 따로 만들지 않고 `beq`를 비롯한 여러 명령어들을 조합해서 쓰는 것이 성능 면에서 더 좋기 때문에 조합해서 쓴다.<br><br><br>

# 명령 실행 단계
1) `caller`가 `callee`에게 파라미터를 넘긴다.
2) `caller`가 `callee`에게 제어권을 넘긴다.(실행)
3) `callee`가 스택에 메모리를 할당한다.
4) `callee`가 태스크를 수행한다.
5) `callee`가 `caller`가 접근할 수 있는 곳에 결과를 둔다.
6) `callee`가 `caller`에게 제어권을 넘긴다.<br><br>

* `Procedure` 실행에는 `Leaf`와 `Non-Leaf` 방식이 있는데 `Leaf`는 자기 자신을 포함한 어떤 함수도 호출하지 않는 것이고 `Non-Leaf`는 자기 자신을 포함한 함수를 호출하는 것이다. 
* 프로그래밍 할 때 흔히 작성하는 값 하나를 리턴하고 끝나는 함수는 `Leaf` 방식이고 재귀 함수와 같은 형태는 `Non-Leaf`로 이루어진다.

## 메모리 영역
* `Text` : 프로그램 코드(명령어)가 있는 영역
* `Static data` : 전역 변수가 있는 영역
* `Dynamic data` : `heap` 영역이라고도 하며 동적으로 할당된 메모리가 있는 영역. 메모리 주소를 가리키는 포인터는 아래에서 위로 이동한다.
* `Stack` : 함수가 호출되면 생기는 지역 변수가 있는 영역. 메모리 주소를 가리키는 포인터는 위에서 아래로 이동한다.<br><br><br>

# 코드가 실행되는 과정
1) 프로그래밍 언어로 프로그램을 작성한다.
2) 컴파일러가 어셈블리어로 번역한다.
3) 어셈블러가 기계어로 번역한다.
4) 기계어로 번역하면서 내가 쓴 코드를 이용해서 만든 기계어 오브젝트와 라이브러리에서 가져오는 코드로 만든 오브젝트가 생기는데 링커가 두 오브젝트 코드들을 합쳐서 실행파일로 만든다.
5) 로더가 실행파일을 메모리에 올려서 실행상태로 만든다.<br><br><br>

# 알고리즘과 수행속도
* 명령어 수와 `CPI`가 낮은 것이 무조건 성능이 좋은 것은 아니다. 성능에 영향을 미치는 것은 여러가지 요인이 있다.
* 컴파일러 최적화는 알고리즘에 영향을 많이 받는다.
* 그렇기 때문에 뭐니뭐니해도 알고리즘이 효율적이어야 성능이 좋아진다.<br><br><br>

# 배열과 포인터
* 둘 다 배열을 다룰 때 사용할 수 있지만 배열 인덱스에 접근하려면 내부적으로 인덱스의 주소값을 계산하는 과정이 필요하다. (시작 주소에서부터 몇 칸 떨어져 있는지...)
* 하지만 포인터는 그런 연산이 필요없이 그냥 4씩 더해주면서 다음 메모리 주소로 이동하면 된다.
* 그렇지만... 최신 컴파일러는 내가 직접 포인터 연산하는 코드를 쓰는 것과 배열 인덱스로 접근하는 코드가 같은 성능을 낼 수 있도록 최적화를 다 해 준다.
* 그래서 같은 동작을 수행하는 코드라면 배열 인덱스를 사용하는 코드를 써도 무방하며 포인터를 사용한 코드보다 이해하기도 더 쉽다. 포인터에 비해 버그를 일으키는 코드를 작성할 확률도 줄어드니까 그냥 배열을 쓰자.<br><br><br>

# x86 Instructions
* `MIPS`와는 명령어 셋이 다르며 설계 면에서도 차이가 있다. 
* `MIPS`에 비해 다소 복잡하게 설계되어 있어 고성능으로 만들기 어려운 `CISK` 아키텍처다. 
* 그래서 고성능을 내기 위해 하드웨어가 내부적으로 복잡한 원래 명령어를 간단한 명령어들로 쪼갠 다음에 실행하는 방식을 쓴다.(결국 `RISC`와 같은 매커니즘으로 실행되게 된다고 볼 수 있다)
* 이렇게 보면 인텔은 진작에 망했어야 할 거 같지만 시장 점유율을 성공적으로 높이면서 자리잡았기 때문에 인텔 프로세서에서 실행되는 프로그램들이 많다보니 여전히 높은 점유율을 차지하며 지금까지 오고 있는 것이다.<br><br><br>

# 결론
* 명령어 여러 개를 한꺼번에 처리하면 효율적이겠지만 그만큼 하드웨어 게이트(로직) 수가 많아지면서 실행 속도가 느려진다. 그리고 다른 명령어도 같이 느려진다.
* 그래서 간단한 명령어를 여러개 조합해서 쓰는 것이 효율적이다. (`RISK Processor` 철학)
* 어셈블리 코드를 쓰면 기계어와 가까워서 좋은 성능을 낼 수 있지만 최신 컴파일러는 `C` 언어와 같은 고급 언어로 쓴 코드도 어셈블리어와 비슷한 성능을 낼 수 있도록 최적화를 다 해 주기 때문에 그냥 고급 언어를 쓰는 것이 생산성이 더 높고 좋다. (어셈블리어는 생산성이 낮다)
***************************************

# 출처
* [KOCW 영남대학교 최규상 교수님 공개강의](http://www.kocw.net/home/search/kemView.do?kemId=1388791&ar=relateCourse)
