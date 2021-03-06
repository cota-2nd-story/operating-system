### 컴퓨터의 전원을 누르면 생기는 일

#### 1. 전원이 잘 공급되는지 확인
* CPU의 이전 값을 지운다.
* CPU 레지스터인 PC를 Main board에 있는 ROM에 설치되어 있는 BIOS의 부트 프로그램 주소 값으로 초기화 한다.
* BIOS에게 제어권을 넘긴다.

#### 2. BIOS 실행
* 컴퓨터를 키면 가장 먼저 실행되는 프로그램이다.
* CPU에 문제가 없는지 확인한다.
* POST(Power on Self Test) 과정을 수행한다. 
  * 주요 기본 장치들에 이상이 없는지 확인한다. (Fast boost 활성화 시 생략.)
* Hard Disk를 돌면서 부트로더를 찾는다.
* 부트로더의 이미지를 메모리의 0x7c00 어드레스로 복사한다.
* 부트로더에게 제어권을 넘긴다.
```
BIOS는 어디에 있는가?

Main board의 ROM에 각인(설치)되어 있는 프로그램이다.
```

#### 3. Boot Loader 실행
* MBR에 있는 Master boot code를 실행한다.

##### 3-1. 1차 Boot Loader 실행
* 1차 부트로더는 MBR이다.
* MBR에 Boot code를 실행한다.
* Boot code는 MBR에 있는 Partition을 읽어 그 데이터로 부팅을 한다. (2차 Boot Loader 실행)

##### 3-2. 2차 Boot Loader 실행
* MBR의 최대 용량이 부족하기 때문에 복잡한 운영체제를 위해서 필요하다.
* 2차 부트로더는 운영체제마다 다르다. (GRUB, SYSLINUX, LILO, BOOTMGR, NTLDR 등이 있다.) 
* 커널 압축 해제 후 메모리에 적재한다.
* 최종적으로 제어권을 운영체제의 커널로 넘겨준다

### 요약
* bios -> 1차 부트 로더 (부팅을 시작하기 위한 프로세스) -> 2차 부트로더 (진짜 부팅을 하는 부분) -> 커널을 로드


## 부록 (?)
##### Main board
* cpu, gpu, hard disk 등 여러 Hard ware를 꼽을 수 있는 기판이다.
* BIOS가 설치되어 있는 ROM은 Main board의 일부이다.
##### POST (Power on Self Test)
##### 0x7c00 어드레스로 복사
* IBM사가 메모리의 0x00007c00 ~ 0x00007dff 번지(크기 512바이트) 를 부트 섹터가 읽혀지는 어드레스로 지정했기 때문.
##### MBR
https://ghostshell.tistory.com/303
* Boost sector를 찾아가기 위한 주소록이다.
* 운영체제가 어디에, 어떻게 위치해 있는지를 식별하여 컴퓨터의 주기억장치에 적재될 수 있도록 하기 위한 정보를 가지고 있다.
* 운영체제가 저장되어 있는 파티션의 부트 섹터 레코드를 읽을 수 있는 프로그램을 포함하고 있다.
* 부트 섹터 레코드에는 다시 운영체계의 나머지 부분들을 메모리에 적재시키는 프로그램을 담고 있다.
* 하드 디스크의 가장 앞 부분에 존재하는 512mb 크기의 영역이다.
  * Boot code (440byte, 0~)
    * 부팅을 하기 위한 정보가 들어있다.
    * 운영체제를 부팅시키기 위해서는 부트 파티션(active partition)을 찾아서, 해당 파티션의 MBR의 BootStrapCode를 실행 시켜야 한다.
  * Primary partition table (64byte, 446~)
    * 16byte씩 주 파티션에 대한 정보가 삽입된다.
  * MBR Signature (2byte, 510)
    * 부트로더로 인식되기 위한 정보가 있다.
##### Boot Sector
* 디스크의 다른 부분에 저장되는 부팅 프로그램을 담을 수 있는 기억 장치의 첫 섹터를 말한다.
* 1섹터는 512 바이트이다.
