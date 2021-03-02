---
layout: lab
num: lab03
ready: true
desc: "Using gdb"
assigned: 2021-02-18 9:00:00.00-8
due: 2021-02-24 23:59:00.00-8
---

# Goals for this lab

By the time you have completed this lab, you should be able to

* Learn to debug your program using basic gdb commands


# Step by Step

## Step 0: Getting Started

This lab may be done solo, or in pairs.
Before you begin working on the lab, please decide if you will work solo or with a partner.
As stated in previous labs, there are a few requirements you must follow if you decide to work with a partner. I will re-iterate them here:
* Your partner must be enrolled in the same lab section as you.
* You and your partner must agree to work together outside of the lab section in case you do not finish the lab during your lab section. You must agree to reserve at least two hours outside of the lab section to work together if needed. You are responsible for exchanging contact information in case you need to reach your partner.
* If you choose to work with a partner for a future lab where pair programming is allowed, then you must choose a partner you have not worked with before.
* You MUST add your partner on Gradescope when submitting your work EACH TIME you submit a file(s). After uploading your file(s) on Gradescope, there is a “Group Members” link at the bottom (or “Add Group Member” under “Groups”) where you can select the partner you are working with. Whoever uploaded the submission must make sure your partner is part of your Group. Click on “Group Members” -> “Add Member” and select your partner from the list.
* You must write your Name(s) and Perm number on each file submitted to Gradescope.
Once you and your partner are in agreement, choose an initial driver and navigator, and have the driver log into their account.



## Step 1: Copying some programs from my directory
Visit the following web link—you may want to use “right-click” (or “control-click” on Mac) to bring up a window where you can open this in a new window or tab:

[Lab03 Files](https://github.com/ucsb-cs24-kozerawski-w21/lab03_data)

You should see a listing of several C++ files. Please copy those files into your local lab02 Github repo directory.

If so, you are ready to move on.


# Step 2: Understand the Code and Fix the list.cpp

This lab is a simplified edition of the linked list compared with the midterm. In addition to fewer methods to be implemented, there’s no cursor in this linked list class, so there are differences when you maintain the list. The declaration of this list is provided in ‘list.hpp’ header file.

As you see in the midterm, to construct a linked list there should be nodes first. Here the ‘Node’ is defined as a struct instead of a class, but it also contains a data field ‘T val’ and a pointer pointing to the next node ‘Node *next’. There are also similar methods in the struct which have already been implemented as you can read in the header file. There’s no ‘InsertAfter()’ method, but you can still create new nodes in the linked list by calling the constructor with arguments or the copy constructor. The static member ‘alloc_cnt’ records how many nodes in total you’ve created in the program. The static variable belongs to the struct (or class) itself but not to any specific object. You may not use it in your implementation of the list.
To practice your debugging skill, in this lab you will be provided with a version of draft codes list.cpp which have some bugs. You can edit on it, correct those bugs, and submit on gradescope. Some brief instructions of how to use gdb will be provided below.

In this lab, you will need to run your code in CSIL since GDB debugger and Googletest (gtest) are preinstalled. First, clone the starter files to CSIL. There are four files, and you only need to debug and submit **list.cpp** to Gradescope. We provide you Makefile and some test cases in test.cpp. Please have a look at the sample test cases and feel free to add more. To run the tests, use command **make** and **./test**. 

We will introduce GDB (the GNU Project debugger) in this lab. It is a very powerful tool for analyzing what your program is doing at run-time. Here are some helpful tutorials, [link 1](https://ucsb-cs32.github.io/topics/tools_gdb/) and [link 2](https://www.youtube.com/watch?v=OpVMB7DNlmY&t=282s&ab_channel=RobertMartin). Before using GDB, make sure you have -g flag in CXXFLAGS in your Makefile. **Every time you change your Makefile you should always do a make clean first to rebuild your tests.** After **make**, use **gdb ./test** to start debugging! There are some useful GDB commands listed next.

## GDB Commands Summary
The following is a list of the most useful commands inside the gdb - [also available at this link](http://www.cs.uregina.ca/Links/class-info/330/CompileDebug/170_gdb.html).
gdb provides online documentation. Just typing help, you will obtain a list of topics.

**file**
"file executable" specifies which program you want to debug.

**run**
"run" starts the program running under gdb. The program is the one that you have previously selected with the file command, or on the unix command line when you started gdb. You can give command line arguments to your program on the gdb command line. You can do this the same way you would on the unix command line, except that you are saying run instead of the program name. For example,

run 5 20 40 60

You can even do input/output redirection: run > outfile.txt.

**list**
"list linenumber" prints out some lines from the source code around linenumber. If you give it the argument function it will print out lines from the beginning of that function.

Just list without any arguments will print out the lines just after the lines that you printed out with the previous list command.

**break**
"break" sets a breakpoint in your program.

A `breakpoint` is a spot in your program where you would like to temporarily stop execution in order to check the values of variables, or to try to find out where the program is crashing, etc.

"break function" sets the breakpoint at the beginning of function. If your code is in multiple files, you might need to specify filename:function.

"break linenumber" or "break filename:linenumber" sets the breakpoint to the given line number in the source file. Execution will stop before that line has been executed.

**delete**
"delete" deletes all breakpoints that you have set. 
"delete number" deletes breakpoint numbered number. You can find out what number each breakpoint is by doing info breakpoints. (The command info can also be used to find out a lot of other stuff. Do help info for more information.)

**clear**
"clear function" deletes the breakpoint set at that function. Similarly for linenumber, filename:function, and filename:linenumber.

**step**
"step" goes ahead and execute the current source line, and then stop execution again before the next source line.

**next**
"next" continues until the next source line in the current function (actually, the current innermost stack frame, to be precise). This is similar to step, except that if the line about to be executed is a function call, then that function call will be completely executed before execution stops again, whereas with step execution will stop at the first line of the function that is called.

**until**
"until" is like next, except that if you are at the end of a loop, "until" will continue execution until the loop is exited, whereas "next" will just take you back up to the beginning of the loop. This is convenient if you want to see what happens after the loop, but don't want to step through every iteration.

**print**
"print expression" prints out the value of the expression, which could be just a variable name. To print out the first 25 (for example) values in an array called list, you would do 
print list[0]@25
 

**quit**
"quit" is used to exit the gdb debugger.


## Implementation Details
* Node<T>* head;
* Node<T>* tail;
	* Pointers pointing to the head and the tail of the list. Same as ‘front’ and ‘rear’ in the midterm.
* List();
	* Constructor. Initializes ‘head’ and ‘tail’ as NULL.
* List(List const& o);
	* Copy constructor. Makes a hard copy of the list ‘o’. You should create a list in ‘this’ of the same size and storing the same data as ‘o’.
* List& operator=(List const& o);
	* Overloaded assignment operator. The difference between the copy constructor is that when ‘this’ list is not empty you should clear it first.
* ~List();
	* Destructor. Clears the list. There’s a ‘clear()’ method in the following. You can just call it here.
* bool empty() const;
	* Checks if ‘this’ list is empty. A non-empty list should have a non-NULL head pointer. And when you maintain the list, an empty list should always have NULL head and tail pointers.
* size_t size() const;
	* Counts the size of the list. You should go from the head node to its next one by one. The tail node’s ‘next’ pointer is of course NULL.
* T& front() const;
	* Returns the data ‘val’ in the head node.
* T& back() const;
	* Returns the data ‘val’ in the tail node.
* T& at(size_t index) const;
	* Returns the data ‘val’ in the index-th node. Since there’s no cursor in the list, you should go from the head one by one to the index-th node first.
* void clear();
	* Clears the whole list.
* void insert(size_t index, T const& value);
	* Inserts a node containing data ‘value’ at the position ‘index’. First go to the position ‘index - 1’, then create a new node by calling the constructor, and link it into the list. Remember to maintain the ‘head’ and ‘tail’ pointers.
* void pop_front();
	* Deletes the head node.
* void push_front(T const& value);
	* Creates a new head node and stores the data ‘value’.
* void pop_back();
	* Deletes the tail node. You have to go to the one before the tail first.
* void push_back(T const& value);
	* Creates a new tail node and stores the data ‘value’.
* void erase(size_t index);
	* Erases (deletes) the node at the position ‘index’.
* void erase(size_t first, size_t count);
	* Erases (deletes) the ‘count’ number of nodes after (including) the node at position ‘first’.
* friend bool operator==(List<C> const& lhs, List<C> const& rhs);
	* Judges if two lists ‘lhs’ and ‘rhs’ are identical. Identical means they should have the same length and store the same data.
* void render(std::ostream& out) const;
	* This is an associated method which is used to print out a whole list. The overloaded ‘<<’ operator and it have been implemented in the header file. You can use them for debugging.


## Step 3: Test Your Code and Upload to Gradescope
The Autograder will use some test cases to check if your implementations are correct. In order to verify them, you’ll need to write your own test code, which can be a ‘main’ function to print out the results, before the submission. Then, write a Makefile to link all dependencies to make and run your test. The lab assignment “Lab03” should appear in your Gradescope dashboard in CS 24. If you haven’t submitted anything for this assignment yet, Gradescope will prompt you to upload your files. For this lab, you will only need to upload your modified file (i.e. trie.cpp). If you already submitted something on Gradescope, it will take you to their “Autograder Results” page. There is a “Resubmit” button on the bottom right that will allow you to update the files for your submission. For this lab, if everything is correct, you’ll see a successful submission passing all of the Autograder tests.


**Remember to add your partner to Groups Members for this submission on Gradescope if applicable. At this point, if you worked in a pair, it is a good idea for both partners to log into Gradescope and check if you can see the uploaded files for Lab03.**
