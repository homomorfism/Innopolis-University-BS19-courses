
#### Exercise 1
+ Use `size` shell command to determine the size of text, data and bss segments of any of your programs. Save the output to file ex1/txt

#### Solution 1

```console
$ size ex2.out
   text	   data	    bss	    dec	    hex	filename
   3165	    632	      8	   3805	    edd	ex2.out
```

#### Exercise 2

+ Write a C program that dynamically allocates memory for an array of `N` integers, fills the array with incremental values starting from 0, prints the array and deallocates the memory. 

+ Program should prompt the user to enter `N` before allocating the memory.

#### Solution 2

```c

#include <stdio.h>
#include <stdlib.h>

int main() {
    int N;

    // prompt the user to enter N
    scanf("%d", &N);

    // dynamically allocate memory for an array of N integers
    int *array = malloc(N * sizeof(int));

    // fill the array with incremental values starting from 0
    for (int i = 0; i < N; i++) {
        array[i] = i;
    }

    // print the array
    for (int i = 0; i < N; i++) {
        printf("%d ", array[i]);
    }
    printf("\n");

    // deallocate the memory
    free(array);
}
```

#### Exercise 3

+ Complete the following code template according to the comments. The purpose of the program is to create an initial array of a user-specified size, then dynamically resize the array to a new user-specified size.


#### Solution 3

```c
#include <stdlib.h>
#include <stdio.h>

// Enter original array size:5
// 100 100 100 100 100 
// Enter new array size: 7
// 100 100 100 100 100 0 0

int main(){
	//Allows you to generate random number
	srand(time(NULL));

	// Allows user to specify the original array size, stored in variable n1.
	printf("Enter original array size:");
	int n1=0;
	scanf("%d",&n1);

	//Create a new array of n1 ints
	int* a1 = malloc(n1 * sizeof(int));
	int i;
	for (i = 0; i < n1; i++){
		//Set each value in a1 to 100
		a1[i] = 100;
		
		//Print each element out (to make sure things look right)
		printf("%d ", a1[i]);
	}

	//User specifies the new array size, stored in variable n2.
	printf("\nEnter new array size: ");
	int n2=0;
	scanf("%d",&n2);

	//Dynamically change the array to size n2
	a1 = realloc(a1, n2 * sizeof(int));

	//If the new array is a larger size, set all new members to 0. Reason: dont want to use uninitialized variables.
    for (int i = n1; i < n2; i++)
        a1[i] = 0;
    
	for(i = 0; i < n2; i++){
		//Print each element out (to make sure things look right)
		printf("%d ", a1[i]);
	}
	printf("\n");
	
	//Done with array now, done with program :D
	
	return 0;
}
```

#### Exercise 4

Write your own `realloc()` function using `malloc()` and `free()`

+ `realloc()` changes the size of the memory block pointed to by ptrto size bytes. The contents will be unchanged in the range from the start of the region up to the minimum of the old and new sizes.
+ Newly allocated memory will be uninitialized
+ If ptris `NULL`, the call is equivalent to `malloc(size)`
+ If size is equal to zero, the call is equivalent to free(ptr)
+ Unless ptris NULL, it must have been returned by an earlier call to `malloc()`, `calloc()` or `realloc()`

#### Solution 4

```c
#include <stdlib.h>
#include <stdio.h>
#include <malloc.h>
#include <string.h>


int min(int a,int b){
    // return min of two integers
    return a > b ? b : a;
}

void *custom_realloc(void *ptr, int size){
    void *new = NULL;

    if (size > 0){
        int prev_size;
        // First, need to get prev size of pointer
        if (ptr == NULL) {
            prev_size = 0;
        }
        
        else {
            prev_size = malloc_usable_size(ptr);
        }
        // allocate new block of memory
        new = malloc(size);
        printf("mem copy with prev_size %d and size %d\n", prev_size, size);
        // copy content of `ptr` in `new`
        memcpy(new, ptr, min(prev_size, size));
    }

    free(ptr);
    return new;
}


int main(int argc, char const *argv[]){
    
    int N;

    scanf("%d", &N);

    int *array = malloc(N * sizeof(int));
    for (int i = 0; i < N; i++) {
        array[i] = i;
    }

    array = custom_realloc(array, 2*N * sizeof(int));

    for (int i = 0; i < 2*N; i++) {
        printf("%d ", array[i]);
    }
    printf("\n");

    free(array);
}
```

#### Exercise 5
+ Find and fix all the code that generates segmentation faults
```c
#include <stdio.h> 
int main() { 
    char **s;
    char foo[] = "Hello World"; 
    *s = foo;
    printf("s is %s\n”,s);
    s[0] = foo;
    printf("s[0] is %s\n",s[0]);
    return(0);
    }
```
#### Solution 5

```c
#include <stdio.h>
#include <stdlib.h>

int main() {
    // just allocate memory ¯\_(ツ)_/¯
    char **s = malloc(sizeof(char *));
    char foo[] = "Hello World";
    *s = foo;
    printf("s is %s\n", s); // should it be %p instead of %s
    s[0] = foo;
    printf("s[0] is %s\n",s[0]);
    return(0);
}
```