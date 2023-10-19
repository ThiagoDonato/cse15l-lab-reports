# 1. Using the commands with no arguments
## cd
```
[user@sahara ~]$ cd
```
There was no output and the working directory was /home when this command was run. Doing cd without any arguments just takes you to your root/home directory. This output is not an error.
## ls
```
[user@sahara ~]$ ls
lecture1
```
This command listed everything that was in the current working directory (/home). In this case there was only lecture1. Output is not an error.
## cat
```
[user@sahara ~]$ cat
^C
```
This command tried to read each file parameter and print out standard output. I didn't specify any files, so it wasn't reading anything. This is not an error, terminal is waiting for an input. To get back to the command line, I used control+C. Working directory was still /home.
# 2. Using the command with a path to a directory as an argument
## cd
```
[user@sahara ~]$ cd lecture1
[user@sahara ~/lecture1]$
```
When I ran `cd lecture1` the working directory was home. After running it, I changed it to /home/lecture1. Output was not an error.
## ls
```
[user@sahara ~/lecture1]$ ls /home/lecture1/messages
en-us.txt  es-mx.txt  pt-br.txt  zh-cn.txt
```
w.d is home/lecture1, but the command that was run specified that I wanted to list all the files in the directory /home/lecture1/messages, so that's what we got as an output. Output is not an error.

## cat
```
[user@sahara ~/lecture1]$ cat  /home/lecture1/messages
cat: /home/lecture1/messages: Is a directory
```
w.d was /home/lecture1. The cat command can't read a directory and print out standard output, it can only read files. That's why we get the message warning me that /home/lecture1/messages is a directory. Thus, output is an error message.

# 1. Using the command with a path to a file as an argument
## cd
```
[user@sahara ~/lecture1]$ cd /home/lecture1/messages/pt-br.txt
bash: cd: /home/lecture1/messages/pt-br.txt: Not a directory
```
w.d was /home/lecture1. This output is an error warning me that cd takes a directory as an argument, and I gave it a file path.
## ls
```
[user@sahara ~/lecture1]$ ls /home/lecture1/messages/pt-br.txt
/home/lecture1/messages/pt-br.txt
```
w.d was /home/lecture1. Using ls on a file lists only the file specified, since it exists. That is the output we got. This output is not an error.
## cat
```
[user@sahara ~/lecture1]$ cat  /home/lecture1/messages/pt-br.txt
Ola Mundo
```
w.d was /home/lecture1. This time, since we gave cat a file path, it read the data from the file and printed the content as output. Output was not an error

