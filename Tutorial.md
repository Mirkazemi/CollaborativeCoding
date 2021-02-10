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
If you want to create a new project folder you first need to create it and then to go to it.
```console
$ cd path/to/somewhere
$ mkdir myproject
$ cd myproject
```
Now you are ready to initiat the a Git repository and keep it under cotrol version by typing:
```console
$ git init
```
