# Find Command:


The source I used: [Link](https://www.hostinger.com/tutorials/how-to-use-find-and-locate-commands-in-linux/)

## Find -size Command
you can use find -size to search for files in your home directory that are of a certain size. You can add + to the size argument to specify files that are greater than or equal to that size; adding - would specify files that are less than or equal to that size.

for example, if you use this command:

```
find . -size +200k
```
then it will search for all files in technical that are 200 kb or more, and you will get this output (with your specific ieng6 account instead of mine).
```
./911report/chapter-13.4.txt
./911report/chapter-13.5.txt
./911report/chapter-3.txt
./government/About_LSC/commission_report.txt
./government/Env_Prot_Agen/bill.txt
./government/Gen_Account_Office/GovernmentAuditingStandards_yb2002ed.txt
./government/Gen_Account_Office/Statements_Feb28-1997_volume.txt
./government/Gen_Account_Office/d01591sp.txt
```

Here is another example:

```
find . -size -2k
```
This command will search for all files in technical that are 2 kb or less, and it will give this output:
```
./plos/pmed.0020191.txt
./plos/pmed.0020226.txt
```


## Find -atime Command:

The find -atime command searches for files that were accessed a specified number of days ago. You can add + to the days argument to specify files that were accessed that many days or more; adding - would specify files that were accessed that many days or less.

for example, the command:
```
find . -atime -1
```
will find all the files in technical that I accessed less than a day ago, and produces this output:
```
./biomed/1471-2369-3-10.txt
./biomed/1471-2369-3-6.txt
./biomed/1471-2369-3-9.txt
./biomed/1471-2369-4-1.txt
./biomed/1471-2369-4-5.txt
```
Another example is this command, which will search for files in technical that I accessed more than a day ago. 
```
find . -atime +1
```
It will give this output:
```
./plos/journal.pbio.0030050.txt
./plos/journal.pbio.0030051.txt
./plos/journal.pbio.0030056.txt
./plos/journal.pbio.0030062.txt
./plos/journal.pbio.0030065.txt
./plos/journal.pbio.0030076.txt
./plos/journal.pbio.0030094.txt
./plos/journal.pbio.0030097.txt
./plos/journal.pbio.0030102.txt
./plos/journal.pbio.0030105.txt
./plos/journal.pbio.0030127.txt
./plos/journal.pbio.0030129.txt
./plos/journal.pbio.0030131.txt
./plos/journal.pbio.0030136.txt
./plos/journal.pbio.0030137.txt
```

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
find . -not -name "*pmed*"
```
gives you all the files in the technical direcotry except for files with "pmed" in their name (its too long of a list to show
here completely, here is a small part of the output).
```
./biomed/1471-2180-2-22.txt
./biomed/1471-2180-2-26.txt
./biomed/1471-2180-2-29.txt
./biomed/1471-2180-2-32.txt
./biomed/1471-2180-2-35.txt
./biomed/1471-2180-2-38.txt
./biomed/1471-2180-2-7.txt
./biomed/1471-2180-3-10.txt
```

## Find -type Command

If you add -type to your find command, you can search for specific types of data in your system. <br>
For example, this command searches for all the directories within your working directory.
```
find -type d
```
It will return this output:
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
And this command searches for all the normal files in your working directory.
```
find -type f
```
It will return this output(note: this is just a small part of the output, the full output is too long. The full output has all of the normal files in the technical directory and its subdirectories).
```
./biomed/1471-2350-2-2.txt
./biomed/1471-2350-2-8.txt
./biomed/1471-2350-3-1.txt
./biomed/1471-2350-3-12.txt
./biomed/1471-2350-3-7.txt
./biomed/1471-2350-3-9.txt
./biomed/1471-2350-4-2.txt
./biomed/1471-2350-4-3.txt
./biomed/1471-2350-4-4.txt
./biomed/1471-2350-4-6.txt
./biomed/1471-2369-3-1.txt
./biomed/1471-2369-3-10.txt
./biomed/1471-2369-3-6.txt
```
