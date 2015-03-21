### General / Misc
* [http://git-scm.com/](http://git-scm.com/)
* [https://www.atlassian.com/git/tutorials/](https://www.atlassian.com/git/tutorials/)



### Branches

* [https://pcottle.github.io/learnGitBranching/](https://pcottle.github.io/learnGitBranching/)

Show all branches

```
~/Code/test123 (master) $ git branch
  ScottAmes-patch-1
  gh-pages
* master
```


See last commits on all branches

```
git branch -v
```

See diff on two branches

```
$ git diff master..gh-pages
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

___

### Pretty Commit History

Color coded commit history, one per line
 
```
$ git log --oneline --abbrev-commit --all --graph --decorate --color
```
___

### Diffs

[http://git-scm.com/docs/git-diff](http://git-scm.com/docs/git-diff)

Compare the version before the last commit and the last commit.

```
$ git diff HEAD^ HEAD
```

___

### Fast Forward

[http://ariya.ofilabs.com/2013/09/fast-forward-git-merge.html](http://ariya.ofilabs.com/2013/09/fast-forward-git-merge.html)

Turn fast-forward off

[http://stackoverflow.com/questions/16453941/how-to-set-no-fast-forward-as-default-when-using-git-merge](http://stackoverflow.com/questions/16453941/how-to-set-no-fast-forward-as-default-when-using-git-merge)

```
git config --global merge.ff false
```
