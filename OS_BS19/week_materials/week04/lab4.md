#### Exercise 1

Create a program that declares a variable n,
forks a new process and prints ```“Hello from
parent [PID - n]”``` and ```“Hello from child [PID -
n]”``` from parent and child processes
respectively. Run it 10 times and explain the
output
- Hint: to run it N times you can write a shell
script


#### Solution 1

Each process that we create has his unique number, that's why pid of each created process is incrementing

- ex1.c

```c
#include <stdio.h>
#include <sys/types.h>

int main() {
	int n;
	pid_t p_id = fork();

	if (p_id == 0) {
		printf("Hello from child [%d - %d]\n", getpid(), n);
	} else {
		printf("Hello from parent [%d - %d]\n", getpid(), n);
	}
}
```

- ex1.sh

```for i in {1..10}; do ./ex1; done```

---

#### Exercise 2

Write a program that calls ```fork()``` in a loop 3
times and sleeps for 5 seconds. Run the
program in background and run pstree
command several times. Look at the output
and tell how many processes are created.
Explain the result.
 Change the program so that it would call ```fork()```
5 times. See how the result changes



#### Solution 2

We are creating recursively in total 8 processes:
- when creating each process the instructions are also copied, so:
    * "main" process in loop creates 3 process:
    * first process creates 2 child processes (first iteration is completes, needed 2), and first child create also another process
    * second process created 1 child process (two iterations are gone), and this child also created one more child process (thrird iteration)
    * third process does not create anything (three interations are gone)

```c
#include <stdio.h>
#include <sys/types.h>
#include <unistd.h>

int main() {
    for (int i = 0; i < 3; ++i) {
        fork();
        sleep(5);
    }
}
```

---

#### Exercise 3

Write your own simplistic shell. It should read user input and be able to run a command without parameters, such as ```pwd, ls, top, pstree``` and so on
- Hint: use ```man system```



#### Solution 3

```system``` is used for executing instructions from shell

```c
#include <stdio.h>

int main() {
	char buf[200];
	while(1) {
		scanf("%s", buf);
		system(buf);
	}
}
```

---

#### Exercise 4

Extend your previous code to handle
commands with parameters and running
processes in background
- Hint: use ```man fork``` and ```man execve```


#### Solution 4

The function ```read_cmd``` parses input line into words & returns array on strings, which will be executing in the child process.

Note: it is better to use ```scanf``` instead of ```fgets```.

```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <sys/types.h>
#include <unistd.h>

char **read_cmd() {
    char** args = (char**)malloc(sizeof(char*) * 100);


    char buf[100];
    fgets(buf, 100, stdin);
    //printf("Entered string:%s, length:%llu", buf, strlen(buf));

    int curr_word = 0, curr_letter = 0;
    args[curr_word] = (char*)malloc(sizeof(char) * 100);

    for (int i = 0; i < strlen(buf); ++i) {
        char symbol = buf[i];

        if (symbol == ' ') {
            args[curr_word][curr_letter] = '\n';
            curr_word++;
            args[curr_word] = (char*)malloc(sizeof(char) * 100);
            curr_letter = 0;

            continue;
        }

        if (symbol == '\n') {
            args[curr_word][curr_letter] = '\n';
            args[curr_word + 1] = (char*)0;
            break;
        }

        args[curr_word][curr_letter] = symbol;
        curr_letter++;

    }
    return args;
}

int main() {

	while(1) {
		char **args = read_cmd();

		int pid = fork();
		if (pid == 0) {
			execve(args[0], args, (char*)0);
		}
	}
}
```


