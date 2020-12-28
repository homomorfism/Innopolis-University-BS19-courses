#### Exercise 1

Write a program to simulate the first come, first served (FCFS) algorithm.
-  The implementation should show the following
metrics
    * Completion time(CT)
    *  Turn around time(TAT)
    * Waiting time(WT)
    * Average Turnaround time
    * Average waiting time
    
- The program should accept number of processes, arrival time and burst time.

#### Solution 1

Please add comments here!
1. We sort input values by time of arrival
2. Let's go one by one:
    * We give each process a quantim
    * If quantum exceeded and burst time not -> switch to another process
    * Else -> mark process inactive and go to next process
 3. Calculate needed metrics 


#### Exercise 2 