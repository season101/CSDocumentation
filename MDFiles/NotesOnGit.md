# Introduction to Git
Git is the most popular Version Control System(VCS). With VCS, We can track history of  our code and work together.

VCS is of two types. They are:
1. Centralized System : Single server for hosting the code. eg. Subversion.

2. Distributed System : Code is present on all host. eg: Mercurial, Git, etc.

## Git
Git is a popular distributed VCS system. It is open source, super fast and scalable.

### Using Git
* Git can be used from command line which is the fastest method and also requires some expertise.

* Many modern Code editors and IDEs support the GUI which is easier for the beginners.

Note: Git has also its own GUI app or we can use Gitkraken or Source tree which are great third-party GUI apps.

### Why Command line
GUI Tools lacks many features, Also, Command line is readily available.
To start learning mixture of both can be used.

### Git installation
> First verify if git is installed or not.

```bash
 $ git --version
```
If you see some version of git installed then we are good to go else we can download it from git official website.

### Configuring Git
We have to first configure git settings with these specifications:
1. Name
2. Email
3. Default editor
4. Line Ending

Git configuration can be setup at different levels.
1. SYSTEM: *All users*
2. GLOBAL: *All repository of current user*
3. LOCAL: *The current repository*

> Configuring git configuration for the users

```bash
$ git config --global user.name "First Name"
```

```bash
$ git config --global user.email "username@domain.com"
```
```bash
$ git config --global core.editor "code --wait"
```

>We can even run this command to open up our .gitconfig file using default text editor and make changes from there.

```bash
$ git config --global -e
```
**Note** : Windows and macOS/Unix Handles line breaks differently. In windows it is done by \r -Carriage Return \n -Line Feed and in macOS/Unix it is handled by \n -Line Feed.

We can handle this issue by configuring the config file for core.autocrlf property.

> In windows

```shell
> git config --global core.autocrlf true
```


> In MacOS/Linux

```bash
$ git config --global core.autocrlf input
```

 ## Creating Snapshots

### Creating Git Repository
Lets start by making a directory for our project. To make it a git repository run the command:
 ```bash
git init
 ```

### Git Basic Workflow
What are the basis of git workflow. We have two directories now. One that is our project directory and another is the hidden .git directory/repository.

- First We Modify some files in our project directory. We then commit it to git repository. This is called taking snapshot.

- Concept of **Staging Area**. It is an conceptual place where we propose our next snapshot or commit. If after review we think its good to go, We go ahead and commit changes to our git repository.

- Every git commits are unique and identified by ID and contains information about Message, Date/Time, Author and Complete Snapshot of the files during that commit.

### Staging files
Git automatically doesn't stages all the files that we create in our project. We manually have to store them to the staging area. We can check on the overall status of the project by running following command:
```bash
git status
```
It lists us the files in our project directory that are being tracked or are not tracked.

We can add files to our staging area by running following command.
```bash
git add filename1 filename2
```
or we can add all files at once by running command:
```bash
git add .
```
> this command adds all the files from our root of project directory recursively to the staging area.

### Committing Changes
