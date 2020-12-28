#### Task 1

A set of operations that can be combined so that they appear to the rest of the system to be a single operation is called:
Select one:
- ```Mutual exclusion```
- ```Bounded buffer```
- ```Atomic operation``` <- **Correct**
- ```Critical region```
- ```Race conditions```

#### Task 2

Producer sleeps until awakened by consumer when buffer is NOT full; Consumer sleeps until awakened by Producer when buffer is NOT empty. This is:
Select one:
- ```Atomic operation```
- ```Solution to the bounded buffer problem ``` <- **Correct**
- ```Bounded buffer problem```
- ```Race condition```
- ```Priority inversion```

Sleep & wake locks are a way for avoiding race condition 

#### Task 3

The situation when a higher priority process has to wait for a lower priority process is called:
Select one:
- ```Bounded buffer problem```
- ```InterProces communication```
- ```Priority inversion ``` <- **Correct**
- ```Atomic operation```
- ```Race condition```

Logically, no other choices suits.

#### Task 4

The situation when a process is continuously testing a variable until some value appears is called:

Select one:
- ```Strict alternation```
- ```Priority inversion```
- ```Atomic operation``` 
- ```Busy waiting``` <- **Correct**, obviously

#### Task 5

Consider the 2-process solution to the critical section (‘i’ refers to the current process and ‘j’ is the other one): 

(as in slides on lecture 5 we consider flag and turn to be shared)


Process 1
```
repeat
     flag[i]:=true;
     turn := j;
     while ( flag[j] and turn ==j ) do no-op;
     <critical section>
     flag[i] := false;
     <remainder section>
 until false;
```

Process 2
```
repeat
     flag[j]:=true;
     turn := i;
     while ( flag[i] and turn ==i ) do no-op;
     <critical section>
     flag[j] := false;
     <remainder section>
 until false;
```

This solution satisfies:

Select one:
- ```Mutual Exclusion``` 
- ```Bounded Wait (no process should have to wait forever to enter into critical section)``` 
- ```Progress (process should eventually be able to complete)```
- ```All of the above ``` <- **Correct**

This is the Peterson solution, it satisfy all conditions of critical region. 
(Please write more understandable explanation to it).

#### Task 6

Which of the following are necessary to create a working solution to avoid race conditions?

Select one or more:
- ```All the processes must have different priorities```
- ```No process should enter its critical region inside a loop```
- ```No two processes may be simultaneously inside their critical regions ``` <- **Correct**
- ```No process running outside its critical region may block any process``` <- **Correct**
- ```More than one instance of any program should not be allowed to run simultaneously```
- ```No process should have to wait forever to enter its critical region ``` <- **Correct**

> Although this requirement avoids race conditions, it is not sufficient for having
parallel processes cooperate correctly and efficiently using shared data. We need
four conditions to hold to have a good solution:
>- No two processes may be simultaneously inside their critical regions.
>- No assumptions may be made about speeds or the number of CPUs.
>- No process running outside its critical region may block any process.
>- No process should have to wait forever to enter its critical region.

Tanenbaum, 120 page.

#### Task 7

The following two functions P1 and P2 that share a variable B with an initial value of 2 execute concurrently:
```c
P1() { 
   C = B – 1; 
   B = 2*C;  
}
```

```c
P2() {
   D = 2 * B;
   B = D - 1; 
}
```
The number of distinct values that B can possibly take after the execution is:

Select one:
- ```3``` 
- ```1```
- ```4```
- ```2```
- ```5```


There are following ways that concurrent processes can follow

```
C = B – 1;   // C = 1
B = 2*C;    // B = 2
D = 2 * B;   // D  = 4
B = D - 1;   // B  = 3


C = B – 1;   // C = 1
D = 2 * B;   // D = 4
B = D - 1;   // B = 3
B = 2*C;    // B = 2

C = B – 1;  // C = 1
D = 2 * B; // D =  4
B = 2*C;  // B = 2
B = D - 1;  // B = 3

D = 2 * B; // D =  4
C = B – 1;  // C = 1
B = 2*C;  // B = 2
B = D - 1;  // B = 3

D = 2 * B; // D =  4
B = D - 1;  // B = 3
C = B – 1;  // C = 2
B = 2*C;  // B = 4
```

There are 3 different possible values of B: 2, 3 and 4

#### Task 8

Consider the following two-process synchronization solution
Process 0	
```c
Entry: loop while (turn == 1)
  Critical region;
Exit: turn = 1;
Some other code;
```

Process 1
```c
Entry: loop while (turn == 0)
  Critical region;
Exit: turn = 0;
Some other code;
```
The shared variable turn is initialized to zero. Which one of the following is TRUE?

P.S.Progress requirement: no process running outside its critical region may block any process

P.S.S. Bounded wait requirement: no process should have to wait forever to enter its critical region

Select one:
- ```This solution violates mutual exclusion requirement```
- ```This solution violates progress requirement. Neither process is able to enter its critical section without a second process which might be too slow``` <- **Correct**
- ```This solution violates bounded wait requirement```
- ```This is a correct two-process synchronization solution```

> No process should have to wait forever to enter its critical region.

#### Task 9

Are advantages of interrupt disabling:

Select one:
- ```It's easy and efficient on multiprocessors``` <- No, we can only disable interrupts only on one core.
- ```It slows interrupt response time``` <- Disadvantage
- ```It is efficient as it disables preemption and monopolises all of the CPUs``` <- No, comment will be added!
- ```All of the above.```
- ```None of the above ``` <- **Correct**