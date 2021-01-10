#### Exercise 1


+ There is a command such as `free` but we can get the physical and virtual memory size using the following commands.
    - systeminfo| find "Physical Memory"
    - systeminfo| find "Virtual Memory“

#### Solution 1

```console
$ free
              total        used        free      shared  buff/cache   available
Mem:       16278332     8679360     1244056     1525164     6354916     5607820
Swap:       8192704       35652     8157052
```

#### Exercise 2

+ Write a C program that runs for 10 seconds. Every second it should:
    - allocate 10 MB of memory
    - fill it with zeros
    - sleep for 1 second
+ Compile and run the program in the background (./ex2 &) and run `vmstat1` at the same time. Observe what happens to the memory. Pay attention to siand sofields. 
+ Add comments to your source code with your findings.
+ Hint: use `memset(ptr, value, size)` to fill the allocated memory


#### Solution 2
+ Unfortunately the `amount_to_allocate` needs to be selected for each machine independently
```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <unistd.h>

int main(int argc, char const *argv[]){
    int ONE_MEGABYTE = 1024 * 1024;
    int amount_to_allocate = 1000 * ONE_MEGABYTE;
    for (int i = 0; i < 10; i++){
        char *a = malloc(amount_to_allocate);
        memset(a, 0, amount_to_allocate);
        sleep(1);
    }
    
    return 0;
}
/*
From the man:
si: Amount of memory swapped in from disk (/s).
so: Amount of memory swapped to disk (/s).

So, `si` and `so` start increasing when page swapping starts

procs -----------memory---------- ---swap-- -----io---- -system-- ------cpu-----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa st
 3  0      0 1865408 1360392 4379024    0    0     0     0 12963 13763 10  7 84  0  0
 0  0      0 839288 1360392 4379012    0    0     0     0 12992 15012  9  8 83  0  0
 2  0      0 801236 1360392 4378500    0    0     0     0 12967 14805  6  4 90  0  0
 0  0   1024 192048 1354520 4014564    0  556   288  1040 13398 14774 10 12 78  0  0 <-- swpd, so, si become non zero
 2  0   2816 171260 1257468 3139744   32 1220   524  1220 13181 14161 10 14 76  0  0
 2  0   2816 181984 1250984 3105548    0    4  1184     4 12946 13469 11  5 84  0  0
 0  0  10752 167788 955764 2434292    0 8104     4  8104 13332 14285 10 12 78  0  0
 3  0  19456 137840 526088 1904332   48 8436   180  8436 13752 15498  9 15 77  0  0
 0  0  19968 237064 494584 1827084   28  428  6472   480 13409 14482 12  6 82  1  0
 1  0  31488 231676  41396 1256620   32 11624 13962 11788 16174 15596  9 15 76  1  0
 2  0  31488 10463748  45212 1275216    0    0 21668     0 13682 15220  9  9 80  1  0
*/
```
#### Exercise 3

+ Run `top-d 1` or `top -i1` on macOS
+ Run ex2 program in the background and then run `top`
+ Add comments to your source code with your findings.

#### Solution 3
ex2 uses a lot of CPU and memory :)
##### ex3.txt:
```$
$ top
PID   USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND                                                                                                             
15154 lev       25   5 3076516 2,789g   1188 R  33,4 18,0   0:01.20 ex2 out                                                                        
 8137 lev       20   0 6283576 297688  50404 S  25,2  1,8  17:57.41 zoom                                                                           
10141 lev       20   0 12,115g 229412  56768 S  13,2  1,4   2:55.07 code                                                                           
 4711 lev        9 -11 2130896  11348   6816 S  10,3  0,1   3:40.36 pulseaudio                                                                     
10060 lev       20   0  835136  87172  43940 S   7,3  0,5   0:36.97 code                                                                           
 4519 lev       20   0 1832352 105728  59144 S   6,3  0,6   2:00.96 Xorg                                                                           
10111 lev       20   0  514292  67560  39188 S   4,6  0,4   1:04.63 code                                                                           
 4698 lev       20   0 3945080 167128  42584 S   4,3  1,0   1:50.79 gnome-shell
```

#### Exercise 4

+ Write a C program that runs for 10 seconds. Every second it should:
    - allocate 10 MB of memory
    - fill it with zeros
    
    - print memory usage with `getrusage()` function
    - sleep for 1 second

#### Solution 4

+ I decided to increase amount from 10 MB to 1000 MB
+ `man getrusage`

```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <unistd.h>
#include <sys/resource.h>

int main() {
    int ONE_MEGABYTE = 1024 * 1024;
    int amount_to_allocate = 1000 * ONE_MEGABYTE;
    
    for (int i = 0; i < 10; i++) {
        char *a = malloc(amount_to_allocate);
        memset(a, 0, amount_to_allocate);
        
        // create r variable
        struct rusage *r = malloc(sizeof(struct rusage));
        
        // store resource usage in r variable
        getrusage(RUSAGE_SELF, r);
        
        printf("ru_maxrss: %ld\tru_minflt: %ld\n", r->ru_maxrss, r->ru_minflt);
        sleep(1);
    }

    return 0;
}
```
#### Exercise 5

+ What is the difference between a physical and a virtual address? Describe using your own words. Save your answer to `ex5.txt`

#### Solution 5
##### ex5.txt:
```
Physical address (PA) is exactly the memory of the computer (RAM). 

However, it's hard to work with PA without any abstraction, because you need to work 
with blocks without adjacent addresses. That's why we need Virtual address (VA)

VA is convenient abstraction that allows us to work with memory as 
if it is sequential and continuous. Also VA helps when we need more memory than RAM has
```

#### Exercise 6

+ A machine has 16-bit virtual addresses. Pages are 8 KB. How many entries are needed for a single-level linear page table? Explain your computations. Save your answer to `ex6.txt`

(Hint: Modern Operating Systems, 3.3.2)

#### Solution 6

##### ex6.txt:
```
8KB = 2^13 bytes, it means that for offset we need exactly **13** bits
We have 16 bits for virtual memory, but 13 of them are used for offset, 
so 16-13=3 bits for page number.

    Answer: 2^3 = 8 entries in page table
```