### starvation problem

- 처리 되어야 할 프로세스가 우선순위가 낮아 CPU로 부터 처리가 되지 않는 상황

### Convoy effect

- 소요기간이 긴 프로세스가 먼저 CPU에 점유되어 있어서 다른 프로세스가 실행되지 못하는 상황

### Longest job first scheduling algorithm

- 버스트 타임이 가장 긴 프로세스 먼저 처리하는 스케줄링
- 비선점 스케줄링이다.
- 우선순위 스케줄링이다.

### Longest remaining time first scheduling algorithm

- 남은 버스트 타임이 가장 긴 프로세스를 먼저 처리하는 스케줄링
- 선점 스케줄링이다.
- 우선수위 스케줄링이다.

### Round robin scheduling algorithm

- 모든 프로세스를 일정한 시간만큼 돌아가면서 처리한다. (먼저 들어온 순서대로)
- 오늘날 OS에서 가장 흔히 사용된다.
