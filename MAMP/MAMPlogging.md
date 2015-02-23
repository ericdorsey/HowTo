# Configure MAMP logging
**Objective:**  
Turn on Apache access log, and configure a Virtual Host access and error log.

Instructions for OSX.

### Enable and Configure the Apache Acess Log
MAMP has this disabled by default. Creates log of Apache ```GET``` and ```POST``` requests.

Open ```/Applications/MAMP/conf/apache/httpd.conf```, find the  ```#CustomLog "/Applications/MAMP/logs/apache_access.log" common``` line. We're not going to uncomment this one, but will instead create our own custom line. 

Insert a new line, referencing the default log location, ```/Applications/MAMP/logs/```:

```
# If you prefer a logfile with access, agent, and referer information
# (Combined Logfile Format) you can use the following directive.
  
CustomLog /Applications/MAMP/logs/apache_access_log.log combined

```

Of note, the **error** logs are turned on by default for Apache, MySQL and PHP:

```
/Applications/MAMP/logs $ ls -1
apache_error.log
mysql_error_log.err
php_error.log
```

### Configure Access & Error Logging for a Virtual Host

Open ```/Applications/MAMP/conf/apache/extra/httpd-vhosts.conf```. Configure the ```ErrorLog``` and ```CustomLog``` for your Virtual Host. In this example, they are both configured to go to the specific project, but you could set each to go to the main Apache log location, ```/Applications/MAMP/logs``` if you want your Virtual Hosts logs mixed in with your default logs.

```
<VirtualHost *:8888>
    ServerAdmin webmaster@golfcard
    DocumentRoot "/Users/my/local/path"
    ServerName golfcard.local
    ErrorLog /Users/my/local/path/logs/apache_error.log
    CustomLog /Users/my/local/path/logs/apache_access.log combined
</VirtualHost>
```
### Restart MAMP Apache:  
```
/Applications/MAMP/bin/apache2/bin/apachectl stop
```

**MAMP Stopped:**
![MAMP stopped](images/MAMP_ApacheStopped.png)

```
/Applications/MAMP/bin/apache2/bin/apachectl start
```

**MAMP Started:**
![MAMP started](images/MAMP_ApacheStarted.png)

### View logs

View logs in the locations you set in your ```CustomLog``` and ```ErrorLog``` definitions above. 

