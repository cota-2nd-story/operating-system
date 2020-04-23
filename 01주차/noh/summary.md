
### Program은 hard disk에 저장된다.
- 프로그래밍 언어로 작성된 코드가 있다.
- 이 코드를 컴파일러가 binary code로 컴파일한다.
    - 컴퓨터는 binary code만 이해할 수 있기 때문이다.
- 컴파일된 코드는 hard disk에 저장된다. 

### 우리가 Program을 열면 생기는 일
- .exe 파일을 실행한다.
- CPU는 해당 파일의 해당하는 프로그램을 RAM에서 찾는다.
- RAM에서 존재하지 않으면 Hard disk에서 찾는다.
- Hard disk에서 해당 Program을 복사한다.
- 복사된 Program을 process라고 부른다.
- Process는 RAM으로 이동된다.
- CPU가 Process를 line-by-line으로 읽어 실행한다.



### Process state 
- 프로그램을 실행한다.
- 프로세스가 생성된다. (new state)
- 프로세스는 RAM으로 옮겨진다.
- 프로세스는 CPU에게 읽혀질 준비가 되었다. (ready state)
- CPU는 프로세스를 line-by-line으로 읽으며 실행한다 (Running state)
- I/O의 수행을 처리 할 수도 있다. (I/O state)
- 모든 처리가 끝나면 프로세스는 RAM에서 제거된다. (Terminated state)


### 프로세스는 프로그램 실행에 필요한 명령어들과 실행할 때 필요한 데이터 영역을 가지고 있다.
- 프로세스는 stack, heap, global variables, program 영역으로 이루어져 있다.
- stack은 함수 호출 시 생성되는 데이터가 저장된다.
- heap은 동적으로 필요시에 생성되는 데이터가 저장된다.


### OS
- 컴퓨터의 전원을 키면 Hard disk에 있는 운영체제가 복사되어 RAM으로 옮겨진다.
- 운영체제는 자원을 관리한다.
- 자원은 CPU, MEMORY, I/O Device, ... 등이 있다.
    - CPU는 process를 읽어들어 실행한다.
    - Memory는 여러가지 데이터를 저장한다.
    - I/O Device 는 사용자의 입력을 받거나 데이터를 출력해준다.
- Process의 schedule 을 관리한다. 
    - CPU가 하나의 Process만 실행하면 다른 Process는 실행되지 않기 때문이다.
    - CPU는 여러 Process를 번갈아 가면서 실행할 수 있다.
    - process가 정지 되었다가 다시 실행 될 때, 어디까지 실행되었는지를 알아야 한다.
    - 해당 정보는 PCB 라는 곳에 저장된다.

### PCB
- 프로세스가 생성될 때 만들어진다.
- 운영체제가 프로세스의 정보를 저장해 놓는 곳이다.
- process가 인터럽트 되었다가 다시 실행 될 때, 어디까지 실행되었는지를 기억하여 실행에 차질이 없도록 하는 역할을 한다.
    - 어느 코드부터 실행해야 하는지는 Program counter라는 레지스터에 저장된다.
    - 사용중이었던 file, device 들을 기억하는 영역도 존재한다.
- PCB는 Kernel stack에 저장된다.

### Kernel
- CPU를 제어하는 Software이다.
- CPU, Memory, devices, application 들과 연결되어 있다.
- 이 자원들에 대한 접근을 중재한다.
- 운영체제에서 가장 중요한 역할을 한다.
- 입출력을 관리한다.
- 소프트웨어의 요청을 받는다.
- 요청을 CPU가 처리할 수 있도록 변환한다.
- 많은 프로그램들 중 어느것이 CPU에 할당되어야 하는지 결정할 책임이 있다. (scheduling)

### I/O device
- 입 출력 장치에는 Buffer가 있다.
- RAM에서 입, 출력을 기다리는 프로세스가 있다면 Buffer를 통해 데이터가 전달된다.

