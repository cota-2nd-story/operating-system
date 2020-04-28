### 스케줄러는 OS의 code이다.

### process와 관련된 시간
* arrival time
    * 하드디스크에서 RAM으로 옮겨진 시간
* burst time
    * CPU에 의해서 실행되는 시간
* completion time
    * 실행이 종료되어 RAM에서 제거된 시간
* turn around time
    * Arrival time에서 부터 completion time 까지의 시간
* waiting time
    * RAM에서 CPU로 부터의 실행을 기다리는 시간
* response time
    * Arrival time에서 CPU로 부터의 실행을 기다리는 시간
* i/o time
    * I/O의 처리를 기다리는 시간

### process의 상태를 바꾸는 3가지 스케줄러

* long term scheduler
    * 하드 디스크에서 RAM으로 프로세스를 이동시킨다. (new -> ready)
* short term scheduler
    * ready 상태의 프로세스들 중에 어떤 프로세스를 실행 시킬지 결정한다. (ready -> running)
* medium term scheduler
    * 실행되지 않으면서 메모리만 차지하는 프로세스를 hard disk로 옮긴다. (swap-out)
    * 나중에 실행할 수 있을 때 다시 메모리로 가져온다. (swap-in)

### 선점 스케줄링과 비선점 스케줄링
* 실행중인 프로세스가 끝나지 않았음에도 다른 프로세스를 실행 시킬 수 있으면 선점 스케줄링, 없으면 비선점 스케줄링이다.

### cpu가 실행할 프로세스를 정하는 스케줄러
* shortest job first 
    * burst time이 가장 작은 프로세스를 실행시킨다.
    * 비선점 스케줄링이다.
    * 우선순위 스케줄링이다.
* shortest remaining time first
    * 현재 남은 burst time이 가장 작은 프로세스를 실행시킨다.
    * 선점 스케줄링이다.
    * 우선순위 스케줄링이다.
* first come first served
    * arrival time이 가장 작은 프로세스를 실행시킨다.
    * 비선점 스케줄링이다.
    * 비 우선순위 스케줄링이다.