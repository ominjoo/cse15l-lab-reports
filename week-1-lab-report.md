# Minjoo O: CSE15L Lab 1 Report
---
## Using command: `cd`

**Using the command with no arguments:** \
![Image](cd-no-arg.png) 
* The working directory was: /home/lecture1
* Using the command `cd` with no following argument switches the user's location from the current directory to the home directory because when there is no argument or directory to switch the terminal into, the terminal goes to its default directory, which is the home.
* This output is not an error. Using the command `cd` should take the user to the home directory.
  
**Using the command with a path to a directory as an argument:** \
![Image](cd-path-direct.png) 
* The working directory was: `/home`
* The command `cd` with a path to a directory as an argument allows the user to switch directories. So, because the working directory was `/home`, and the argument or path provided (`lecture1`) is a directory within the home directory, the output is that we are now in the lecture1 directory (`/home/lecture1`)
* This output is not an error. Using the command `cd` with a valid argument (path to directory) should take the user to the specified directory.
  
**Using the command with a path to a file as an argument:** \
![Image](cd-path-file.png)
* The working directory was: `/home/lecture1`
* This output is due to the fact that the `cd` command cannot accept a file or anything that is not a directory as an argument. The `cd` command is used to changed from one directory to another directory, not to access files.
* This output is an error. The `cd` command cannot execute because the argument provided is not a path to a directory.
  
---

## Using command: `ls`

**Using the command with no arguments:** \
![Image](ls-no-arg.png) 
* The working directory was: /home
* Using the command `ls` with no following argument lists the files and directories of the directory that we are currently in. Since we are in the home directory, we see lecture1 listed.
* This output is not an error. Using the command `ls` should list the files and directories of the directory we are in.
  
**Using the command with a path to a directory as an argument:** \
![Image](ls-path-direct.png) 
* The working directory was: `/home`
* Even though we are in the home directory, because we used the `ls` command with `lecture1` as the argument, the files and directories contained within lecture1 are listed. 
* This output is not an error. Using the command `ls` with a directory as an argument should list its files and directories.
  
**Using the command with a path to a file as an argument:** \
![Image](ls-path-file.png)
* The working directory was: `/home/lecture1`
* Since we are in the lecture1 directory, we can access its files. When we use `ld` with a file name as an argument, it simply repeats the file name because files are not folders and therefore cannot contain more files or directories
* This output is not an error. Using the command `ls` with a filer as n argument just repeat its file name.
