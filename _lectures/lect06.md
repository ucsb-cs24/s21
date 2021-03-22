---
lecture_date: 2021-04-14
num: "lect06"
desc: "Big 3, Operator Oveloading, GDB, intro to pa01"
ready: false
pdfurl: /lectures/CS24_Lecture6.pdf
annotatedpdfurl: /lectures/CS24_Lecture6_ann.pdf
annotatedready: false

---

# Code from lecture
[{{site.lect_repo}}/tree/master/lec-05]({{site.lect_repo}}/tree/master/lec-06)

# Topics
## The big three 
 18 * Constructor
 19     - Default and parameterized constructors (Review)
 20     - Initializing const member variables using initialization lists
 21 * Destructor
 22 * Copy-constructor
 23 * Copy-assignment
 24
 25 ## Operator overloading
 26 * We will overload some common operators for the complex class.

## gdb

* Demo of gdb commands 
 - To use gdb, compile with the -g flag
 - Setting breakpoints (b)
 - Running programs that take arguments within gdb (r arguments)
 - Continue execution until breakpoint is reached (c)
 - Stepping into functions with step (s)
 - Stepping over functions with next (n)
 - Re-running a program (r)
 - Examining local variables  (info locals)
 - Printing the value of variables with print (p)
 - Quitting gdb (q)
 - Debugging segfaults with backtrace (bt)
* Refer to the [gdb cheat sheet](http://darkdust.net/files/GDB%20Cheat%20Sheet.pdf) (handout given in class). More practice in lab 03.

* More on operator overloading
	- ==, !=, << 
	
* Use cases for friend functions
* Review C++ memory management and using valgrind
