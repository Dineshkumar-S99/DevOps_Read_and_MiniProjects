Git is an open source Distributed version control system which allow us to work on different versions of the same file [i.e:like content tracker] or to work on the histories of a file. allow us to have backup.

**different types of version control system**

1. **Local VCS** → in local file/server eg:filename_with_time_and_date
2. **centralized VCS** → have common server and allow users to have certain code and allow user to lock the code base which they are working, but here everyone don't have whole code eg: CVS, subversion, Preforce
3. **Distributed VCS** → everyone has a same updated version of code eg:Git locally and remote- GitHub, GitLab

**Branch** - Branch are nothing but pointers to a certain commit or to the previous commit.

**Head** → shows  where we are right now in the repository and points to the latest/last commit made in that branch. even if we switch the branch the head will also switch.

**There are two types of merge** 

1. **fast-forward merge** → which is the most common merge which git tries, when the current branch doesn’t have any commits after the new branch got created. if so it will perform fast forward merge.
2. **no-fast-forward merge** → here the current main branch/other will also have commits after the branch has been created. so now to merge it will create a new commit with merge message and then will merge two branches.

### Commands
→ to initialize the local repository
	git init
→ to add the user email
	git config --global user.email "email" 
→ to add the user id
	git config --global user.name "name/id" 
→ to see the added username and email
	git config --global --list 
→ to add the remote repository
	git remote add origin <url> 
→ to check the remote repo url
	git remote -v
→ to remove the remote repo
	git remote remove origin 
→ to add the files to the staging area
	git add <filename or . > 
→ to see the status of the file in stagin area or files history of commits
	git status 
→ to commit the files in staging area
	git commit -m "msg" 
→ to push the commited changes to the remote repo
	git push -u origin <main/branchname>
→ to change the master branch as main branch
	git branch -M main 
→ to push all the branches
	git push --all origin
→ to pull the remote repo to local or to pull specific remote branch to local and this will also update the local repo 
	git pull <url> 
→ to have complete copy of the remote repo, mostly it will clone the main branch
	git clone <url> 
→ to clone the exact branch we want and can also save it in name as we want
	git clone -b <branchname> <url> 
→ fetch all the latest changes to the repo but won't update it unlike pull
	git fetch <url> 
→ to overcome the non fast forward error
	git pull origin main --allow-unrelated-histories 
→ to see all the previous commits and info about the commit hash, author and cmt date
	git log 
→ to see logs in less format and with less id characters (i.e: to view in compact way)
	git log --oneline 
→ to see the last n number of commits
	git log -n number 
→ to see the changes we did in the particular commit
	git show <commitd> 
→ to see all the local branches
	git branch 
→ to create a branch
	git branch <bname> 
→ to delete the branch
	git branch -d <bname> 
→ to see both local and remote branches
	git branch -a 
→ to create a new branch
	git branch -C <branchname> 
→ to  create a new branch and switch to that branch 
	git checkout -b <branchname> 
→ to switch between branches
	git checkout/switch <branchname> 
→ to merge the given branch with the current branch
	git merge <bname> 
→ merge branch with cmt msg
	git merge <bname> -m "msg" 
→ merge thebbranch without ff error
	git merge --no-ff <bname> 
→ this file can be used for exception, if we don't want a file to be VC then use this file and mention those files inside this eg: like key, pswd
	.gitignore 
→ to revert the file to previous version even if not made to staging area
	git checkout <filename> 
→ to remove the file
	git rm filename 
	  → will just remove the file from git and tracking, the file will remain in the system (but not the best way to do because sometime we may accidentaly stage back again so use .gitignore)
	      1. git rm - - cached <filename> 
	  → will also remove the file from the device
	      1. git rm -f <filename> 
→ shows the changes we did before staging and now
	git diff 
→ to revert back to prev version if the file is staged
	git diff --cached 
→ to remove it from the staging area (i.e: to unstage)
	git restore --staged <filename> 
→ to get back to the cmt id but will leave a history
	git revert cmtid 
→ to get back to the previous commit
	git revert HEAD 
→ revert back and don't leave any history and even del histories after the id
	git reset --hard cmtid 
→ to generate an ssh pub and priv key
	ssh-keygen.exe 
→ will create an rsa based ssh pub and private key
	ssh-keygen -t rsa -C email 
→ to update the git
	git update -git-for-windows 
→ to remove the file from cached so that it can be ignored by gitignore even though we commited it before
	git rm --cached <filename> 
→ to discard the changes in the working directory. i.e: even before staging (note: this will be only for previously commited files)
	git restore <filename> 
    1. and it will also work in case where if we have a file that we staged and again we modified it, now it shows modified twice, one to be commited and other to be staged, here we can use git restore
→ to list the changed files as well
	git log - - name-only 
→ to revert the last change we made or committed
	git reset --soft HEAD~1 
→ to see previous commit history along with the branch they were committed on
	git log --graph --decorate` 
→ to merge the fetched changes from origin to our branch (can direcly pull to do  fetch and this merge)
	git merge origin/master 
1. 
2. .
3. .
4. .

The URL that we used to connect the local and remote repository are called Connection string.

origin is nothing but an aliasing name we give to an remote repository.

fetching will update the local branch to the origin master and point to the latest changes made on origin master. and to point we have to merge the origin master into the local master (can directly pull instead these - cmd: git pull origin master).

Git Pull - is two commands in one include both fetch and merge.

Fork - fork is just like cloning but cloning/ creating our own copy of the repository/project to our remote repository (i.e:GitHub, GitLab etc.). and then send a pull request to update your changes to the repo where we forked.

when we want to have our own branch to have all latest changes from the main branch we can do it in two ways

1. merge the main with our branch (will create new merge commits to merge the changes)
2. rebasing the branches (like putting one on top of another one.) so instead merging we moving one on top of another.
    1. git rebase master - this will put our branch on top of master branch. now our branch will also have all the changes made in the master branch.

note: when we are merging it won’t create a new commit hash, but in rebasing it will create a new hash, which means it’s like modifying the history but most cases its not a problem just creates extra logs.

since there is no merge commits, we don’t have any clarity on what’s happening.

Interactive Rebasing;

rebase command also let us to modify the history before rebasing. lets take scenario where we want to have multiple commits as single commit we can do so by using rebase.

eg: we want to convert last 4 commits into one we can do it by 

git rebase -i HEAD~4   → this says git we want to interactively rebase last 4 commits. now it will open a prompt and show us all the options that can be used.

now all four commits will be shown and will have key works pick. eg:

	pick cmthash cmtmsg
	pick cmthash cmtmsg
	pick cmthash cmtmsg
	pick cmthash cmtmsg

now pick which commit we want and squash rest (squash is like reduce) 

	pick cmthash cmtmsg
	squash cmthash cmtmsg
	squash cmthash cmtmsg
	squash cmthash cmtmsg

it will pick the last commit and squash rest and will become single commit with the pick commitid

 When we want to copy only certain commit to the main branch not everything In the current branch we can use command cherry-pick 

 git cherry-pick cmtId → now only that particularly commit will get copied to the main branch.

Git revert cmtId → this will help us to revert back to the commitid we specified but this will also create a new commit Id hash

We can also reset or revert back without creating a new commit id, using reset commands and have two types 

1. git reset - - soft HEAD~1 → this will keep the changes we made in the last commit and revert back
2. git reset - - hard HEAD~1 → This will delete all the changes we made in the last commit and revert back, so we don’t have anything to commit after the reset 

lets take scenario where we want to fix bugs in different program while we are working on a different program and we want a clean workspace for the bug fixing what can be done,

we can use stashing (git stash)

git stash → everything in the working/staging area will be sent to the stash

git stash pop → will now bring back all the files from stash to working area.

git stash list → to view all the contents in the stash

git stash show stash@{n} → n can be the number of stash, like 1st stash, 2nd stash, we can able to view them.

eg: git stash show stash@{3} → will show the 3rd stash

git stash pop → will remove the stash that’s lastly added.

eg: stash0 - story3, stash1 - story2, stash2 - story1 now git pop will take out story1

git stash pop stash@{n} → to pop the particular stash we want.

note: we can stash multiple files and it will get pilled up on upon other like stack FILO.

git reflog → shows all the actions that we executed on a repo like commits, merges, resets, reverts, etc. similar like git log but also shows the commits and commands

lets takes a scenario where we did hard reset but later found the commit is most important, and now to revert back we use reflog.

git reflog → shows all the alterations made. and by seeing the commit we can revert back based on the information 

eg: to get back to previous state 

git reset —hard hashfromreflog

note: even this action will also be pushed to reflog

working of GIT

git nothing but a key value store, when we add file to commit the contents of the file are  hashed using SHA-1 algorithm.

the hash is used as a keyname for the folders and stores the file using that key name.

git has two types of commands 

1. porcelain commands → these are some commands those are easy to remember like.
    1. git add
    2. git status
    3. git commit
    4. git stash, etc
2. plumbing commands → with this we can get access to the internals of git. by using the plumbing commands we can create the hash ourselves. these are things that happens when we execute a git commands
    1. git hash-object
    2. git ls-files
    3. git rev-parse
    4. git ls-remote,
    5. git cat-file -p hash etc

with hash-object we can hash an object followed by its name, just like the git commit command that creates hash this also does the same. 

git hash-object filename

this will return a hash

eg: bea8d7fee8e7b11c2235ca623935e6ccccd8bac3

here first **two characters** of the hash are used as key. this is **name of the folder** that **store the contents of the file.**

so if we try to commit the same exact hash will be created. 

the folder is visible when we open the .git/objects folder, we can see the folders of the hash

eg: be in our case, and inside that we can see the value of the hash is stored in there

to view the contents of the file, we can use another command git cat-file -p hash → -p is to print the contents of the hash

and we can just give couple of hash values, eg: in our case

git cat-file -p bea8d7

these are just so much identical to commit, but in commit we get little more information, 

eg: if we do same to the commit’s hash, we have infos like

tree, parent, author and committer

author is a user and an author to that change, 

committer is a user that committed the commit

folders in object folder can be of three types,

1. commit → is just a simple commit
2. tree → is a folder on our file system that’s associated with a repository
3. blob → is just a piece of data

note: each commit holds reference to more trees and blobs

eg: the first commit reference to the tree and tree to the blob

but the next commit will reference to the tree and tree will reference the current/new blob and also the previous blob.

basically commit stores a reference to a folder structure, that’s how we can go back to different commits with trees that reference to different blobs.