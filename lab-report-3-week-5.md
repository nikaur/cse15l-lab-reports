# Week 5 Lab Report 

The following report considers the command find, and explores three command-line options for this command. 

## **Find**

### **Command-Line Option 1:** ***-iname option***

This command-line option is similar to the -name option, however, it is case-insensitive which would be especially helpful if we are looking for a file but don’t know if some of the letters in the file name are or are not capitalized. 

*Example 1:*

```
$ find ./technical -iname "Biomed"

./technical/biomed
```

In this situation, we are looking for a directory called “biomed” but when using the find command we use “Biomed” instead. The -iname option makes it possible for us to still find this directory which is useful considering how easy it is to make case errors. 

*Example 2:* 

```
$ find ./technical/government -iname "*ALCOHOL*"

./technical/government/Alcohol_Problems
```

This is another situation where we are looking for a directory but when we type the name we use all capital letters when the actual directory name doesn’t. The -iname option shows us the directory we are looking for anyways, making it so that different formatting/naming preferences between people don’t make it difficult to still find the necessary information. 

*Example 3:* 

```
$ find ./technical/government/About_LSC -iname "*on*"

./technical/government/About_LSC/Comments_on_semiannual.txt
./technical/government/About_LSC/Special_report_to_congress.txt
./technical/government/About_LSC/CONFIG_STANDARDS.txt
./technical/government/About_LSC/commission_report.txt
./technical/government/About_LSC/ONTARIO_LEGAL_AID_SERIES.txt
./technical/government/About_LSC/LegalServCorp_v_VelazquezOpinion.txt
./technical/government/About_LSC/ODonnell_et_al_v_LSCdecision.txt
./technical/government/About_LSC/conference_highlights.txt
```

Here, we are able to find all files under the ./technical/government/About_LSC directory that have the letters “on” and this includes text files such as “CONFIG_STANDARDS.txt” and “ONTARIO_LEGAL_AID_SERIES.txt” and “ODonnell_et_al_v_LSCdecision.txt”. Having the find command be case insensitive means that we aren’t missing out on important file name information because of different naming systems. Some files are named in all capital letters, and if the command wasn’t case insensitive, we wouldn’t have found these files. 

### **Command-Line Option 2:** ***-type option***

This command-line option helps optimize the find command results by allowing you to specify what you are looking for if you know what that is – such as a file or a directory. 

*Example 1:* 

```
$ find ./technical/government -type d -iname "*o*" 

./technical/government
./technical/government/About_LSC
./technical/government/Env_Prot_Agen
./technical/government/Alcohol_Problems
./technical/government/Gen_Account_Office
./technical/government/Post_Rate_Comm
```

In this example, we specify that the type we are looking for is “d” or directory. Since the find command is recursive, specifying that we are only looking for “o” in the subdirectories of ./technical/government means that our output will not contain the subdirectories/files within the ./technical/government ‘s subdirectories. This filters our output so we can get the information that we need and not more than that. 

*Example 2:* 

```
$ find ./technical -type f -iname "*rr*" 
	
./technical/government/Media/Terrorist_Attack.txt
./technical/government/Media/Barr_sharpening_ax.txt
./technical/biomed/rr73.txt
./technical/biomed/rr74.txt
./technical/biomed/rr171.txt
./technical/biomed/rr167.txt
./technical/biomed/rr166.txt
./technical/biomed/rr172.txt
./technical/biomed/rr37.txt
./technical/biomed/rr196.txt
./technical/biomed/rr191.txt

```

In this situation, we’re in the directory ./technical and we specify that we’re looking for the type file denoted by “f”. Since find is recursive, it goes through all directories and subdirectories to find all the files with the characters “rr” and the first two lines of the output reflect how there are no directories listed, and only files which helps filter the output. 

*Example 3:* 

```
$  find ./technical -type d -iname "*e*"

./technical
./technical/government
./technical/government/Env_Prot_Agen
./technical/government/Alcohol_Problems
./technical/government/Gen_Account_Office
./technical/government/Post_Rate_Comm
./technical/government/Media
./technical/biomed
./technical/911report
```

Similar to example 1, this example looks through all of the subdirectories in technical as well as in technical to find all subdirectories with the character “e” as shown in the output above. This is especially useful if we are trying to go through a directory and find all directories related to a specific topic. 

### **Command-Line Option 3:** ***-maxdepth option***

This command-line option helps us go through a large file system and control how far into the structure the find command will go. 

*Example 1:*

```
$ find ./technical -maxdepth 1 -type d -name "*o*"

./technical/government
./technical/plos
./technical/biomed
./technical/911report
```

This example involves the -type command as well as the -maxdepth command where since the find command is recursive it stops at the depth of 1 and doesn’t go into the government, plos, biomed, or 911report directories to find the character “o”. This helps filter the output so that the search doesn’t go beyond what is necessary if we only want to find all the folders of a certain name but don’t need the files in those folders. 

*Example 2:*

```
$ find ./technical -maxdepth 2 -type f -name "*rr*"

./technical/biomed/rr73.txt
./technical/biomed/rr74.txt
./technical/biomed/rr171.txt
./technical/biomed/rr167.txt
./technical/biomed/rr166.txt
./technical/biomed/rr172.txt
./technical/biomed/rr37.txt
./technical/biomed/rr196.txt
./technical/biomed/rr191.txt
```

In this example, the maxdepth of 2 goes beyond and into the directories government, plos, biomed, and 911report to look for files that have the characters “rr” in them. This would be useful in situations where there’s a lot of folders and we don’t know which folder has the file we’re looking for. 

*Example 3:*

```
$ find ./technical -maxdepth 3 -iname "*ob*"

./technical/government/Alcohol_Problems
./technical/government/Media/Barnes_new_job.txt
./technical/government/Media/Bias_on_the_Job.txt
```

In this situation, we set the maxdepth to 3 so that when we’re looking through, it is going to look at the subdirectories within government, plos, biomed, and 911report to find either directories or files with the characters “ob” and output them which would be relevant if we have a lot of folders but no idea which folder or files are relevant to what we’re searching for. 