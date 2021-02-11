## Collaborative Coding

In this tutorial we review the basic Git commands for working with repositories.

Git is a command line based tool although it is partially supported by many graphical user interfaces (e.g. some of code editors).  Thus is this tutorial we only focus using Git in the command line.

We also suppose that you have already installed git on your computer. For installation, you may follow these [instructions](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) for Linux, Windows, macOS operating systems.

In order to check if the Git has already been installed, open a terminal and check the version of it:
```console
$ git --version
```

### Initial Configuration
All the commits in Git are stored based on the identity of the user thus the first step after installation of Git is to set name and email of the user.
```console
$ git config --global user.name "John Smith"
$ git config --global user.email "John.Smith@mail.com"
```
The ```--global``` means that name and email of the user are set for all of your repositories.  If you already set the configuration you can see the name and email of user by following commands:

```console
$ git config user.name
$ git config user.email
```

### Initiating a Git Repository 
Generally there are two methods for obtaining a repository. The first one is to convert a directory on your computer to a repository and the second one is to clone a remote repository. The second method will be explained in the sections related to using Github and Gitlab.

If you have a project folder that is not under version control then you first need to go to that directory.
```console
$ cd path/to/myproject
```
In this tutorial, we create a new project folder. 
```console
$ cd path/to/somewhere
$ mkdir myproject
$ cd myproject
```
Now you are ready to initiate the a Git repository by typing:
```console
$ git init
```
### Tracking the files
Before going to the next step, we need to know the meaning of **tracked** and **untracked** files in a repository. The tracked files are those one for which you have a snapshot from the last changes. The untracked one are the files that have been edited but the last changes have not been tracked by Git. So if we create a new file (not an empty file) it is an untracked file until we ask the repository to record a snapshot of the file. Let's try it. We create a file, for example a Hello World python script and check how Git recognizes this file.

Creating the file:
```console
$ echo "print(f'Hello World')" > helloworld.py
```
To check the status of the files in the repository we use the ```status``` option.
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
It shows that ```helloworld.py``` is an untracked file.  We use the ```add``` and ```commit``` functions to add and commit changes to git.
The ```add``` recognizes the changes in the targeted file and places it in the staging area. The ```commit``` takes available changes in staging area and makes a snapshot of the current state repository and assigns it a hash. A hash is the identifier of a snapshot.

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
The state of the repository tells us that ```helloworld.py``` is ready to be committed. So let's commit it and add a message using the ```-m``` option. The message should be a short description of the changes being committed.
```console
$ git commit -m "adding helloworld.py to the code"
```
### Commit history
After several commits you can look back to the history of the commits. Until now we only had a single commit, let’s make two other ones and then review the history of commits. The first commit was after we wrote ```helloworld.py```. For the second commit, we write the german and french version of hello world code. For the third one we edit all three files by adding associated language to the output of the print function.

Second commit:
```console
$ echo "print(f'Hallo Welt')" > hallowelt.py
$ echo "print(f'Bonjour le monde')" > bonjourlemonde.py
$ git add *
$ git commit -m "Adding German and French versions of Hello world."
```
In above, we wrote ```git add *``` or we could wrote ```git add *.py``` add all matching files. It is a faster way instead of typing the name of each file individually.

Third commit:
```console
$ echo "print(f'English: Hello World')" > helloworld.py
$ echo "print(f'German: Hallo Welt')" > hallowelt.py
$ echo "print(f'French: Bonjour le monde')" > bonjourlemonde.py
$ git add *
$ git commit -m 'Print the language in the output'
```

Now we have three commits (three snapshots from the repository). Let's have a look to them by typing:

```console
$ git log
```
The output is like below and shows the author information, time and date of commits, message of commits and a unique for each commit. 
```
Author: Mirkazemi <mohammad.mirkazemi@gmail.com>
Date:   Thu Feb 11 05:08:56 2021 +0100

    Print the language in the output

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
Now we can have an overview on all versions of our code. In the first version, we have a hello world code. In the second version, the french and german versions of the hello world were added and in the last one the output of all codes are changed. 

### Moving between different version of a code
Whenever you make a commit Git takes a snapshot of your repository so you can ask Git to recall the previous version of your code. For example, at the moment your code can print "language: Hello World" in three languages of english, german and french. Perhaps your colleague asks you for the previous version of the code that only prints "Hello World" in three languages. You do not need to edit your code to that version. Git memorizes every commits and you can ask Git to recall that version of your code using related hash:

```console
$ git checkout d5817901ca4877ae50a4334e0a7df0b92cbb62b2
```
Now all the files are changed to the previous version. Let's check it and see the content of the files:
```console
$ cat *.py
```

The files contents are:
```
print(f'French: Bonjour le monde')
print(f'German: Hallo Welt')
print(f'English: Hello World')
```

### Git Branching
Branching is a powerful tools for developing a software on different paths. For example, you have software tool that works propelry but you are asked to add a feature into it (e.g. adding a new data vidualization feature to present your results). You do not need to make changes in your last version on master branch. You can create a new branch for developing data visulaization and merge it later to the master branch.

Lets go back to our super simple example. Assume that we want to have a english hello world programm that print the world in upper case. Thus we create a new branch based on the second commit and  
![alt text](https://github.com/Mirkazemi/CollaborativeCoding/blob/main/images/git-branches.png)



