## Collaborative Coding

In this tutorial we review the the basic Git commands for working with repositories.

Git is a command line based tool although it is partially supported by many graphical user interfaces (e.g. some of code editors).  Thus is this tutorial we only focus uisng Git in command line.

We also soppuse that you have already isntalled git on your computer. For installation, you may follow these [instructions](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) for Linux, Windows, macOS operating systems.

### Initial Configuration
All the commits in Git are stored base on the identity of the user thus the first step after instalation of Git is to setup the configuration of Git by name and email of the user.
```console
$ git config --global user.name "John Smith"
$ git config --global user.email "John.Smith@mail.com"
```
The ```--global``` means that name and email of the user are set for all of your repositores.  If you already set the configuration you can see the name and email of user by following commands:

```console
$ git config user.name
$ git config user.email
```


