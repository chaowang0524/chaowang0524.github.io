---
layout: default
---

## Introduction to Course Command Line Tools for Linguists

[Command Line Tools for Linguists](https://studies.helsinki.fi/courses/course-unit/hy-CU-134651633-2021-08-01) is a great course for those students who are new to the UNIX environment. The course is very practical, helping you learn the essentials of the command line over seven weeks.

In this course, two brilliant and helpful teachers will support students to go through a variety of topics in command line tools, starting with the fundamentals of UNIX commands and customizing shell settings. Students will become proficient in working with remote servers, a crucial skill for ambitious projects. Then there are UNIX-based text processing techniques, regular expressions, and environment variables. At last, students get to know how to adopt Git into their work flow.

This course is strongly focusing on hands-on, real-world learning. Most tasks students tackle in the assignments are designed to mimic the tasks used in the project, ensuring students develop skills that are immediately applicable.

Below is a brief introduction to each week's content with some sample code (some are my personal code just for reference):



### Week 1

#### Introduction to Command Line Environment

In the first class, the course started from basic file processing commands in UNIX like `cd`, `mv`,`touch` and `wget` to some basic text processing commands in text editors like `nano` or `emacs` in UNIX. I learned some of the basic commands before but never get to chance to use them. To me, the first week is a great way to polish my rusted skills.  Some commands used in the Week 1 are:

````
cat -n some_file.txt # show content of `some_file.txt` with line numbers

mv file1 file2 # rename `file1` as `file2`

cp file1 file2 # copy `file1` as `file2`

man COMMAND # check the <command> manual
````



A Linux Cheat Sheet offered in the course material:



![alt](assets/images/LCS.png)



### Week 2

#### Navigating a UNIX System

This week covers a bit more on the navigating the file system on UNIX, like using `..`and `~` to quickly change directories, `in` to create links, `chmod`  to change permissions and `kill` to terminate processes. Also, we learned how to do SSH connection, which to me is very useful and important for my work flow. Some commands used in this week are: 

```
chmod +x filename # make the file executable

cat life_of_bee.txt | sort | less # sort the file in line alphabetically from A-Z

kill <PID> # terminate the process using its PID

ssh username@RemoteServerName # Connect to the remote server (can be edited in ~/.ssh/config)
```



Below is a list of `chmod` common permissons for reference:



| Chmod numbers | Permission | Description                  |
| ------------- | ---------- | ---------------------------- |
| `400`         | r--------  | Readable by owner only       |
| `500`         | r-x------  | Avoid Changing               |
| `600`         | rw-------  | Changeable by user           |
| `644`         | rw-r--r--  | Read and change by user      |
| `660`         | rw-rw----  | Changeable by user and group |
| `700`         | rwx------  | Only user has full access    |
| `755`         | rwxr-xr-x  | Only changeable by user      |
| `775`         | rwxrwxr-x  | Sharing mode for a group     |
| `777`         | rwxrwxrwx  | Everybody can do everything  |



### Week 3

#### Basic Corpus Processing

This week the course started to dive into the world of text processing. The content began with knowledge of encodings like  "ASCII" and "UTF-8". Then it covers some text processing commands like `tr` and some useful tools like `|` and `>`. I also learned how to use `grep` and `egrep` or `grep -e` , which leads us to the regular expressions.  Some of the commands used in this week are:

```
dos2unix book.txt # convert DOS file to UNIX file (remove the carriage return)

cat book.txt  2> errors.txt| tr '\n' ' ' > output.txt # Take all content in book.txt, remove all the new line characters then send it to `output.txt`. Any generated error message will be sent to `errors.txt`.

cat life_of_bee.txt | grep -E "\bpre(\w|[-])*ed\b" | wc -l # Find all the matched words using regular expression from the file life_of_bee.txt then count how many of them. The matched pattern is "a word starts with 'pre' then followed by (any or no) no-blank characters or any `-` then end with 'ed'".
```



Below is a list of common encodings for European languages:



- [Latin-1 (ISO-8859-1: Western European)](http://www.madore.org/~david/computers/unicode/cstab.html#Latin-1)
- [Latin-2 (ISO-8859-2: Central European)](http://www.madore.org/~david/computers/unicode/cstab.html#Latin-2)
- [Latin-3 (ISO-8859-3: South European and Esperanto)](http://www.madore.org/~david/computers/unicode/cstab.html#Latin-3)
- [Latin-4 (ISO-8859-4: Baltic, old)](http://www.madore.org/~david/computers/unicode/cstab.html#Latin-4)
- [Cyrillic (ISO-8859-5)](http://www.madore.org/~david/computers/unicode/cstab.html#Cyrillic)
- [Arabic (ISO-8859-6)](http://www.madore.org/~david/computers/unicode/cstab.html#Arabic)
- [Greek (ISO-8859-7)](http://www.madore.org/~david/computers/unicode/cstab.html#Greek)
- [Hebrew (ISO-8859-8)](http://www.madore.org/~david/computers/unicode/cstab.html#Hebrew)
- [Latin-5 (ISO-8859-9: Turkish)](http://www.madore.org/~david/computers/unicode/cstab.html#Latin-5)
- [Latin-6 (ISO-8859-10: Nordic)](http://www.madore.org/~david/computers/unicode/cstab.html#Latin-6)
- [Thai (ISO-8859-11, unofficial)](http://www.madore.org/~david/computers/unicode/cstab.html#Thai)
- [Latin-7 (ISO-8859-13: Baltic, new)](http://www.madore.org/~david/computers/unicode/cstab.html#Latin-7)
- [Latin-8 (ISO-8859-14: Celtic)](http://www.madore.org/~david/computers/unicode/cstab.html#Latin-8)
- [Latin-9 (ISO-8859-15: Revised Western European)](http://www.madore.org/~david/computers/unicode/cstab.html#Latin-9)
- [DEC Multilingual Character Set](http://www.madore.org/~david/computers/unicode/cstab.html#DEC-MCS)



### Week 4

#### Advanced Corpus Processing

This week focuses on the some of the advanced techniques in text processing. I learned how to use `sed` command to process like pattern substitution `sed s/A/B/g` and deletion  `sed /A/d` . It also helped me review and practice the techniques from last week especially for `egrep` and regular expression. Some of the commands used in the weeks are:

```
cat life_of_bee.txt | tr -s '\n\t\r ' '\n' | tr -dc "A-Za-z0-9'\n" | tr 'A-Z' 'a-z' | sort | uniq -c | sort -nr > life_of_bee.ic.freq # Take all the content from life_of_bee.txt, remove all of the 'tab characters' and 'carriage return' then squeeze the blank lines. Then, remove all the characters that are not letters nor numbers nor new line characters. Lower all characters, sort the content in alphabetical order, group up the duplicated lines, sort the lines according to the number in a descending order then send the final result to 'life_of_bee.ic.freq'

cat life_of_bee.sent | grep -E "\bcomb\b"  | grep "\bhoney\b"| wc -l # Take all content from life_of_bee.sent file, find all the matched lines contain the word 'comb', then from which the next `grep` finds all the matched lines that contain the word 'honey'. Then count the appearances. 

cat life_of_bee.sent | sed -E 's/.* //' | tr -cd "A-Za-z0-9\n'" | sort | uniq -c | sort -nr | head -1 # Take all content from life_of_bee.sent file, remove all the characters in each line expect the last word, from which remove all the characters that are not letters nor numbers nor new line characters, sort alphabetically in a ascending order, group up the result then sort in a descending order according to the number. Take the first value (the highest).
```



Below shows some of the basic patterns of regular expression:



| **Syntax**       | **Description**                                              | **Example pattern** | **Example matches**         | **Example non-matches**    |
| ---------------- | ------------------------------------------------------------ | ------------------- | --------------------------- | -------------------------- |
| `^`              | match start of line                                          | `^r`                | rabbitraccoon               | parrotferret               |
| `$`              | match end of line                                            | `t$`                | rabbitfoot                  | trapstar                   |
| `\A`             | match start of line                                          | `\Ar`               | rabbitraccoon               | parrotferret               |
| `\Z`             | match end of line                                            | `t\Z`               | rabbitfoot                  | trapstar                   |
| `\b`             | match characters at the start or end of a word               | `\bfox\b`           | the red fox ranthe fox ate  | foxtrotfoxskin scarf       |
| `\B`             | match characters in the middle of other non-space characters | `\Bee\B`            | treesbeef                   | beetree                    |
| `.`              | Anything except for a linebreak                              | `c.e`               | cleancheap                  | acertcent                  |
| `\d`             | match a digit                                                | `\d`                | 6060-8422b\|^2b             | two**___                   |
| `\D`             | Match a non-digit                                            | `\D`                | The 5 cats ate 12 Angry men | 5210032                    |
| `\w`             | Match word characters                                        | `\wee\w`            | treesbee4                   | The beeeels eat meat       |
| `\W`             | Match non-word characters                                    | `\Wbat\W`           | At batSwing the bat fast    | wombatbat53                |
| `\s`             | Match whitespace                                             | `\sfox\s`           | the fox atehis fox ran      | it’s the fox.foxfur        |
| `\S`             | Match non-whitespace                                         | `\See\S`            | treesbeef                   | the bee stungThe tall tree |
| `\metacharacter` | Escape a metacharacter to match on the metacharacter         | `\.``\^`            | The cat ate.2^3             | the cat ate23              |



### Week 5

#### Scripting and Configuration Files

First the material talks about customize the `.bashrc` file which I think is very useful and making my work flow more efficient and smooth. Then I learned how to write script in bash and this is very new to me and I realized how convenient to use programs in bash as oftentimes I will have to use Git or SSH that are also work in bash. Below is a program I wrote for myself and please read the code comment for reference:



```
#! /bin/bash

# Take a script file as an argument 
# Add an execute permission to the script file
# Run the .sh script file

apar() {
    # Check if at least one argument (script file) is provided
    if [ $# -lt 1 ]; then
        echo "Usage: apar <script_file>"
        echo "Example: apar myscript.sh"
        return 1
    fi

    script_file="$1"

    # Check if the script file exists
    if [ ! -f "$script_file" ]; then
        echo "Error: Script file '$script_file' does not exist."
        echo "Example: apar myscript.sh"
        return 1
    fi

    # Add execute permission to the script file
    chmod +x "$script_file"

    # Run the script
    "./$script_file"
}
```



Some of the useful aliases that I'm currently using:



```
# Aliases

# Show all files under the directory
alias la="ls -a"

# Fast config
alias cb="nano ~/.bashrc"

# Fast cd back
alias ..="cd .."

# Fast cd to Commandline course folder
alias cmd="cd ~/Desktop/Year\ 1/Command-Line\ Tools\ for\ Linguists/KIK-LG221/cmdline_course/

# Run 'bundle exec jekyll serve'
alias jrun="bundle exec jekyll serve & sleep 2 && open http://127.0.0.1:4000"
```



### Week 6

#### Installing and Running Programs

This week's content is very pratical as it talks about Python packages and virtual environment. I used to get into trouble with Python versions and packages so I found this weeks content particularly helpful. 

To create a Python venv:

```
python -m venv <name>
```

To activate the Python venv:

```
source <name>/bin/activate
```

Now I'm able to change Python's path in the environment variables or to use alias in `.bashrc` to change the default `pip` command like `alias pip="pip python3.12 -m"` to avoid any errors (I just upgraded to Python 3.12).

Then we learned about `make` command which is a program for batch jobs with syntax like:

```
target: file1 file2 ...
      some_command # Target is the output file, `file1` and `file2` are the arguements needed by `some_command`. `some_command` is the program to be executed on `file1` and `file2`.
```

If you are a language techonoly student or enthusiast, you are most likely using Pytorch. Below is the command I use to install PyTorch in my local environment:

![alt](/assets/images/pytorch.png)

and in the virtual environment:

![alt](/assets/images/venv.png)



### Week 7

#### Version Control

At last week, we learned about Git and Github. I used Github before so to me this week is a review what I learned before. Git is very important in people's work flow especially one working with Github and it is considered as one of the must-have skills on the market. So this week's content is very practical and critical. 

When you run Git on your machine for the first time, you will have to set your username at email address:

```
git config --global user.name "<Your username for Git>"

git config --global user.email "<Your email address>"
```

Some of the useful commands in Git:

```
git clone ...... # download the repo from Github
git status # check the current status of this repository (and check if this is one indeed)
git add <changed file name or the file you want to commit> # Add the change for committing
git commit -m "commit message" # commit the change
git branch <name> # create a new branch for the repo
git checkout <name> # Switch to an existing git branch
git push origin <branch name> # push the commit to the branch
git merge <branch name> # Merge the branch <branch name> into current branch
```



[< Go back](/)

