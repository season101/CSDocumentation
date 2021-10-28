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
> This command adds all the files from our root of project directory recursively to the staging area.

### Committing Changes

TO commit the files from the staging area to the git repository run the following command.
```bash
git commit -m "Our message for commit."
```
However it is essential sometimes to write a long description for our commit to explain the changes. Then we run the command:
```bash
git commit
```
> It opens up the commit message in our default editor where in first line we can write our short message of 80 chars long followed by long description in the next line.

### Best Practices for git commits
1. Commit size matters: Our git commits shouldn't be of large size neither the smallest too.

2. Try to commit often. Each commit should make logically sense.

3. Don't mixup the various logical or code for different issues. One commit should fix a single issue.

4. Use the past tense. Action followed by the noun.

### Skipping the Staging Area
We can skip the process for staging our files to staging area overall and use command:
```bash
git commit -am "Commit message"
```
It still works but it is not best practice to directly commit changes to the git repository. Only do so if you are sure that your files don't need to be reviewed.

### Removing Files
Removing the file is done by simple bash or cmd command but git flags it as modified because it is still present in our staging area. We can verify this by running command:
```bash
git ls-files
```
It is then essential for us to run command:
```bash
git add deletedfilename.txt
git commit -m "Deleted deletedfilename.txt"
```

This whole operation can be simply handled by single command:
```bash
git rm deletedfilename.txt
```

### Renaming or Moving Files
Files can be moved by using command:
```bash
mv file1.txt savedas.js
```
> This saves file file1.txt as savedas.js and file1.txt is deleted. Don't forget
to add the new file to stage the file.

Both renaming and adding file to staging area can be performed by single command:
```bash
git mv file1.txt savedas.js
```
> Changes are made to working directory and staged directory at the same time.

### Ignoring Files

It is necessary to ignore some files as it just increases the overhead for the project. It can be done by creating a file **.gitignore** on the root of the working directory. Files that needs to be ignored by simply putting every kind in
new line. *Regex* can be used to define multiple files and the relative paths to the file. However, if the file had already been committed to the git repository the gitignore is not going to work.

**Note: To solve this issue file or directory should be removed from the staging area and then commit to git repository. This can be achieved by following command:**

```bash
"--cached flag removes file only from the staging area."
git rm --cached filenameORdirname
```
Various projects produces temporary files not necessary to be tracked. More information on this can be found at: [https://github.com/github/gitignore](https://github.com/github/gitignore)

### Git Short Status
The command `git status` results in very long description. Instead it can be supplied by flag -s for short to display short status message.
```bash
> git status -s
A  file1.js
M  file2.txt
```

### Viewing Staged Files
Before committing your files to git repository, make sure you review your changes in the staging area. For this we use
`git diff --staged` to view the changes in the files in the terminal. It shows what codes are going to be committed to the git repository.
**Changes in the old files are indicated by -- sign and changes in the new files are added by the ++ sign**.
Also `git diff` only shows us the changes between working directory and staging area.
