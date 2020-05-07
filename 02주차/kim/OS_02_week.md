# Types of Scheduler, Context Switching



## Context

프로세스는 각각 PCB와 그와 관련된 속성들을 가지고 있다. Process Id, Program Counter 등등이 이에 속한다. 이렇게 프로세스와 더불어 PCB, 속성들을 합쳐서 하나의  Context라고 부른다.

## Swapping

RAM에 저장될 수 있는 프로세스의 갯수가 총 3개라고 할 때,

현재 P1, P2, P3 3개의 프로세스가 RAM에 저장되어 있다고 가정해보자.

즉, RAM이 수용할 수 있는 프로세스의 양이 꽉 찬 상황이다.

여기서 각각의 프로세스는 우선순위라는 속성 값을 숫자로 가지고 있다. 숫자가 높을 수록 우선순위가 높다고 볼 수 있는데, 만약 하드디스크에서 new state 인 프로세스 P4가 생성되는 상황을 가정해보자.

1. 그렇다면 RAM에 P4 적재할 공간이 있는지를 확인할 것이다.
2. 그러나 P1, P2, P3 총 3개의 프로세스가 이미 모든 RAM 공간을 차지하고 있어 그냥 적재는 불가능하다.
3. 그래서 우선순위를 보고 결정하게 된다.
4. P4가 현재 RAM에 적재된 프로세스들보다 더 높은 우선순위를 갖는다면 우선순위가 낮은 프로세스가 다시 하드디스크로 옮겨지고 그 자리에 새로운 프로세스 P4가 저장된다.

여기서 하드디스크로 옮겨진 프로세스가 P3이었다면 P4는 SWAP-IN이 되었고 P3 SWAP-OUT이 되었다고 말한다.

## Context Switch

CPU에 할당받는 프로세스가 바뀌는 과정을 이야기한다.

만약 현재 P1이 CPU에 의해 처리되고 있었는데, 더 우선순위가 높은 P2가 하드디스크에서 생성되고 RAM에 적재된다고 가정해보자.

그러면 P1보다 더 높은 우선순위의 프로세스가 RAM에 등장했기 때문에 CPU 할당을 변경해야한다. 다시말해, P2에 CPU를 할당해야한다. 우선순위가 더 높은 프로세스가 처리되는 것이 옳기 때문이다.

이 상황에서 기존에 처리되고 있던 P1에 대한 정보들을 어딘가에 저장해야한다. 왜냐하면 P2 프로세스 처리 완료 이후 다시 P1을 처리해야하는데 어디까지 처리했고 어디서부터 처리해야하는지 알아야하기 때문이다. 즉, P1에 대한 Context를 저장하고 P2에 대한 Context 정보들로 CPU 처리를 하게 된다. 이렇게 한 프로세스애 대한 Context 정보가 저장되고 다른 프로세스의 Context 정보로 처리가 변경되는 과정을 Context Switch라고 한다.



# Various Times of Process



## Point in time vs Duration in time

- A라는 사람이 있다.
- 1 AM에 사무실에 도착했다.
- 그리고 3AM에 사무실을 떠났다.
- A 사람이 사무실에 도착한 1AM과 사무실을 떠난 3AM을 point in time이라 볼 수 있다.
- A 사람은 1AM부터 3AM까지 2시간동안 사무실에서 일을 했다.
- A 사람이 일한 2시간의 시간을 duraction in time이라 한다.
- Arrvival Time
  - 프로세스가 HD에서 RAM으로 적재된 point in time을 뜻한다.
- Burst Time (= Execution Time)
  - CPU를 할당받아 처리되는 duration time을 뜻한다.
- Completion Time
  - 프로세스가 CPU에 의해 완전히 처리되기까지의 point in time을 뜻한다.
- Turn-around Tim
  - 프로세스가 RAM에 적재되고나서부터 CPU에 의해 완전히 처리되기 까지의 duration in time을 뜻한다.
  - Completion Time - Arrival Time
  - Burst Time + I/O Time + Waiting Time
- Waiting Time
  - CPU에 의해 처리되던 P1이 더 우선순위가 높은 P2의 등장으로 Context Switch 가 발생하여 P2가 CPU에 의해 처리될 때 P1은 wait state가 되고 P2가 처리되고 다시 P1이 CPU 할당을 받기 까지의 duration time을 뜻한다.
- Response Time
  - RAM에 프로세스가 적재된 후로부터 CPU할당을 받기까지의 시간을 뜻한다.
- I/O Time
  - I/O 데이터를 input 하거나 output 하는 duration time을 뜻한다.



# Types of Scheduling Algorithms



## Process State

- ready state
  - RAM에 적재돼있고 CPU에 처리되고 있지 않는 프로세스의 상태. 또한 I/O 이벤트를 기다리고 있지도 않는 상태다.
- I /O state
  - I/O 이벤트를 기다리고 있는 프로세스의 상태
- running state
  - CPU에 처리되고 있는 프로세스의 상태

## Preemptive Scheduling Algorithms

더 우선순위가 높은 프로세스가 생기면 현재 CPU를 점유하고 있는 프로세스가 멈추고 우선순위가 더 높은 프로세스가 CPU를 점유하는 알고리즘을 말한다.

## Non-Preemptive Scheduling Algorithms

이 알고리즘은 P1, P2, P3가 RAM에 적재되어있고 P1이 CPU에 의해 처리되고 있을 때 P1보다 더 우선순위가 높은 P4가 하드디스크에서 RAM에 적재되어도 이미 처리되고 있던 P1이 해제되지 않고 완전히 처리될 때 까지 CPU를 점유하는 것이 특징이다.

- 현재 P1이 running state 라고 가정해보자.

- P2, P3는 ready state이고 P4는 I/O state다. 그리고 P4 가 P2, 3보다 우선순위가 높다.

- P1이 완전히 처리되기 전까지는 그 외 다른 프로세스는 CPU에 의해 처리될 수 없다.

- 여기서 P1이 완전히 처리가 된 후 RAM에서 제거된다면 누가 CPU를 할당받을까?

  → **P4라고 생각할 수 있지만 그렇지 않다. P4는 I/O 이벤트를 기다리고 있기 때문에 이 상태가 끝날 때 까지 CPU를 할당받지 않는다.**

- 즉, 스케줄러 알고리즘은 오로지 ready state 의 프로세스가 대상이 된다. I/O state 의 프로세스는 block 된다.

  - I/O state를 Blocked state라고 한다.



## Shortest Job First Scheduling Algorithm

- 가장 짧은 처리 시간을 갖는 프로세스가 CPU를 할당받는 알고리즘이다.

- Non-preemptive scheduling algorithm

- priority based algorithm

  - 짧은 처리 시간을 갖는 프로세스는 높은 우선순위 값을 가질 것이고 긴 처리 시간을 갖는 프로세스는 낮은 우선순위 값을 갖게 된다.

- 처리시간이 우선순위의 기준이기 때문에 RAM에 적재된 AT이 아무리 이르더라도 비선점적이기 때문에 이후에 도착한 더 높은 우선순위 (더 짧은 처리 시간)을 갖는 프로세스들에 의해 처리 순서가 뒤로 밀려날 수 있다는 단점이 있다.

- 즉 처리시간이 높은 프로세스는 TAT가 커질 수 있다.

  → Waiting Time이 커질 수 있기 때문

- 만약 먼저 RAM에 적재된 (먼저 도착한) 프로세스가 처리시간이 매우 긴 경우에도 프로세스 처리가 비효율적으로 이어질 수 있다.

  - 우선순위에 의해 결정되는 스케줄링이지만 RAM에 적재됐을 때 다른 프로세스가 없다면 처리시간에 상관없이 먼저 도착한 프로세스가 CPU에 처리되는데 그 시간이 매우 길다면 비선점 방식이기 때문에 그 뒤에 도착한 매우 짧은 처리시간을 갖는 프로세스들의 Waiting Time이 커지기만 한다.



## SRTF Scheduling Algorithm

- Preemptive Algorithms
- Preemptive version of SJF
- 현재 처리되고 있던 프로세스가 있더라도 우선순위가 더 높은 프로세스가 RAM에 적재된다면 더 우선순위가 높은 프로세스가 CPU를 할당받고 처리된다.
- 같은 우선순위를 갖는 프로세스가 RAM에 적재되어있을 때 CPU를 할당하는 방식에 대해서는 구체적은 룰은 없다. → 추가 확인 필요

비선점 스캐줄링 알고리즘에서 Response Time은 Waiting Time과 같다.

- Response Time
  - 프로세스가 CPU 할당을 받은 시간 - Arrival Time(RAM 도착, 적재 시간)
- 프로세스가 CPU를 할당받으면 완료될때까지 Context Switch가 발생하지 않기 때문

그러나 선점 스캐줄링 알고리즘에서는 이는 true가 아니다.



## FCFS Scheduling Algorithm

- 가장 빨리 도착한 프로세스가 가장 빨리 처리된다.
- 비선점 스캐줄링 알고리즘이다.
- 우선순위 값을 이용하지 않는다. → 우선순위 값과 관계없이 RAM에 적재된 순서대로 프로세스가 처리되기 때문

### FCFS with Context Switching  Overhead

- context switching overhead = 1 time unit
- 컨텍스트 스위칭되는 시간은 1 기본 시간 단위다. (millisecond)
- CPU Efficiency  = Useful Time / Total Time
  - Useful Time
    - 실제 CPU가 프로세스를 처리한 시간
    - Context Switching Time은 CPU가 Idle 상태의 시간이다. 즉, 일을 하고 있지 않은 시간 → Unuseful Time
  - Total Time
    - RAM에 적재된 모든 프로세스가 CPU에 의해 처리 완료되는 시간
    - CPU가 일을 하고 하지 않는 시간 모두를 포함한다.
- CPU Inefficiency Time = CPU Idle Time / Total Time
  - CPU Idle Time
    - 컨텍스트 스위칭이 일어나는 시간과 같이 CPU가 일을 하지 않는 시간