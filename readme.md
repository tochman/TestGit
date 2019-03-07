# Basic navigation in Git

* `cd <directory>` changes directory (use `..` to go up a level).
* `mkdir <directory name>` creates a directory
* `touch <filename.extension>` creates a file.
* `rm <filename>` removes a file.
* `rm -fr <directory name>` removes a non-empty directory.
* `mv <file or directory> <destination path>` moves a file or directory.
* `mv <old file or directory name> <new file or directory name>` renames a file or directory.
* `mv --force <OLD_NAME> <new_name>` renames a file or directory changing capitalization; failing to use the force argument means changes in capitalization will not be picked up by all systems, including Github.

# Git and GitHub for Version Control
## General ideas:

### If have not "cloned" a repository from online, then you will first "initialize" a repository on your computer.  
You navigate to the repository then use `git init`.  
This will create some hidden files in the repository which are used by Git in order to track changes made to files in the repository.

### `git status` will give you a summary of the status of your local repository.

### You work on files in a "workspace".  
When you have modified them in ways you want to save, you add them to a "staging area".  
   This is done with `git add <filename>`.
   `git add .` will add all existing tracked files.

### Once you have several changes you want to save permanently, you save them onto your "branch".  
This is done with `git commit`.  
   `git commit -m 'message'` allows you to leave the commit message in a single line when you commit.  
   `git commit -a` allows you to commit tracked files without "staging" first.  
   `git commit -am` allows you to do both of the above arguments in one line.  
If you ever need to revert a branch backwards to an earlier commit, I think you would use `git reset --hard <commit hash>`.

### You may have several "branches" on any one project.  
If you have changes but are not ready to commit them, but you need to change branches to do other work before you can finish making the current changes, you can save your working changes with `git stash`.  
You can retrieve those changes with `git pop` or possibly `git stash apply`.

### It is best practice to never work directly on the master branch.  
Rather, you will create a different branch to do your work on where you will do your staging and committing and only at a much later stage will your branch be merged with the master branch.  
   To create a new branch, use `git branch <name>` and switch to it with `git checkout <name>`.  
      You can do this in one line with `git checkout -b <branch name>`.  
Merging branches is done with `git merge <name>`.  
If you have conflicts, you will be prompted and you will need to fix them before the merge can be finished. It is perhaps easiest to handle the conflicts on Github using the web interface.

### All of the above steps refer to changes you make on your local repository (on your own computer).  
Working with a remote repository means having your code online where others can "clone" it as well as suggest "pulls".  
   To "clone" an online repository locally on your machine, use `git clone <html>`.  
   Once you have navigated into the "cloned" repository it behaves just like any other local repository.  
If the remote repository has changes which are not reflected in your local repository, you can do `git fetch origin` followed by `git merge` to update your local repository.  
   `git pull origin` should work the same way as `git fetch origin` followed by `git merge`.

### You can monitor and alter the connections to a remote branch using `git remote`, although one is recommended to look at the documentation for detailed information.  
From the Coffee'N'Code Workshop I think that `git remote -v` will show you other connections, `git remote add <email>` will add a connection, and `git remote upstream <email>` will alter where a connection sits in the version control (please read further documentation since this is not a clear explanation).

### To send changes on your local repository to the 'head' of the branch on the remote repository, use `git push origin HEAD`.  
You may need user name and password to submit the changes.  
Recall that it is best practice to never 'push' onto the master branch. Rather, 'push' onto another branch and then use Github to submit a 'pull' request to the master branch.  
   This will allow more version control with better record keeping.

### After you have used Github to merge branches onto the master, some housekeeping needs to be done.  
You may choose to delete branches on Github that you no longer want to work on.  
Your local repositories will no longer be up-to-date.  
   To check for differences between your local repositories and the remote run `git fetch origin`.  
   Each branch will have to be updated individually, which is accomplished by `git checkout <branch>` and `git pull origin`.  
   You can also switch to the master branch and update it by the same process, but remember that you are usually working on a different branch to maintain the integrity of the master branch.  
To delete the references in your local repository to branches you have deleted on Github, use `git remote prune origin`.


# Services mentioned at Coffee 'N Code event which may be worthing looking into
 
* ['SemaphoreCI'](https://semaphoreci.com/) for testing pull requests on Github before they get merged. Free for open repositorues. Paid for private (closed sourced) repositories
* 'Selenium' + 'Chrome Driver' (in Ruby) or 'Puppeteer' for running automated tests to make sure all parts of an app or website are functional.
* ['Codacy'](https://www.codacy.com/) for cross-checking code quality/style.
