# Lab Report 1

## Using command `cd`
1. Without any arguments:
   ```
   [user@sahara ~]$ cd
   ```
   There was no output to this singular line of code. Because we didn't provide any arguments, nothing changed and the directory remained unaltered.
   
2. With a path to a file as an argument:
   ```
   [user@sahara ~]$ cd test
   bash: cd: test: Not a directory
   [user@sahara ~]$ 
   ```
   Prior to running the command, I created an empty file called "test" in /home resulting in an output stating that the cd command can only be used for directories. As such, attempting to change directory to an individual file results in this error message.
   
3. With a path to a directory as an argument:
   ```
   [user@sahara ~]$ cd lecture1
   [user@sahara ~/lecture1]$ 
   ```
   Putting lecture1 as an argument changed the directory from /home to /home/lecture1, as can also be seen above.

## Using command `ls`
1. Without any arguments:
   ```
   [user@sahara ~/lecture1]$ ls
   Hello.class  Hello.java  messages  README
   ```
   The output displays all files and folders contained in /home/lecture1. Because we did not provide any arguments, java defaulted to giving us the list of files and folders in the current directory.
   
3. With a path to a file as an argument:
   ```
   [user@sahara ~/lecture1]$ ls Hello.java
   Hello.java
   ```
   The output simply returns the name of the file, given that files do not 'contain' other files in them.
   
3. With a path to a directory as an argument:
   ```
   [user@sahara ~/lecture1]$ ls messages
   en-us.txt  es-mx.txt  pt.br.txt  zh-cn.txt
   ```
   The output returns a list of all files and folders contained in /home/lecture1/messages. This is similar behavior to running ls without any arguments. If the directory had been /home/lecture1/messages, running ls without any arguments, the output would be the same as directly above.
   
## Using command `cat`
1. Without any arguments:
   ```
   [user@sahara ~]$ cat
   1  
   1
   pwd
   pwd
   ```
   Running cat in this case, without arguments, exits the terimal out of the command interface, preventing us from running any other commands. Anything we type here and then subsequently run is repeated in the output.
   
2. With a path to a file as an argument:
   ```
   [user@sahara ~/lecture1]$ cat Hello.java
   import java.io.IOException;
   import java.nio.charset.StandardCharsets;
   import java.nio.file.Files;
   import java.nio.file.Path;

   public class Hello {
     public static void main(String[] args) throws IOException {
       String content = Files.readString(Path.of(args[0]), StandardCharsets.UTF_8);    
       System.out.println(content);
     }
   }
   ```
   Running cat here returns all of the contents of the file, that being Hello.java in this case. 
   
3. With a path to a directory as an argument:
   ```
   [user@sahara ~/lecture1]$ cat messages
   cat: messages: Is a directory
   ```
   Running cat with a directory will give us an output that says the argument is a directory, hinting at the fact that it would be more appropriate to use a file as the argument. This is an error.
