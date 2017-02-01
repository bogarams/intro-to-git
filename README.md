# intro-to-git
Introduction to Git
Installing Git:
--------------
If you’re on Fedora, you can use yum:
$ sudo yum install git-all

If you’re on a Debian-based distribution like Ubuntu, try apt-get:
$ sudo apt-get install git-all

On windows, 
http://git-scm.com/download/win

Below installer includes a command line version of Git as well as the GUI:
http://windows.github.com

Create project:
Create a repo 'intro-to-git' in cloud9.
mkdir intro-to-git
cd intro-to-git
git init 
=>Initialises the git within the directory where it is invoked from.Starts a empty git repo called .git in the directory /home/ubuntu/workspace/intro-to-git/.git/.

bogarams:~/workspace/intro-to-git $ git init
Initialized empty Git repository in /home/ubuntu/workspace/intro-to-git/.git/
bogarams:~/workspace/intro-to-git (master) $ 
bogarams:~/workspace/intro-to-git (master) $ ls -a
./  ../  .git/
bogarams:~/workspace/intro-to-git (master) $ 

.git folder inside contains all the files that git needs to operate.

Three areas of operations/storage in GIT.
#Working Directory
	Area where all our files/folders and changes are living all the time.
#Staging area
	Files and folders that we add to this area before moving to repository.
#Git Repository
	Place where our snapshots are stored.

Create a file called README.cmd.
bogarams:~/workspace/intro-to-git (master) $ touch README.md
bogarams:~/workspace/intro-to-git (master) $ ls -ltr
total 0
-rw-r--r-- 1 ubuntu ubuntu 0 Jan 28 06:42 README.md
bogarams:~/workspace/intro-to-git (master) $ cat README.md 
bogarams:~/workspace/intro-to-git (master) 
README.cmd currently exists only in our working copy. Git repo does not know anything about it.
To add to repo, we first add to staging area and then commit to add to repo area.

Use git status command, to check if the working directory is clean, to check what files have been created and what files needs to be added so to be tracked, what files still needs to be committed, which branch we are on, status of working directory/staging/repo.

bogarams:~/workspace/intro-to-git (master) $ git status
On branch master

Initial commit

Untracked files:
  (use "git add <file>..." to include in what will be committed)

        README.md

nothing added to commit but untracked files present (use "git add" to track)
bogarams:~/workspace/intro-to-git (master) $ 

To add file to staging area:
bogarams:~/workspace/intro-to-git (master) $ git add README.md 

To remove file from staging area:
git rm --cached README.md 

To add the file from staging area to repo area:
git commit -m "Message"

bogarams:~/workspace/intro-to-git (master) $ git commit -m "Added README.md"
[master (root-commit) cbd621c] Added README.md
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 README.md
bogarams:~/workspace/intro-to-git (master) $ 

To see history of commits:
git log

To add all files including hdden files from the same directory:
git add -A

To add specific type of files:
git add *.html

To unstage a file:
git reset HEAD <fileName>

Ignoring files/folders from working directory while adding them to repo:
Create a hidden file called .gitignore

bogarams:~/workspace/intro-to-git (master) $ git status
On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

        new file:   .hidden.txt
        new file:   file1.txt
        new file:   file2.txt
        new file:   first.html

Untracked files:
  (use "git add <file>..." to include in what will be committed)

        mycsv.csv
        second.html

bogarams:~/workspace/intro-to-git (master) $ touch .gitignore
bogarams:~/workspace/intro-to-git (master) $ echo "mycsv.csv" >> .gitignore
bogarams:~/workspace/intro-to-git (master) $ cat .git
.git/       .gitignore  
bogarams:~/workspace/intro-to-git (master) $ cat .gitignore 
mycsv.csv
bogarams:~/workspace/intro-to-git (master) $ 
bogarams:~/workspace/intro-to-git (master) $ echo "second.html" >> .gitignore
bogarams:~/workspace/intro-to-git (master) $ cat !$
cat .gitignore
mycsv.csv
second.html
bogarams:~/workspace/intro-to-git (master) $ 
bogarams:~/workspace/intro-to-git (master) $ git status
On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

        new file:   .hidden.txt
        new file:   file1.txt
        new file:   file2.txt
        new file:   first.html

Untracked files:
  (use "git add <file>..." to include in what will be committed)

        .gitignore

bogarams:~/workspace/intro-to-git (master) $

Git Branches:
-------------
-------------
Listing all branches:
bogarams:~/workspace/intro-to-git (feature1) $ git branch
* feature1
  master
bogarams:~/workspace/intro-to-git (feature1) $ 

Current branch has prefix *.

Creating/Adding a branch:
git checkout -b <branch name>

bogarams:~/workspace/intro-to-git (master) $ git checkout -b feature1
Switched to a new branch 'feature1'
bogarams:~/workspace/intro-to-git (feature1) $

Git will auto switch to new branch after creation.

Changing/switching branches:
git checkout master
bogarams:~/workspace/intro-to-git (feature1) $ git checkout master
Switched to branch 'master'
bogarams:~/workspace/intro-to-git (master) $ 

Merging branches:
To merge a branch feature1 into master.

bogarams:~/workspace/intro-to-git (feature1) $ git checkout master
Switched to branch 'master'
ogarams:~/workspace/intro-to-git (master) $ git merge feature1
Updating 8a2a039..93c0f7d
Fast-forward
 feature1file.txt | 0
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 feature1file.txt
bogarams:~/workspace/intro-to-git (master) $ 

To delete a branch:
------------------
git branch -d <branch name>

bogarams:~/workspace/intro-to-git (feature1) $ git branch
* feature1
  master
bogarams:~/workspace/intro-to-git (feature1) $ git checkout master
Switched to branch 'master'
bogarams:~/workspace/intro-to-git (master) $ git branch -d feature1
Deleted branch feature1 (was 93c0f7d).
bogarams:~/workspace/intro-to-git (master) $ git branch
* master
bogarams:~/workspace/intro-to-git (master) $ 

Checking out commits:
--------------------
Git allows us to checkout any of the commits from our log. This means we can go back and look at the code from our earlier commits without losing any of our current commits. This is especially useful when you're current codebase is broken, but you have an earlier commit with working code.

1) Make sure you're inside of your project's directory, using the cd command.
2) Once inside of the directory, use git log to view your log history.
3) You can scroll down to earlier commits by hitting enter (return)
4) Once you locate the commit you want to checkout, copy the hash key from the commit.The hash key is the alphanumeric string that comes after the word "commit".
5) Exit out of git log by pressing Q
6) Type git checkout 7484e645 (replace the hash with one from your selected commit) and hit enter
7) Now you can look around inside of this commit and copy any code that you need. If you'd like to start working from this commit, but don't want to overwrite any of the code from the branch that you're currently on (in this case it's master) then you can type git checkout -b <branch_name> to create a new branch to begin working from.
8) Once you're done working from this commit, you can return to the most recent commit on the branch of your choosing by typing git checkout <branch_name>, in this case I typed git checkout master and it returned me to my most recent commit on the master branch.

Note: When you checkout an earlier commit, you are now in a "detached HEAD" state, this means that you are no longer on the commit that is being pointed to by the HEAD. The HEAD, in git, is a pointer to the most recent commit of whichever branch you are currently on.


	
