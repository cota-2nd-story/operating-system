# 3강 
### Combination of hardware, software, data
- used in order to solve the problem human beings

### H/W
#### CPU
- fetch the programs(software) from the memory
- and then it will execute it
- program: a collection of instructions
#### MEMORY
- programs will be stored insade the memory
- RAM: accessing data is very fast (comparing to HD)
- Hard disk: stored in hard disk is permanent
- cache
- register
#### why are we using these many levels of memory
- every memory system has its own advantages as well as disadvantageous

### cpu - ram - hard disk
- cpu will take the program line-by-line and then it will execute it

# 4강
### High level program cannot be directly placed inside the hard disk
- because CPU can only understand binary code
- program will be converted into a binary code
- compiler will convert program software(high level program) to machine code (low level program)

### Cpu never be able to access the hard disk 
- cpu can only access thm RAM
- cpu는 ram에서 원하는 프로그램을 찾는다.
- ram에 없을 경우 hard disk에서 ram으로 복사한 후에 사용한다.


# 5강
### Resource management
- OS will manage resources 
- whole machine code is placed in the hard disk of computer
- cpu cannot access the hard disk directly
- cpu can only access the ram directly
- so we need to move the program from hard disk to ram
- algorithm will be implemented by operating system
 - os code have a lot of functions 
#### OS is implementing resource allocation
- RAM 에는 용량 제한이 있다.
- 곧 사용하게 될 프로그램은 hard disk에 있다.
- 어느 것이 곧 필요한 지를 해결하는 알고리즘이 필요하다.
- 이러한 일고리즘은 operating system을 통해 실행된다.
#### Resources
- cpu, ram, printer...
#### Process scheduler
- The process scheduler is a part of the operating system that decides which process runs at a certain point in time.
#### Short-term scheduler
- The short-term scheduler (also known as the CPU scheduler) decides which of the ready, in-memory processes is to be executed (allocated a CPU)
#### Long-term scheduler
- decides which jobs or processes are to be admitted to the ready queue (in main memory)

# 6강
### operating system nothing but a program which is going to act as a resource manager
### operating systems program will always be present inside the RAM
- which means... whenever we switch-ON the computer these operating system program will be loaded inside the RAM
- This code (os) will always be present inside the RAM
- this set of addresses called OS space
- remaining space is used for placing our programs (application programs) called user space
### How a program actually is being executed
- source program -> compiler -> machine code -> hard disk
- this program will be loaded into the RAM
- once it is loaded into the RAM, will be taken by the CPU line-by-line and executed
- once it is done, this program will be completely removed from the RAM

### I/O Device
- Any I/O device will have a buffer associated with it
- ex) monitor will have buffer
- buffer means nothing but memory or register
### Why buffer is actually helpful
#### ex) how a calculator application works in our computer (2+3=5)
- calculator is present inside the RAM
- I enter 2 in the keyboard
- 2's binary format is nothing but 010
- this will come into the buffer
- because computer can understand only binary format
- 010 will be moved into the RAM
- I type 3 in keyboard
- 011 will overwrite in the buffer
- will also be moved inside the RAM
- once this is moved into the RAM, the CPU will take both 010 and 011 inside it's registers
- CPU will also be having a buffer or register
- all the operands will be fetched into the register 
- and operation will be done by the CPU
- and result will be over-written in one of the registers
- result(101) ill be placed inside the RAM
- this has to be displayed in the monitor
- this will be placed in the monitor's buffer
- as a result of which we are able to see the result in our computer's screen
#### ex) edit document
- document present inside the hard disk
- first, this document will be moved from hard disk to RAM
- because CPU cannot access the hard disk directly
- edit with ms-word
- changes to the document and then we again placed the document into the hard disk
- hard disk can act as an input device as well as it can act as an output device
- but keyboard can always act as an input device

### program can undergo something called as I/O
- our program is actually waiting for I/O for some time

### Turn-around time
- waiting time + burst time + i/o time


# 7강
### we already know that any program in our computer will be converted into a machine code(also called as .exe code)
### And then it will be placed inside the hard disk

### What do we actually mean by a process
- let us assume I have opened my computer
- I have double clicked the google chrome icon
- which means I have opened the Google chrome software
- Now what our CPU will do is...
- it will check the Google Chrome's program
- or search the google chrome's program in our RAM
- assume the program is not available inside the RAM
- this program might have to be moved from hard disk into RAM
- a new copy of Google Chrome will be created
- `this program is called as a process`
#### program has been executed or this program has been opened by my computer a new copy of this program will be created and this is what we mean by a process
#### If you open 2 google chrome Windows at the same time, program two instances of Google Chrome's program will be created inside the hard disk. these two are process which are created for this program


### new state -> ready state -> running state -> I/O state -> terminated state-> suspend ready state -> suspend wait state 
- we open the Google Chrome software
- program has actually created process
- Now we say that this process is in `NEW STATE`
- because this process is being newly created
- this process will actually be moved into the RAM
- Google Chrome is now present inside the RAM
- process is waiting for some event to happen (executed by CPU, undergo I/O, ...)
- this process is in `READY STATE`
- this process actually ready for execution or for I/O
- Now incase if the process is being executed by the CPU taking line-by-line
- we say that the process is a `RUNNING STATE`, which means the process is being run by the CPU
- Now in case if the process is in RAM and it is performing some I/O event
- I/O performing means either reading or writing from I/O devices
- this process is in `I/O STATE`
- it is also called `BLOCK STATE`
- once a process has actually completed its execution which means it is completely done with everything
- it will be completely removed from the RAM
- this process is in `TERMINATED STATE`


# 8강
### degree of multiprogramming
- maximum number of processes which can be placed in the RAM in our computer
- RAM can be will only a finite number of processes which can be placed
- ex) Size of RAM is 4GB, size of a single process is 4 KB
- size of RAM / size of a single process = 4GB/4KB = 2^20 bytes

### What is mean by G-B
- 1 Byte = 8 bits
- 1 KB = 2^10 Bytes
- 1 MB = 2^20 Bytes
- 1 GB = 2^30 Bytes
- 1 TB = 2^40 Bytes


# 9강
### What are the various types of operating systems we have
- one thing is nothing but Batch operating system
### Batch operating system
- Batch operating system is actually not used today
- it is being used long back
- means the degree of multiprogramming is always 1
- one process which can be present inside the RAM
- I will be placing one process inside the RAM
- Only after the completion of this process I will be fetching the next process from the hard disk
- disadvantage with this is 
- ex) P1 needs I/O, P1 is doing I/O -> our CPU will be idle.
- execution and I/O can not be done at the same time for a particular process

#### CPU efficiency
- useful time of CPU / total time of CPU
- which means out of the total time you have got how much time are you really using the CPU


### Multiprogramming operating system
- which is very popular
- we can have more than one process in the RAM
- ex) P1 is being executed by the CPU then one of the other processes can undergo I/O
- I'm not allowing the CPU to remain idle
- `concurrent processing`

### Multiprocessing operating system
- multiprocessing OS can have more than one CPU
- while 1 process is being executed by one cpu, some other process will also be executed by other CPU
- this is `Parallel processing`
- which means we are executing more than one process at the same time
- but multiprogramming operating systems were not doing parallel processing
- this is concurrent processing
- we are using today in our computers is multiprocessing operating system

### there is a difference between parallel processing and concurrent processing 
- If we have only 1 CPU and we keep on changing the processes and we keep on executing... we say that as concurrent processing
- 엄마가 두 손으로 두 딸에게 밥을 동시에 주면 parallel, 엄마가 한 손으로 두 딸에게 번갈아 가면서 주면 한 명이 먹는 동안 한명은 기다려야 한다. 이 경우에는 concurrent processing. it's a very funny example 
- advantage with parallel processing is be faster than concurrent processing
- disadvantage with parallel processing is system cost will increase
- because we're having more than one CPU... the cost of processor is very high

# 10 강
- we will mostly be using something called as multiprogramming os

# 11 강 
- 포스팅: stack과 heap의 차이. heap은 무엇이지?
### Passive entity, 
- If user opens a program, process will be created.
- it also called as `Passive entity`, `Active entity`

### the process will not only contain program but also some more thing
- stack -> <- heap | static variables, global variables | program
- process will definitely contain the program
- it will also have some things
- our program will be full of functions
- function might call other functions
- this might keep on going for sometime
- now just to keep track of the function calls, we need something called a `stack`
- that is the reason we are having this stack memory
- stack is nothing but just a memory
#### now our program might also have something called dynamic memory allocation
- using malloc() or calloc()
- these function calls are actually used to dynamically allocate memory
- dynamically allocate means allocating memory at the runtime
- whenever we use malloc() or calloc() within our program, `heap` space is actually used for all those dynamic memory allocation
#### The size of the heap and stack memory has not been determined.
- some programs may need more space for stack, in that case stack will go till here whereas heap will be having only small space
- in some programs heap may need more space, in that case the heap will be allocated more space something
- simple words... this space() is not equally divided between stack and heap
### this complete process we is created for a program is also part of process control block 
- every process we will be having a process control block
- if we have 10 processes then we will having 10 process control blocks
### static and global variables
- within our program, we might use static keyword
- ex) static int i
- these variables will be separately placed in the static variable
- local variable which is defined within a function 
- for local variables the space will be allocated within the stack which means we have already seen that all function calls will be stored within the stack
- but global variables will be allocated separately
- they will not be allocated within the stack
- they will be allocated in this particular space inside the PCB

### what the various attributes we have for a process
- attributes are nothing but properties
### process id
- `process id`, program counter, process state, general purpose registers, poi, list of open files, list of open devices, protection
- process id is nothing but a unique number
### program counter
- program counter
- ex) If there is a 3 processes in ready state, OS might have to select one among the 3 processes to be executed by CPU
- `that is the main functionality of OS`
- the main functionality of os is nothing but `resource allocation`
- os is big program
- there will be some part of the program which will be actually use in order to define
- scheduler is nothing but a program which is part of our os program
- which is executing the CPU first.
- every process will of course get the CPU  
- there is no doubt about that
- but what is the order in with them will be getting the CPU?
- that is being decided by our scheduling algorithm
- this code be implemented in lot of ways (FCFS, SJF,  ...)
- `program counter` will actually instruction number
- instruction number is nothing but the line of program from where I need to continue the execution
- program counter nothing but a register
### general purpose register 
- `general purpose register` is similar to program counter
- when it is being executed by the CPU should have used some registers that has to be also remembered
### list of open files, devices 
- similarly there will be a list of open files which means the files which are opened by process that has to be also remembered
### protection
- particular process has some space
- it has something called as stack space and heap space which means for function calls it uses the stack space and for dynamic allocation of space it uses the heap space
- ex) p3 will have a particular stack space and heap space and p4 will also be having its own stack space and heap space in its PCB
- now p4 should not access p3's space
- our operating system needs to make sure that a process is not using space of another process