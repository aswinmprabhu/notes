Process management  
  
The kernel stores the list of processes in a **circular doubly linked list** called the task list. Each element in the task list is a process descriptor of the type **struct task\_struct**  
  
**End of stack** -> struct thread\_info -> **struct task\_struct**  
  
The default maximum value of pid is only **32,768 (that of a short int)**, although the value optionally can be increased as high as four million (linux/threads.h)  
  
If the system is willing to break compatibility with old applications, the administrator may increase the maximum value via **/proc/sys/kernel/pid\_max**.  
  
Task state  
TASK\_RUNNING - **The process is runnable / running**  
TASK\_INTERRUPTIBLE - **The process is sleeping (that is, it is blocked)**  
TASK\_UNINTERRUPTIBLE - **This state is identical to TASK\_INTERRUPTIBLE except that it does not wake up and become runnable if it receives a signal**  
  
All processes are descendants of the **init process**, whose PID is **one**. The kernel starts init in the last step of the boot process. The init process, in turn, reads the system initscripts and executes more programs.  
  
Process creation  
fork(), **creates a child process that is a copy of the current task**. It differs from the parent only in its PID (which is unique), its PPID (parent’s PID, which is set to the original process), and certain resources and statistics, such as pending signals, which are not inherited. The second function, exec(), **loads a new executable into the address space and begins executing it**  
  
Copy-on-write  
In Linux, fork() is implemented through the use of copy-on-write pages. Copy-on-write (or COW) is a **technique to delay or altogether prevent copying of the data. Rather than duplicate the process address space, the parent and the child can share a single copy. When written to, a copy is made.**   
fork followed by exec becomes very fast.  
  
fork() implemented via **clone()** syscall.  
**0** returned in child and **pid of child** returned in parent.  
  
Threads  
  
To the Linux kernel, there is no concept of a thread. Linux implements all threads as standard processes.  
  
Threads are created the same as normal tasks, with the exception that the {{clone() system call is passed flags corresponding to the specific resources to be shared:  
clone(CLONE\_VM | CLONE\_FS | CLONE\_FILES | CLONE\_SIGHAND, 0);}}  
  
**Kernel Threads**  
Normal proceess that don't have address space used by kernel to delegate background tasks  
  
Process Termination  
  
**exit()** sycall -> do\_exit() -> Set PF\_EXITING, **release addr space, exit semaphores and files, set exit\_code** -> exit\_notify() -> Does reparenting **to another thread/init find\_new\_reaper()** -> At this point state is **EXIT\_ZOMBIE** (only mem is process descriptor and kernel stack) -> **wait()** by parent -> release\_task()  
  
Parent dies children become **orphan** => Reparent to **another thread in same group or to init**. Init routinely calls wait to clean zombies.

---
