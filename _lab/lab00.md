---
layout: lab
num: lab00
ready: false
desc: "Getting started"
assigned: 2021-03-31 15:00:00.00-8
due: 2021-04-02 23:59:00.00-8
---


# Introduction

Your first lab for this week is an introduction to programming on CSIL and tools for this course. The intended outcomes are:

* Get to know the course staff and help us get to know you
* Learn about the tools you will be using in this class: gradescope and github
* This lab will count towards 2% of your total lab grade. All other labs are weighed equally.

This lab must be completed INDIVIDUALLY. In the subsequent labs you are encouraged to work with your programming partner.
 

# Get setup with the tools for this course

## Create a CoE account if you don't have one already

We encourage you to complete all programming assignments by logging in to the machines in the Computer Science labs, or to connect remotely. To do this you will need a **College of Engineering account**. You can create an account online at <a href="https://accounts.engr.ucsb.edu/create" target="_blank">https://accounts.engr.ucsb.edu/create</a>.

If you are enrolled in <i>any</i> CoE course this quarter (including CS24), you can create your account immediately. If you are not, you will need to contact the ECI Help Desk at <a href="mailto:help@engineering.ucsb.edu">help@engineering.ucsb.edu</a>.

## Get setup with github

We will be using github.com in this course.   We have created an organization called ucsb-cs24-s19-mirza on github.com where you can create repositories (repos) for your assignments in this course.   The advantage of creating private repos under that organization is that the course staff (your instructors, TAs and mentors) will be able to see your code and provide you with help, without you having to do anything special.

To join this organization, you need to do three things.

1. If you don't already have a github.com account, create one on the "free" plan. Visit [www.github.com](www.github.com)

2. If you don't already have your @umail.ucsb.edu email address associated with your github.com account. go to "settings", add that email, and confirm that email address.

3. Visit our [Github Sign Up Tool: https://ucsb-cs-github-linker.herokuapp.com/](https://ucsb-cs-github-linker.herokuapp.com/), login with your github.com account, click "Home", find this course (CS24-S21), and click the "join course button".   That will automatically send you an invitation to join the course organization on github. 

4. Accept the invitation that appears in your browser (from step 3) or log into your account on [www.github.com](www.github.com) to accept the invitation.

## Get setup with gradescope

We will use gradescope to grade all your homeworks, exams and lab/programming assignments. You should have received an email notification with instructions about logging into gradescope.

Log into our class site on[www.gradescope.com](www.gradescope.com): {{site.name}}    and navigate to the lab00 assignment

# Implement and submit a simple C++ program 

## Open a Terminal and write a simple "Hello World" program 

Open a **terminal window**, which will be the environment you use to write, compile, and run your programs.

If you are working on your laptop, whether Windows, Mac or Linux, the instructions below will tell you how to connect to `cstl.cs.ucsb.edu`. For now its okay to connect to that server, however in the future please connect to one of the following machines:

* `cstl-01.cs.ucsb.edu`
* `cstl-02.cs.ucsb.edu`, etc.
* etc.
* through `cstl-48.cs.ucsb.edu`

If you are on a Mac laptop, open a terminal and type the 
following ssh command to connect to one of the servers remotely

```
ssh -X yourCoEaccount@cstl-02.cs.ucsb.edu
```
If you are using a Windows, you will need to install the program
[MobaXterm](https://mobaxterm.mobatek.net/)

For more information on how to ssh, please refer to Step 1 of lab00 from
cs16: [https://ucsb-cs16-w19-mirza.github.io/lab/lab00/](https://ucsb-cs16-w19-mirza.github.io/lab/lab00/)

You'll get much better performance on those individual machines, because they are much less heavily loaded and have newer hardware, as compared to `cstl.cs.ucsb.edu`.

## Create cs24 and lab00 directories

Now that your environment is set up, you will need to create a directory that will contain all your work for the course. Then, inside that directory, you will need to create another directory to contain your work for this assignment.

To create your CS24 directory, use the <b>mkdir</b> command. Type the following in the terminal and press enter:

```
$ mkdir cs24
```
Change into that directory and create a lab00 directory

```
$ mkdir lab00
$ cd lab00   
```

Create a new file called <code>hello.cpp</code> using an editor of your choice (either vim or emacs)

Useful links related to emacs

* <a href="https://www.gnu.org/software/emacs/tour/" target="_blank">emacs tour from the GNU organization (makers of emacs)</a>

* <a href="https://www.gnu.org/software/emacs/refcards/pdf/refcard.pdf" target="_blank">emacs commands - a handy reference card</a>

* <a href="http://www.jesshamrick.com/2012/09/10/absolute-beginners-guide-to-emacs" target="_blank">a beginner's guide to emacs</a>

Useful information related to <b>vim</b> for UNIX-based OS

* To customize your vim environment for a better coding experience with C/C++ copy this .vimrc file from the instructor folder to your home folder using the following command:

```
cp /cs/faculty/dimirza/vim-configuration/example_dotvimrc/.vimrc ~/
```

* <a href="http://www.vim.org/about.php" target="_blank">About vim</a>

* <a href="http://tnerual.eriogerg.free.fr/vimqrc.html" target="_blank">vim commands - a handy reference card</a>

* <a href="https://www.fprintf.net/vimCheatSheet.html" target="_blank">another reference cheat sheet for vim</a>

This assignment only needs you to write a program in hello.cpp that prints out two lines on the display, and nothing else. **The output should look exactly as follows** (no space before or after each line, except the 2 newlines):

```
Hello, world!
I am ready for CS24!
```

## Create a repo on github in our class organization

For this lab and all subsequent programming assignments, you should start by creating a repo in the ucsb-cs24-s19-mirza organization following these steps

* Navigate to your dashboard on [www.github.com](www.github.com). From the left drop down menu, select the class organization as shown in the figure below:
![select-org](select-org.png){:height="500px"}

* Click on the green "New repository" button to create a new repository.

* Type the name of your repo following the naming convention lab00_your-github-username. For example if your github username is jgaucho, you should name your repo as lab00_jgaucho. If you are working with a partner, include your partner's github username in the name of the repo. e.g. lab00_jgaucho_alily

* Select the "Private" visibility option so that other students in the org cannot view your code.

* Add the C++ .ignore option from the frop down menu and click on "Create repository". See screenshot below.

![new-repo](enter-org/pic5.png){:height="500px"}


## Upload your code using github's web interface 

* Upload your hello.cpp file to the new repo you created in the previous step. To do this, you should be physically present on a lab machine or in cstl where you have access to a web browser and a local copy of your hello.cpp program. On your web browser, navigate to your repo on github. Click on the "Upload files" button.

* Now either drag and drop the "hello.cpp" file from your machine or use the "Choose your files" option to browse through your local directory and upload the file. Then press the green "Commit new files" button. Navigate back to your repo to see that the hello.cpp file is correctly listed along with the other files. Click on it and you should see your code on github's web interface. Continue to explore the web interface of your github repo. For example, try clicking on the "commits" link in your repo. What does that show you and what do you think it means?

* In the subsequent labs we will integrate using the git command line into our workflow. You may find this [cheatsheet of git commands](https://education.github.com/git-cheat-sheet-education.pdf) handy.

## Submit your program for grading to gradescope

It's time to submit your program to gradescope. Go to [www.gradescope.com](www.gradescope.com). Log into your account and navigate to our course site.Select this assignment. Then click on the "Submit" button on the bottom right corner to make a submission.

You will be given the option of directly uploading files from your local machine or submitting the code that is in a github repo. We recommend that you choose the latter option as shown in the figure below. This will ensure that our staff sees the version of code on github that you submitted to gradescope.

![submit](enter-org/gradescope-submission.png){:height="500px"}

You should receive 50 points on this part of the assignment.

Congratulations on completing the workflow for CS24 programming assignments using the tools that we will be using in this class i.e. gradescope and github. In the next labs we will integrate the command line interface of github into this workflow