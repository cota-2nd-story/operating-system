# Starvation



- ready 상태의 프로세스가 CPU를 무기한 할당받지 못하는 문제를 말한다.
  - 예를 들어, SJF 스케줄링 알고리즘에서 job의 길이가 긴 프로세스는 상대적으로 job의 길이가 짧은 프로세스에게 우선순위가 밀려 CPU 할당이 계속 미뤄지게 될 수 있다. (waiting indefinitely)
- 어느 우선순위 기반 스케줄링 알고리즘은 starvation 문제에 놓일 가능성이 있다.
  - 선점 / 비선점이든 상관없이 우선순위에서 밀리는 프로세스가 계속 starvation 상태에 놓일 수 있다.
- FCFS 스캐줄링 알고리즘은 starvation 문제에 놓이지 않는다.
  - 왜냐하면 이는 우선순위 기반 스케줄링이 일어나지 않고 먼저 온 순서대로 처리되기 때문이다.



# Convoy Effect



- 작은 프로세스 (작은 프로세스란, 매우 작은 처리 시간을 갖고 있는 프로세스를 말한다.)가 현재 처리되고 있는 매우 큰 프로세스 작업이 끝나기를 기다리는 현상을 말한다.
- 이 현상은 다른 알고리즘과 비교하여 높은 Waitiing Time과  TAT(Turn-around Time)을 야기할 수 있다.
  - TAT에는 WT가 들어가기 때문에 WT가 증가하면 당연히 TAT가 증가한다.
- Convoy Effect는 비선점 스케줄링 알고리즘에서만 발생한다.
  - 비선점 스케줄링 알고리즘은 현재 CPU 할당을 받은 프로세스가 있다면 RAM에 있는 다른 프로세스는 반드시 해당 프로세스 처리가 완료된 이후에 CPU를 할당받을 수 있다.
  - 그렇기 때문에 RAM에 매우 짧은 처리 시간을 갖는 프로세스가 있더라도 현재 CPU에 처리되고 있는 프로세스가 매우 긴 처리 시간을 갖는다면 그 시간만큼 반드시 기다리게 된다.
  - 그러나 선점 스케줄링 알고리즘에서는 새로운 프로세스가 RAM에 할당될 때마다 현재 처리 중인 프로세스와 새로운 프로세스간의 우선순위를 비교하고 새로운 프로세스가 더 높은 우선순위를 갖는다면 Context Swiching이 발생한다.
  - 그래서 선점 스케줄링 알고리즘(LRTF 제외)에서는 아무리 큰 프로세스가 CPU를 점유하고 있더라도 언제든지 CPU 할당은 다른 프로세스로 바뀔 수 있기에 Convoy Effect가 발생하지 않는다.



# Throughput



- 특정 시간에 처리(실행)된 프로세스의 갯수
- 프로세스의 갯수 / 스케줄 길이
- Throughput이 높다는 것은 컴퓨터 효율이 더 높다는 뜻이다.
  - 특정 시간내에 처리된 프로세스의 수가 더 많다는 뜻이기 때문
  - 여러개의 프로세스가 모두 처리되기까지는 어떤 스케줄링 알고리즘이 적용돼도 동일할 것. 그러나 특정 시간을 기준으로 더 많은 프로세스가 처리됐다면 사용자에게 더 많은 일을 했다고 나타낼 수 있다.
- FCFS은 SJF보다 Throughput이 더 작거나 같다.
  - 모든 프레세스가 모두 처리된 시점에는 Throughput이 같지만 그 외 시간에는 SJF가 더 높은 수치를 가지게 된다. 동일 시간 내에 더 짧은 처리 시간을 갖는 프로세스에 CPU를 할당하는 것이 더 많은 프로세스를 처리할 수 있기 때문이다.
- 당연히 SRTF 스케줄링 알고리즘이 제일 높은 Throughput을 가진다.
  - 프로세스가 RAM에 새롭게 적재될 때마다 가장 짧은 처리 시간을 갖는 프로세스를 처리하기 때문에 비선점의 SJF보다도 더 높은 Throughput 값을 갖게 된다.



# Longest Job First Scheduling Algorithm



- RAM에 적재된 프로세스들 중에서 가장 긴 처리시간 (Execution Time / Burst Time)을 갖는 프로세스에게 CPU를 할당하는 알고리즘.
- 비선점 스케줄링 알고리즘이다.
- 우선순위 기반 알고리즘이다.
- Disadventages
  - Starvation
    - 처리시간 기반의 우선순위를 가지고 스케줄링일 하기 때문에 Starvation이 존재
  - Convey Effect
    - 긴 처리 시간을 갖는 프로세스가 우선으로 처리되기 때문에 상대적으로 짧은 시간을 갖는 프로세스의 Waiting Time이 길어질 수 있다.
  - Less Throughput
    - 비선점 스케줄링 알고리즘이면서 동시에 긴 처리시간을 우선으로 처리되기 때문에 SJF나 SRTF 알고리즘에 비해 동일 시간 Throughput이 매우 낮을 수 밖에 없다.
  - Practically very difficult implementation
    - 기본적으로 Burst Time을 예상하는 것은 매우 어려운 일인데 이를 우선순위로 계산되어야하는 알고리즘에 대해서는 구현자체가 어렵다.
    - LJF 또한 프로세스의 처리시간 BT 기반으로 처리되는 알고리즘이기 때문에 BT 계산에 대한 어려움이 존재한다.



# Longest Remaining Time First Scheduling Algorithm



- LJF의 선점 알고리즘 형태다.
- Disadvantage
  - Starvation 이 존재
    - 프로세스의 처리시간 BT를 기준으로 우선순위를 매기기 때문에 CPU를 무기한 할당받지 못하는 프로세스가 발생할 수 있다.
  - Convoy Effect
    - 선점 스케줄링 알고리즘에는 대게 나타나지 않지만 LRTF는 특징이 처리시간이 긴 프로세스가 우선으로 처리되기 때문에 상대적으로 작은 프로세스들의 WT가 길어질 수 있다.
  - Less Throughput
    - 프로세스의 긴 처리시간이 우선적으로 처리되기 때문에 동일 시간 처리된 프로세스의 갯수가 낮을 수 밖에 없다.
  - Practically difficult to implementation
    - 프로세스의 BT를 계산하는거 자체가 아렵기 때문
- 만약 RAM에 있는 프로세스의 BT가 같다면 도착한 시간이 빠른 순으로 처리된다. (BT가 같을 시 FCFS 알고리즘이 적용)
- LRTF의 간차트를 보면 다른 알고리즘과는 다르게 매 time unit 마다 우선순위 비교가 이뤄진다.
  - 그 이유는, LRTF의 우선순위는 남아있는 BT가 기준이 되기 때문에 한번 처리될 때마다 BT 값이 변하기 때문이다.
  - 비슷한 SRTF 알고리즘에서는 time unit이 지남에 따라 BT가 변해도 그 값은 줄어들기 때문에 BT가 가장 짧았던 프로세스는 계속 가장 짧은 BT로 남게된다. 그래서 매 time unit 마다 우선순위 비교가 아닌, 새로운 프로세스가 RAM에 적재될 때 마다 우선순위 비교가 이뤄진다.



# Round Robin Scheduling Algorithm



## Time Quantum

- 프로세스가 다른 프로세스에 의해 선점되지 않고 처리될 수 있는 최대 시간

## Round-robin Scheduling Algorithm

- Time Quantum + FCFS
  - 프로세스는 RAM에 적재된 순서대로 처리되는데 일정 시간 Time Quantum 처리된 후 다음 프로세스가 처리된다.
  - 일정 시간이 지나면 해당 프로세스는 CPU가 헤재되며 다음 차례의 프로세스가 처리되는데 그 역시 일정시간동만 진행된다. 이렇게 CPU가 헤제된 프로세스들은 queue에 저장되며 queue에 저장된 순서대로 CPU에 의해 돌아가며 처리된다.
  - 처리가 완료된 프로세스는 queue에 저장되지 않는다. → 더 이상 처리될 필요가 없기 때문
  - 프로세스가 queue에 저장되면 이후 스케줄러가 CPU를 할당할 때의해 해당 프로세스를 queue에서 지우는데, 처리가 완료된 프로세스가 queue에 저장되면 이미 완료된 프로세스에 대한 스케줄링이 이뤄지게 되어 불필요한 행위가 발생하게 된다.
- RR 알고리즘은 Time Quantum을 기반으로 동작한다.
- Queue 자료구조를 사용한다.
- 가장 유명하고 오늘날 많은 OS에서 사용하는 알고리즘이다.
- TQ가 증가할 수록
  - Context Switching이 감소한다.
  - Response Time이 증가한다. → 좋지 않은 현상
    - 프로세스가 CPU에 의해 처리되기까지의 시간 (Response Time)이 길어질수록 프로세스가 늦게 반응하는 것이기 때문

### Advantages of RR Scheduling Algorithm

- Starvation 문제가 없다.
  - RR은 우선순위 기반으로 돌아가는 알고리즘이 아니라 FCFS 기반으로 돌아가기 때문에 Starvation이 존재하지 않는다. (with Time Quantum)
- Convoy Effect가 없다.
  - 여러 프로세스들이 일정 시간 Time Quantum 마다 처리되기 때문에 작은 프로세스가 큰 프로세스가 처리되기까지 기다리는 현상이 발행하지 않는다.
- Practically Implementable
  - 프로세스별 BT를 계산하는 로직이 필요없기 때문에 구현이 복잡하지 않다.

### Limitation of RR Scheduling Algorithm

- SJF, SRTF만큼 Throughput이 좋지 않다.
  - 일정 시간 Time Quantum 마다 프로세스가 실행되기 때문에 작은 프로세스 먼저 처리하는 알고리즘에 비해 Throughput이 좋을 수 없다.