23rd October 2019

## GIT for collaboration

- `git log --oneline` = to be able to see the commits
- `git log --oneline --graph --decorate`



##### Roles of the teams

- Maintainers =  core  group = work on the repo daily

- Trusted Group 

  - branching/ feature branch

  - can be merged back to the main repo after, thus do not need to clone the project again 

    

    ###### GIT commands to create branch from master 

    - `git branch <name>`- add a new branch

    - `git branch --list` - to see the list of branches
    - `git checkout <name>` - to switch to the new branch 
    - `git merge <name>` - to merge back to the master 
    - `git branch -D <name>`- to delete the branch
    - `git checkout -b <name>` - directly creates the branch subtract and switch to the branch

    

    ###### Possible to branch out from another branch

    - usually have a master, staging branch, then branch out from the staging branch 

      

  - may require to resolve merge conflict - will require to re-commit the file 

  - `git merge --abort` - aborts the merge conflict resolution - when you try to resolve the merge conflict, but possible problems faced and you want to revert back to original condition and restart

    - ###### Try to avoid!

      - `git revert xxxxx` - where xxxxx is the hash number - can get when you `git log --oneline` - creates a new commit that tries to undo what was done on that particular commit represented by the hash
      - `git reset --hard xxxxx` - deletes the commit from the entire tree! code will be lost 
      - `git reset -- soft` and `git reset --mixed`

  - `git checkout xxxxx` - will be able to see the version of the committed file

  

  - ###### Pushing the branch called staging remotely

    - `git push --set-upstream origin staging`

      

- Untrusted Group 

  - fork - take a code from another person's repository and moves it to your own repository

  - Git Clone to local

  - make changes and commit

  - Git Push

  - pull request - from the other person's page

  - the other person will be required to approve your input first before you can merge

    



## Trunk Based Development

- keeps pushing the master rather than creating new branches
- 2 commits and 2 push per day ideally



#### Git Rebase

- resolve the conflict at the branch first before merging back into the master
- Do not merge before resolving the conflict at the branch first 
- after 
- `git pull --rebase` = combination of git.fetch and git.rebase
- if conflict : resolve the issue then `git add .` ,`git rebase --continue`, `git push`
- if no conflict: `git push`

