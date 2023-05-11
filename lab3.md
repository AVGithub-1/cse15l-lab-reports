# Find Command:


The source I used: [Link](https://www.hostinger.com/tutorials/how-to-use-find-and-locate-commands-in-linux/)

## Find ~ Command
you can use find ~ to search for files in your home directory

for example, if you use this command:

```
find ~ -name pmed.0020274.txt
```
then you will get this output (with your specific ieng6 account instead of mine).
```
/home/linux/ieng6/cs15lsp23/cs15lsp23fg/stringsearch-data/technical/plos/pmed.0020274.txt
```

Here is another example:

```
find ~ -name biomed
```
and this output 
```
/home/linux/ieng6/cs15lsp23/cs15lsp23fg/stringsearch-data/technical/biomed
```


## Find . Command:

The find . command searches for files and directories in your current, working directory.

for example, the command:
```
find . -name biomed
```
produces the output
```
./stringsearch-data/technical/biomed
```
because the biomed directory is in the current directory. However, say we enter the biomed directory and then try to 
find the plos directory with this command:
```
find . -name plos
```
then it doesn't return anything because the plos directory is not in the biomed directory, our current directory.


## Find -not Command

Adding -not to your find command allows you to search for everything in a directory except for the keyword you put into 
the command. For example, while in the technical directory, the command:
```
find -not -name "*.txt"
```
returns the output
```
.
./911report
./biomed
./government
./government/About_LSC
./government/Alcohol_Problems
./government/Env_Prot_Agen
./government/Gen_Account_Office
./government/Media
./government/Post_Rate_Comm
./plos
```
Notice that they are all not .txt files.

Another example:
```
find. -not -name "*pmed*"
```
gives you all the files in the technical direcotry except for files with "pmed" in their name (its too long of a list to show
here).

## Find -type Command

If you add -type to your find command, you can search for specific types of data in your system. <br>
For example, this command searches for all the directories within your working directory.
```
find -type d
```
And this command searches for all the normal files in your working directory.
```
find -type f
```
