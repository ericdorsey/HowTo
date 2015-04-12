### Disable / Enable AirDrop 

Turn AirDrop off:

```defaults write com.apple.NetworkBrowser DisableAirDrop -bool YES```

Turn AirDrop back on:

```defaults write com.apple.NetworkBrowser DisableAirDrop -bool NO```

You’ll need to logout and log back in to see the changes.

___

### OSX Version

```
$ sw_vers
ProductName:	Mac OS X
ProductVersion:	10.10.2
BuildVersion:	14C1510
```

___

#### Paste from clipboard into a file 

```
$ pbpaste > foo.txt
```

