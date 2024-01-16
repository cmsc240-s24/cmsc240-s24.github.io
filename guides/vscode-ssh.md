---
layout: default
permalink: /guides/vscode-ssh
title: VScode with SSH client
---

# Running VSCode with SSH via `cs01 - cs06.richmond.edu`

> You can use this guide write code using VSCode while using `ssh` connection to `cs01 - cs06.richmond.edu` (the UR Computer Science Linux machines). 
>

1. Install Visual Studio Code (VS Code)
[https://code.visualstudio.com/download](https://code.visualstudio.com/download)

2. Install the [Remote - SSH Extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-ssh)

3. Install SSH on your local computer
   - Ubuntu/Debian : Comes pre-installed but if it doesn't
   - MacOS : Comes pre-installed
   - Windows : Install [Git for Windows](https://git-scm.com/download/win) comes with an ssh client

4. If you are using a wireless connection, you must connect via the **urwin** network.
   If you are connecting from off campus, then use the UR VPN
   - See this [guide](https://spidertechnet.richmond.edu/TDClient/1955/Portal/KB/ArticleDet?ID=93543) from SpiderTechNet for more details.

5. Open a new VSCode Window
   - Open the command pallet with **F1** key. On MAC OS you may need to hit **fn-F1** ("Function" key and F1 at the same time). 
   - Type `Remote-SSH: Connect to host`
   - Then enter `YOUR_URNETID@cs01.richmond.edu` where `YOUR_URNETID` is your NetID for UR. 
   - The available Linux machines are cs01 - cs06.  You may need to try multiple machines if one of them is powered off.
   - If prompted for the operating system, select Linux, and hit select that you want to continue when it mentions a fingerprint.
   - Hit enter, and you may be prompted for a password, enter your UR account password
   - Once your connected you should see a blue bar at the bottom left saying something like `SSH cs01.richmond.edu.`



### Setting up an SSH key on Linux with GitHub

> Note you only need to do this once

1. Once your connected to `cs01 - cs06` via instructions above open an integrated terminal
   - Open the command pallet with **F1** key
   - Type/select `Terminal: Create New Terminal` 
   - Alternatively you can `Terminal` menu and select `New Terminal`
   - Note:  You should be on a remote terminal it will have a prompt that reads something like `[dbalash@cs01 ~]$`

2. Follow these steps to generate a ssh-key with `ssh-keygen`
   - In the terminal type
   ```
   ssh-keygen
   ```
   - **Hit enter to each of the questions**
   - No, you do not need a passphrase

3. Follow these steps to copy your public key
   - In the terminal type
   ```
   cat .ssh/id_rsa.pub
   ```
   - This will print out your public key, select and copy it from the terminal
   - Make sure you copy the whole thing beginning with `ssh-rsa` ending with something like `urnetid@cs01` or `urnetid@l1-jps-225-lx07`
  
4. Go to [github.com](https://github.com) and add your SSH key
   - make sure you're logged in
   - select your icon in the upper right
   - select settings
   - select `SSH and GPG Keys` from the options
   - click the green button `New SSH key`
   - Paste your ssh-key you copied from above in there and hit enter
   
5. To test the secure connection run the following command in the terminal.
   ```Shell
   ssh -T git@github.com
   ``` 
6. It may ask the following "Are you sure you want to continue connecting (yes/no/[fingerprint])?" Type `yes` and hit `Enter`.

7. If you seen the message "You've successfully authenticated, but GitHub does not provide shell access." It worked!  You are done with the setup and you shouldn't need a password to push/pull your repos.  

### Setting up your git profile on `cs01 - cs06`

> You only need to do this once
   
1. Once your connected to `cs01` via instructions above open an integrated terminal
   - Open the command pallet with **F1** key
   - Type/select `Terminal: Create New Terminal` 
   - Alternatively you can `Terminal` menu and select `New Terminal`
2. In the terminal run the following commands
   ```
   git config --global user.name "JohnDoe23"
   git config --global user.email johndoe@example.com
   ```
   - Where `JohnDoe23` is replaced with your GitHub username and `johndoe@example.com` is replaced with the email address you used to sign up to GitHub

3. To verify your settings run the following command.
   ```
   git config --list
   ```
4. Done.






