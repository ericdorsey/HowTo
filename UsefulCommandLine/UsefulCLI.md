

### Disable / Enable AirDrop 

Turn AirDrop off:

```defaults write com.apple.NetworkBrowser DisableAirDrop -bool YES```

Turn AirDrop back on:

```defaults write com.apple.NetworkBrowser DisableAirDrop -bool NO```

You’ll need to logout and log back in to see the changes.

___

### Recursive ```grep``` for text "foo" from current folder down

```
$ grep -r "foo" .
```
___

### Pull matching URLs (using ```grep```) from one file, output to another:

```
$ grep -oE '\b(https?|ftp|file)://[-A-Za-z0-9+&@#/%?=~_|!:,.;]*[-A-Za-z0-9+&@#/%=~_|]' orginalFile.txt > outputFile.txt
```

___

### Safely use ```rm``` 

Use the ```-i``` confirmation flag when running ```rm``` commands. From ```$ man rm```:

```
-i          Request confirmation before attempting to remove each file, regardless of the file's per-
                 missions, or whether or not the standard input device is a terminal.  The -i option over-
                 rides any previous -f options.
```

When deleting folders recursively w/ subfolders, run ```$ rm -rfi``` and get prompted for each file:

```
~/Temp $ ls temp123/
derp2.html   foo.test.bak testfoo.foo

~/Temp $ rm -rfi temp123/
examine files in directory temp123/? y
remove temp123//derp2.html? y
remove temp123//foo.test.bak? y
remove temp123//testfoo.foo? y
remove temp123/? y
~/Temp $
```
___
### Shortcut Keys

```
Ctrl
----
Ctrl + A:  Go to the beginning of the line you are currently typing on 
Ctrl + E:  Go to the end of the line you are currently typing on 
Ctrl + L: Clears the Screen, similar to the clear command 
Ctrl + U; Clears the line before the cursor position. If you are at the end of the line, clears the entire line. 
Ctrl + H Same as backspace 
Ctrl + R: Let's you search through previously used commands 
Ctrl + C Kill whatever you are running 
Ctrl + D Exit the current shell 
Ctrl + Z Puts whatever you are running into a suspended background process. fg restores it. 
Ctrl + W Delete the word before the cursor 
Ctrl + K Clear the line after the cursor 
Ctrl + T Swap the last two characters before the cursor 

Esc
----
Esc + T Swap the last two words before the cursor 
Esc + F Forward one word 
Esc + B Backward one word
Esc + Delete Delete word to left of cursor
```
