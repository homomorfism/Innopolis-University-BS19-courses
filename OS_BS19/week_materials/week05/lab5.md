#### Exercise 1

Create a program that runs N threads similar to one
explained in the tutorial. Each thread should output its
number and some text, then exit
- Main program should inform about thread creation
- Run the program and discuss the results
- Fix the program to force the order to be strictly thread
1 created, thread 1 prints message, thread 1 exits and
so on
- Hint: use gcc -pthread ex1.c to compile

#### Solution 1

Explanation will be added!

```c
#include <stdio.h>
#include <pthread.h>
#include <stdlib.h>
#include <unistd.h>

#define N 5

pthread_t thread_id[N];

void* print(int i) {
	printf("This is thread %d!\n", i);
	pthread_exit(NULL);
}

int main(int argc, char const *argv[]) {
	int status;

	for (int i = 0; i < N; ++i) {
	
		status = pthread_create(&thread_id[i], NULL, print, i);

		if (status) {
			printf("Error!\n");
			exit(1);
		}
		printf("The thread %d was created!\n", i);

		pthread_join(thread_id[i], NULL);

	}

	pthread_exit(NULL);
}
```

---

#### Exercise 2


 Write a shell script that produces a file of sequential numbers by reading the last number in the file, adding 1 to it, and then appending it to the file. Run one instance of the script in the background and one in the foreground, each accessing the same file
- How long does it take before a race condition manifests
itself? What is the critical region?
- Modify the script to prevent the race
- Hint: use ln file file.lock to lock the data file


#### Solution 2 

Explanation will be added!

```bash
while : 
do
	if ln ex2.txt ex2.lock; then
	    end=$(tail -n 1 < ex2.lock)
	    ((end = end + 1))
	    echo "$end" > ex2.lock
	    rm ex2.lock
	fi
done

```

---

#### Exercise 3

Write a producer-consumer problem that uses threads and shares a common buffer. However, do not use semaphores or any other synchronization primitives to guard the shared data structures. Just let each thread access them when it wants to. Use sleep and wakeup to handle the full and empty conditions. See how long it takes for a fatal race condition to occur. For example, you might have the producer print a number once in a while. Do not print more than one number every minute because the I/O could affect the race conditions.
- Hint: you can use use global variables to
implement sleep and wakeup routines
- Normally, it is done by using condition variables


#### Solution 3

German's solution:


```c
#include <stdio.h>
#include <pthread.h>
#include <unistd.h>

#define BUFFER_SIZE 1337

pthread_cond_t FULL, EMPTY;
int count = 0;

void *producer_routine() {
  while (1) {
    if (count == BUFFER_SIZE) {
      printf("Producer is tired :c\nGonna sleep a bit!\n");
      sleep(1);
    }
    ++count;
    printf("Producer made item number %d!\n", count);
    if (count == 1) { // we have at least one product
      printf("Get item, consumer!\n");
      pthread_cond_signal(&FULL);
    }
  }
}

void *consumer_routine() {
  while (1) {
    if (count == 0) {
      printf("Why did you wake me up? \nThere is nothing\n");
      sleep(1);
    }
    --count;
    printf("Consumber got item number %d!\n", count);
    if (count == BUFFER_SIZE - 1) { // we have not full buffer, fire up producer
      printf("Need item, producer!\n");
      pthread_cond_signal(&EMPTY);
    }
  }
}

void main() {
  pthread_t producer_thread, consumer_thread;

  pthread_cond_init(&FULL, 0);
  pthread_cond_init(&EMPTY, 0);

  pthread_create(&producer_thread, NULL, producer_routine, NULL);
  pthread_create(&consumer_thread, NULL, consumer_routine, NULL);

  pthread_join(producer_thread, 0);
  pthread_join(consumer_thread, 0);
}

```


#### Exercise 4


#### Solution 4


