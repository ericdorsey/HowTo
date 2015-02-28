# Create GitHub Project Pages

**What**:  
Pages hosted at http://yourusername.github.io/projectname

___

The official Github guide:  
[https://help.github.com/articles/creating-project-pages-manually/](https://help.github.com/articles/creating-project-pages-manually/)

They say:
> The safest way to do this is to start with a fresh clone

So they recommend creating a freshly cloned repo, which I guess they are trying to protect the original code base. Is the idea then that you merge from the original repo to your new ```gh-pages``` repo whenever you make a change (which you need to merge branches anyway with the Thinkful method below) and need to update the github.io project page?

I prefer the Thinkful method below -- having both ```master``` and ```gh-pages``` branhces in the same (*original*) repo.
___

Thinkful tutorial:  
[http://www.thinkful.com/learn/a-guide-to-using-github-pages/start/existing-project/project-page/existing-repo/](http://www.thinkful.com/learn/a-guide-to-using-github-pages/start/existing-project/project-page/existing-repo/)

Example following the Thinkful methodology, which starts in the existing repo:

> At the command line, make sure you are in your local project repo.

```
$ cd /path/to/repo
```

> Create a new branch called ```gh-pages``` and check it out.
The branch name ```gh-pages``` is a special branch that github uses to get files to build and publish from.

```
~/PhpstormProjects/Mermaid (master) $ git checkout -b gh-pages
Switched to a new branch 'gh-pages'
```

> Make sure your home page is at the base of your repo directory and is named ```index.html``` so that GitHub knows to display it.  
Push your new branch to GitHub!

```
~/PhpstormProjects/Mermaid (gh-pages) $ git push origin gh-pages
Total 0 (delta 0), reused 0 (delta 0)
To https://github.com/ericdorsey/MermaidExample.git
 * [new branch]      gh-pages -> gh-pages
```

Now we have ```master``` and ```gh-pages``` branches:  

```
~/PhpstormProjects/Mermaid (gh-pages) $ git show-branch
* [gh-pages] initial commit
 ! [master] initial commit
--
*+ [gh-pages] initial commit
```
___

## Mirror ```gh-pages``` to ```master```

**What:**  
Keep ```master``` and ```gh-pages``` branches in sync.

Stack Overflow discussion:  
[http://stackoverflow.com/questions/5807459/github-mirroring-gh-pages-to-master](http://stackoverflow.com/questions/5807459/github-mirroring-gh-pages-to-master)

___

### Keep things up to date manually

[http://stackoverflow.com/a/5824720/853178](http://stackoverflow.com/a/5824720/853178)

Commit a change to ```master```

Checkout ```gh-pages```, merge changes from ```master```, push origin (local ```gh-pages```) to Github, switch back to master:

```
~/PhpstormProjects/Mermaid (master) $ git checkout gh-pages
Switched to branch 'gh-pages'

~/PhpstormProjects/Mermaid (gh-pages) $ git merge master
Updating bf57e50..b3dffc7
Fast-forward
 index.html | 4 ++++
 1 file changed, 4 insertions(+)
 
~/PhpstormProjects/Mermaid (gh-pages) $ git push origin gh-pages
Total 0 (delta 0), reused 0 (delta 0)
To https://github.com/ericdorsey/MermaidExample.git
   bf57e50..b3dffc7  gh-pages -> gh-pages
   
~/PhpstormProjects/Mermaid (gh-pages) $ git checkout master
Switched to branch 'master'

```

Changes will now be visible at:  
```http://yourname.github.io/projectname```.

___


### Keep things up to date automatically

*Note: This assumes you've already created the ```gh-pages``` branch as above.*

From [http://stackoverflow.com/a/28035663/853178](http://stackoverflow.com/a/28035663/853178)

> If you want to push both to ```master``` and ```gh-pages``` automatically each time you run git push origin, you probably want to add a Refspec to the git config of your repo.

> So, according to the git-scm book, you can add two [RefSpecs](http://git-scm.com/book/it/v2/Git-Internals-The-Refspec#Pushing-Refspecs), by adding two push values to the repo config file ```.git/config```:


```
[remote "origin"]
	url = https://github.com/<github_user>/<repo_name>
	fetch = +refs/heads/*:refs/remotes/origin/*
	push = refs/heads/master:refs/heads/master
	push = refs/heads/master:refs/heads/gh-pages
```

What does this do? 

> That will cause a ```git push origin``` to:

> 1. Push the local master branch to the remote master branch
> 2. Push the local master branch to the remote gh-pages branch

> by default.

Commit a change to ```master```.

Push changes to both branches simultaneously -- **Note that we are running ** ```$ git push origin``` **with *no branch specified*** (ie, nothing after ```origin```). 

Both branches updated:

```
~/Code/test123 (master) $ git push origin
Counting objects: 3, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 288 bytes | 0 bytes/s, done.
Total 3 (delta 1), reused 0 (delta 0)
To https://github.com/ericdorsey/test123.git
   32febb4..6710877  master -> gh-pages
   32febb4..6710877  master -> master
```

Changes will now be visible at:  
```http://yourname.github.io/projectname```.

---

### Useful Links
* [http://git-scm.com/book/it/v2/Git-Internals-The-Refspec#Pushing-Refspecs](http://git-scm.com/book/it/v2/Git-Internals-The-Refspec#Pushing-Refspecs)
* [http://stackoverflow.com/questions/5807459/github-mirroring-gh-pages-to-master](http://stackoverflow.com/questions/5807459/github-mirroring-gh-pages-to-master)
* [https://pages.github.com/](https://pages.github.com/)
