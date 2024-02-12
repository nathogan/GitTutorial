Hello, I am Nathaniel Hogan and I will be writing
this tutorial about how to use git.
This tutorial is using git version
2.39.3 (Apple Git-145)
First of all navigate to your desktop
and create a git repo by typing the following
commands:
```
cd Desktop
git init practice
```
Then enter this repo by typing 
```
cd practice
```
What we did there was create a repo using 
the init command named "practice"
Then create a python file (I named mine
file1.py) and open it and write the code
given below:
```
touch file1.py
open file1.py
```
```
print('hello world')
# this is what a comment looks like
for i in range(5): # loop
    print(str(i+1))
print('end')
```
Then add the file from the working tree
to the staging area, which means from where
you work on the code into the place where you
can prepare code to be added to the actual
repository.
Use the commands:
```
git add file1.py
```
To check the files that are being staged
you can:
```
git status
```
Then since this is all that we want to add to
the repo, we can commit the file using:
```
git commit file1.py -m "first commit"
```
If you want to add more things to
the file, open the file again and add the
line
```
print('adding more things to say')
```
Then add and commit the file again.

Now branch the repository to see how
working on separate branches at once works.
To do this use the commands:
```
git branch A
git switch A
```
Modify the python file in this branch by 
opening the file now and adding another line
```
print('this is branch A')
```
Then commit this file into the new branch A
and switch to main to add more there:
```
git commit file1.py -m "branching the project"
git switch main
```
Once in main, modify the python file 
one last time, adding 
```
print('developing main a bit more')
```
Then add and commit again, which means that 
there are two branches that both added
code in line 7, which will cause a small
issue later.

Then we are going to merge these two branches,
which is something that happens frequently
when working on projects, which will cause
a merge conflict when trying to make one file
that contains both of the terminal commits
in each branch. Since you are in the main branch,
you can just enter the line 
```
git merge A
```
and git will merge the current and the given
branches. The terminal might tell you that
there was an issue with the merge, so open
the file again, you should see:
```
print('hello world')
# this is what a comment looks like
for i in range(5): # loop
    print(str(i+1))
print('end')
print('adding more things to say')
<<<<<<< HEAD
print('developing main a bit more')
=======
print('this is in branch A')
>>>>>>> A
```
Let's say that we want the line
'this is in branch A' to come first, then
delete the lines with <, =, >, and swap the 
order of the print statements. This should
ook like:
```
print('hello world')
# this is what a comment looks like
for i in range(5): # loop
    print(str(i+1))
print('end')
print('adding more things to say')
print('this is in branch A')
print('developing main a bit more')
```
This means that it will now print in the
order that we want it, so by entering the
commands below you are able to finish the 
process of merging:
```
git add file1.py
git merge --continue
```
It will open vim to edit the comment, so you
can type a, then when it says INSERT at the
bottom, hit the esc key and type ':wq'.
This should initialize the message to
"Merge branch 'A'". This means that you have 
successfully completed a merge.

If you have a remote repository, for example
if you cloned a repo from github or somewhere, 
then you would be able to then push your commits
using ```git push remotename main``` where remotename
is the name of your remote repo (usually origin).

If you wanted to clone a repo (for example this repo),
head back to the desktop using ```cd ..``` to move
one level up and type ```git clone https://github.com/nathogan/GitTutorial```,
which will make a new repo, however this time with a remote
repository as well. This means that if you make a change
to the markdown file that this tutorial is comprised
of, you can add, commit, and finally push your changes.
This is in fact how I am editing this document, every time I
need to add something, like some of the code, I push the code 
to the online github repo, which is how you are able to see
the most up-to-date version.