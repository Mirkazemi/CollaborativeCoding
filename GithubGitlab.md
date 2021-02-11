## Collaborative Coding

In this tutorial, we learn how to make a copy of repository and develope it in a group.

Github is a distributed version control and source code management tool. They provide developers to share software and code in collaboration. As a user in Github your can make a copy of codes of someone else and separately work on it. The action of making a copy of a software is called **fork**. Once you have forked a repo, you own your forked copy. This means that you can edit the contents of your forked repository without impacting the parent repo.

Please go to the https://github.com/Mirkazemi/HelloWorldProject
On the right hand side of the page you can find the fork button. ![logs_graph](https://github.com/Mirkazemi/CollaborativeCoding/blob/main/images/form.png)

Please click on it then you will have an independent copy of the **HelloWorldProject**.

When you create or fork a repository on GitHub, it exists as a remote repository. You can clone your repository to create a local copy on your computer and sync between the two locations. To clone the repository, first find the 'code' button and click on it:
![logs_graph](https://github.com/Mirkazemi/CollaborativeCoding/blob/main/images/code-button.png)

To clone the repository using HTTPS, under "Clone with HTTPS", click on below button to copy the HTTPS address of repository.
![logs_graph](https://github.com/Mirkazemi/CollaborativeCoding/blob/main/images/https-url-clone-cli.png)

Now, as explained in Git Tutoral create a project folder and initiate Git:

```console
$ cd path/to/somewhere
$ mkdir myproject
$ cd myproject
$ git init
```
Now we use the HTTPS address to clone the repository on the computer:

```console
$ git clone https://github.com/YOUR-GITHUB-USERNAME/HelloWorldProject.git
```
The code is cloned on your computer and you can work on it. As the first example, we want to make a change in the 'helloworld.py' file. Please open 'HelloWorldProject/helloworld.py' in a text editor and add a line for printing 'Hallo Welt" to the end of file. The content of the file will be below:

```
print(f'Hello World')
print(f'Hallo Welt')
```
Please save the file. Now we commit our change to the local Git repository:
```console
$ git add *
$ git commit -m 'adding german hello world to helloworld.py'
```
