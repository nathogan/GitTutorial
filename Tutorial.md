Hello and welcome to my git tutorial.
I am Nat Hogan and this tutorial is
going to teach you how to use git via
the terminal.

Start by installing git on your device,
I am currently using git version 2.39.3
for Apple.

Start by making a git repository on your
desktop. Open the terminal and go to the 
desktop by typing ```cd Desktop``` into 
the commandline. Then type ```git init reponame```
where reponame is the name of the repo. 

Then enter the repo using ```cd reponame``` 
and create a python file using ```touch filename.py``` 
and open this py file using ```open filename.py```
and write some simple code, let us start with 
```print('hello world')```, then save the file
and add this file to the staging area with 
```git add filename.py```. What this does
is it saves your work to a special area
which can then be pushed into the main branch.
Push it now using the ```git commit filename.py```.

Then you will have to write a comment describing
what the commit is. Write something like "first
commit to main". To save using vim, the terminal
text editor, you have to press 'esc' ':wq'.

This should commit your first bit of code to
your repository. Committing is basically 
uploading your code to the repository so that
anyone with access to the repository can pull
it for themselves.

You can check the status of your added files
using ```git status``` and you can see the 
commits clearly using ```git show```.

Open your python file again, but remove the
print statement that you have and instead make
a loop. Write
```
for x in range(5):
    print('I can count to ' + str(x))
```
which should write 5 lines to the terminal when run.

We will make a new branch for this, so write 
```git branch A```, which will create a branch name A.
Then switch to that branch using ```git switch A```.

Then ```git add filename.py``` into the new branch.
Then ```git commit filename.py``` into this branch.

Now you have 2 branches which have 2 different files in them.
Now say that we want to combine them back, there would
be an issue because there are different lines
of code on line 1.

First returning to the
main branch with ```git switch main```. 
We can add more code to the original file by opening
filename.py in this branch (you will notice
that the original print statement is there)
and modifying the 2nd line of the file to 
```print('hello sun')```.
Then git add filename.py and git commit filename.py.

In order to combine these two files, while in 
the main branch type ```git merge A```.
It should say that automatic merge
failed, and that we must fix conflicts and commit the result.
Open filename.py. You should see some arrows
and the word HEAD, the first code, some equal signs, 
the second code, and some arrows followed by A.

```
<<<<<<< HEAD
print('hello world')
print('hello sun')
=======
for x in range(5):
    print('I can count to ' + str(x))
>>>>>>> A
```

If we want the order to be this way, delete the arrows,
branch names and equal signs, otherwise put the
code together however you want it. When you are done,
save the file and once again git add it. Then
git commit it. This combines the two branches,
and if you open the file now it will have both
of the codes and if you run it it will now print
hello world, hello sun, and I can count from 0 to 5.

If you have a remote repository, for example
if you cloned a repo from github or somewhere, 
then you would be able to then push your commits
using ```git push remotename main``` where remotename
is the name of your remote repo.
