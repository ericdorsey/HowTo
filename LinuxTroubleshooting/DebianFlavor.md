
```
eha@pfreya:/tmp$ sudo cron restart
cron: can't lock /var/run/crond.pid, otherpid may be 970: Resource temporarily unavailable
```

```
eha@pfreya:/tmp$ sudo /etc/init.d/cron restart
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service cron restart
Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) and then start(8) utilities,
e.g. stop cron ; start cron. The restart(8) utility is also available.
cron stop/waiting
cron start/running, process 2899
eha@pfreya:/tmp$ ps aux | grep cron
root      2899  0.0  0.0  23652  1020 ?        Ss   09:13   0:00 cron
```

