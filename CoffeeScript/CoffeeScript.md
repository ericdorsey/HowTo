
[http://coffeescript.org/](http://coffeescript.org/)

#### Coffeee REPL

```
$ coffee
```

Multi line within REPL. Use `ctrl-v`, must use 4 spaces for indent:

```
coffee> pets = ["foo", "bar", "blah"]
[ 'foo', 'bar', 'blah' ]
------> for pet, index in pets
.......     console.log pet, index
foo 0
bar 1
blah 2
```