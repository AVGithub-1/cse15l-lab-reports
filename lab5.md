# Part 1

## Original Post

**What environment are you using(computer, operating system, web browser, terminal/editor, and so on)?**

I am using VSCode and running my files in a bash terminal on my local machine.


**Detail the symptom you're seeing. Be specific; include both what you're seeing and what you expected to see instead. 
Screenshots are great, copy-pasted terminal output is also great. Avoid saying "it doesn't work".**

When I run my runner.sh script, which is supposed to compile and run my java program, Scenario.java, it returns an unexpected output. 

This is my bash script, runner.sh:

![Image](https://raw.githubusercontent.com/AVGithub-1/cse15l-lab-reports/main/cs15l_lab5pic1.jpg)

It is meant to run the command 
```javac Scenario.java``` 
to compile Scenario.java, then run Scenario.java with the command line arguments 5 and 2
if successfully compiled.

My java program, Scenario.java, is meant to take in a number as a command line argument and run a method called multiplier with the 
command-line argument as the input value. The multiplier method is supposed to return an array with all values from 1 to n (its first
input parameter) multiplied by factor(it's second input parameter). Then, after the mutiplier method is run, the array it returns should be 
be printed out.

This is the code for Scenario.java:<br>

![Image](https://github.com/AVGithub-1/cse15l-lab-reports/blob/main/cs15l_lab5pic2_1.JPG)

However, when runner.sh tries to compile Scenario.java, it runs into this error:

![Image](https://raw.githubusercontent.com/AVGithub-1/cse15l-lab-reports/main/cs15l_lab5pic3.JPG)


**Detail the failure-inducing input and context. That might mean any or all of the command you're running, a test case, 
command-line arguments, working directory, even the last few commands you ran. Do your best to provide as much context as you can.**

The failure inducing input seems to be when runner.sh runs the line java Scenario 5 2

## TA Response

Hi Akhil! I believe you are facing this error because when you define the returnArray variable, you set its length equal to 
the input parameter factor instead of n. Why don't you try changing line 9 to create an array of type int with length n.

## Student Follow-Up Response

I tried your suggestion and it worked! 

Here is my edited code:

![Image](https://raw.githubusercontent.com/AVGithub-1/cse15l-lab-reports/main/cs15l_lab5pic4.JPG)

and here is my new output: <br>
![Image](https://raw.githubusercontent.com/AVGithub-1/cse15l-lab-reports/main/cs15l_lab5pic5.JPG)

The bug I had was that in line 11 of Scenario.java, in the multiplier method of the Scenario class, I created the object returnArray
as an int array with the size of factor instead of size n. However, since the for loop below it iterates from 0 to n-1, and 
adds an element to returnArray every time, if n is greater than factor then returnArray will be full and you won't be able to access 
any indices greater than factor-1. This leads to an ArrayIndexOutOfBoundsException.


## Setup Information

Directory that contains runner.sh bash script and Scenario.java program: /c/Users/Akhil/CS15L_Lab5

Contents of runner.sh file(it never gets changed):

```
javac Scenario.java

if [ $? -eq 0 ]; then
    echo "Compilation successful. Running the Java program..."
    echo ""


    java Scenario 5 2
else
    echo "Compilation failed. Please check the Java source code and try again."
fi
```

Contents of Scenario.java before fixing the bug:

```

import java.util.Arrays;

class Scenario{

    //returns an array of size n where each element is its index multiplied by 2 
    public static int[] multiplier(int n, int factor){

        int[] returnArray = new int[n];
        for(int i = 0; i < n; i++){
            returnArray[i] = factor*(i+1);
        }
        
        return returnArray;
    }


    public static void main(String[] args){

        int[] multArray = multiplier(Integer.parseInt(args[0]), Integer.parseInt(args[1]));

        System.out.println(Arrays.toString(multArray));
    
    }

}
```

command-line commands I ran to trigger the bug(in order): 

```
javac Scenario.java
```

```
java Scenario.java 5 2
```

What to edit:
in line 9 of Scenario.java, in the brackets of new int[factor], replace "factor" with "n".



# Part 2:

In the second half of the quarter, I learned how bash scripts work and how useful they can be when testing and developing 
programs. I thought it was really helpful because now that I know how to use them, I don't have to keep typing out several
commands in my terminal and instead can just put them all in a bash script and just run that script!.
