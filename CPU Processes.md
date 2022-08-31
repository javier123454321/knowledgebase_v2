- A running program with a defined machine state
- # [[machine state]]
    - Which part of the machine can a program read and update while it is running.
    - machine memory
        - where instructions lie, the data to be written by the program. The memory that a process can access is part of the process )called address space
- # The Process API
    - All OSs will have an api to do some basic operations
        - Create a new process
        - Destroy (forcefully)
        - Wait for process to finish
        - Status
        - ![](https://firebasestorage.googleapis.com/v0/b/firescript-577a2.appspot.com/o/imgs%2Fapp%2FJavier-knowledge-graph%2FplsSiOSubx.png?alt=media&token=409481df-3c87-423d-a3e2-d9a5ec5f8309)
- # Turning a program into a process
    - Step 1. Loading code and data into memory (the [[address space]] of the process) Requires transforming the executable data of a program from a disk into memory.
    - Step 2. Allocate memory for the program's stack - Local variables, Function Parameters, return addresses. It also allocates memory to the heap.
    - Step 3. create the basic input/output files for stdin, stdout, and stderr which will handle intearction and feedback to the user.
    - Step 4. Once everything is allocated to the process, it starts the program and yields control of the cpu to the newly created process.
- # Process States
    - Running || Ready || Blocked
    - ![](https://firebasestorage.googleapis.com/v0/b/firescript-577a2.appspot.com/o/imgs%2Fapp%2FJavier-knowledge-graph%2FRZMYGwgx7b.png?alt=media&token=fb8fbce4-4c53-4acb-beeb-ffc5c8ee045e)
    - Blocked processes remain blocked until some event happens. 
    - Which part of the machine can a program read and update while it is running.
- # [[Data Structures]]
    - An [OS]([[Operating Systems]]) is a program, and has data structures that track pieces of information. 
        - It tracks a process list for all processes that are ready, running, blocked, and its relation to other processes. Also initial state (loading) final state (closing but not cleaned up)
            - Final state
                - Allows parent process to examine return code of exited process (0 if success in UNIX)
            - Each process has a register context that loads the state of a process and will resume there once the process is resumed.
        - Process Control block (PCB) contains the information about a specific process.
- # CPU Process Creation in UNIX
    - Example:
        - ```c
[[include]] <stdio.h>
[[include]] <stdlib.h>
[[include]] <unistd.h>

int main(int argc, char *argv[]) {
	printf("hello world (pid:%d)\n", (int) getpid());
	int rc = fork();
	if (rc < 0) {
		// fork failed
		fprintf(stderr, "fork failed\n");
		exit(1);
    }
	else if(rc==0){
		// child (new process)
		printf("hello, I am child (pid:%d)\n", (int) getpid());
    else {
		// parent goes down this path (main)
		printf("hello, I am parent of %d (pid:%d)\n",
        	rc, (int) getpid());
        }
      return 0;
    }```
            - OUTPUTS:
                - hello world (pid:29146)
hello, I am parent of 29147 (pid:29146)
hello, I am child (pid:29147)
                - 29146 created a fork with an equivalent pid. this doesn't start running at `main()` but at the `fork()` function on line 7
                    - The child isn't an exact copy, it has a copy of the address space (it's own virtual machine) but the return value is different
                        - It is non-deterministic, a CPU scheduler is in charge of deciding which process runs next
                            - Leads to problems in multi-threaded programs and is studied in relation to concurrency.
        - Using `wait()`
            - ```c
[[include]] <stdio.h>
[[include]] <stdlib.h>
[[include]] <unistd.h>
[[include]] <sys/wait.h>

int main(int argc, char *argv[]) {
	printf("hello world (pid:%d)\n", (int) getpid());
 	int rc = fork();
 	if (rc < 0) { 
      // fork failed; exit
      fprintf(stderr, "fork failed\n");
      exit(1);
    } else if (rc == 0) {//child (new process)}
      printf("hello, I am child (pid:%d) \n", (int) getpid());
	} else {
      int rc_wait = wait(NULL);
      printf("hello, I am parent of %d (rc_wait: %d) (pid: %d)\n",
            rc, rc_wait, (int) getpid());
	}
	return 0;
}```
                - The `wait()` call stops execution of the parent until the child program is executed
        - Using `exec()`
            - ```c
[[include]] <stdio.h>
[[include]] <stdlib.h>
[[include]] <unistd.h>
[[include]] <string.h>
[[include]] <sys/wait.h>

int main(int argc, char *argv[]) {
	printf("hello world (pid:%d)\n", (int) getpid()); int rc = fork();
	if (rc < 0) { // fork failed; exit
      fprintf(stderr, "fork failed\n");
      exit(1);
    } else if (rc == 0) { // child (new process)
      printf("hello, I am child (pid:%d)\n", (int) getpid());
      char *myargs[3];
      myargs[0] = strdup("wc"); // program: "wc" (word count) 
      myargs[1] = strdup("p3.c"); // argument: file to count 
      myargs[2] = NULL; // marks end of array 
      execvp(myargs[0], myargs); // runs word count 
      printf("this shouldn’t print out");
    } else { // parent goes down this path (main)
      	int rc_wait = wait(NULL);
		printf("hello, I am parent of %d (rc_wait:%d) (pid:%d)\n",
               rc, rc_wait, (int) getpid());
    }
  return 0;
}
```
            - Outputs
                - hello world (pid:29383)
hello, I am child (pid:29384)
29 107 1030 p3.c
hello, I am parent of 29384 (rc_wait:29384) (pid:29383)
                - `exec()` overrides the current executable file with the code segment to run. It runs a new program from within the current process
    - A UNIX shell runs code after the creating a `fork()` but before calling `exec()`, creating the right environment for a program to run.[*](((VQP7r6Usn))) {{[[r/moved]]}}
