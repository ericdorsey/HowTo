## Links

### General / Misc
* [http://git-scm.com/](http://git-scm.com/)
* [https://www.atlassian.com/git/tutorials/](https://www.atlassian.com/git/tutorials/)

### Educational

* [http://onlywei.github.io/explain-git-with-d3/](http://onlywei.github.io/explain-git-with-d3/)

### Two factor auth

* [https://github.com/blog/1614-two-factor-authentication](https://github.com/blog/1614-two-factor-authentication)
* [https://github.com/blog/1614-two-factor-authentication](https://github.com/blog/1614-two-factor-authentication)
* [https://help.github.com/articles/creating-an-access-token-for-command-line-use/](https://help.github.com/articles/creating-an-access-token-for-command-line-use/)
* [https://help.github.com/articles/caching-your-github-password-in-git/#platform-all](https://help.github.com/articles/caching-your-github-password-in-git/#platform-all)
* [http://blog.apericore.com/enabling-https-access-to-your-github-repositories-after-enabling-two-factor-authentication/](http://blog.apericore.com/enabling-https-access-to-your-github-repositories-after-enabling-two-factor-authentication/)
___

## Commands

### Branches

* [https://pcottle.github.io/learnGitBranching/](https://pcottle.github.io/learnGitBranching/)

Show all branches

```
~/Code/test123 (master) $ git branch
  ScottAmes-patch-1
  gh-pages
* master
```

#### New Branch ```create-file-function```

```
$ git checkout -b create-file-function
```

#### See last commits on all branches

```
git branch -v
```

#### See diff on two branches

```
$ git diff master..gh-pages
```

#### Delete unneeded branch (already been merged)

```
~/Code/HostMAC (master) $ git branch
  bcambl-multios_arp_mac_regex
  bcambl-regex-ip-check
  getping_to_msResponse
* master
  osx
~/Code/HostMAC (master) $ git branch -d osx
Deleted branch osx (was cdcbab8).
~/Code/HostMAC (master) $ git branch
  bcambl-multios_arp_mac_regex
  bcambl-regex-ip-check
  getping_to_msResponse
* master
```

#### Force local ```master``` to match repo after Pull Request
From [http://stackoverflow.com/questions/1125968/force-git-to-overwrite-local-files-on-pull](http://stackoverflow.com/questions/1125968/force-git-to-overwrite-local-files-on-pull)

Opened a new dev branch, ```osx```, had merged that as a Pull Request into ```master``` via GitHub. Now need to get local repo in line with the just updated remote ```master``` (ie, get local ```master``` showing PR changes):

```
~/Code/HostMAC (master) $ git fetch --all
Fetching origin
~/Code/HostMAC (master) $ git reset --hard origin/master
HEAD is now at c4ae523 Merge pull request #15 from ericdorsey/osx
~/Code/HostMAC (master) $ git log -1
commit c4ae523def1857fc672114b29cfbb9e25bafb45e
Merge: 343b7d4 cdcbab8
Author: Eric Dorsey <dorseye@gmail.com>
Date:   Thu Mar 19 23:11:32 2015 -0600

    Merge pull request #15 from ericdorsey/osx

    OSX functionality improvments
```



### Pretty Commit History

#### Color coded commit history, one per line
 
```
$ git log --oneline --abbrev-commit --all --graph --decorate --color
```
___

### Diffs

[http://git-scm.com/docs/git-diff](http://git-scm.com/docs/git-diff)

#### Compare the version before the last commit and the last commit.

```
$ git diff HEAD^ HEAD
```

___

### Errors

* [http://christoph.ruegg.name/blog/git-howto-revert-a-commit-already-pushed-to-a-remote-reposit.html](http://christoph.ruegg.name/blog/git-howto-revert-a-commit-already-pushed-to-a-remote-reposit.html)

#### Last `$ git push origin master` was wrong. 

Details: (Owner of the remote, no one else is contributing on this repo). We want to reset the remote back to last commit.

On `master` of local branch:

```
$ git reset HEAD^ --hard
HEAD is now at 95f318a add random image functionality
```

Fails because origin (remote) ahead of master (local):

```
$ git push origin master
To https://github.com/ericdorsey/Hubot.git
 ! [rejected]        master -> master (non-fast-forward)
error: failed to push some refs to 'https://github.com/ericdorsey/Hubot.git'
hint: Updates were rejected because the tip of your current branch is behind
hint: its remote counterpart. Integrate the remote changes (e.g.
hint: 'git pull ...') before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.
```

We can force the push to overwrite remote with `-f`:

```
~/Code/Hubot (master) $ git push origin master -f
Total 0 (delta 0), reused 0 (delta 0)
To https://github.com/ericdorsey/Hubot.git
 + 149f043...95f318a master -> master (forced update)
```


___

### Fast Forward

[http://ariya.ofilabs.com/2013/09/fast-forward-git-merge.html](http://ariya.ofilabs.com/2013/09/fast-forward-git-merge.html)

#### Turn fast-forward off

[http://stackoverflow.com/questions/16453941/how-to-set-no-fast-forward-as-default-when-using-git-merge](http://stackoverflow.com/questions/16453941/how-to-set-no-fast-forward-as-default-when-using-git-merge)

```
git config --global merge.ff false
```

___

### File Rename

#### Update Files Renamed via Bash 

```
$ mv UsefulCLI.md BashUsefulCLI.md

```

```
$ git status
On branch master
Changes not staged for commit:
  (use "git add/rm <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

	deleted:    UsefulCLI.md

Untracked files:
  (use "git add <file>..." to include in what will be committed)

	BashUsefulCLI.md
	OSXUsefulCLI.md
```

```
$ git rm UsefulCLI.md
rm 'UsefulCommandLine/UsefulCLI.md'
~/HowTo/UsefulCommandLine (master +) $ git add BashUsefulCLI.md
```

```
$ git status
On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

	renamed:    UsefulCLI.md -> BashUsefulCLI.md
	new file:   OSXUsefulCLI.md
```

#### Rename a File via Git

```
$ ls
foo.txt
```

```
$ git mv foo.txt foo2.txt
~/temp/baz (master +) $ git status
On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

	renamed:    foo.txt -> foo2.txt
```

