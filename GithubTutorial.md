## Collaborative Coding

In this tutorial, we learn how to use Github for individual and group projects.

Github is a distributed version control and source code management tool. It allows developers to code in a collaboration. As a user in the Github you can make a copy of codes of someone else and separately work on it. The action of making a copy of a software is called **fork**. Once you have forked a repository, you own your forked copy. This means that you can edit the contents of your forked repository without impacting the parent repo.

Please go to the https://github.com/mirkazemi1984/HelloWorldProject
On the right hand side of the page you can find the fork button. ![logs_graph](https://github.com/Mirkazemi/CollaborativeCoding/blob/main/images/form.png)

Please click on it then you will have an independent copy of the **HelloWorldProject**.

When you create or fork a repository on GitHub, it exists as a remote repository. You can clone your repository to create a local copy on your computer and sync between the two locations. To clone the repository, first find the 'code' button and click on it:
![logs_graph](https://github.com/Mirkazemi/CollaborativeCoding/blob/main/images/code-button.png)

To clone the repository using HTTPS, under "Clone with HTTPS", click on below button to copy the HTTPS address of the repository.
![logs_graph](https://github.com/Mirkazemi/CollaborativeCoding/blob/main/images/https-url-clone-cli.png)

Now, as explained in Git Tutorial create a project folder and initiate Git:

```console
$ cd path/to/somewhere
```
Now we use the HTTPS address to clone the repository on the computer:

```console
$ git clone https://github.com/YOUR-GITHUB-USERNAME/HelloWorldProject.git
```
The code is cloned on your computer and you can work on it. Go into the project and inspect history of Git commits:
```console
$ cd HelloWorldProject
$ git log
```
```
commit 35d77fa770d78c76f321a3c36bfee3e746b4bf5c (HEAD -> main, origin/main, origin/HEAD)
Author: mirkazemi1984 <78924139+mirkazemi1984@users.noreply.github.com>
Date:   Fri Feb 12 06:31:04 2021 +0100

    initial commit: creating helloworld.py
```
The first commit is made by the author of the original repository that you forked.

As the first example, we want to make a change in the 'helloworld.py' file and **push** the changes into the remote fork repository. Please open 'helloworld.py' in a text editor and add a line for printing 'Hallo Welt" to the end of file. The content of the file will be below:

```
print(f'Hello World')
print(f'Hallo Welt')

```
Please save the file. Now we commit our change to the local Git repository:
```console
$ git add .
$ git commit -m 'adding german hello world to helloworld.py'
```

Now check the commit history:
```console
$ git log --pretty=oneline
```
You recent commit comes on the top of the commit from the author of the original repository:
```
32c01f10ca228650a3902bf77d96d7fc7fa73644 (HEAD -> main) adding german hello world to helloworld.py
35d77fa770d78c76f321a3c36bfee3e746b4bf5c (origin/main, origin/HEAD) initial commit: creating helloworld.py
```

### Pushing to a Remote Repository
The git **push** command is applied to upload local repository to a remote one.
```console
$ git push <remote> <name-of-branch>
```

We want to push the local repository to its remote origin. The Git recall the origin of your local repository. 
```console
$ git remote -v
```
```
origin	git@github.com:YOUR-GITHUB-USERNAME/HelloWorldProject.git (fetch)
origin	git@github.com:YOUR-GITHUB-USERNAME/HelloWorldProject.git (push)
```
The **fetch** origin is the repository you cloned (or simply you downloaded). The push origin is the targeted repository for uploading. You can also check that there is only 'main' branch is available for your forked reposity on Github. So we push the local reopsitory to the main branch of remote repository by:

```console
$ git push origin main
```

If you check the forked repository, you will find out that it is updated.

### Cloning a Remote Branch
In collaborative coding project, each member of a team develops part or parts of the project. Each part of project is actually develop on a branch of a repository. After a successful progress, you can merge your branch into main or other higher rank branches.

![logs_graph](https://github.com/Mirkazemi/CollaborativeCoding/blob/main/images/gitflow_1.png)

Source: https://lucamezzalira.com/2014/03/10/git-flow-vs-github-flow/

So assume that you are a team member of Hello World project and you are responsible for developing part of Hello World project that prints 'Hello World' in upper case. You create a new branch 'uppercase' on the forked repository, clone the branch, and edit the code. Then you push back the local repository on your computer to the 'uppercase' branch of Hello World project. Usually you decide with your colleagues if you want to merge the 'uppercase' branch into 'main' branch and have a new version of Hello World project with a new feature of printing in upper case.

We first create a new branch in Github repository and name it 'uppercase'. In the page of the forked repository click on 'main' and enter the name of the new branch like below figure and press Enter.

![logs_graph](https://github.com/Mirkazemi/CollaborativeCoding/blob/main/images/uppercase_branch.png)

Now again clone the repository:
```console
$ git clone https://github.com/YOUR-GITHUB-USERNAME/HelloWorldProject.git
```
If you review the commit history of the repository you figure out that you also have two branches of 'main' and ‘uppercase’.
```console
$ cd HelloWorldProject
$ git log
```
```
Author: YOUR_USERNAME <YOUR_EMAIL>
Date:   Fri Feb 12 08:07:12 2021 +0100

    adding german hello world to helloworld.py

commit 35d77fa770d78c76f321a3c36bfee3e746b4bf5c
Author: mirkazemi1984 <78924139+mirkazemi1984@users.noreply.github.com>
Date:   Fri Feb 12 06:31:04 2021 +0100

    initial commit: creating helloworld.py
```    
Now we swith to the uppercase branch, create a new file for printing 'Hello World' in upper case.

```console
$ git checkout uppercase
```
```
Branch 'uppercase' set up to track remote branch 'uppercase' from 'origin'.
Switched to a new branch 'uppercase'
```

We create a new file 'helloworld_uppercase.py' with the following content and save it:
```
print('HELLO WORLD')
print('HALLO WELT')
```

Now we need to commit changes into Git repository:

```console
$ git add .
$ git commit -m "adding helloworld_uppercase.py for printing upper case hello world"
```
Our local repository is ready to be pushed to the 'uppercase' branch of the remote repository:

```console
$ git push origin uppercase
```

Now the remote Github repository is updated by our local repository including 'helloworld_uppercase.py'. You can click on the 'compare and pull request' button to compare branches and request for merging them.



