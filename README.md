# TestGit
Learning to use command line with Github

General ideas:
If have not "cloned" a repository from online, then you will first "initialize" a repository on your computer.
You navigate to the repository then use `git init`.
This will create some hidden files in the repository which are used by Git in order to track changes made to files in the repository.

`git status` will give you a summary of the status of your local repository.

You work on files in a "workspace".
When you have modified them in ways you want to save, you add them to a "staging area".
    This is done with `git add <filename>`.
    `git add .` will add all existing tracked files.

Once you have several changes you want to save permanently, you save them onto your "branch".
    This is done with `git commit`.
    `git commit -m 'message'` allows you to leave the commit message in a single line when you commit.
    `git commit -a` allows you to commit tracked files without "staging" first.
You may have several "branches" on any one project.
If you have changes but are not ready to commit them, but you need to change branches to do other work before you can finish making the current changes, you can save your working changes with `git stash`.
You can retrieve those changes with `git pop` or possibly `git stash apply`.

To create a new branch, use `git branch <name>` and switch to it with `git checkout <name>`.
Merging branches is done with `git merge <name>`.
If you have conflicts, you will be prompted and you will need to fix them before the merge can be finished.

All of the above steps refer to changes you make on your local repository (on your own computer).
Working with a remote repository means having your code online where others can "clone" it as well as suggest "pulls".
To "clone" an online repository locally on your machine, use `git clone <html>`.
Once you have navigated into the "cloned" repository it behaves just like any other local repository.
If the remote repository has changes which are not reflected in your local repository, you can do `git fetch origin` followed by `git merge` to update your local repository.
`git pull origin` should work the same way as `git fetch origin` followed by `git merge`.
To send changes on your local repository to the remote repository, use `git push origin`.
You may need user name and password to submit the changes.