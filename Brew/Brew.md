

* [Documentation](https://github.com/Homebrew/homebrew/tree/master/share/doc/homebrew#readme)
* [Brew FAQ](https://github.com/Homebrew/homebrew/blob/master/share/doc/homebrew/FAQ.md#faq)
* [Keep Homebrew up to date](https://blog.safaribooksonline.com/2014/03/18/keeping-homebrew-date/)

List Brew Installed Packages:

```
~ $ brew list -l
total 0
drwxr-xr-x  3 ericdorsey  admin  102 Feb 14 15:09 cscope
drwxr-xr-x  3 ericdorsey  admin  102 Feb 14 15:09 git
drwxr-xr-x  3 ericdorsey  admin  102 Feb 14 15:09 htop-osx
drwxr-xr-x  3 ericdorsey  admin  102 Feb 14 15:09 jpeg
drwxr-xr-x  4 ericdorsey  admin  136 Feb 14 15:09 macvim
drwxr-xr-x  3 ericdorsey  admin  102 Feb 14 15:09 redis
drwxr-xr-x  3 ericdorsey  admin  102 Feb 14 15:09 vim
```

___

Change self back to owner of `/usr/local` for Homebrew.
 
[http://stackoverflow.com/questions/14527521/brew-doctor-says-warning-usr-local-include-isnt-writable](http://stackoverflow.com/questions/14527521/brew-doctor-says-warning-usr-local-include-isnt-writable)


```
$ sudo chown -R $USER /usr/local/
```