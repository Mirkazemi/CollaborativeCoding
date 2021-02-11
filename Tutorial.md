## Collaborative Coding

In this tutorial we review the the basic Git commands for working with repositories.

Git is a command line based tool although it is partially supported by many graphical user interfaces (e.g. some of code editors).  Thus is this tutorial we only focus uisng Git in command line.

We also soppuse that you have already isntalled git on your computer. For installation, you may follow these [instructions](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) for Linux, Windows, macOS operating systems.

In order to check if the Git has already been installed, open a terminal and check the version of it:
```console
$ git --version
```

### Initial Configuration
All the commits in Git are stored base on the identity of the user thus the first step after installation of Git is to set name and email of the user.
```console
$ git config --global user.name "John Smith"
$ git config --global user.email "John.Smith@mail.com"
```
The ```--global``` means that name and email of the user are set for all of your repositores.  If you already set the configuration you can see the name and email of user by following commands:

```console
$ git config user.name
$ git config user.email
```

### Initiating a Git Repository 
Generally there are two methods for obtaining a repository. The first one is to convert a dictory on your computer into a repository and the second one is to clone a remote repository. The second method will be explained in the sections related to using Github and Gitlab.

If you have project folder that is not under version control then you first need to go to that directory.
```console
$ cd path/to/myproject
```
In this toturial, we create a new project folder. 
```console
$ cd path/to/somewhere
$ mkdir myproject
$ cd myproject
```
Now you are ready to initiat the a Git repositoryby by typing:
```console
$ git init
```
### Tracking the files
Before going to the next step, we need to know the meaning of **tracked** and **untracked** files in a repository. The tracked files are those one for whom you have snapshot from the last changes. The untracked one are the files that have been edited but the last changes have not tracked by the Git. So if we create a new file (not an empty file) it is an untracked file until we ask the repository to recond a snapshot of the file. Let's try it. We create a file, for example a Hello World python script and check how Git recognizes this file.

Creating the file:
```console
$ echo "print(f'Hello World')" > helloworld.py
```
To check the status of the files in repository we use ```status``` option.
```console
$ git status
```
The output is like:
```
On branch master

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)

	helloworld.py

nothing added to commit but untracked files present (use "git add" to track)
```
It shows that ```helloworld.py``` is an untracked file.  We use the ```add``` and ```commit``` functions to add and commit a changes to git.
The ```add``` recognizes the changes in targeted file and places it in stagging area. The ```commit``` takes available changes in stagging are and makes a snapshot of the current state repository and assigns it a hash. A hash is the identifier of a snapshot.

First we try the add function and then we check the status of the repository.
```console
$ git add helloworld.py
```
```console
$ git status
```
The output is:
```
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
  
	new file:   helloworld.py
```
The state of repository tells us that ```helloworld.py``` is ready to be committed. So let's commit it and add a message using ```-m``` option. The message should be a short description of the changes being committed.
```console
$ git commit -m "adding helloworld.py to the code"
```
### Commit history
After several commits you can look back to the history of the commits. Until now we only had a single commits let do two other ones and then review the history of commits. The first commit was after we writing ```helloworld.py```. For the second commit, we write the the german and french version of hello world code. For the third one we edit all three files by adding associated langauge to the output of the print function.

Second commit:
```console
$ echo "print(f'Hallo Welt')" > hallowelt.py
$ echo "print(f'Bonjour le monde')" > bonjourlemonde.py
$ git add *
$ git commit -m "Adding German and French versions of Hello world."
```
In above, we wrote ```git add *``` or we could wrote ```git add *.py``` add all matching files. It is a faster way instead of typing the name of each file individualy.

Second commit:
```console
$ echo "print(f'English: Hello World')" > helloworld.py
$ echo "print(f'German: Hallo Welt')" > hallowelt.py
$ echo "print(f'French: Bonjour le monde')" > bonjourlemonde.py
$ git commit -a -m 'Print the langauge in the output'
```
In the last commit, we skiped the stagging area. The add function allows us to select among modifications and make a commit. But in the most of the cases a developer wants to make a commit on all the modified files so the staging area (using ```add``` function) is redundent. Using ```-a``` we skip the staging area and make a commit on all the changes in the repository. 

Now we have three commits (three snapshots from the repository). Let's have a look to them by typing:

```console
$ git log
```
The output is like below and shows the author information, time and date of commits, message of commits and a unique for each commit. 
```console
Author: Mirkazemi <mohammad.mirkazemi@gmail.com>
Date:   Thu Feb 11 05:08:56 2021 +0100

    Print the langauge in the output

commit d5817901ca4877ae50a4334e0a7df0b92cbb62b2
Author: Mirkazemi <mohammad.mirkazemi@gmail.com>
Date:   Thu Feb 11 05:08:33 2021 +0100

    Adding German and French versions of Hello world.

commit 5d6f059b2cea94c0c4369c20c1883e03f5e6f314
Author: Mirkazemi <mohammad.mirkazemi@gmail.com>
Date:   Wed Feb 10 21:37:11 2021 +0100

    adding helloworld.py to the code
```
There are many options to change the format of the output of ```git log``` but a simplest one is:
```console
$ git log --pretty=oneline
```
that shows the hash and message of each commit in one line:
```
21df35152a69052219edecbcf65b9df9406e807d Print the langauge in the output
d5817901ca4877ae50a4334e0a7df0b92cbb62b2 Adding German and French versions of Hello world.
5d6f059b2cea94c0c4369c20c1883e03f5e6f314 adding helloworld.py to the code
```
Now we can have overview on all version of our code. In the first version, we have a helloworld code. In the second version, the french and german versions of the hello world were added and in the last one the output of all codes are changed. 

### Moving between different version of a code
Whenever you make a commit Git takes a snapshot of your repository so you can ask Git to recall the previous version of your code. For example, at momment your code can print "langauge: Hello World" in three langauges of english, german and french. Perhaps your colleague asks you for the previous version of the code that only prints "Hello World" in three langauges. You do not need to edit your code to that version. Git memorizes every commits and you can ask Git to recall that version of your code using related hash:

```console
git checkout d5817901ca4877ae50a4334e0a7df0b92cbb62b2
```
Now the all the files are changed to the previous version
