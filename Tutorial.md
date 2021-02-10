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

### Git Repository 
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
Before going to the next step, we need to know the meaning of **tracked** and **untracked** files in a repository. The tracked files are those one for whom you have snapshot from the last changes. The untracked one are the files that have been edited but the last changes have not tracked by the Git. So if we create a new file (not an empty file) it is an untracked file until we ask the repository to recond a snapshot of the file. Let's try it. We create a file, for example a Hello World python script and check how Git recognizes this file.

Creating the file:
```console
$ echo "print(f'Hello World!')" > helloworld.py
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




