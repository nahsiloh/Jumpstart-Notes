3rd sept 2019

## Visual Code

https://thoughtworks-jumpstart.gitbook.io/book/developer-tools/vs-code-shortcuts

`ctrl p`= search for files

`ctrl shift p` = search for commands

#### cmd prompt 

`code .`= command prompt to open current directory on vs code



##### The Debugger

- for code exploration 

- see the call stack 

- debugging code instead of adding console.log()

  

## Git

https://thoughtworks-jumpstart.gitbook.io/book/developer-tools/git

- version control tool, to save versions of copy 

#### Configure Git

set name and email:

- `git config user.name`
- `git config user.email`



#### Check parent and child history

- `GitK`



#### Working with Git

- `git init`= start a git repository
- `git status`= check status of the directory

![img](https://blobscdn.gitbook.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-LBJBL3Fj_tcfkvqLj9P%2F-LQ-DvuojV-KEAeykCDj%2F-LQ-E3-HbEdc7gO1Asqp%2Fgit-overview.jpg?generation=1540823467895946&alt=media)

- #### 3 stages in Git

  - ##### Repository

    - when file is inside here is Git considered saved
    - `git commit`= make a commit to git
    - `git commit -m README.me` or `git commit -message README.me`= commit with a message flag to git   
    - data structure of a linked list

  - ##### Staging

    - preparation for saving
    - `git add README.me` = to move file to staging
    - `git add -p README.me` or `git add --patch README.me`= shows the code to add to staging with confirmation on the file before pushing to stages
    - `git reset README.me`= to unstage selected file
    - `git diff --staged` = to see the difference in the file during staging

  - ##### Working Directory

    - ongoing working files
  - `git add -N README.me` = to get file in working directory
    
    - `git diff` =  to see the differences in the file at working directory




- #### Pushing to Github

  - `git remote add origin https://github.com/nahsiloh/learning_git.git` 
- note that "origin" is just a conventional name
  
  - 2 options to push remotely
- `git push origin master` = where "origin" can be changed to another name
    
    - `git push --set-upstream origin master` is the same as `git push -u origin master` = "origin" is set by default




- #### Pull vs fetch

  - `git pull` = `git fetch`+`git merge`

    