---
layout: default
permalink: /guides/vscode-git
title: Setting up VS Code
---

# Using VSCode with Git and SSH to Complete/Submit a programming Assignment

> Before starting, you should have completed the [VScode Setup Guide with SSH](vscode-ssh). This guide assume you have VScode and SSH capabilities installed, as well as the VSCode extension Remote Development Extension. 


1. Accept the GitHub classroom assignment and follow the link to the repository. For example, if you are working on Lab 1, after accepting the assignment, you'll have a new repository named `lab-1-username` where `username` is your GitHub username. The assignments can all be found on the [schedule page](../schedule.md).

2. Copy the repository link by clicking the `Code` button and then the `SSH` label, followed by the `copy/paste` button. You should have already set up an ssh key by following this [guide](vscode-ssh.md).
   ![Github Repo Link](/images/module1-git.png)

3. In a VSCode window where you have connected remotely to a Linux machine, cs01-cs06 (refer to this [guide](vscode-ssh.md)). Click the `Source Control` icon on the left hand side. Then click the `Clone Repository` button.
   ![VScode New Window, Explore, Clone Repository](/images/Clone-Repo.png) 
4. Paste the repository link that you copied in step 2 in the command pallet. 
   ![Enter repo link](/images/Clone-Repo2.png)
5. Choose a folder where you want to clone the repository. Save it wherever you want, but I like to create a folder called `Repos` or `cs240` to save my projects.
   ![Confirm Location](/images/Clone-Repo3.png)
6. Go ahead and open the repo in this window by selecting `Open`
   ![Open in this window](/images/Clone-Repo-Open.png)
7. Click Yes, I trust the authors to continue.
   ![Init Complete](/images/Clone-Repo-Trust-Authors.png)
8. Once complete, you'll have your workspace ready to go.
   ![Init Complete](/images/Clone-Repo-Working.png)
9. Do your work. **Save your changes.** And once done, you need to commit your work. Start by clicking on the `Source Control` symbol on the left.
   ![Repo symbol](/images/VSCodeGitRepoSymbol.png)
10. Add the modified files (or new files) to be staged for commit by pressing the `+` next to the files you want to add.
   ![add files to the commit](/images/VSCodeGitChanges.png)
11. The files are now staged.
   ![add files to the commit](/images/VSCodeGitStagedChanges.png)
12. Type a message in the text area above the `Commit` button. Click the &#10003;`Commit` button to perform the commit.
   ![add files to the commit](/images/VSCodeGitCommitMessage.png)
13. Finally, **push** your changes to GitHub by clicking the `...` button, followed by selecting `Push` from the dropdown menu.
   ![Push changes](/images/VSCodeGitPush.png)
14. **Alternatively**, you could click the `Sync` button, which will both **push** your changes, and **pull** down any changes to the repository that exist on GitHub.  
   ![Push changes](/images/VSCodeGitSync.png)  
15. Finally, finally, you should go back to GitHub as a final check to make sure you pushed all your changes.
   ![Push changes](/images/VSCodeGitGitHub.png)


## Using the git command line in the integrated terminal

You can also use the command line to do the git commands. 

```
git add file.txt        #add a file to the commit
git commit -m "message" #perform the commit with the commit message
git push                #push the commit to GitHub 
```

If you want to add all the files that have been modified and commit all at once, use the following

```
git commit -a -m "message" 
```


## Asking you to set up your git profile?

If you're getting a error saying you need to setup your name and email, then open the integrated terminal on your remotely connected (cs01 - cs06) VSCode window. Then follow the steps below.

> You only need to do this once
   
1. In the terminal run the following commands 
   ```
   git config --global user.name "JohnDoe23"
   git config --global user.email johndoe@example.com
   git config --global pull.rebase false
   ```
   - Where `JohnDoe23` is replaced with your GitHub username and `johndoe@example.com` is replaced with the email address you used to sign up to GitHub

2. To verify your settings run the following command.
   ```
   git config --list
   ```
3. Done.
