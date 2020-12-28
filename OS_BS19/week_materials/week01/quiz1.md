
####  Task 1
What is the correct value to return to the operating system upon the **successful completion** of a program?
Select one:

- ```0``` <- **Correct** (macros ```EXIS_SUCCESS``` equals to ```1```)
- ```Programs do not return a value.```
- ```1```
- ```-1```

---

#### Task 2
What is the only function all **C** programs **must contain**? Select one:
- ```main()``` <- **Correct** (```int main() {}``` is entry point for executing program in C)
- ```system()```
- ```program()```
- ```start()```

---

#### Task 3

What punctuation is used to signal the **beginning** and **end** of **code blocks**? Select one:

- ```( and )```
- ```BEGIN and END```
- ```-> and <-```
- ```{ and }```  <- **Correct**

---


#### Task 4

What punctuation **ends** most lines of C code? Select one:
- ```.```
- ```:```
- ```;```  <- **Correct**
- ```'```

---

#### Task 5

Which of the following is a **correct comment**? Select one:
- ```/* Comment */ ``` <- **Correct**
- ```** Comment **```
- ```*/ Comments */```
- ```{ Comment }```

---

#### Task 6

Which of the following is **not** a correct variable **type**?

Select one:
- ```float```
- ```real``` <- **Correct**
- ```int```
- ```double```
- ```All of them are correct```

---

#### Task 7

Which of the following is the **correct** operator **to compare** two variables?

Select one:
- ```=```
- ```==``` <- **Correct**
- ```:=```
- ```equal```

---

#### Task 8

Which of the following shows the **correct** syntax for an **if** statement?
Select one:
- ```if { expression }```
- ```if ( expression )``` <- **Correct**
- ```expression if```
- ```if expression```

---

#### Task 9

Which of the following is **TRUE**? (Means correct declaration)
Select one:
- ```1```
- ```42```
- ```.1```
- ```-1```
- ```All of the above``` <- **Correct** (obviously)

---

#### Task 10

Evaluate ```!(1 && !(0 || 1))```. Select one:

- ```Unevaluatable```
- ```TRUE``` <- **Correct** (```!(1 && !(0 || 1)) = !(1 && !1) = !(1 && 0) = !0 = 1```)
- ```FALSE```

---

#### Task 11

What is the **final value** of x when the next code is run?

```
int x;
for(x=0; x<10; x++) {}
```
Select one:
- ```10``` <- **Correct** (it will be executed 10 times -> ```x = 10```)
- ```9```
- ```0```
- ```1```

---

#### Task 12

**When** will the following code block execute?

```while (x < 100) ```

Select one:
- ```While it wishes```
- ```When x is less than one hundred ``` <- **Correct** (obviously)
- ```When x is greater than one hundred```
- ```When x is equal to one hundred```

---

#### Task 13

Which is **not** a loop structure?

Select one:
- ```for```
- ```repeat ... until``` <- **Correct**
- ```do ... while```
- ```while```

---

#### Task 14

How many **times** is a do-while loop guaranteed to loop?

Select one:
- ```1``` <- **Correct**
- ```0```
- ```Variable```
- ```Infinitely```

---

#### Task 15

Which is **not** a proper prototype?

Select one:
- ```int funct(char x, char y);```
- ```double funct(char x)``` <- **Correct** (missing parentheses).
- ```All of them are wrong```
- ```char x();```
- ```void funct();```

---

#### Task 16

What is the **return type** of the function with prototype:

```int func(char x, float v, double t); ```

Select one:
- ```char```
- ```int``` <- **Correct** ( function indeed return ```int``` value)
- ```float```
- ```double```

---

#### Task 17

Which of the following is a **valid function call** (assuming the function exists)? Select one:
- ```funct x, y;```
- ```funct(); ``` <- **Correct** (in parenthesis no parameters inputs)
- ```funct```
- ```int funct();```

---

#### Task 18

Which of the following is a **complete function**? Select one:

- ```void funct(int) { printf("Hello"); ```

- ```int funct();```

- ```int funct(int x) { return x = x + 1; }``` <- **Correct** ( opening/closing curly brackets, has body)

- ```void funct(x) {printf("Hello");}```

---

#### Task 19

Which of the following is the proper **declaration of a pointer**?

Select one:
- ```int &x;```
- ```int x;```
- ```ptr x;```
- ```int *x; ``` <- **Correct** (obviously)

---

#### Task 20

Which of the following gives the **memory address** of integer variable ```a```? Select one:
- ```a;```
- ```address(a);```
- ```*a;```
- ```&a;``` <- **Correct** (we add ```&``` to variable to get the address of variable, where it is located)

---

#### Task 21

Which of the following gives the **memory address** of a variable pointed to by pointer ```a```? Select one:
- ```address(a);```
- ```a;``` <- **Correct** (```a``` is a pointer variable - it already contains the address of variable, pointed by ```a```)
- ```&a;```
- ```*a;```

---

#### Task 22

Which of the following gives the **value** stored at the address pointed to by pointer ```a```? Select one:
- ```&a;```
- ```val(a);```
- ```*a;``` <- **Correct** (if ```a``` is of ```T*``` type, then ```*a``` is value the pointer is stored)
- ```a;```


---


#### Task 23

Which of the following is a suitable system call to **allocate** memory in C? Select one:
- ```create```
- ```new```
- ```malloc``` <- **Correct** (```malloc```, ```calloc``` are used for allocating memory in _C_).
- ```value```

---

#### Task 24

Which of the following is a suitable system call to **deallocate** memory in _C_?

Select one:
- ```remove```
- ```clear```
- ```delete```
- ```free``` <- **Correct**(```free(T*)``` deallocate memory in _C_).

---

#### Task 25

Assume that we have a **struct** with a **field** var and a variable b of such struct. How can we **access** the field var of b?

Select one:
- ```b.var;```  <- **Correct** (```b``` is of type ```struct T```, that's why for accessing fields we use ```.``` operator).
- ```b->var;```
- ```b>var;```
- ```b-var;```

---

#### Task 26

Assume that we have a **struct** with a field var and a variable b of type **pointer** to such struct. How can I **access** the field var through b? Select one:
- ```b>var;```
- ```b-var;```
- ```b.var;```
- ```b->var;``` <- **Correct** (```b``` is of type ```struct T*```, that's why for accessing fields we use ```->``` operator).

---

#### Task 27

Which of the following is a **properly defined struct**? Select one:
- ```struct a_struct {int a;}; ``` <- **Correct** (obviously, revise _C_ syntactics).
- ```struct {int a;}```
- ```struct a_struct int a;```
- ```struct a_struct {int a;}```

---

#### Task 28

Which properly declares a **variable** of **struct foo**? Select one:
- ```foo;```
- ```int foo;```
- ```struct foo var; ``` <- **Correct** (idk why)
- ```struct foo;```







