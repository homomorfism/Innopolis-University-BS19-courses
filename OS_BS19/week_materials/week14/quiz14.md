#### Task 1

Which of the following are TRUE of deadlock prevention and deadlock avoidance schemes? Select one or more:

- ```In deadlock prevention, the request for resources is always granted if the resulting state is safe ```
- ```In deadlock avoidance, the request for resources is always granted if the result state is safe ``` <- **Correct**
- ```Deadlock avoidance is more restrictive than deadlock prevention ```
- ```Deadlock avoidance requires knowledge of resource requirements a priori ``` <- **Correct**
- ```Deadlocks prevention is just slightly different from deadlocks avoidance, but the main principle used in both strategies is the same```

idk

#### Task 2

Which statements about resources are **TRUE**? Select one or more:

- ```Resources can be preemptable and non-preemptable ``` <- **Correct**
- ```The memory is always preemptable ``` <- **False**, memory of printer or or some registers in device controller,
  e.x. (idk)
- ```A process that tries to access non-preemptable resource, which is already taken by another process, is usually killed by an OS``` <
    - **False**, not killing but returning some error code
- ```In general, deadlocks occur when working with non-preemptable resources ``` <- **Correct**
- ```A resource for which process might compete can be (but not limited by) a hardware device or a file ```<- **
  Correct**, obviously

> Resources come in two types
> - Preemptable, meaning that the resource can be taken away from its current owner (and given back later). An example is memory.
> - Non-preemptable, meaning that the resource cannot be taken away. An example is a printer.

> In general, deadlocks involve nonpreemptable resources. Potential deadlocks that involve preemptable resources can usually be resolved by reallocating resources from one process to another. Thus, our treatment will focus on nonpreemptable resources.

#### Task 3

Which statements about the deadlocks are **TRUE**? Select one or more:

- ```The resource deadlock is the only situation that is a “true deadlock”, other deadlock types are called livelock or starvation ```
- ```A combination of any three out of four conditions (mutual exclusion, hold-and-wait, no-preemption, circular wait) is sufficient for deadlocks to occur```
- ```The minimum number of processes that can cause a deadlock is 2 ``` <- **Correct**
- ```In general, there are four strategies to deal with deadlocks ``` <- **Correct**
- ```Resource deadlocks may occur even in systems with no parallelism ```

> In general, four strategies are used for dealing with deadlocks.
> 1. Just ignore the problem. Maybe if you ignore it, it will ignore you.
> 2. Detection and recovery. Let them occur, detect them, and take action.
> 3. Dynamic avoidance by careful resource allocation.
> 4. Prevention, by structurally negating one of the four conditions.

#### Task 4

The condition that a process may hold a resource while awaiting assignment of additional resources... Select one or
more:
more:

- ```...is called the "transitive wait" condition```
- ```...is called the "hold-and-wait" condition ``` <- **Correct**
- ```...is called the "circular wait" condition```
- ```...is one of the necessary conditions for deadlock ``` <- **Correct**
- ```...is not a necessary condition for deadlock```

> Coffman et al. (1971) showed that four conditions must hold for there to be a (resource) deadlock:
> 1. Mutual exclusion condition. Each resource is either currently assigned to exactly one process or is available.
>2. Hold-and-wait condition. Processes currently holding resources that were granted earlier can request new resources.
>3. No-preemption condition. Resources previously granted cannot be forcibly taken away from a process. They must be explicitly released by the process holding them.
>4. Circular wait condition. There must be a circular list of two or more processes, each of which is waiting for a resource held by the next member of the chain.

#### Task 5

One algorithm simulates the possible future execution of the system, based on the assumption that every process will
only complete after its declared maximum total reFortunately, there is another techni- que that can usually be employed
to break communication deadlocks: timeouts. In most network communication systems, whenever a message is sent to which a
re- ply is expected, a timer is started. If the timer goes off before the reply arrives, the sender of the message
assumes that the message has been lost and sends it again
(and again and again if needed). In this way, the deadlock is broken.source allocations have all been satisfied, to see
if the maximum future requests of all processes can be satisfied, and so they will all be able to complete. This is used
for:
Select one:

- ```Deadlock prevention ```
- ```Deadlock avoidance``` <- **Correct**, Banker algorithm
- ```Deadlock detection```
- ```Deadlock minimization```

#### Task 6

Which of the following statements are **TRUE**? Select one or more:

- ```Communication deadlock is a problem of cooperation synchronization ``` <- **Correct**
- ```Resource deadlock is a problem of cooperation synchronization```
- ```One possible way to prevent communication deadlock is to order the resources used by all parties``` <- It is
  correct for resource deadlock. not communication deadlocks
- ```Timeouts can be used to detect communication deadlocks and recover from them ``` <- **Correct**
- ```All the deadlocks occurring in communication systems are communication deadlocks```

> Communication deadlock is an anomaly of cooperation synchronization. The processes in this type of deadlock could not complete service if executed independently. ... Fortunately, there is another techni- que that can usually be employed to break communication deadlocks: timeouts. In most network communication systems, whenever a message is sent to which a re- ply is expected, a timer is started. If the timer goes off before the reply arrives, the sender of the message assumes that the message has been lost and sends it again(and again and again if needed). In this way, the deadlock is broken.

> Not all deadlocks occurring in communication systems or networks are communication deadlocks. Resource deadlocks can also occur there. ... Suppose that all the packets at a router A need to go to B and all the packets at B need to go to C and all the packets at C need to go to D and all the packets at D need to go to A. No packet can move because there is no buffer at the other end, and we have a classical resource deadlock, albeit in the middle of a communications' system.

#### Task 7

Suppose ```n``` processes, ```P1, …. Pn``` share m identical resource units, which can be reserved and released one at a
time. The maximum resource requirement of process ```Pi``` is ```Ri```, where ```Ri > 0```. Which one of the following
is a minimal sufficient condition for ensuring that deadlock does not occur? Select one:

- ```∀i,Ri<m```
- ```∀i,Ri<n```
- ```\sum_{i=1}^{n} R_i < m + n ``` <- **Correct**, idk
- ```\sum_{i=1}^{n} R_i < (m * n) ```

#### Task 8

A system has n resources ```R0, ..., Rn-1```, and ```k``` processes ```P0, ..., Pk-1```. The implementation of the
resource request logic of each process Pi is as follows:

```c
if (i % 2 == 0) {
  if (i < n) request Ri
  if (i + 2 < n) request Ri + 2
}
else {
  if (i < n) request Rn-i
  if (i + 2 < n) request Rn - i - 2
}
```

In which one of the following situations is a deadlock possible? Select one:

- ```n = 40, k = 26```
- ```n = 21, k = 12``` <- **Correct**, idk
- ```n = 20, k = 10```
- ```n = 41, k = 19```

#### Task 9

An operating system uses the Banker’s algorithm for deadlock avoidance when managing the allocation of three resource
types R0, R1, and R2 to three processes P0, P1, and P2. The table given below presents the current system state. Here,
the Allocation matrix shows the current number of resources of each type allocated to each process and the Max matrix
shows the maximum number of resources of each type required by each process during its execution.

### Allocation matrix

|     | R0  | R1  | R2  |
| --- | --- | --- | --- |
| P0  | 1   | 0   | 0   |
| P1  | 2   | 3   | 1   |
| P2  | 2   | 2   | 2   |
| P3  | 1   | 1   | 1   |
| P4  | 3   | 1   | 3   |

### All requests matrix

|     | R0  | R1  | R2  |
| --- | --- | --- | --- |
| P0  | 3   | 1   | 5   |
| P1  | 1   | 1   | 0   |
| P2  | 0   | 2   | 2   |
| P3  | 1   | 7   | 4   |
| P4  | 6   | 2   | 1   |

Available resources are represented by vector ```A = (3, 2, 2)```. The system is currently in a safe state. Consider the following independent requests for additional resources in the current state:

```REQ1: P0 requests 0 units of R0, 0 units of R1 and 2 units of R2```
```REQ2: P1 requests 2 units of R0, 0 units of R1 and 0 units of R2```
Which one of the following is TRUE? Select one:

- ```Only REQ1 can be permitted ```
- ```Only REQ2 can be permitted``` <- **Correct**
- ```Both REQ1 and REQ2 can be permitted```
- ```Neither REQ1 nor REQ2 can be permitted```

idk, need to think here

#### Task 10

There are five processes P0, …, P4 working with three resource types R0, R1 and R2. The table given below presents the
current system state. Here, the Allocation matrix shows the current number of resources of each type allocated to each
process and the Request matrix shows the number of resources requested by each process.

### Allocation matrix

|     | R0  | R1  | R2  |
| --- | --- | --- | --- |
| P0  | 1   | 0   | 0   |
| P1  | 2   | 3   | 1   |
| P2  | 2   | 2   | 2   |
| P3  | 1   | 1   | 1   |
| P4  | 3   | 1   | 3   |

### All requests matrix

|     | R0  | R1  | R2  |
| --- | --- | --- | --- |
| P0  | 3   | 1   | 5   |
| P1  | 1   | 1   | 0   |
| P2  | 0   | 2   | 2   |
| P3  | 1   | 7   | 4   |
| P4  | 6   | 2   | 1   |

Available resources are represented by vector``` A = (1, 1, 1)```. Which processes are locking each other? Select one or
more:

- ```P0``` <- **Correct**
- ```P1```
- ```P2```
- ```P3``` <- **Correct**
- ```P4``` <- **Correct**

1. We release P1, because ```(1, 1, 0) < (1, 1, 1)```: now ```A = (1, 1, 1) + (2, 3, 1) = (3, 4, 2)```
2. We release P2, because ```(0, 2, 2) < (3, 4, 1)```: now ```A = (3, 4, 2) + (2, 2, 2) = (5, 6, 4)```
3. We can not release P0, because ```(3, 1, 5) not less than (5, 6, 4)```
4. We can not release P3, because ```(1, 7, 4) not less than (5, 6, 4)```
5. We can not release P4, because ```(6, 2, 1) not less than (5, 6, 4)```
