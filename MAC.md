## Links
* [Startup key combinations](https://support.apple.com/en-us/HT201255)
* [QuickLook plugins](https://github.com/sindresorhus/quick-look-plugins)
* Find duplicates: [Disk Drill](https://www.cleverfiles.com/disk-drill-mac.html)
* [Find Empty Folders](http://www.tempel.org/FindEmptyFolders) but also ```find . -type d -empty -delete```
* [Knock Knock](https://objective-see.com/products/knockknock.html) like autoruns
* [Task explorer](https://objective-see.com/products/taskexplorer.html) like procmon and filemon
* [Rectangle app](https://rectangleapp.com/) window move/resize, alternatives to sizeUp
* [Things 3 export](https://github.com/thingsapi/things-cli)

## Reset the System Management Controller (SMC)
From [link](https://www.makeuseof.com/tag/reset-macs-smc-pram/), reset the SMC on a pre-2018 MacBook with a non-removable battery:
* Shut down your Mac.
* Press and hold Shift, Control, Option on the left side of the keyboard.
* Now press and hold the Power button as well.
* Hold all the keys down for 10 seconds.
* Release all the keys and turn on your MacBook.

## Reset PRAM/NVRAM
PRAM (parameter random access memory) and NVRAM (non-volatile random access memory) hold information about the configuration of a Mac.

#### From command line ([link](https://apple.stackexchange.com/questions/354627/resetting-pram-through-terminal))
```sudo nvram -c```

#### Startup key combination ([link](https://www.makeuseof.com/tag/reset-macs-smc-pram/))
* Shut down your Mac.
* Press the power button.
* Before the grey screen appears, press the Command, Option, P, and R keys at the same time.
* Hold the keys until your computer restarts and you hear the startup sound a second time.
* On Macs with the T2 Security Chip, hold the keys until the Apple logo appears and disappears for the second time.
* Release the keys.

## Disable DEP notifications
References:
* [Turning off Device Enrollment Notifications on MacBook Pro - Ask Different](https://apple.stackexchange.com/questions/297293/turning-off-device-enrollment-notifications-on-macbook-pro)
* [Disable Device Enrollment Notification on Mac.md](https://gist.github.com/sghiassy/a3927405cf4ffe81242f4ecb01c382ac)
* [Disable Device Enrollment Program (DEP) notification on macOS Catalina.md](https://gist.github.com/henrik242/65d26a7deca30bdb9828e183809690bd)

On Big Sur, to Disable MDM (Device Enrollment) notifications:
* Restart in Recovery Mode (Command+R)
* From Utilities: Startup Security Utility
* A 3-choices popup appears: select (No security). Note: not the case for me, but does not appear to be essential
* Restart again in Recovery Mode (Command+R)
* Run “mount” in Terminal from Utilities
* Write down the disk associated with /Volumes/Macintosh HD (mine was /dev/disk2s5)
* umount /Volumes/Macintosh\ HD
* mkdir /Volumes/Macintosh\ HD
* then: mount -t apfs -rw /dev/disk2s5 /Volumes/Macintosh\ HD
* cd /Volumes/Macintosh\ HD/System/Library/LaunchAgents
* mkdir disabled
* mv com.apple.ManagedClientAgent.* disabled/
* mv com.apple.mdmclient.* disabled/
* cd ../LaunchDaemons
* mkdir disabled
* mv com.apple.ManagedClient.* disabled/
* mv com.apple.mdmclient.* disabled/
* csrutil authenticated-root disable (this will turn off Signed System Volume SSV, preventing FileVault)
* bless —folder /Volumes/Macintosh\ HD/System/Library/CoreServices —bootefi —create-snapshot
* reboot
* not strictly necessary, but add these to hosts:
```
0.0.0.0 iprofiles.apple.com
0.0.0.0 mdmenrollment.apple.com
0.0.0.0 deviceenrollment.apple.com
0.0.0.0 gdmf.apple.com
```
If you ever reset PRAM, you need to boot again into recovery and disable authenticated-root.

It is not going to boot otherwise, since the startup disk has been tampered with.

## Show/hide files on Mac
* Reveal in Finder / Open dialog: ```Command+Shift+Period```
* Reveal permanently in Finder: ```defaults write com.apple.Finder AppleShowAllFiles true```, ```killall Finder```
* Hide/Reveal, method 1: ```mv filename .filename``` and ```mv .filename filename```
* Hide/Reveal, method 2: ```chflags hidden filename``` and ```chflags nohidden filename```
* Hide/Reveal, method 3: ```SetFile -a V filename``` and ```SetFile -a v filename```
* Reveal, method 4: ```xattr -d com.apple.FinderInfo filename```

Security through obscurity, [unicode lookalikes](https://gist.github.com/StevenACoffman/a5f6f682d94e38ed804182dc2693ed4b): aceijopxy ~= асеіјорху
