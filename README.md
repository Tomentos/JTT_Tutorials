# Welcome to this short tutorial on Git
![Git_Logo](./img/logo.png "Git Logo")

## What is Git
Git is a version control program made by Linux Torvalds (he’s also known for creating Linux). It’s main features are to easily track changes, features, versions and updates. There is much more that git can do, but I will keep this tutorial to the basics to not confuse or scare anyone off.

Git is supported by most code editors. The ones that don’t natively support it most likely have an add-on to add support. Because of that, the interface for git can be different for every single editor that is being used. In this tutorial I will focus on commandline inputs and the Visual Studio Code interface for Git.

## Where to get Git
Git can be downloaded directly for [the official website](https://git-scm.com/).

There are options for different installers, operating systems and even portable versions depending on what is best for your system and your preferences!

One important step that you should do before starting to use git is settings your name and email address. Since git is supposed to track who did what to the code, you need to provide some details on who you are. Note that you don't need to provide *real* data if you are not comfortable providing it. You can set the needed data using the following commands:
```
git config --global user.name "Your Name"
git config --global user.email "your.email@address.com"
```

## How to set up Git
The first step is to install the file you just downloaded. If you are using the portable version, make sure that the extraction foler is in the `$PATH`.

Git work with repositories. Repositories are basically just projects, that’s why for simplifications sake, I will use the two term interchangably in this documentation.

You declare the root folder (or main folder) of your project to git, and git will do the rest. You do that by making sure you are in the root folder of your project and then type the following command into your console: `git init`

This will give us the following output:
```bash
hint: Using 'master' as the name for the initial branch. This default branch name
hint: is subject to change. To configure the initial branch name to use in all
hint: of your new repositories, which will suppress this warning, call:
hint: 
hint:   git config --global init.defaultBranch <name>
hint: 
hint: Names commonly chosen instead of 'master' are 'main', 'trunk' and
hint: 'development'. The just-created branch can be renamed via this command:
hint: 
hint:   git branch -m <name>
Initialized empty Git repository in /***************/JTT/GitBasics/.git/
```

In VSCode, you can simply navigate to the Git Source Control on righthand panel and click `Initialize Repository`.

![img1](./img/img1.png "Documentation Image #1")

You may not see anything change in your project. This is because the files are hidden by default. Git created a new folder called `.git` in which all changes are saved.

***DO NOT EDIT ANYTHING IN THIS FOLDER MANUALLY***

Git should be the only thing to access this folder directly. Any manual change can completely break your entire repository.
![img2](./img/img2.png "Documentation Image #2")

## How to use git

Now you can start to code. And as you go on, you will notice certain cues in your editor. In this example case, I have files that are marked green with a letter `U` and a notification saying `4` on the Git Source Control panel.

In this scenario this means the following; The files marked with a green `U` are the files that have been newly created. The `4` on the Git Source Control means that Git has detected `4` new changes in this project.

![img3](./img/img3.png "Documentation Image #3")

In this example there is only the green `U`, but there are some more indicators of changed files. I will list them all here real quick:

- Green U - Newly created
- Orange M - Modified
- Red D - Deleted
- Greyed out - Ignored

Now let's save our changes first before we dive deeper into git.

You have different options for what you can do. You can revert the file into it's state from the last commit. In this case, that would be an empty file because we didn't commit anything yet.

You can open the file. In larger projects with many files, it makes sense to not always have all of them open. So this button just opens the document at the exact place where a change has been made.

You can stage the changes. Staging means that you declare a change as "ready to commit". That means if you press the bug `Commit` button at the top of the Git Source Control, the stashed changes will be commited.

All of those options are not only available on a file level. You can go to the changed places with the `Open File` button and stash or revert every single line idividually. This is used when you have two individual changes in a file and want to mark just one of them as ready to commit while still working on the other.

You can also just mark every single change as ready to commit at once. This is a feature that is used not so often. In larger projects it only happens rarely that *everything* just so happens to be ready to commit at once. So this is only used in small projects where this might very well happen, like this one so let's do that.

After the changes have been marked, you just need to enter a commit message. This message should shortly explain what exactly you did to the code here. Note that you *cannot* commit changes *without* a commit message.

![img4](./img/img4.png "Documentation Image #4")

**Congratulations! you just made your first commit in git!**

### Committing in the commandline

The commandline equivilents for staging and commiting and reverting are as follows:

Staging
```
git add "file"
```

Commiting
```
git commit -m "Commit Message"
```

Reverting
```
git revert "file"
```

## Tagging with git

What's the difference between tagging and commiting?

With a commit, you sum up different edits in your project and explain what these changes do.

With a tag, you sum up different commits in your project and add these changes to a new overall version of the program.

Creating tags is really simple. In VSCode, you can click a button to create one for you. It is in the Git Source Control, under the three little dots in the Tags category. You will be prompted to give the Tag a name and a description. Tagging is generally used for new releases of a software, so it is important to make sure there is no unfinished code in the project.

![img5](./img/img5.png "Documentation Image #5")

The tag will also be visible in the VSCode Checkout function. The Checkout Function allows you to go back in the history of your project and see what it looked like at that specific point. So let't talk about that a bit deeper now.

### Tagging in the commandline

The same process in the commandline is in my opinion a bit more straight forward. You only have to enter the following command:
```
git tag -a "Git Basic Tutorial v0.1" -m "Created a Tutorial in Markdown that teaches how to set up and use commits in your project"
```

## Viewing the history of a project

There are multiple ways view the history in a git project. You can check out the past commits, or you can check out the tags.

Not that the checkout function is built into VSCode as well, but only shows you branches and tags. However, when using the commandline, you can also check out every single commit individually.

### Checkout tags
You can access that by clicking on the small branch icon in the very bottom left of VSCode. Then a pop-up will appear with a selection of branches and tags. This tutorial does not teach branches, so you can ignore those if you do not understand Git well enough yet.

![img6](./img/img6.png "Documentation Image #6")

#### Checkout tags in the commandline

To Checkout a tag in commandline, you can use the following command:
```
git checkout Git-Basic-Tutorial-v0.1
```

### Checkout commits

Checking out commits is only possible in the commandline.

You can type the following command in the console to get the commit history printed: `git log`
```
commit 7aaead9e5c68f13fb76ba68ea53ff7b47935927a (HEAD -> master)
Author: Tomentos <<**********@@gmail.com>
Date:   Wed Feb 8 19:48:47 2023 +0100

    Added images and commandline to tagging doc

commit 67d02d9d5e36c837256e86a68dd363cb53c5369c
Author: Tomentos <<**********@@gmail.com>
Date:   Wed Feb 8 19:44:38 2023 +0100

    Added a short description for tagging

commit dcd507c6fe88f10a849bc5737fe74568a1c21497
Author: Tomentos <**********@gmail.com>
Date:   Wed Feb 8 19:43:25 2023 +0100

    Created and written doc up until how to commit
```
Using the `git log` command, you get some basic information like who made the commit, when the commit was made, the commit message and in what branch the commit has been made. This tutorial still does not teach branches, so you can ignore those if you do not understand Git well enough yet.

The most imortant thing when it comes to commits are the IDs. Everytime you need to work with a past commit, you need to provide the ID of the commit. However, you only ever need the first few symbols of the ID. So in this case `dcd507c6` is sufficient.

Now checking out this commit works the same way as checking out a tag would, except that you just use this above ID as a replacement for the name; like this: `git checkout dcd507c6`.
