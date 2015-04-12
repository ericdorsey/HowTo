#### Standards Checking
* [https://github.com/jcrocholl/pep8](https://github.com/jcrocholl/pep8)
* [https://github.com/GreenSteam/pep257](https://github.com/GreenSteam/pep257)

#### Useful Links
* [http://blog.manbolo.com/2014/09/27/use-python-effectively-on-os-x](http://blog.manbolo.com/2014/09/27/use-python-effectively-on-os-x)
* [Python Call Graph](https://pycallgraph.readthedocs.org/en/master/index.html) - *module that creates call graph visualizations for Python applications*


#### Python version (OSX, Linux, Win):

```
$ python --version
```

#### Which `pip` module version

```
$ pip show Jinja2
---
Name: Jinja2
Version: 2.7.3
Location: /Library/Python/2.7/site-packages
Requires: markupsafe
~/Code/HostMAC (remove-get-name) 
```

```
$ pip freeze | grep Jinja2
Jinja2==2.7.3
```
#### Upgrade `pip`

```
$ sudo pip install -U pip
```

#### Virtual Env

* [http://virtualenv.readthedocs.org/en/latest/index.html](http://virtualenv.readthedocs.org/en/latest/index.html)
* [https://virtualenvwrapper.readthedocs.org/en/latest/#](https://virtualenvwrapper.readthedocs.org/en/latest/#)

#### Create virtual env:

```
$ virtualenv ENV_FOOBAR
$ cd ENV_FOOBAR/
$ source bin/activate
(ENV_FOOBAR)$ which python
/Users/ericdorsey/Temp/ENV_FOOBAR/bin/python
(ENV_FOOBAR)$ which pip
/Users/ericdorsey/Temp/ENV_FOOBAR/bin/pip
```

Stop using the virtual env: `deactivate` leaves the virtual env:


```
(ENV_FOOBAR)~/Temp/ENV_FOOBAR $ deactivate
```

#### Create Python3 virtual env:

*dependency: Brew installed Python3 already*

```
$ virtualenv -p /usr/local/bin/python3 ENV_ANOTHER_PYTHON3
Running virtualenv with interpreter /usr/local/bin/python3
Using base prefix '/usr/local/Cellar/python3/3.4.3/Frameworks/Python.framework/Versions/3.4'
New python executable in ENV_ANOTHER_PYTHON3/bin/python3.4
Also creating executable in ENV_ANOTHER_PYTHON3/bin/python
Installing setuptools, pip...done.
```

Python Call Graph in virtual env:

```
$ bin/pycallgraph graphviz -- foo.py
```

___

#### Update `pip` 

```
$ pip install --upgrade pip
```

#### iPython

```
$ pip3 install ipython[all]
```



