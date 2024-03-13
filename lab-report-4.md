# Lab Report 4 - Vim (Week 7) - Phillip Leyva Ramirez

In this lab report, I follow the steps found in https://ucsd-cse15l-w24.github.io/week7/index.html with the assistance of various bash and vim commands to publish a bugfixed commit of my own fork of the following respository: https://github.com/ucsd-cse15l-s23/lab7.

## Steps 1-3.
Before beginning any work on ieng6 in the subsequent steps, I deleted a fork of `lab7` that I had already made prior and copied a new one. I did this to ensure I had a fresh fork of `lab7` that hasn't had any work done on it. I also made my SSN key for ieng6 for the first time so ensure I could sync my work on ieng6 together with the new fork of `lab7` on GitHub.

## Step 4.
![image](https://github.com/pleyvaramirez/cse15l-lab-reports/assets/156385234/80a6a75f-5bf5-4dba-a3ae-02441f4d1ffd)

I typed in the command `ssh pleyvaramirez@ieng6-201.ucsd.edu` to connect my local command prompt to ieng6. After I completed the prompt to fill in my user password, I proceeded as normal. Also note that I intentionally typed in `ieng6-201` in this command instead of simply `ieng6` just to avoid getting connected to `ieng6-203`, which does not contain the cruial `javac` command.

## Step 5.
![image](https://github.com/pleyvaramirez/cse15l-lab-reports/assets/156385234/1212241e-7b10-4db4-904f-50ff24798df3)

Using the SSH key I had created for ieng6, I used `git clone` and `git@github.com:ucsd-cse15l-s23/lab7.git` to retrieve `lab7` and all files in it locally. I purposefully used the SSH key instead of the html link of my fork, https://github.com/pleyvaramirez/lab7, because doing so allows me to commit and push all changes I will make locally in `lab7` onto my GitHub fork, which I will explain in more detail in step 9.

## Step 6.
Before I compiled and ran all the files in `lab7`, I typed and ran `cd lab7` and then `ls` to read out all files contained in `lab7`. This is when I noticed a file called `test.sh`. I took a guess that this executable file must contain `javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java` and  `java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ListExamplesTests`, and used `bash test.sh` instead of typing out those two commands seperately. Since I had seen files called `test.sh` in lectures and labs before that served the same function of compiling and running files, I figured that this must do the same thing. The output below shows that executing `test.sh` did in fact cause the JUnit tests in `ListExamplesTests.java` to run. We were told that some tests would fail, and the output below showed that to indeed be the case:

![image](https://github.com/pleyvaramirez/cse15l-lab-reports/assets/156385234/94a8544f-2789-4749-af6d-e1d7dd14e206)

Note: I did go back later and typed `cat test.sh` to output everything contained in this file, as I realized that I assumed that it must run the proper `javac` and `java` commands as opposed to verifying that fact for myself. The output below confirmed that it did in fact contain these commands and only these commands:

![image](https://github.com/pleyvaramirez/cse15l-lab-reports/assets/156385234/598644ff-b1d4-4637-a724-f94e82a1fde4)

This shows us that `test.sh` compiles evry file in `lab7` by executing `javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java`, and then `java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ListExamplesTests` to run the test cases in `ListExamplesTests.java`. This .sh file is helpful as this streamlines the process of compiling and running our files. We don't have to go through the process of either retyping or scrolling up through my bash history for `javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java` and `java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ListExamplesTests` every time we want to compile and run our files when we can instead use `bash test.sh`. This is arguably less error prone too.


## Step 7.
Right after testing for these failures, I typed the command `vim ListExamples.java` below:
![image](https://github.com/pleyvaramirez/cse15l-lab-reports/assets/156385234/65fc93df-2dd7-48c3-8170-9e241b8a33c3)

This sended me into `ListExamples.java` while in the vim editor. Now that I was inside `ListExamples.java` with Vim, I began navigating its editor to locate and fix the bugs that caused the previous two test cases to fail. THe starting point for my cursor happened to fall on the "x" in the line containing `index1 += 1;` inside the third `while` loop of the method:

![image](https://github.com/pleyvaramirez/cse15l-lab-reports/assets/156385234/99bb9846-c815-4e93-81a1-89407063cc8b)

I observed that the bug was that this line incremented `index` with `index1 += 1;` instead of incrementing `index2`. The heys pressed from opening the vim editor from until I fixed the bug were [l] [x] [i] [2] [esc], where [l] moved me to the right 1 space, [x] removed the character I was on, [i] allowed me to insert a character, [2] being the chracter I inserted, and finally [esc] to go back to normal mode. This sequence of keys fixes the bug in the `merge` method by replacing `index1` with `index2`. The following image shows the bugfixed `merge` method:

![image](https://github.com/pleyvaramirez/cse15l-lab-reports/assets/156385234/3413b092-a5d4-4e6d-b282-a002c4f1ea46)

After this bug was fixed, I then began looking into moving my cursor towards the `filter` method, which is displayed below:

![image](https://github.com/pleyvaramirez/cse15l-lab-reports/assets/156385234/d296888c-9161-4f8a-af5c-029963b4e496)

Continuing where I left off in with my previous keystrokes on Vim, I used the following keys to approach and then fix the bug: [Ctrl+u] [j] [j] [j] [j] [j] [j] [j] [j] [j] [j] [$] [k] [k] [k] [k] [k] [x] [x] [x], where [Ctrl+u] moved me up half a page, [j] moves up me a line, [$] moved me to the end of the line, [k] moved me 1 space to the left, and [x] deleted the character that the cursor was on top of. In this case, the bug was that every string element in the new ArrayList was being moved to the first element instead of after the last element in the list. The following image shows wthe bugfixed `filter method` which gets rid of this problem:

![image](https://github.com/pleyvaramirez/cse15l-lab-reports/assets/156385234/ae452305-6f65-4d4e-a2b1-81d00a17779c)

FInally, I exited the vim editor using the following keys: [:] [w] [q] [!], where [:] allowed me to type in a command, [w] to save, anf finally [q] and  [!] to quit the vim editor. 

Note that there were certain keystrokes like <Ctrl+u> that I didn't know about prior to his lab report, so I consulted the following site: https://vimsheet.com/.
This site dubs itself the "Great Vim Cheat Sheet", listing some common and very applicable Vim commands.

## Step 8.
![image](https://github.com/pleyvaramirez/cse15l-lab-reports/assets/156385234/6f762042-828c-4c9b-87e2-33e816f17866)

The `bash test.sh` command was 2 commands up in my bash history, so I pressed the up arrow to get to it again. I then reran the command just like I did in step 6. The output in this case was different however, now showing that all the test cases passed. This is what I was looking for now that I had fixed the bugs with Vim in the previous step.

## Step 9.
I typed the command `git add ListExamples.java` to tell Git to stagw the changes I made in this file. Then, I typed and executed `git commit -m`, followed by a commit message afterwards. This command recorded and saved all the changes I made in `ListExamples.java` locally. The message I wrote out summarized what changes I made in `ListExamples.java`, that was, getting rid of the bugs in the `filter` and `merge` methods so that the test cases could now pass. FInally, I used the command `git push`. This published the local changes I made of my fork of lab7 onto GitHub, https://github.com/pleyvaramirez/lab7. This is why using a SSH key to clone `lab7` was more efficent. Now that we have a new update for the repository locally, we can simply upload it onto GitHub directly.
![image](https://github.com/pleyvaramirez/cse15l-lab-reports/assets/156385234/0ff7a3b0-bb0e-4ed0-8bbc-d2a8a6b99fa1)

