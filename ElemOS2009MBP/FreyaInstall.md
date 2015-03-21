# Elementary OS (Freya) on 2009 MacBook Pro

* [http://www.rodsbooks.com/refind/linux.html#efistub](http://www.rodsbooks.com/refind/linux.html#efistub)
* [http://www.rodsbooks.com/refind/installing.html#installsh](http://www.rodsbooks.com/refind/installing.html#installsh)
* [http://elementary.io/support](http://elementary.io/support)

___

### System freeze on boot
```nomodeset``` issue,

From:
[http://sourceforge.net/p/refind/discussion/general/thread/c30a6920/](http://sourceforge.net/p/refind/discussion/general/thread/c30a6920/)

Running a 2009 Macbook Pro with Elementary OS (Freya).

rEFInd correctly sees both OSX and Linux 3.13.0-46-generic.

On boot, system freezes at line "EFI VGA driver issue" unless I:

* Highlight Linux 3.13.0-46-generic
* Hit F2 - I see "Boot with normal options, boot into single user mode, return to main menu"
* Hit F2 again - I see the rEFInd Line Editor
* On the rEFInd Line Editor, I leave everything default, except at the end I add " nomodeset" and hit enter. Elementary OS boots fine after.

I want to make ```nomodeset``` a permanent, automatic argument to this Linux kernel booting. How can I accomplish this?

Googling indicates there should be a way with either ```refind.conf``` or ```linux_refind.conf```, but I don't have either one of these files.

* Do I have to create them myself? 
* And if so, where do I put them? /boot/ ...? somewhere else?
* Where do I see / edit the current rEFInd menu options like "boot with normal.." etc?

___

So.. kind of hacked this workaround together and it's working (and by working, I mean this "overwrites" the default boot options that were created by rEFInd, and it successfully automatically passes the nomodeset argument), but wondering if there is a way to tell rEFIind to use a grub config or something more.. stable? This will break on next kernel upgrade as I'm manually entering the UUID. Nevertheless, here's what I did:

* On the Elementary (Freya) partition, in
/boot
I created a ```refind_linux.conf``` file:

```
/boot $ touch refind_linux.conf
```

Added to ```refind_linx.conf```:

```
"My New Menu Option" "ro root=UUID={my unique UUID here} intird=boot\initrd.img-3.13.0-46-generic nomodeset"
```

Would definitely like to know the right way to do all this, though?

___

> You did it right, EXCEPT that you should omit the ```intird=boot\initrd.img-3.13.0-46-generic``` part. rEFInd can figure out which initrd file to link to which kernel, based on their version strings, so you don't need to include such a specification unless you deviate from the normal (for most distributions) naming of initrd files.
 
> Incidentally, the ```mkrlconf.sh``` script that comes with rEFInd will create a ```/boot/refind_linux.conf``` file. It would probably omit the necessary nomodeset option, but you can always add that back. If you were to run it now, it would refuse to create a new file because one already exists, but you could rename yours beforehand or use the ```--force``` option to force it to do so. --[Roderick W. Smith](https://sourceforge.net/u/srs5694/profile/)

Above reply worked. 
___

### Re-run rEFInd installer in Elementary
Previously had run this in OSX, but it didn't create any folder structure under ```/boot/```, running again inside Elementary it created ```/boot/efi/EFI/BOOT```

```
eha@pfreya:~/refind-bin-0.8.7$ pwd
/home/eha/refind-bin-0.8.7
eha@pfreya:~/refind-bin-0.8.7$ ls -la
total 228
drwxrwxr-x  7 501 dialout  4096 Mar 15 12:12 .
drwxr-xr-x 20 eha eha      4096 Mar 15 14:55 ..
drwxr-xr-x  3 501 dialout  4096 Feb  8 12:07 banners
-rw-r--r--  1 501 dialout 35147 Sep 17  2012 COPYING.txt
-rw-r--r--  1 501 dialout  5846 Feb  4 13:31 CREDITS.txt
drwxr-xr-x  4 501 dialout  4096 Aug 12  2013 docs
-rw-r--r--  1 501 dialout 12292 Mar 15 12:12 .DS_Store
drwxr-xr-x  2 501 dialout  4096 May 13  2014 fonts
-rwxr-xr-x  1 501 dialout 44093 Mar  1 18:54 install.sh
drwxr-xr-x  2 501 dialout  4096 Feb 15 16:13 keys
-rw-r--r--  1 501 dialout  2204 Sep 17  2012 LICENSE.txt
-rwxr-xr-x  1 501 dialout  1773 Dec 18  2013 mkrlconf.sh
-rwxr-xr-x  1 501 dialout  9361 Jan  5  2013 mvrefind.sh
-rw-r--r--  1 501 dialout 66551 Mar  1 17:58 NEWS.txt
-rw-r--r--  1 501 dialout  3924 Jan  6  2013 README.txt
drwxrwxr-x  7 501 dialout  4096 Mar 15 12:18 refind
-rw-r--r--  1 501 dialout   834 Mar 15 11:47 refindInstall.txt

 $ sudo ./install.sh 
```
___
### Install GVim

```
 $ sudo apt-get install gvim
```


### Install Node Package Manager
```
$ sudo apt-get install npm
``` 

### Install Remarkable 
What: Markdown editor

```
 $ npm install remarkable --save
 
```

### Install Python ```pip```

```
 $ sudo apt-get install python-pip
```

### Python Beautiful Soup

```
 $ pip install BeautifulSoup4
```

### Python header files 

```
 $ sudo apt-get install python-dev
``` 

### Fix / Repair ```apt-get``` dependencies

```
$ sudo apt-get -f install
```

### Install Git

```
$ sudo apt-get install git

```
___
### Static IP

*Note that DHCP worked by default w/ no config*

```
sudo gvim /etc/network/interfaces

```

Added the ```auto eth0``` text:

```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.30
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1

```

```
$ sudo /etc/init.d/networking restart
```

___

### Automatic updates at 4AM

Create ```Auto.sh```:
```
#!/bin/bash
# Runs every day at 4AM, see root crontab
# /var/log/apt/term.log
# /var/log/dpkg.log
myDate=$(date +"%Y-%m-%d | %r")
updateString="'apt-get update -y' and 'apt-get upgrade -y' ran | $myDate"
echo $updateString >> /home/eha/Code/AutoUpdates/log/AutoUpdate.log 
#echo $updateString
apt-get update -y && apt-get-upgrade -y

```

Add entry in ```root``` crontab:

```
0 4 * * * /home/eha/Code/AutoUpdates/Auto.sh
```

___

### Kill Bluetooth
From [http://askubuntu.com/questions/67758/how-can-i-deactivate-bluetooth-on-system-startup](http://askubuntu.com/questions/67758/how-can-i-deactivate-bluetooth-on-system-startup)

Makes bluetooth icon in upper right menu off by default on boot. 

Add:

```
$ sudo gvim /etc/rc.local
```

```
rfkill block bluetooth
```
