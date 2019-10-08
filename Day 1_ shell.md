2nd sept 2019

https://github.com/thoughtworks-jumpstart/learn-shell

## Shell

### Navigating around

- `pwd` = show current path

- `ls`= list content

- `ls -l` or `ls -lah` = list content with properties

- `cd ~` = return to home folder

  

### Read files

- `less README.md` = To enter a text document reading format (press `q ` to exit)
- `cat hello.txt` = displays text file starting from the end of the file



### Move or Rename files

- Move file = `mv ./hello.txt ./folder/hello/`

- Move and rename = `mv ./hello.txt ./folder/hello/goodbye.txt`

  

### Create files and Directories

- `mkdir oasis && touch wonderwall.txt` = to create a folder and create a text file 
- `&&` = to allow for another command to happen after the first one is executed. 
- `touch file{1..5}.txt`= creates 5 text files
  - file1.txt .. file5.txt

### Delete files and directories

-  `rm -r folder`= delete folder
- `rm file`= remove file



### See history and search commands

- `history` = to see history of commands
- `ctrl r`= to search for commands



### Pipe

- pipe `|` = allows to pipe the output of one command as the input for another command
- eg. `wc` = count; `-l`= lines; `-m`= characters; `-w`=words 
  - `cat ./pop/adele/hello.txt | wc -l`

### Path

- environment variable on Unix-like operating systems, where a set of directories are specified where executable programs are located.
  - `echo $PATH`= to check the list of PATHS

- To note difference between BSD vs GNU operating system 

 **To run scripts:**



Chmod permissions

-rw-r--r-- 1 lisha 197609  31 Sep  2 16:53 apple

 

Although this will work for window platform, when uploaded to server, it is not executed due to incorrect permissions. 

** require to run: *chmod u+x apple*



 ![1567475384327](C:\Users\lisha\AppData\Roaming\Typora\typora-user-images\1567475384327.png)

 `.bash_profile`= 

`aliases`

\-          Something about your self, 

\-          Your resume 

\-          Something you want to write about 