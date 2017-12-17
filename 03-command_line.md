# Learn command line

Please follow and complete the free online [Bash Scripting Tutorial](https://ryanstutorials.net/bash-scripting-tutorial/) or [Codecademy's Learn the Command Line](https://www.codecademy.com/learn/learn-the-command-line). These are helpful tutorials. You should be able to go through these in a couple of hours.

**Note:** Bash is not installed on a PC. Rather, PC users must install Cygwin. Once Cygwin has been installed, the command line interface witll _emulate_ bash. You can find all information regarding Cygwin [here](https://www.cygwin.com/).

---

### Q1.  Cheat Sheet of Commands  

Here's a list of items with which you should be familiar:  
* show current working directory path
* creating a directory
* deleting a directory
* creating a file using `touch` command
* deleting a file
* renaming a file
* listing hidden files
* copying a file from one directory to another

Make a cheat sheet for yourself: a list of at least **ten** commands and what they do.  (Use the 8 items above and add a couple of your own.)  

> > 1.) show current working directory path : pwd  
    2.) creating a directory : mkdir  
    3.) deleting a directory : rm -r  
    4.) creating a file using `touch` command : touch textfile.txt  
    5.) deleting a file : rm  
    6.) renaming a file : mv text.txt text2.txt  
    7.) listing hidden files : ls -a   
    8.) copying a file from one directory to another : cp biopic/cleo.txt historical/  

---

### Q2.  List Files in Unix   

What do the following commands do:  
`ls`  : lists all files and directories  
`ls -a`  : list all files (including hidden files) and directories
`ls -l`  : list all file and directories in long format  
`ls -lh` :  print sizes in human readable form in long format 
`ls -lah`  print files (including hidden files) in human readable form in long format  
`ls -t`  : order files and directories by time they were last modified  
`ls -Glp`  : list files and directories but does not include owner in long format and includes parent directories as needed



---

### Q3.  More List Files in Unix  

Explore these other [ls options](http://www.techonthenet.com/unix/basic/ls.php) and pick 5 of your favorites:

> > 1.) -g  
    2.) -1  
    3.) -x  
    4.) -F  
    5.) -d  

---

### Q4.  Xargs   

What does `xargs` do? Give an example of how to use it.

> > It is a command that converts input from standard input into arguments into a command. For example:  
  find /tmp -mtime +14 | xargs rm : This will find files that are more than 2 weeks old in the temp file and then pipe them into xargs       command to be removed.

 

