# Lab Report 3 - Phillip Leyva Ramirez, PID: A17546555
# Part 1 - Bugs

For this part, we will examine the `reversed` method starting at line 14 in ArrayExamples.java from Lab 4, identify what the bug is, and come up with a solution addressing the bug. 

 ```
 static int[] reversed(int[] arr) {
      int[] newArray = new int[arr.length];
      for(int i = 0; i < arr.length; i += 1) {
          arr[i] = newArray[arr.length - i - 1];
      }
      return arr;
  }
```

1. Failure inducing input
```
 @Test
  public void testReversed2() {
    int[] input1 = {1, 2, 3};
    assertArrayEquals(new int[]{3, 2, 1}, ArrayExamples.reversed(input1));
    assertArrayEquals(new int[]{1, 2, 3}, input1);
  }
```
In this example we create the `input1` array, apply the `reversed` method on it, and compare it to another array in which we manually reversed the order of elements in input1.

2. Input (no failure)
```
 @Test
  public void testReversed() {
    int[] input1 = { };
    assertArrayEquals(new int[]{ }, ArrayExamples.reversed(input1));
  }
  ```
In this example, we use `reversed` on `input1`, an empty array. In this case the output happened to be exactly what we expect, an empty array.

4. JUnit Test Output
![Screenshot 2024-02-27 195006](https://github.com/pleyvaramirez/cse15l-lab-reports/assets/156385234/3099c32d-53ff-4ac2-9cd8-e7c965e0f450)


5. The purpose of the `reversed` method is to create a new array containing all the elements of the input array in reverse order. The method as it is currently written is not doing this. Although `newArray` is correctly defined, the method in the fourth line is actually replacing every element i in input array `arr` with its corresponding element in `newArray` . This is not correct because we want to fill up `newArray`. `arr` itself should remain unaltered by the method. Furthermore, the method returns the `arr` array, not `newArray`. Because we want a new array to be properly filled and returned, we also should swap every instance of `arr` with `newArray` and vice versa in the fourth and sixth lines:
```
  static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      newArray[i] = arr[arr.length - i - 1];
    }
    return newArray;
  }
```

# Part 2 - Researching The `grep` Command [^1]
Recalling that the function `grep` command is to search for a desired string of characters inside a file and output the lines where there was a match which what we're looking for, we can modify the general premise of this command in countless ways:

Using `-c` on `grep` with a file:
```
leyva@LAPTOP-NDKQRBFE MINGW64 ~/docsearch/technical (main)
$ grep -c "United Airlines Flight 175" 911report/chapter-1.txt
5
```
I wanted to find out the total number of times that "United Airlines Flight 175" is mentioned in `chapter-1.txt`. Using `-c` on a file and providing the specific pattern of characters we're looking for, we can see that the function of this command option is to output an integer value recording how many times this pattern appeared in this file. In thus example, "United Airlines Flight 175" appeared a total of 5 times in 911report/chapter-1.txt. This number is useful for figuring out how much our keyword is talked about. For example, if there had been 0 mentions of "United Airlines Flight 175" in  911report/chapter-1.txt, that suggests to us that we wouldn't find much information on this flight in this file.

Now, using `-cr` on `grep` with a directory:
```
leyva@LAPTOP-NDKQRBFE MINGW64 ~/docsearch/technical (main)
$ grep -cr "United Airlines Flight 175" 911report
911report/chapter-1.txt:5
911report/chapter-10.txt:0
911report/chapter-11.txt:0
911report/chapter-12.txt:0
911report/chapter-13.1.txt:0
911report/chapter-13.2.txt:4
911report/chapter-13.3.txt:0
911report/chapter-13.4.txt:0
911report/chapter-13.5.txt:1
911report/chapter-2.txt:0
911report/chapter-3.txt:0
911report/chapter-5.txt:0
911report/chapter-6.txt:0
911report/chapter-7.txt:1
911report/chapter-8.txt:0
911report/chapter-9.txt:2
911report/preface.txt:0
```
Using `-c` on a directory requires adding `-r` to recursively search through every file contained in the directory. In essence, `-cr` outputs a list in which every file in the directory is displayed alongside the count of the number of times our desired pattern appeared within that file. This might be useful when we want to compare across files where a keyword appears the most, and where it doesn't appear as often. In this specific example, we can see that "United Airlines Flight 175" appeared 5 times and 4 times in 911report/chapter-1.txt and 911report/chapter-13.2.txt respectively, the most out of all the other files. This suggests that we should take a look at these two files first if we want to learn more about United Airlines Flight 175.

Using `-i` with a file:
```
leyva@LAPTOP-NDKQRBFE MINGW64 ~/docsearch/technical (main)
$ grep -i "cardiovascular" biomed/1468-6708-3-1.txt
        trials to detect survival differences or cardiovascular
          Study design: The Cardiovascular Health
          The Cardiovascular Health Study (CHS) is a
          cardiovascular disease (prevalent heart disease,
        CHS Cardiovascular Health Study
```
The `-i` command is useful when we want to search for a keyword or phrase insentivively. In other words, capitialization no longer matters in our keyword when we apply `-i`. As can be seen above, we wanted to find the word "cardiovascular" in biomed/1468-6708-3-1.txt. Instances where cardiovascular is capitalized would not have been included in the output if we hadn't applied `-i`.

Using `-ir` with a directory [^2]:
[^2]: The ellipis was added to indicate that there was more to the output that I did not explcitly include in this lab report here for the sake of simplicity.
```
biomed/1468-6708-3-1.txt:        trials to detect survival differences or cardiovascular
biomed/1468-6708-3-1.txt:          Study design: The Cardiovascular Health
biomed/1468-6708-3-1.txt:          The Cardiovascular Health Study (CHS) is a
biomed/1468-6708-3-1.txt:          cardiovascular disease (prevalent heart disease,
biomed/1468-6708-3-1.txt:        CHS Cardiovascular Health Study
biomed/1468-6708-3-10.txt:        endpoint, combined cardiovascular disease (CVD)
biomed/1468-6708-3-10.txt:          atherosclerotic cardiovascular disease (ASCVD), and ST-T
biomed/1468-6708-3-10.txt:          most cardiovascular risk factors compared to those
biomed/1468-6708-3-10.txt:          atherosclerotic cardiovascular disease (ASCVD) (29-33% of
...
biomed/cc4.txt:          cardiovascular instability, in whom an accurate
biomed/cc991.txt:          cardiovascular monitors (Sirecust; Siemens, Danvers,
biomed/cvm-2-4-180.txt:        end-point events in cardiovascular clinical trials. Limited
biomed/cvm-2-4-187.txt:        by site investigators in recent cardiovascular trials have
```
Similarly to searching for a keyword within one file, we can use `-i` recursively on a directory to search for all instances of a keyword across all files regardless of whether or not it is capitalized. For example, when we searched for cardiovascular above, we were able to find "cardiovascular" and also "Cardiovascular".

Using `-n` with a file:
```
leyva@LAPTOP-NDKQRBFE MINGW64 ~/docsearch/technical (main)
$ grep -n "Florida" government/About_LSC/Comments_on_semiannual.txt
67:1 California, Colorado, Florida, Illinois, Indiana, Maine,
170:retained consultants to assist planning efforts in Florida, North
```
The `-n` command option adds the line number in which our preferred set of characters was found by `grep`. In `government/About_LSC/Comments_on_semiannual.txt`, we can see that "Florida" can be found in lines 67 and 170 of the file. This is a very efficent way of not only identifying whether a keyword is inside a file, but also identifying where in the file it is located.

Using `-nr` with a directory:
```
leyva@LAPTOP-NDKQRBFE MINGW64 ~/docsearch/technical (main)
$ grep -nr "Equal Justice Conference" government/About_LSC
government/About_LSC/Comments_on_semiannual.txt:197:At the Equal Justice Conference ("EJC") held in March 2001 in
government/About_LSC/Comments_on_semiannual.txt:276:2001 Equal Justice Conference, and others are planned later in
government/About_LSC/Comments_on_semiannual.txt:318:Practices" at the March ABA/NLADA Equal Justice Conference.
government/About_LSC/Comments_on_semiannual.txt:335:during the March ABA/NLADA Equal Justice Conference. Approximately
government/About_LSC/Progress_report.txt:313:Equal Justice Conference in March.
government/About_LSC/Progress_report.txt:522:conjunction with the Equal Justice Conference and participated in a
government/About_LSC/Strategic_report.txt:661:Equal Justice Conference to give Internet access to conference
```
Using `-n` combined with `-r` scans every file in a directory and for every line of text it identifies as containing our keyword, it outputs the file name and line number. This is an efficient way of searching for all instances of a string and finding the exact location for each and every instance.

Using `-w` with a file:
```
leyva@LAPTOP-NDKQRBFE MINGW64 ~/docsearch/technical (main)
$ grep -w "up" government/Alcohol_Problems/DraftRecom-PDF.txt
care, a clinic follow-up, or another health or social service. The
sets up the expectation that something has to follow. Without
assist in follow-up and continuity of care.
medicine departments. If we were to choose one place to set up a
anti-hypertensives with some type of follow-up.
```
As can be seen above `-w` is used to ensure that our string of characters is not part of a larger sequence of strings. In this example, using `-w` helped print all the times that up appeared as its own word, excluding all other instances in which the characters "u" and "p" comprised a larger word. This is helpful for when we want to search for a certain string on its own without including the cases where the string is merely a substring of a larger string.

Using `-wr` with a directory:
```
leyva@LAPTOP-NDKQRBFE MINGW64 ~/docsearch/technical (main)
$ grep -wr "Dec" government/Media
government/Media/FortWorthStarTelegram.txt:On Dec. 31, West Texas Legal Services will merge with Legal
government/Media/FortWorthStarTelegram.txt:On Dec. 9, the U.S. Supreme Court will hear arguments about the
government/Media/Greedy_Generous.txt:Dec. 23, 2002
government/Media/Program_Lodges.txt:With Liebler's help, Stimpson was given until Dec. 29 to move.
government/Media/Survey.txt:Phoenix on Dec. 7 to finalize its report for the ABA's general
```
Using `-wr` to search for "Dec", what we got as an output was a list of all the instances in which December was abbreviated to "Dec" across all files contained in government/Media.

[^1]: I refered to https://www.geeksforgeeks.org/grep-command-in-unixlinux/ in order to discover all of these command options for `grep`.
