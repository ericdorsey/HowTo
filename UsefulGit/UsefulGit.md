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

___

Color coded commit history, one per line
 
```
$ git log --oneline --abbrev-commit --all --graph --decorate --color
```

### Fast Forward

[http://ariya.ofilabs.com/2013/09/fast-forward-git-merge.html](http://ariya.ofilabs.com/2013/09/fast-forward-git-merge.html)

Turn fast-forward off

[http://stackoverflow.com/questions/16453941/how-to-set-no-fast-forward-as-default-when-using-git-merge](http://stackoverflow.com/questions/16453941/how-to-set-no-fast-forward-as-default-when-using-git-merge)

```
git config --global merge.ff false
```
