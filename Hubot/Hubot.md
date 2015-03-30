
#### Send commannds to Hubot at startup

[https://github.com/github/hubot/issues/613](https://github.com/github/hubot/issues/613)

```
expect -c 'spawn bin/hubot;sleep 5;expect "Hubot> ";send "\$ roll 3d6\n";expect eof'
```

```
expect -c 'spawn bin/hubot;sleep 1;expect "Hubot> ";sleep 3;send "hubot help\n";expect eof'
```