# Lab Report 1 - Week 2

[Class Instructions](https://ucsd-cse15l-w22.github.io/week/week1/)

*This tutorial is for a Windows computer

## Step 1: Installing Visual Code Studio

> Install Visual Code Studio using the link [here](https://code.visualstudio.com/). Make sure to download the Windows version of VSCode.

This is a screenshot of what my VSCode looks like when I open it. Yours might look a little different:
![Image](Lab_Report_Week_2_Screenshots/VSCode.png)

***

## Step 2: Remotely Connecting

> Since you are using a Windows computer, you have to follow the extra steps to install OpenSSH Client and OpenSSH Server. The instructions to do so are [here](https://docs.microsoft.com/en-us/windows-server/administration/openssh/openssh_install_firstuse). Follow these instructions up until the title "Connect to OpenSSH Server." **Make sure you are running VSCode and/or Powershell as an administrator.** If you do not, the commands will not work. [Here](https://docs.microsoft.com/en-us/visualstudio/ide/user-permissions-and-visual-studio?view=vs-2022#:~:text=On%20the%20Windows%20desktop%2C%20right,and%20then%20select%20OK%20again.) are instructions for how to run VSCode as an admin on Windows 10.
> After that, find your account info for the CSE 15L class using [this link](https://sdacs.ucsd.edu/~icc/index.php). It may tell you you need to reset the password for the account. If so, do it. The effects of the password change might take some time to take effect. Your account should have the name cs15lwi22--, where the "--" would be replaced by letters specific to your account.
> To connect to the server, run the command `ssh cs15lwi22--@ieng6.ucsd.edu`, but with the "--" replaced by the letters in your account. If a question about authenticity pops up, answer "yes." It will then ask for the password (that you may have changed in this step). If the password doesn't work, wait some more. It could just be that the password change hasn't gone into effect yet. If the password works, you will connect to the server.

This is a screenshot of what messages could pop up after the password works:
![Image](Lab_Report_Week_2_Screenshots/Remotely_Connecting.png)

***

## Step 3: Trying Some Commands
> Once you've connected to the server, you can try out some commands there. You can also log off the server with the command `exit` or by doing Ctrl-D and try some commands on your computer. Since the server uses the Linux OS, and you computer should use the Windows 10 OS, some commands might not work on both of them, and they could do different things.
> Some commands are:
- cd (changes directory to the directory you specify after it)
- ls (lists files and directories in the current directory)
- pwd (tells you the name of the current directory)
- mkdir (makes a directory with the name you type after it)
> You can also search the internet for other commands to try

This is an image of the commands on the server:
![Image](Lab_Report_Week_2_Screenshots/Commands_Linux.png)

This is an image of the commands on my laptop:
![Image](Lab_Report_Week_2_Screenshots/Commands_Windows.png)

***

## Step 4: Moving Files with scp
> I managed to move the WhereAmI.java file pretty easily to the server. I then logged into the server did the command ls and saw that the file was there. I then ran the javac and java commands to run the file. The getProperty method gets the property for the computer it's run on. I know this because on my computer, System.getProperty("os.name") gave "Windows 10," while on the school server, it gave "Linux."

This is an image of me moving "WhereAmI.java" to the school server and running the java file.
![Image](Lab_Report_Week_2_Screenshots/Moving_Files_and_Doing_Java.png)

***

## Step 5: Setting an SSH Key
> During the lab, I managed to generate a ssh key, but when I went to run the extra commands needed for the Windows OS, they just would not work. I got stuck at this point during the lab. But later, in my own time, I figured out the issue. I wasn't connected to VSCode as an administrator, so I couldn't run those commands. Like I mentioned in Step 2, I figured out how to do that. And then the commands worked. But after that, I had issues figuring out how to copy the public key into the school server. I messed up and created a directory called "authorized_keys" in .ssh in the server instead of a textfile, and I kept trying over and over, because I couldn't figure out what was going wrong. I was managing to copy the public key into the "authorized_keys" directory, but it obviously didn't stop the need for a password to connect to the server. I finally realized my mistake, and deleted the directory I made, and then ran the command that copied the key into a textfile. And then I could connect to the school server without a password.

This is an image of me connecting to the server without a password:
![Image](Lab_Report_Week_2_Screenshots/SSH_Key.png)

***

## Step 6: Optimizing Remote Running
> First, I copied a java file I made called "TestFastEdit.java" into the server. I then tried doing the javac and java commands in one line by typing out `ssh cse15lwi22aad@ieng6.ucsd.edu "javac TestFastEdit.java; java TestFastEdit"`. It worked, compiling and running the file in one line. I thought about it for some time and reread the lab instructions to understand how the quotation marks and semi-colons worked in the command line. I came up with the line `scp TestFastEdit.java cs15lwi22aad@ieng6.ucsd.edu:~/; ssh cs15lwi22aad@ieng6.ucsd.edu "javac TestFastEdit.java; java TestFastEdit"` that I thought would copy the file and compile and run it on the school server in one line. It worked. I used a semicolon to separate the scp and ssh commands. Then I put the javac and java commands in between quotation marks and separated by a semicolon. The quotes made sure both commands ran on the server through the ssh command.
> Typing the entire line out took some time, but when I made an edit to the file, I used the up arrow to rerun the command, so it only took a second or two.

This is an image of me copying, compiling, and running the java file on the server in one line:
![Image](Lab_Report_Week_2_Screenshots/Optimizing_Remote_Running.png)
