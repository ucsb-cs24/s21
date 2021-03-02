---
layout: lab
num: lab04
ready: true
desc: "Evaluating postfix and prefix expressions with stacks"
assigned: 2021-02-25 9:00:00.00-8
due: 2021-03-03 23:59:00.00-8
---

# Goals for this lab

By the time you have completed this lab, you should be able to

* Understand the meaning and purpose of typical stack operations
* Evaluate expressions in postfix  form and prefix form
* Convert between prefix notation and postfix notation

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

[Lab04 Files](https://github.com/ucsb-cs24-kozerawski-w21/lab04_data)

You should see a listing of several C++ files. Please copy those files into your local lab04 Github repo directory.

If so, you are ready to move on.


# Step 2: Understand the code in given files

In this lab, you will be given three header files  (i.e. operators.hpp, postfix.hpp and prefix.hpp). You need to first understand the code to finish the postfix.cpp and prefix.cpp. As you can see from the given files, you should make use of the **stacks** to implement several methods to **evaluate the postfix and prefix expressions and convert between postfix notation and prefix notation.**
The descriptions of the functionalities of the methods are listed below:
* **float evalPostfix(char const* s);**    Evaluate the postfix expression;
* **std::string postfixToPrefix(char const* s);**   converting the postfix to prefix notation;
* **float evalPrefix(char const* s);**    Evaluate the prefix expression;
* **std::string prefixToPostfix(char const* s);**  converting the prefix to postfix notation; 


# Step 3: Learn the concepts of postfix and prefix expression and implementation with stacks

**Infix:** We are most accustomed to arithmetic expressions in infix form - number operator number - where the operator is between the two numbers, as in 7 + 5. With this form, it is necessary to consider the precedence of operators and the effects of parentheses, which makes 7 + 5 * 3 different than (7 + 5) * 3, for example.

**Postfix:** An expression is called the postfix expression if the operator appears in the expression after the operands. Simply of the form (operand1 operand2 operator). The first infix expression above translates to 7 5 + in postfix, the second one translates to 7 5 3 * + and the third one is 7 5 + 3 * in postfix form.
Example : AB+CD-* (Infix : (A+B) * (C-D) )

**Prefix:** An expression is called the prefix expression if the operator appears in the expression before the operands. Simply of the form (operator operand1 operand2).The first infix expression above translates to + 7 5 in postfix, the second one translates to + 7 *5 3 and the third one is * + 7 5 3 in postfix form.
Example : *+AB-CD (Infix : (A+B) * (C-D) )

**After you understand the basic knowledge of  postfix and prefix expressions, you should learn how to implement different algorithms with stacks. We will offer you two algorithms for reference.**


**Postfix Expression Evaluation Algorithm**
* create a stack for operands (just need this one stack)
* loop through all the tokens in the expression:
	* identify the token
	* if token is an operand: push it on the stack
	* if token is an operator (means time to perform a calculation):
		* pop an operand - last one pushed, so it is on right side of calculation
		* pop a second operand - for the left side of the calculation
		* perform the calculation, and push the result on the stack
* Done: result is on top of stack

Exceptions would be thrown if (a) a token cannot be identified, (b) there are less than two operands on the stack when an operator is encountered, or (c) the stack does not have exactly one operand left on it at the end of the loop.

**Algorithm for Converting Prefix to Postfix:** 
* Read the Prefix expression in reverse order (from right to left)
* If the symbol is an operand, then push it onto the Stack
* If the symbol is an operator, then pop two operands from the Stack 
	* Create a string by concatenating the two operands and the operator after them. 
	string = operand1 + operand2 + operator 
	And push the resultant string back to Stack
* Repeat the above steps until the end of the Prefix expression.


# Step 4: Finish the postfix.cpp and prefix.cpp

Now you can try to finish your postfix.cpp and prefix.cpp. Please read the helpful notes as follows and implement all of the methods with stacks.

**Some helpful notes:**
* There is only one `'\0'` at the end of the string. Be careful to not increment past it! (You may want to use a `while` loop rather than a `for` loop.)
* The `readFloat` function in `operators.hpp` is a version of `std::strtof` with corrected constness. Look up `std::strtof` to determine its behaviour!
* Floating-point numbers, as accepted by your spec, may start with a `-`. Make sure your program does not mix up those floats with that operator!
* When translating prefix to postfix or postfix to prefix, trim whitespace from the beginning and end of both the input and output. You only care about the equation, not how many spaces came before it!

# Step 5: Test Your Code and Upload to Gradescope

The Autograder will use some test cases to check if your implementations are correct. In order to verify them, you’ll need to write your own test code, which can be a ‘main’ function to print out the results, before the submission. Then, write a Makefile to link all dependencies to make and run your test. 
The lab assignment “Lab04” should appear in your Gradescope dashboard in CS 24. If you haven’t submitted anything for this assignment yet, Gradescope will prompt you to upload your files. **For this lab, you will only need to upload your modified files (i.e.postfix.cpp and prefix.cpp).** If you already submitted something on Gradescope, it will take you to their “Autograder Results” page. There is a “Resubmit” button on the bottom right that will allow you to update the files for your submission. For this lab, if everything is correct, you’ll see a successful submission passing all of the Autograder tests.

**Remember to add your partner to Groups Members for this submission on Gradescope if applicable. At this point, if you worked in a pair, it is a good idea for both partners to log into Gradescope and check if you can see the uploaded files for Lab04.**
