---
layout: post
title: Learning command line
description: Learnings from "Learn Enough Command Line to Be Dangerous" tutorial 
---

This is a documentation I do to keep myself organized in my stydies. 

Here I am going to write only the things that were new to me, when I was going through the tutorial. 
Find full tutorial by following this [LINK](https://www.learnenough.com/command-line-tutorial/basics). 


<div class="table-wrapper">
					<table class="alt">
						<thead>
							<tr>
								<th>Tutorial</th>
								<th>Time to complete / hrs</th>
								<th>Price</th>
							</tr>
						</thead>
						<tbody>
							<tr>
								<td>Learn Enough Command Line to Be Dangerous</td>
								<td>3</td>
								<td>Free</td>
							</tr>
						</tbody>
					</table>
				</div>

It took me 3 hours total within 2 days to complete this tutorial: 
![time to complete](/assets/images/time-to-learn-command-line.png)

----------------
### Terminal keyboard shortcuts 
One of the common ways to edit the line is to use Control key (usually `Ctrl` or `⌃`). 

* `⌃ + A` => get to the begging of the line immidiately 
* `⌃ + E` => get to the end of the line immidiately 
* `⌃ + U` => clears the begging of the line and let's you start over immidiately
* for multi-line text use `⌥ + mouse pointer click` to navigate to the specific place in your text 
* `⌃ + L` => does the same thing as `clear` command 

### Manipulating files
Here's the list of the commands that I did not know about earlier: 
* `diff` => used for the comparison of files that are similar but not identical
  
  Here's an example: 
  ```
  $ diff sonnet_1.txt sonnet_1_lower_case.txt
  < That thereby beauty's Rose might never die,
  ---
  > That thereby beauty's rose might never die,
  ```
* `mv` command, which is short for 'move' is used to rename files as well. 
  
  The code below would rename the file `test` to `test_file.txtz`: 
  ```
    $ echo "test text" > test
    $ mv test test_file.txt
    $ ls
    test_file.txt
  ```
* use `-f` ('f' for 'force') to override the implicit `-i` option
* use `-h` option when listing files in a given directory to have "human-readable" view on the files. This will basically change size in bytes to _kilobytes_:

  ```
  RBM-DNAIDA-A01:commandLineTasks dnaida$ ls -hl
  total 256
  -rw-r--r--  1 dnaida  staff    93K May 29 21:37 sonnets.txt
  ```
  
### Inspecting files

I really liked the command `curl` which allows you to download content from any given URL. 

This way I was able to download the HTML content from my website homepage `https://www.dmytronaida.com`, save it to a file on my machine and open in browser window all from the terminal: 

```
RBM-DNAIDA-A01:commandLineTasks dnaida$ curl https://www.dmytronaida.com > site.html
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100  6416  100  6416    0     0  72548      0 --:--:-- --:--:-- --:--:-- 72909
RBM-DNAIDA-A01:commandLineTasks dnaida$ ls 
site.html		sonnet_1_complete.txt	sonnets.txt
RBM-DNAIDA-A01:commandLineTasks dnaida$ chrome site.html 
-bash: chrome: command not found
RBM-DNAIDA-A01:commandLineTasks dnaida$ open ./site.html 
RBM-DNAIDA-A01:commandLineTasks dnaida$ 
```

* `head` => shows the first 10 lines of the file 
* `tail` => shows the last 10 lines of the file 
* `wc` => word, line, and byte count for a given file 
  
  ```
  RBM-DNAIDA-A01:commandLineTasks dnaida$ wc sonnets.txt 
    2620   17670   95635 sonnets.txt
  ```
* `less` => allows backward movement  in the  file  as well as forward movement. 
  * when, scanning through a file using `less` command: 
    * `f` for 'forward' one page
    * `b` for 'back' one page
    * `/<string>` for searching matching keywords in file


### Working with directories

* `open` => open files and directories with the default program
* `cd -` => brings you back to the previous directory, whatever it was

