# Lab Report 1
## `cd`
![Image](cd_none.png) <br>
Absolute path: `/Users/nian-nianwang/lecture1` <br>
Why: without any arguments, it sets working directory back to the home directory <br>
Error: not an error

![Image](cd_directory.png) <br>
Absolute path: `/Users/nian-nianwang` <br>
Why: the directory `lecture1` exists under the home directory and directs to `lecture1` <br>
Error: not an error

![Image](cd_file.png) <br>
Absolute path: `/Users/nian-nianwang/lecture1` <br>
Why: directory is not changed and threw an error because a file is not a directory for `cd` command <br>
Error: it is an error, `cd` doesn't direct to a file directory

## `ls`
![Image](ls_none.png) <br>
Absolute path: `/Users/nian-nianwang/lecture1` <br>
Why: without any arguments, it lists all the files in the current directory, which is `lecture1` <br>
Error: not an error

![Image](ls_directory.png) <br>
Absolute path: `/Users/nian-nianwang/lecture1` <br>
Why: specifying the path to `messages` lists out the files in the directory `messages` instead of current directory <br>
Error: not an error

![Image](ls_file.png) <br>
Absolute path: `/Users/nian-nianwang/lecture1` <br>
Why: the pathname is a file, `ls` displays the specific file <br>
Error: not an error

## `cat`
![Image](cat_none.png) <br>
Absolute path: `/Users/nian-nianwang/lecture1` <br>
Why: without any arguments, it will just return the input string <br>
Error: it is an error, it doesn't read any file

![Image](cat_directory.png) <br>
Absolute path: `/Users/nian-nianwang/lecture1` <br>
Why: we provided a directly instead of a file and the directory cannot be read like a text file <br>
Error: it is an error, a directly cannot be read

![Image](cat_file.png) <br>
Absolute path: `/Users/nian-nianwang/lecture1` <br>
Why: we provided a file and the en-us.txt file was successfully read, returning the string in the text file <br>
Error: not an error

