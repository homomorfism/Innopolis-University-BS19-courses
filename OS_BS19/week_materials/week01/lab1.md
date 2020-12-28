
#### Exercise 1

Create directory “week1” in home directory.

``` shell
mkdir ~/week1
cd ~/week1
```

List entries in /usr/bin that contain “gcc” in reverse alphabetical order. Save results in **“~/week1/ex1.txt”**.




#### Solution 1


On my machine, the result of ```to be added command``` is

```
x86_64-linux-gnu-gcc-ranlib-9
x86_64-linux-gnu-gcc-ranlib
x86_64-linux-gnu-gcc-nm-9
x86_64-linux-gnu-gcc-nm
x86_64-linux-gnu-gcc-ar-9
x86_64-linux-gnu-gcc-ar
x86_64-linux-gnu-gcc-9
x86_64-linux-gnu-gcc
gcc-ranlib-9
gcc-ranlib
gcc-nm-9
gcc-nm
gcc-ar-9
gcc-ar
gcc-9
gcc
c99-gcc
c89-gcc
```

---

#### Exercise 2

Try some commands and save history to **“~/week1/ex2.txt”**.

```history > ex2.txt```



#### Solution 2

No comments, do whatever you want

---

#### Exercise 3

Write a shell script **“ex3.sh”** that prints time (use ```date``` command), then sleep for 3 seconds (use ```sleep 3```) and prints time again. Run script with:

```sh ex3.sh```




#### Solution 3

Just simply repeat ```date``` and ```sleep n``` commands 3 times.

```
date
sleep 3
date
```

---

#### Exercise 4

Write “Hello world” in the C language. Create source file: ```gedit ~/week1/main.c```

Write program:

```c
#include <stdio.h>
int main()
{
	printf(“Hello World”);
	return 0;
}
```



#### Solution 4

Create black file, write there command, compile and run it:
```
gcc main.c -o main
./main
```

or
```
gcc -o main main.c
./main
```

