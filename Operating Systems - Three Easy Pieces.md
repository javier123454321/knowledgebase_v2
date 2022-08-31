- Type:: [[Book]]
- Author:: [Remzi H. Arpaci-Dusseau](http://www.cs.wisc.edu/~remzi) and [Andrea C. Arpaci-Dusseau ](http://www.cs.wisc.edu/~dusseau)
- Subject:: [[Operating Systems]] [[Programming]] [[computers]]
- Status:: [[In Progress]]
- Abstract::
    - Deals with the basic pieces of an operating system through [[virtualization]], [[persistence]] and [[concurrency]] 
- Summary::
    - [[virtualization]]
        - Computers function by transforming a physical resource into *virtual*
versions of itself (a [[virtual machine]]) in this process called [[virtualization]]. The OS will then expose some native functionality through system calls (APIs or
Standard Libraries). [[virtualization]] allows for shared time (concurrency)
and Memory (resources) CPUs are sometimes considered resource managers.

A CPU, even when single threaded can simulate a concurrent computation
through [[virtualization]]. It has policies on how it does that.

You can effectively have a [[multi threaded]] program that is printing the 
memory space of an operation (a range of bytes that it is allocating to 
its memory) and due to the fact that it is running concurrently, the 
programs will seem to be reffering to the same exact address in the hardware.

Of course that the hardware is managing these collitions, through a process
of virtualizing the memory space and allocating a virtual machine to each 
process. The process then behaves as though it has access to the entire memory
space of the machine and it effectively does have complete access to the virtual
machine. The actual physical hardware however, is compartamentalzing the avcailable
physical memory to each process.
    - [[persistence]]
        - Whereas data in memory is lost easily, a technique is needed to store
data that persists and can be accessed at any point. The hardware is
referred to as the Hard Drive, and the software is referred to as the
FileSystem. Because you are interested in sharing files accross different
processes, you don't want to virtualize the space in whick persistent
bits of data to be stored are kept.

Data is stored to the hard disk via system calls (API requests to the
file system by a program). Then drivers take the job and complicated
logic of writing to the disk, but abstract it away from that which is doing
the request. 

    - [[CPU Processes]]
        - A running program - Data waiting to be sprung into action. The OS turns this data into something useful.
        - A CPU can spin up dozens of programs and simulate different computers through [[virtualization]]. The technique is called [[time sharing]] of the cpu which can spin up as many processes as the user would like, at the cost of performance. [Context switching]([[context switching]]) is the process of stopping the execution of one program and starting another.
        - To start a program, the OS must load code and data into memory into the [[address space]]
    - Limited Direct Execution
        - ![](https://firebasestorage.googleapis.com/v0/b/firescript-577a2.appspot.com/o/imgs%2Fapp%2FJavier-knowledge-graph%2FwDqUVockRL.png?alt=media&token=341ca23e-035c-4773-9a40-4aa637950d70)
        - Operating systems need to share physical memory among many jobs running at the same time. It does this by time sharing the CPU. 
            - Run one process for a little, then run another
        - Performance and Control are required. Control of the program so it doesn't run forever, access information that it is not supposed to.
        - **Direct Execution**
            - 1. Give the program access to the CPU
2. Create process entry in a process list
3. Allocate memory for it
4. Load the program code into memory
5. Locate its entry point (i.e. the main() routing)
6. Jump to entry point and start running the code
                - In C. the open() or read() system calls are just procedure calls which abstract the direct API calls in assembly away from the user
            - Issues: 
                - 1. How to delimit the program from affecting areas which it is not supposed to
                    - Direct Execution is fast because it runs on the hardware directly but the program might need to issue an input/output request that might be restricted or ask for more resources
                    - Solution
                        - Processor modes user and kernel mode
                            - User mode has built in restrictions that limits areas of program execution and kernel mode which is fully permissive
                            - Hardware provides user with a system call to elevate privileges
                                - A program must execute a trap instruction, execute a priviledged command then a return-from-trap instruction
                                    - The os needs to keep the program state in the registers to return correctly after the trap and return-from-trap instruction has fired
                                    - A [[trap table]] dictates which parts of the OS these trap handlers are allowed to affect.
                - 2. How does the CPU stop the process to implement time sharing
                    - If one process is running on the CPU then by definition the OS is **not** running. The OS needs to regain control of the CPU to switch between processes
                    - Solution
                        - Cooperative Solution
                            - We can wait for processes to yield control back to the cpu.
                            - The  CPU can regain control when the process does a system call
                            - If the process does an illegal operation, it calls a trap that likely kills the process
                        - Non-Cooperative Solution
                            - If the process gets stuck in an infinite loop, the only recourse that the OS has to finish it is to reboot the machine unless it uses a timer interrupt.
                                - Given an interval, the OS can take control of the thread in which a process is running and decide whether to yield control back to the process or do another operation
                                    - The OS needs to remember the state of the program for when the return-from-trap instruction yields the process back to the main thread.
            - Once the OS regains control (Cooperatively or non-cooperatively), the scheduler decides whether to yield back the control to the running process
                - context switch
                    - The OS loads information of the soon to be process into a stack and when the current process yields it decides to run the new process and puts information about the old process in the stack. In the next interval, the os does the operation in reverse.
                        - ![](https://firebasestorage.googleapis.com/v0/b/firescript-577a2.appspot.com/o/imgs%2Fapp%2FJavier-knowledge-graph%2FV5hXPjcz_d.png?alt=media&token=b0ff6757-0cdd-46b9-9bc3-77ab6cd75385)
![](https://firebasestorage.googleapis.com/v0/b/firescript-577a2.appspot.com/o/imgs%2Fapp%2FJavier-knowledge-graph%2FDu21kOjIX_.png?alt=media&token=23dbfc26-6133-4b32-822a-59f949f3eb95)
    - Scheduling
        - An os has certain scheduling polices or disciplines derived from assembly lines and other efficiency seeking endeavors.
        - Scheduling Metrics
            - A measurement for something i.e. turnaround time. 
                - $$T_{turnaround} = T_{completion} - T_{arrival}$$
                - if we assume that all jobs arrive at the same time then $$T_{turnaround} = T_{completion}$$
                - Turnaround is a performance metric as opposed to a fairness metric. PErformance can come at the expense of fairness as it could be ideal for performance to not run (some) tasks at all
            - First in First Out (FIFO)
                - As it sounds. Given job a then b then c that arrive almost simultaniously and run for 10 seconds each and run sequentially
                    - $$\frac{Job_{a} + Job_{b} + Job_{c}}{3}$$ which translates to $$\frac{10 + 20 +30}{3} = 20$$ if each job lasts 10 seconds.
                    - If job a lasted 100 seconds then the equation turns to $$\frac{100 + 110 +120}{3} = 110$$ which demonstrates the inefficiency in FIFO
            - Shortest Job First (SJF)
                - Solves this problem $$\frac{10 + 20 +120}{3} = 50$$ which is more than a factor of 2 improvement and optimal
            - **Shortest Time-to-Completion First** (**STCF**) of **Preemptive Shortest Job First **(**PSJF**)
                - A scheduler can preempt a job (stop it from running and switch to another)
                - When a new job enters the queue, the scheduler determines which job has the shortest time to completion and runs that.
            - Response Time
                - the time from when the job arrives in a system to the first time it is scheduled
                    - $$T_{response} = T_{first run} - T_{arrival}$$
                - Each job in STCF has to wait for the previous to be completely finished to start. Bad for interactivity
                - Round Robin Schedule (Time Slicing). 
                    - Run each job a scheduling quantum:
                    - ![](https://firebasestorage.googleapis.com/v0/b/firescript-577a2.appspot.com/o/imgs%2Fapp%2FJavier-knowledge-graph%2FOKEowQUwqZ.png?alt=media&token=f510cf3a-168c-44bd-b4de-9bcec33c35a5)
                - If the CPU spends 1ms per second to switch jobs, we can amortize by waiting 10 seconds to do a switch. Numbers are used here for exageration. Too short of a time slice is too expensive to run.
                - Round Robin is good for Response Time, but much worse for turnaround time, as it stretches each job out as far as it can.
            - Programs with Input/Output
                - Programs halt execution until 
