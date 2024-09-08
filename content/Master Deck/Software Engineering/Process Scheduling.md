Process Scheduling 

  

2 flavours of multitasking -> **Cooperative and Preemptive**

Linux uses the latter.

  

Bad scheduler till 2.4 -> O(1) scheduler (bad for interactive) -> CFS

  

I/O bound vs. Processor bound processes

Unix favours the I/O bound processes giving good latency.

  

Process Prio

\* Nice value is **-20 to 19 (default is 0). Larger means less prio (more nicer to other procs)**

\* Real time prio is **0 to 99. Larger is higher prio. These are at higher prio than normal procs.**

  

CFS assigns a **proportion of the processor** which is f(load on sys, nice value)

If newly runnable proc has consumed less proportion of processor than curr => preempt. 

  

The Linux scheduler is modular, enabling different algorithms to schedule different types of processes. This modularity is called scheduler classes.

  

Each process then runs for a “timeslice” proportional to its weight divided by the total weight of all runnable threads. To calculate the actual timeslice, CFS sets a target for its approximation of the “infinitely small” scheduling duration in perfect multitasking. This target is called the **targeted latency**. Smaller targets yield better interactivity and a closer approximation to perfect multitasking, at the expense of higher switching costs and thus worse overall throughput. Let’s assume the targeted latency is 20 milliseconds and we have two runnable tasks at the same priority. Regardless of those task’s priority, each will run for 10 milliseconds before preempting in favor of the other. If we have four tasks at the same priority, each will run for 5 milliseconds. If there are 20 tasks, each will run for 1 millisecond.

  

CFS imposes a floor on the timeslice assigned to each process. This floor is called the **minimum granularity**. By default it is 1 millisecond. Thus, even as the number of runnable processes approaches infinity, each will run for at least 1 millisecond, to ensure there is a ceiling on the incurred switching costs.

  

The core of CFS’s scheduling algorithm: **Pick the task with the smallest vruntime (runtime weighted by number of runnable procs)**

  

Wait queues

  

Processes put themselves on a wait queue and mark themselves not runnable. When the event associated with the wait queue occurs, the processes on the queue are awakened

  

  

  

Realtime scheduling policies

  

Linux provides two real-time scheduling policies, SCHED\_FIFO and SCHED\_RR. The normal, not real-time scheduling policy is SCHED\_NORMAL. Via the scheduling classes framework, these real-time policies are managed not by the Completely Fair Scheduler, but by a special real-time scheduler, defined in kernel/sched\_rt.c.

  

SCHED\_FIFO implements **a simple first-in, first-out scheduling algorithm without timeslices**. A runnable SCHED\_FIFO task is always scheduled over any SCHED\_NORMAL tasks.

  

Two or more SCHED\_FIFO tasks at the same priority run round-robin, but again only yielding the processor when they explicitly choose to do so. If a SCHED\_FIFO task is runnable, all tasks at a lower priority cannot run until it becomes unrunnable.

  

SCHED\_RR is **SCHED\_FIFO with timeslices**

  

Processor affinity tracked by cpus\_allowed bit mask field of task\_struct.

---
