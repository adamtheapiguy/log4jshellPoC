## Overview
This guide shows how to setup Git in your machine and create a feature branch 

## Generate and use ssh keys for your github account

1. Generate SSH keys for your github account
```
$ ssh-keygen -t rsa -C "john.appleseed@myprototype.io" -f ~/.ssh/github
```
You should be able to see the ssh public key under ~/.ssh/{KeyFileNameForAccount1}.pub. You would use that later on to configure your Github account

2. Add the above keys to ssh client
```
$ ssh-add ~/.ssh/github
```
3. List your ssh keys
```
$ ssh-add -l
```
4. Modify ssh config file. Port 443 combined with ssh.github.com would make sure that you don't have problems with firewalls if any. Firewalls usually block outbound connections to any ports other than 443 or 80
```
$ cd ~/.ssh/
$ touch config
$ vi config

#Account1
Host github.com-john.appleseed.myprototype.io
	HostName ssh.github.com
	Port 443
	User git
	IdentityFile ~/.ssh/github

```
5. Change Permissions on config
```
$ chmod 600 ~/.ssh/config
```
6. Update your Github Account with the SSH Public key you generated in step 1 above.

cat ~/.ssh/github.pub

Then copy content and add it to your Github account at https://github.com/settings/keys

![alt text](https://github.com/adamtheapiguy/log4jshellPoC/blob/main/media-assets/10-github-sshkeys.png?raw=true)

7. Set URL for Git
```
$ git remote set-url origin git@github.com-john.appleseed.myprototype.io:/adamtheapiguy/log4jshellPoC
```
8. Get a copy of this repo
```
$ git clone git@github.com-john.appleseed.myprototype.io:/adamtheapiguy/log4jshellPoC.git
```
9. Do some updates
```
cd log4jshellPoC
vi ??
```
9. push updates
```
$ git add -A
$ git commit -am "commit message, please write clearly the updates you have done as part of the commit"
$ git push

Counting objects: 9, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (9/9), done.
Writing objects: 100% (9/9), 1.41 KiB | 1.41 MiB/s, done.
Total 9 (delta 6), reused 0 (delta 0)
remote: Resolving deltas: 100% (6/6), completed with 4 local objects.
To github.com-john.appleseed.myprototype.io:/adamtheapiguy/log4jshellPoC.git
   ffba2fc..5605747  master -> master
$
```
## How to create a new feature branch?
- Create new directory for the new feature locally on your mac
```
mkdir newUselessFeature
cd newUselessFeature
```
- clone master repo
```
git clone git@github.com-john.appleseed.myprototype.io:/adamtheapiguy/log4jshellPoC
```
- change directory to cloned master
```
$ cd log4jshellPoC
```
- List local branches you have
```
$ git branch
* master
```
- List all local and remote branches
```
$ git branch -a
* master
  remotes/origin/HEAD -> origin/master
  remotes/origin/SWAGGERHUB
  remotes/origin/dev/justAnotherFeature
  remotes/origin/master
```
- 
- To get a baring of the updates I have made
```
$ git status
On branch master
Your branch is up-to-date with 'origin/master'.
nothing to commit, working tree clean
```
- Create a new branch. The below command will create a new branch from master as well checkout out that new branch at the same time
```
$ git checkout -b dev/uselessFeatureBranch
```
- do the changes/develop the new feature
- Stage the updates for commitment
```
$ git add -A
```
- Commit updates to the branch
```
$ git commit -m "commiting useless feature branch"
```
- Push the new feature branch 
```
$ git push --set-upstream origin dev/uselessFeatureBranch
```
