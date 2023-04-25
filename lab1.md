# Attention all CSE 15L Students!

Here are some steps to log into your course-specific account:


### Reset Your Course-Specific Account   <br>   
reset your course-specific account password here [reset password](https://sdacs.ucsd.edu/~icc/index.php) ; your account will have a username of cs15lsp23zz, 
where zz is replaced by two other letters unique to your account. Use this username instead of your normal AD username, so that you're resetting the password
for your course-specific account and not your whole UCSD account.

### Install Visual Studio Code   <br>   
Install Visual Studio Code here: [VSCode](https://code.visualstudio.com/) . 
I already had VSCode installed so I didn't have to install it again.
This is what it looks like when I open VSCode. If you have it installed correctly, your VSCode page should look like this:
![Image](https://raw.githubusercontent.com/AVGithub-1/cse15l-lab-reports/main/vscode_start_page.JPG)

### Remotely Connect To An Ieng6 Server   <br>   
Next, you will remotely connect to an ieng6 server and log in to your course specific account.
If you have windows:
You need to install git from here [Git](https://gitforwindows.org/) . Once you have git installed, you will use it to remotely connect. 
Help with using git bash in VSCode can be found here [Git Bash in VSCode](https://stackoverflow.com/questions/42606837/how-do-i-use-bash-on-windows-from-the-visual-studio-code-integrated-terminal/50527994#50527994)
Afterwards, open a new terminal in VSCode that uses git bash and run this command:
`ssh cs15lsp23zz@ieng6.ucsd.edu`
You will likely get a message like this:
```
The authenticity of host 'ieng6.ucsd.edu (128.54.70.227)' can't be established.
RSA key fingerprint is SHA256:ksruYwhnYH+sySHnHAtLUHngrPEyZTDl/1x99wUQcec.
Are you sure you want to continue connecting (yes/no/[fingerprint])? 
```
Type "yes" and press enter, and then it will prompt you to enter your password. Enter your course-specific password.
The output should look something like this, except with your course-specific account username instead of mine.
![Image](https://raw.githubusercontent.com/AVGithub-1/cse15l-lab-reports/main/remote_connecting.JPG)

### Try Out Some Commands   <br>   
Afterwards, you can try running some commands in the terminal like `cd`(switches your terminal to another directory), `ls`(returns a list of all the files/folders in your current directory), `cp`(copies files from one directory to another), `pwd`(displays your current working directory) and `mkdir`(makes a new directory). For example, you could run `cd ~`, `ls -lat`, `ls <directory>` where `<directory>` is `/home/linux/ieng6/cs15lsp23/cs15lsp23abc`, where abc is another group member's username. 
For example, mine looks like this(Note: some commands throw `Permission Denied` or `No such file or directory`. This is supposed to happen):

![Image](https://raw.githubusercontent.com/AVGithub-1/cse15l-lab-reports/main/trying_commands.JPG)

The first two commands, ```ls -lat``` and ```ls -a```, both return a list of all the files and folders in my current directory, the root directory. The -lat command displays the list vertically and gives some additional information about each item in the directory. The -a command displays the list horizontally but doesn't give any extra information about each item.

The three commands after these return "No such file or directory" due to there not being any files or directories with those absolute paths that are within my root directory.

The next two commands return "Permission Denied" because while the direcotries they try to access are within the ieng6 directory like my current directory, meaning they share a parent directory with my current directory, these directories are meant for other accounts and therefore I am not allowed to access them.
