  

#### Task 1

What is the output of this C code?

```c
#include <stdio.h>
void main()
{
   int a[3] = {1, 2, 3};
   int *p = a;
   printf("%p  %p", p, a);
}
```

Select one:
- ```Compile time error```
- ```Nothing```
- ```Different addresses are printed.```
- ```Same address is printed. ``` <- **Correct**

```a``` is a pointer to array, and ```p = a``` => they have the same addresses.

 
---

#### Task 2

What is the output of this C code?

```c
#include <stdio.h>
void main()
{
   char *s = "hello";
   char *p = s;
   printf("%p\t%p", p, s);
}
```
Select one:
- ```Same address is printed ``` <- **Correct**
- ```Nothing```
- ```Run time error```
- ```Different addresses are printed```

```a``` is a pointer to char string, and ```p = a``` => they have the same addresses.

  
---

#### Task 3

What is the output of this C code?

```c
#include <stdio.h>
void main()
{
   char *s = "hello";
   char *p = s;
   printf("%c\t%c", p[0], s[1]);
}
```

Select one:
- ```h l```
- ```h h```
- ```h e ``` <- **Correct**
- ```Run time error```

```a``` is a pointer to char string, and ```p = a``` => they have the same addresses.

```a[0] = p[0] = 'h'```

```a[1] = p[1] = 'e'```

---

#### Task 4

What is the output of this C code?

```c
#include <stdio.h>
void main()
{
   char *s= "hello";
   char *p = s;
   printf("%c\t%c", *(p + 3),  s[1]);
}
```

Select one:
- ```h e```
- ```l e ``` <- **Correct**
- ```l l```
- ```l o```

```*(p + 3) = p[3] = s[3] = 'l'```

```s[1] = 'e'```

---

#### Task 5

What is the output of the code given below?

```c
#include <stdio.h>
int main()
{
   int ary[4] = {1, 2, 3, 4};
   int *p = ary + 3;
   printf("%d %d\n", p[-2], ary[*p]);
}
```

Select one:
- ```2 4```
- ```2 3```
- ```2 <garbage> (or 0) ``` <- **Correct**
- ```Compile time error```

Explanation will be added!

---

#### Task 6

Consider a compiler where int takes 4 bytes, char takes 1 byte and pointer takes 4 bytes.

```c
#include <stdio.h>
int main()
{
    int arri[] = {1, 2 ,3};
    int *ptri = arri;

    char arrc[] = {1, 2 ,3};
    char *ptrc = arrc;

    printf("sizeof arri[] = %lu ", sizeof(arri));
    printf("sizeof ptri = %lu ", sizeof(ptri));

    printf("sizeof arrc[] = %lu ", sizeof(arrc));
    printf("sizeof ptrc = %lu ", sizeof(ptrc));

    return 0;
}
```

Select one:
- ```sizeof arri[] = 3 sizeof ptri = 4 sizeof arrc[] = 3 sizeof ptrc = 1```
- ```sizeof arri[] = 3 sizeof ptri = 4 sizeof arrc[] = 3 sizeof ptrc = 4```
- ```sizeof arri[] = 12 sizeof ptri = 4 sizeof arrc[] = 3 sizeof ptrc = 1```
- ```sizeof arri[] = 12 sizeof ptri = 4 sizeof arrc[] = 3 sizeof ptrc = 4 ``` <- **Correct**

Size of array ```arri``` = 3 * sizeof(```int```) = 12 bytes

Size of pointer ```ptri``` = sizeof(```int *```) = 4 bytes, because we cast ```int[3]``` to ```int *```.

Size of array ```arrc``` = 3 * sizeof(```char```) = 3 bytes.

Size of pointer ```ptrc``` = sizeof(```char *```) = 4 bytes, as any address pointer.

---

#### Task 7

Which of the following is a properly defined struct?

Select one:
- ```struct {int a;}```
- ```struct a_struct {int a;}```
- ```struct a_struct {int a;};``` <- **Correct**
- ```struct a_struct int a;```

The syntactics of defining struct:

```c
struct [structure tag] {

   member definition;
   member definition;
   ...
   member definition;
} [one or more structure variables];
```

[C - Structures](https://www.tutorialspoint.com/cprogramming/c_structures.htm)