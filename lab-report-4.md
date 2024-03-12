# Lab Report 4 - Vim (Week 7) - Phillip Leyva Ramirez

In this lab report, I follow the steps found in https://ucsd-cse15l-w24.github.io/week7/index.html with the assistance of various bash and vim commands to publish a bugfixed commit of my own fork of the following respository: https://github.com/ucsd-cse15l-s23/lab7.

## Step 4.
![image](https://github.com/pleyvaramirez/cse15l-lab-reports/assets/156385234/80a6a75f-5bf5-4dba-a3ae-02441f4d1ffd)

The `ssh` command connected me to ieng6 after I typed in my user password. I typed in `ieng6-201` to ensure that I do not get connected to `ieng6-203`, which does not contain the cruial `javac` command.

## Step 5.
![image](https://github.com/pleyvaramirez/cse15l-lab-reports/assets/156385234/1212241e-7b10-4db4-904f-50ff24798df3)
Using the SSH key I had created for ieng6, I used `git clone` and `git@github.com:ucsd-cse15l-s23/lab7.git`. I purposefully used the ssh key instead of the html link of my fork, https://github.com/pleyvaramirez/lab7.  

## Step 6.
In order to compile and run all the files in `lab7`, we use `bash` on `test.sh`, a file that was already present when I forked and cloned the original repository.


![image](https://github.com/pleyvaramirez/cse15l-lab-reports/assets/156385234/94a8544f-2789-4749-af6d-e1d7dd14e206)

Using `cat test.sh` catenates this file, outputing everything contained in this file. 

![image](https://github.com/pleyvaramirez/cse15l-lab-reports/assets/156385234/598644ff-b1d4-4637-a724-f94e82a1fde4)

This shows us that `test.sh` compiles evry file in `lab7` using `javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java`, and then uses `java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ListExamplesTests` to run the test cases in `ListExamplesTests`. This is helpful because this streamlines the process of compiling and running our files.




## Step 7.
Right after testing for failures, we enter the vim editor into `ListExamples.java` with this command:
![image](https://github.com/pleyvaramirez/cse15l-lab-reports/assets/156385234/65fc93df-2dd7-48c3-8170-9e241b8a33c3)

Now that we are inside `ListExamples.java` with the vim editor, we begin navigating the editor to locate and fix the bugs.

![image](https://github.com/pleyvaramirez/cse15l-lab-reports/assets/156385234/99bb9846-c815-4e93-81a1-89407063cc8b)
![image](https://github.com/pleyvaramirez/cse15l-lab-reports/assets/156385234/3413b092-a5d4-4e6d-b282-a002c4f1ea46)

Keys pressed: <l><x><i><2><esc>.
This sequence of keys fixes the bug in the `merge` method.

![image](https://github.com/pleyvaramirez/cse15l-lab-reports/assets/156385234/d296888c-9161-4f8a-af5c-029963b4e496)
![image](https://github.com/pleyvaramirez/cse15l-lab-reports/assets/156385234/ae452305-6f65-4d4e-a2b1-81d00a17779c)

Keys pressed: <Ctrl+u><j><j><j><j><j><j><j><j><j><j><$><k><k><k><k><k><x><x><x>
This sequence of keys follows right after.

FInally, we exited vim editor using the following keys:
Keys pressed: <:><w><q><!>.

There were certain keystrokes like <Ctrl+u> that I didn't know about prior to his lab report, so I consulted the following site: https://vimsheet.com/
This site dubs itself the "Great Vim Cheat Sheet", listing some common Vim commands.

## Step 8.
![image](https://github.com/pleyvaramirez/cse15l-lab-reports/assets/156385234/6f762042-828c-4c9b-87e2-33e816f17866)

The `bash test.sh` command was 2 commands up in my bash history, so I pressed the up arrow to get to it again. I then ran the command just like I did in step 6.

## Step 9.
![image](https://github.com/pleyvaramirez/cse15l-lab-reports/assets/156385234/0ff7a3b0-bb0e-4ed0-8bbc-d2a8a6b99fa1)

`git add`
`git commit -m [message]`. This command records and saves all the changes I made in `ListExamples.java`. 
FInally, I used the command `git push`. This published the local changes I made of my fork of lab7 onto GitHub, https://github.com/pleyvaramirez/lab7.

