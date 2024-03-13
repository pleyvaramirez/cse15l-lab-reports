# Lab Report 5 - Putting it All Together (Week 9) - Phillip Leyva Ramirez
## Part 1 - Debugging Scenario

### Step 1.
![image](https://github.com/pleyvaramirez/cse15l-lab-reports/assets/156385234/7e35af9f-1b4b-4ebf-a240-45d64fa241ae)
![image](https://github.com/pleyvaramirez/cse15l-lab-reports/assets/156385234/9976ba4b-327e-4fe4-887a-0e7d0a3f4fbf)

Student: I was a little confused on what the bug is here. I compiled and ran the files but I got errors in both test cases. It seems like the resulting `new` ArrayList is half the length of what I actually want. How could I fix this if I can't see the rest of the array?


### Step 2.

TA: Hello [Student's name], have you tried using the `jdb` command to debug your program? Remember to use `-g` while compiling.

### Step 3.

CSE Student: Thank you, when I tried `jdb` to get the value of testMerge1 I realized that I was using the same index integer for both arrays, when I should be using a seperate index for both `list1` and `list2`. 

### Step 4.
The `lab7` directory structure was as follows:
```
ListExamples.class  ListExamplesTests.class  StringChecker.class  test.sh
ListExamples.java   ListExamplesTests.java   lib
```
The file `test.sh` here contained the following commands:

`javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java
java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ListExamplesTests`

Using `bash test.sh` executes the above commands, which effectively compiles all the files and runs `ListExamplesTests`.

The contents of `ListExamples.java` BEFORE fixing the bug was as follows:
```
class ListExamples {

  // Returns a new list that has all the elements of the input list for which
  // the StringChecker returns true, and not the elements that return false, in
  // the same order they appeared in the input list;
  static List<String> filter(List<String> list, StringChecker sc) {
    List<String> result = new ArrayList<>();
    for(String s: list) {
      if(sc.checkString(s)) {
        result.add(s);
      }
    }
    return result;
  }


  // Takes two sorted list of strings (so "a" appears before "b" and so on),
  // and return a new list that has all the strings in both list in sorted order.
  static List<String> merge(List<String> list1, List<String> list2) {
    List<String> result = new ArrayList<>();
    int index = 0;
    while(index < list1.size() && index < list2.size()) {
      if(list1.get(index).compareTo(list2.get(index)) < 0) {
        result.add(list1.get(index));
        index += 1;
      }
      else {
        result.add(list2.get(index));
        index += 1;
      }
    }
    while(index < list1.size()) {
      result.add(list1.get(index));
      index += 1;
    }
    while(index < list2.size()) {
      result.add(list2.get(index));
      index += 1;
    }
    return result;
  }


}
```
Similarly, the contents of `ListExamplesTests.java` was:

```
import static org.junit.Assert.*;
import org.junit.*;
import java.util.*;
import java.util.ArrayList;


public class ListExamplesTests {
        @Test(timeout = 500)
        public void testMerge1() {
                List<String> l1 = new ArrayList<String>(Arrays.asList("x", "y"));
                List<String> l2 = new ArrayList<String>(Arrays.asList("a", "b"));
                List<String> l3 = ListExamples.merge(l1, l2).toArray();
                assertArrayEquals(new String[]{ "a", "b", "x", "y"}, ListExamples.merge(l1, l2).toArray());
        }

        @Test(timeout = 500)
        public void testMerge2() {
                List<String> l1 = new ArrayList<String>(Arrays.asList("a", "b", "c"));        
                List<String> l2 = new ArrayList<String>(Arrays.asList("c", "d", "e"));        
                assertArrayEquals(new String[]{ "a", "b", "c", "c", "d", "e" }, ListExamples.merge(l1, l2).toArray());
        }

}
```

Triggering the bug was simple, as the only command that needed to be written out was `bash test.sh`.
In order to fix the bug, there should be seperate `index` variables for `list1` and `list2`. This can be done by defining an integer variable `index1` for `list1` and `index2` for `list2`. This way, the two arrayLists are not dependent on the same integer value, making it possible that length of the new arrayList is actually the sum of `list1.size()` and `list2.size()`.


## Part 2 - Reflection

In essence, this class has felt like getting taught a various amount of skills regarding command line arguments and bash commands. I definitely had the impression that there was some basic knowledge that I wasn't quite aware of yet. Pretty much everything that is taught in this course I didn't know at all previously. A good example of this was learning how to use the Vim editor for the first time in one of the lab sections. Although I would not consider myself an expert yet, I now know the most essential commands regarding how to move my cursor (such as [h] [j] [k] [l]), and that I can save and quit using [:w] and [:q] respectively. Something else I learned about Vim was that I could not have th. I learned this when I was working on Practice Skill Demo 5. In one moment, I had the Vim editor open for a specific file, and I eventually had to reboot the command line in PrairieTest. Because I couldn't exit out of the Vim editor properly and save my prior work, I tried reentering in the same file with Vim and was met with a warning. For this reflection, I recreated the steps that lead to this scenario to recieve that same warning:

![image](https://github.com/pleyvaramirez/cse15l-lab-reports/assets/156385234/69d460b9-4ddb-4705-8587-8a44f9c15542)

To solve this issue, I pressed [r] to recover the lost data, and typed the command `rm .ListExamples.java.swp` to get rid of the error message from popping up.
