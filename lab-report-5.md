# Lab Report 5 - Putting it All Together (Week 9) - Phillip Leyva Ramirez
## Part 1 - Debugging Scenario

### Step 1.
![image](https://github.com/pleyvaramirez/cse15l-lab-reports/assets/156385234/7e35af9f-1b4b-4ebf-a240-45d64fa241ae)

![image](https://github.com/pleyvaramirez/cse15l-lab-reports/assets/156385234/9976ba4b-327e-4fe4-887a-0e7d0a3f4fbf)

CSE Student: I was a little confused on what the bug is here. I compiled and ran the files but I got errors in both test cases. It seems like the resulting `new` ArrayList is half the length of what I actually want. How could I see the rest of both arrays?


### Step 2.

TA: Hello, you should try 

### Step 3.

CSE Student: Thank you, I realized that I was using the same index integer for both arrays, when I should be using a seperate index for both `list1` and `list2`. 

### Step 4.



## Part 2 - Reflection

In essence, this class has felt like getting taught a various amount of skills regarding command line arguments and bash commands. I definitely had the impression that there was some basic knowledge that I wasn't quite aware of yet. Pretty much everything that is taught in this course I didn't know at all previously. A good example of this was learning how to use the Vim editor for the first time in one of the lab sections. Although I would not consider myself an expert yet, I now know the most essential commands regarding how to move my cursor (such as [h] [j] [k] [l]), and that I can save and quit using [:w] and [:q] respectively. Something else I learned about Vim was that I could not have th. I learned this when I was working on Practice Skill Demo 5. In one moment, I had the Vim editor open for a specific file, and I eventually had to reboot the command line in PrairieTest. Because I couldn't exit out of the Vim editor properly and save my prior work, I tried reentering in the same file with Vim and was met with a warning. For this reflection, I recreated the steps that lead to this scenario to recieve that same warning:

![image](https://github.com/pleyvaramirez/cse15l-lab-reports/assets/156385234/69d460b9-4ddb-4705-8587-8a44f9c15542)

To solve this issue, I pressed [r] to recover the lost data, and typed the command `rm .ListExamples.java.swp` to get rid of the error message from popping up.
