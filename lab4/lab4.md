# Lab 4

Note: all commands in <> are meant to be keypresses. For example, `<enter>` means press the Enter key.

## Step 4:

I logged into my ieng6 account with by typing this command: `ssh cs15lsp23fg@ieng6.ucsd.edu <enter>`. 
  
![Image](https://raw.githubusercontent.com/AVGithub-1/cse15l-lab-reports/main/lab4/cs15l_lab4pic1.JPG)
![Image](https://raw.githubusercontent.com/AVGithub-1/cse15l-lab-reports/main/lab4/cs15l_lab4pic2.JPG)

## Step 5:

I then cloned my fork of the lab7 repository by typing this command: `git clone git@github.com:AVGithub-1/lab7.git <enter>`.
![Image](https://raw.githubusercontent.com/AVGithub-1/cse15l-lab-reports/main/lab4/cs15l_lab4pic3.JPG)

## Step 6:

I typed `cd lab7 <enter>` to change my directory to the lab7 repository, then I ran the tests using `bash test.sh <enter>`, which ran the commands that compiles all the java files and runs the tests in ListExamplesTests. This showed that one test failed.

![Image](https://raw.githubusercontent.com/AVGithub-1/cse15l-lab-reports/main/lab4/cs15l_lab4pic4.JPG)

## Step 7: 

To start editing, I entered the file using `vim ListExamplesTests.java <enter>` and it showed this:
![Image](https://raw.githubusercontent.com/AVGithub-1/cse15l-lab-reports/main/lab4/cs15l_lab4pic5.JPG)

To edit, I first typed in `/index1 <enter> <N>` to get to the last occurence of "index1" in the file, then `<l> <l> <l> <l> <l> <l>` to get my cursor directly to the right of the 1 in index1, then `<i>` to enter insert mode. I then pressed `<backspace>` to delete the 1 and `<2>` to put a 2. Then I pressed `<Esc>` and `<:><w><q><Enter>` to save and exit the file. It looked like this at the end:
  
![Image](https://raw.githubusercontent.com/AVGithub-1/cse15l-lab-reports/main/lab4/cs15l_lab4pic6.JPG)
 
## Step 8:
  
I ran the tests again with `bash test.sh <enter>`:
  
![Image](https://raw.githubusercontent.com/AVGithub-1/cse15l-lab-reports/main/lab4/cs15l_lab4pic7.JPG)
  
## Step 9:
  
I then used `git add *` to add the changes I made in all of the files in the lab7 repository, then `git commit -m "fixed ListExamples"` to commit my changes with the message "fixed ListExamples" and `git push` to push my changes to the official lab7 repository on my Github account.
  
![Image](https://raw.githubusercontent.com/AVGithub-1/cse15l-lab-reports/main/lab4/cs15l_lab4pic8.JPG)
