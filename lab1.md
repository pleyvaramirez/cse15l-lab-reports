# Lab Report 1

## Using command `cd`
1. Without any arguments:
   ```
   [user@sahara ~]$ cd
   ```
   There was no output to this singular line of code. Because we didn't provide any arguments, nothing changed.
   
2. With a path to a file as an argument:
   ```
   [user@sahara ~]$ cd test
   bash: cd: test: Not a directory
   [user@sahara ~]$ 
   ```
   Prior to, I created an empty file called "test". As such, attempting to change directory to an individual file results in this error message, stating that the cd command can only be used for directories.
   
3. With a path to a directory as an argument:
   ```
   [user@sahara ~]$ cd lecture1
   [user@sahara ~/lecture1]$ 
   ```

## Using command `ls`
1. Without any arguments:
   ```
   [user@sahara ~/lecture1]$ ls
   Hello.class  Hello.java  messages  README
   ```
   
3. With a path to a file as an argument:
   ```
   [user@sahara ~/lecture1]$ ls Hello.java
   Hello.java
   ```
   
5. With a path to a directory as an argument:
   ```
   [user@sahara ~/lecture1]$ ls messages
   en-us.txt  es-mx.txt  pt.br.txt  zh-cn.txt
   ```
   
## Using command `cat`
1. Without any arguments:
   
2. With a path to a file as an argument:
   
3. With a path to a directory as an argument:
