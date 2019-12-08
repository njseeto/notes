---
title: "Command Line Basics"
date: 2019-12-08T12:13:32+05:30
description: "sudo !!"
disqus: false
tags: [command-line]
draft: true
---


`ls -l` → Brings up a list in long format as per below.

![command-line-example](/images/ls.png)


There are 7 columns in total, here is what they mean:

- Access rights
- Number of hard links. This counts the children and parent directories.
- Username of the file’s owner
- The name of the group that owns the file
- The size of the file in bytes
- Date and time of when that file was last modified
- Name of the file or directory

<br>

<pre>ls -alt</pre>

Chains `ls -a`,  `ls -l`, `ls -t` into one command. 
It lists the files/directories in long form in order of when they were last modified and lists dot/hidden files.

<br>

### MANIPULATION

**Copying**

<pre>cp {file from} {file to}</pre>

**Moving**

The below moves and renames a file; batman.txt is renamed to spiderman.txt

<pre>mv batman.txt spiderman.txt</pre>


**Removing**

`rm` → removes a file or an empty directory

`rm -r` → recursively removes

<br>

### REDIRECTION

`echo`

Standard input, standard output and standard error:

- standard input, abbreviated as `stdin`, is information inputted into the terminal through the keyboard or input device.

- standard output, abbreviated as `stdout`, is the information outputted after a process is run.

- standard error, abbreviated as `stderr`, is an error message outputted by a failed process.

<pre>$ echo "Hello" > hello.txt</pre>


Above the `“Hello”` is the stdin and the `>` redirects this input into `hello.txt`

`cat hello.txt` → Will output the contents of the hello.txt file which is Hello

*NOTE:  `>`  overwrites the data in the output source.*


<pre>cat glaciers.txt >> rivers.txt</pre>

`>>` → appends the input information to the output source.


`|` → The pipe takes the standard output of the command on the left and ‘pipes’ it as standard input to the command on the right.


<pre>cat lakes.txt | sort > sorted-lakes.txt</pre>


`sort`

This sorts the input in this case the information inside `lakes.txt`; this sorted list is then piped into a newly created file, `sorted-lakes.txt`


`uniq`

Stands for unique and filters out adjacent duplicates in a file.
A more effective way to remove duplicates is to sort, to allow adjacent copies to be removed.


`grep`

Stands for global regular expression print. It looks for files that match a pattern and returns a result. `grep` is case sensitive. Use `grep -i` makes the command case insensitive.

`grep -R`

Searches all files in a directory and outputs files and lines containing the results.

`grep -Rl`

Similar to above except it only outputs files containing results (no lines).

`sed`

Stands for stream editor. It accepts standard input and modifies it based on an expression before displaying as output data. This function is similar to ‘find and replace’.

<pre>$ sed 's/snow/rain/' forests.txt</pre>

The `s` stands for substitute and must be used when using sed. The command finds the pattern ‘snow’ in forest.txt and replaces this with ‘rain’.
This command will only replace the first instance of snow in the lines.

To capture all instances of a word we need to use `/g` which stands for global.

<pre>$ sed 's/snow/rain/g' forests.txt</pre>