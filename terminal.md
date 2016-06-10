# Terminal

Setting up a web server with terminal (necessary eg when you work with d3 and load external CSVs):
- navigate to folder
- python -m SimpleHTTPServer 8888 &.


<br>
### Terminal expressions

x and y are files like mountains.txt<br>
dir = directory

| input | explanation |
| --- | --- |
| `cd` | move to dir |
| `cd ..` | move up |
| `cd ../..` | move upper |
| `pwd` | print working dir |
| `mkdir` | create dir |
| `touch`| create file |
| `open` | open file |
| `rm` | remove = delete file |
| `rm -r` | remove = delete dir and all child dirs |
| `rmdir` | remove = delete dir and all child dirs |
| `rm -r tmp` | remove stuff with the name "tmp" |
| `ls` | list all files of the current dir |
| `ls -t` | list last files first |
| `ls -a` | list hidde files too |
| `ls -l` | list long form |
| `less` | shows only a few rows, lets you scroll through it |
| `cp` | copy |
| `cp * ..` | copy everything one dir up |
| `cp x y ..` | copy x and y one dir up |
| `cp x y` | copy the content of x in y and delete the content of y |
| `mv` | move |
| `mv x ..` | move x one dir up |
| `mv x y` | rename x to y |
| `cat` | show content of the file |
| `echo "..." > x.txt` | write "..." into x.txt|
| `cat x > y` | copy the content of x in y and delete the content of 2 |
| `cat x >> y` | adds the content of x to the content of y |
| `sort` | sorts the content of a file |
| `uniq` | shows the unique entries of a file |
| `sorts x/uniq` | sorts the unique entries of x |
| `sorts x/uniq > y` | sorts the unique entries of x and puts them into y|
| `grep` | global regular expression print |
| `grep yeah x` | searches and show alle lines with “yeah” in x  |
| `grep -l yeah x` | searches and show alle lines with “yeah” in x, not case sensitive |
| `grep -R yeah /home/…` | searches for “yeah” in a whole dir |
| `curl -O https://bootstrap.pypa.io/get-pip.py`  | download URL file |
| `___ !! --> eg sudo !!` | run same command with prefix |
| `pbpaste` | paste stuff in terminal |
| `pbpaste > lisa.txt` | paste stuff in new file |
| `echo "hi dan" > lisa.txt` | type "hi dan again" in lisa.txt |
| `echo "hi dan again" >> lisa.tx` | type "hi dan again" in lisa.txt, but ADD it to the stuff that's there already |
| `man pbcopy` | manual of pbcopy; press "q" to get out of that |
| `cat lisa.txt [pipe symbol] pbcopy` | the pipe means: take the output from the left side and take it as an input for the right side of the pipe. eg: take content of lisa.txt and copy it |
| `git clone URL` | clones it |
| `then cat readme` | open readme in terminal, follow instructions from there)
| `git log` | get history of commit messags |
| `vi intro.html` | editor IN the terminal whaaaaaaaat |
| `git diff intro.html` | see changes in file |
| `git checkout` | delete all changes since the last commit |
| `cat lisa.txt` | grep data |
| `cat lisa.txt` | grep data > wow.txt` | |



## wildcards


| expression | explanation |
| --- | --- |
| `*.txt` | all text files |
| `*` | all files |
| `m*` | all files starting with "m" |
