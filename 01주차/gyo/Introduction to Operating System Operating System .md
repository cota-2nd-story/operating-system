# Introduction to Operating System / Operating System Concepts

### Computer System

- CPU
- Memory: RAM, HDD, Cache, Register

### 왜 Memory에 다양한 레벨이 존재하는가?

각 레벨의 메모리들은 목적을 가지고 그에 맞는 특징을 가지고 있다. 각 메모리에 대해서 알아보면 ...

- **RAM**: Random Access Memory. 휘발성이기 때문에 파워가 off되면 메모리에 남아 있는 내용을 삭제한다. HDD에 상대적으로 빠르며 비싸다.
- **HDD**: Hard Disk. 비휘발성 메모리이며 따라서 반영구적으로 데이터를 저장한다. RAM에 비해 상대적으로 느리며 저렴하다.
- **Cache**: CPU와 RAM 사이에 존재한다. CPU가 원하는 데이터를 RAM에 접근하지 않고 Cache에서 더 빠르게 가져다 사용할 수 있도록 하는 것이 목적이다. 작고 빠르며 비싸다.
- **Register**: CPU 내부에 존재하는 다양한 용도의 저장공간이다. 프로세서 내에서 매우 빠른 속도로 CPU의 동작을 돕는다. 보통 프로세서 외부에서 가져온 데이터를 레지스터에 저장하여 처리한다. 일반적으로 메모리 중 가장 빠르다.

### 프로그램(응용 프로그램)이 실행되는 과정

HDD에 program이 저장되어 있다. 

→ 사용자는 program을 실행하는 이벤트(액션)를 발생시킨다. 

→ HDD에 저장된 program을 copy&paste 하여 process를 생성한다. 

→ RAM에 process가 올라간다. → CPU는 RAM에 올라간 process를 fetch한다... line by line!

### CPU가 수행하는 Scheduling

- **Long-Term Scheduling**: CPU는 프로그램이나 데이터에 접근하기 위해 RAM을 들여다본다. 하지만 원하는 프로그램이나 데이터가 없으면 HDD의 프로그램을 프로세스로 RAM에 로드하게 되는데, 이를 Long-Term 스케줄링이라고 한다.
- **Short-Term Scheduling**: CPU가 RAM의 프로세스의 접근하는 것을 Short-Term 스케줄링이라고한다. Long-Term 스케줄링에 비해 Short-Term 스케줄링은 매우 빈번하게 일어난다.
- **Mid-Term Scheduling**: RAM에 올려진 프로세스가 CPU로 부터 fetch되지 않거나(ready, not running) 대기 상태조차 아닌 경우(asleep, not ready)에 프로세스를 하드디스크로 다시 돌려보낸다. 다만, 필요에 의해 하드디스크로부터 다시 가져올 수 있다.(관련 개념: 가상 메모리 - 하드디스크의 공간으로 RAM 메모리 확장하기)

위 scheduling을 위한 다양한 알고리즘이 존재하며 cpu는 알고리즘을 담은 function들을 가지고 있다!

### The spaces of RAM

OS의 프로그램도 RAM에 올라가 있다. 이 공간을 OS space라고 한다. 나머지 공간(Remaining space)을 user space라고 하며 응용 프로그램과 데이터들이 올라간다.

### Process vs Program

- **Process**: RAM에 올려져 CPU에 의해 실행되기 위해 HDD에 저장된 program이 copy&paste된 형태. 하나의 program에 복수개의 Copy 가 존재할 수 있다. 즉, 여러 개의 process가 발생 가능하다.(= Active Entity)
- **Program**: HDD에 저장되는 코드 뭉치.(machine code 형태로...) 프로그램.(= Passive Entity)

### State of a Process

1. **New State**: 프로그램으로 부터 copy 된 상태
2. **Ready State**: RAM에서 I/O Event를 Listen하는 상태(대기)
3. **Running State**: CPU에 의해 execute되는 상태. line by line!
4. **I/O State(Blocked State)**: 입출력이 발생하는 상태
5. **Terminated State**: Completely execution, then removed from RAM
6. **Suspend Ready State**
7. **Suspend Wait State**

### Degree of Multi Programming

RAM에 얼마나 많은 process가 올라갈 수 있는지에 대한 정도

*Degree of Multi Programming = Size of RAM / Size of a Single Process*

### Type of OS

- **Batch OS**: DMP = 1(a process in a RAM)
- **Multi Programming OS**: RAM에 1개 이상의 프로세스가 올려질 수 있는 경우. Multitasking과 관련.
- **Multi Processing OS:** CPU가 여러개이다. multiprocessor로 구성되어 있으며 parallel processing 형태로 처리한다.(동시에 여러 일을 한다... , concurrent processing: 번갈아가며 여러 일을 한다.)

### PCB(Process Control Block)의 구성

- Stack: 콜 스택, function과 data가 running 되기 위해 쌓이는 공간, 자료 구조, function 내부에 선언된 local variables가 존재하는 곳이기도 하다.
- Heap: dynamic allocation을 위한 공간, 자료 구조(e.g. c언어의 malloc(), calloc()을 이용한 동적 할당)
- Static Variables & Global Variables
- Program: function의 모음!

프로세스의 개수와 PCB의 개수는 같다!

### Process Attributes

- Process Id: 프로세스를 구분하는 Unique한 값
- Process Counter: the instruction number., 프로세스는 cpu가 가진 Scheduling Algorithm에 의해 우선 순위를 빼앗겨 running 도중에 중단 될 수 있다. 중단 된 프로세스가 다시 재개될 때 그 시작 지점. cpu 내부에 존재하는 register에 저장된다.
- Process State: 위에서 언급한 프로세스의 상태.
- General Purpose Registers: 모든 프로세스가 사용하는 variables를 저장하고 있는 register.
- List of open files: 프로세스가 read 중이던 file의 재개 지점(for remembering)
- List of open devices: 프로세스의 사용되던 device에 대한 정보
- protection: PCB 간에 Heap, Stack의 공유하지 않는다.