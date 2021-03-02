---
layout: lab
num: lab02
ready: true
desc: "Trie"
assigned: 2021-01-28 9:00:00.00-8
due: 2021-02-03 23:59:00.00-8
---

# Goals
By the end of this lab, given a description of a class containing data members and methods, you will be able to:
* Learn a new data structure called Trie
* Write the Big-3 for the class
* Implement some class methods using recursion

For this lab, you will only need to upload your **trie.cpp** to Gradescope, so please do not modify any other files. 

#Step by Step

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

[Lab02 Files](https://github.com/ucsb-cs24-kozerawski-w21/lab02_data)

You should see a listing of several C++ files. Please copy those files into your local lab02 Github repo directory.

If so, you are ready to move on.

## Step 2: Understand the Code and Finish trie.cpp 
Trie is a data structure that is used to save a word list efficiently. Its introduction can be found [here](https://www.youtube.com/watch?v=-urNrIAQnNo). And another visualization tool of Trie structure can be found [here](https://www.cs.usfca.edu/~galles/visualization/Trie.html)

In this lab, you will implement the Trie structure and some algorithms to manipulate it. The declaration of Trie structure is in the head file ‘trie.hpp’. The default constructor, copy constructor, destructor, overloaded ‘=’ operator, the functions used to insert a word, to check if a word is in the Trie, to get one word with a given prefix, are to be implemented in the file ‘trie.cpp’. There also include two functions loading a Trie from in-stream and a file. The details of these functions can be found in the given ‘trie.cpp’ file. 

In these implementations, neither the length of the word nor the length of the input string is specified. That means recursion could be used for the trie structure. **So as a hint, most of the functions are recursive.** After you’ve designed the functions in ‘trie.cpp’, which should be submitted on Gradescope, you should write a test file to check if they are correct.

* Trie()
	* The default constructor that initializes the ‘roots’ array to be all NULL pointers.
* Trie(Trie const& other)
	* The copy constructor that copies ‘other’ into ‘this’;
* ~Trie()
	* The destructor that deallocates memory space in the Trie structure.
* Trie& operator=(Trie const& other)
	* Similar to the copy constructor, it sets the current trie structure identical to ‘other’.
* void insert(char const* const str)
	* Insert a word in ‘str’ into Trie.  Ignores the other characters than letters.
* bool check(char const* const str) const
	* Check if the word in ‘str’ exists in Trie.
* char* firstWithPrefix(char const* const str,unsigned depth) const
	* Returns the first word with a given prefix in ‘str’. ‘depth’ is by default 0 and has no specific functionality here. For example, if there are ‘apple’ and ‘apply’ in the Trie, and the prefix is ‘a’, ‘ap’, ‘app’ or ‘appl’, you should just return the first one ‘apple’ according to the alphabetical order.

**The input word may contain any character, including special characters. However, we only want to store letters of alphabets to tries and ignore any other characters. More specific implementation hints can be found in the comments in trie.cpp file. Please consider the input ‘str’ can also be NULL or an empty string, “”. You will also handle cases where the prefix ‘str’ has a length longer than the word itself.**

## Step 3: Test Your Code and Upload to Gradescope
The Autograder will use some test cases to check if your implementations are correct. In order to verify them, you’ll need to write your own test code, which can be a ‘main’ function to print out the results, before the submission. Then, write a Makefile to link all dependencies to make and run your test. The lab assignment “Lab02” should appear in your Gradescope dashboard in CS 24. If you haven’t submitted anything for this assignment yet, Gradescope will prompt you to upload your files. For this lab, you will only need to upload your modified file (i.e. trie.cpp). If you already submitted something on Gradescope, it will take you to their “Autograder Results” page. There is a “Resubmit” button on the bottom right that will allow you to update the files for your submission. For this lab, if everything is correct, you’ll see a successful submission passing all of the Autograder tests.


**Remember to add your partner to Groups Members for this submission on Gradescope if applicable. At this point, if you worked in a pair, it is a good idea for both partners to log into Gradescope and check if you can see the uploaded files for Lab02.**

