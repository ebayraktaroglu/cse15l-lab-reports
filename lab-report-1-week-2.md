# Week 2 Lab Report
## Step 1: Installing Visual Code Studio

> I had already installed Visual Code Studio for my CSE 11 class last quarter, so I didn't really do anything for this step.

This is an image of my open VSCode:
![Image](Lab_Report_Week_2_Screenshots/VSCode.png)

***

## Step 2: Remotely Connecting

> Since I am working on a Windows laptop, I had to follow the extra steps to install OpenSSH Client and OpenSSH Server. I checked and saw that I already had OpenSSH Client on my laptop, so I thought I was done and ignored all the other necessary steps. This caused problems later on during the lab. But I was still able to remotely connect to the ieng6 server after resetting my password and waiting for the password to update.
> 
> Later, outside the lab, I OpenSSH Server as well. I was getting some errors with the commands I needed to run, and I realized this was because wasn't opening VSCode as an administrator. I researched how to do that, and then the commands worked.

This is an image of me connecting to the server:
![Image](Lab_Report_Week_2_Screenshots/Remotely_Connecting.png)

***

## Step 3: Trying Some Commands
> I connected remotely to the server, then tried some of the commands. I used ls to see the files and directories, then used pwd to see the name of the directory, then used that info to change the directory to perl5. There was nothing in there. I then tried commands on my own computer. I used the ls command, and it worked a little differently than it did on the linux os, but it did show the directories. I used the pwd command, got the directory name, and added \Downloads to change directory (using cd) to Downloads.

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
> First, I copied a java file I made called "TestFastEdit.java" into the server. I then tried doing the javac and java commands in one line by typing out `ssh cse15lwi22aad@ieng6.ucsd.edu "javac TestFastEdit.java; java TestFastEdit`. It worked, compiling and running the file in one line. I thought about it for some time and reread the lab instructions to understand how the quotation marks and semi-colons worked in the command line. I came up with the line `scp TestFastEdit.java cs15lwi22aad@ieng6.ucsd.edu:~/; ssh cs15lwi22aad@ieng6.ucsd.edu "javac TestFastEdit.java; java TestFastEdit"` that I thought would copy the file and compile and run it on the school server in one line. It worked. I used a semicolon to separate the scp and ssh commands. Then I put the javac and java commands in between quotation marks and separated by a semicolon. The quotes made sure both commands ran on the server through the ssh command.
> Typing the entire line out took some time, but when I made an edit to the file, I used the up arrow to rerun the command, so it only took a second or two.

This is an image of me copying, compiling, and running the java file on the server in one line:
![Image](Lab_Report_Week_2_Screenshots/Optimizing_Remote_Running.png)
