- [ ] Reset SMC
- [ ] Reset PRAM/NVRAM
- [ ] Startup key combinations
- [ ] Disable DEP notifications
- [ ] QuickLook tools/plugins
- [ ] Remove duplicates / empty folders
- [ ] Raspberry Pi Time Machine
- [ ] Security powertools
- [ ] Show/hide files on Mac
- [ ] Rectangle window move/resize
- [ ] Things 3

Reset SMC

Smc == system management controller
See: https://www.makeuseof.com/tag/reset-macs-smc-pram/
To reset the SMC on a MacBook with a non-removable battery (pre-2018):

- [ ] Shut down your Mac.
- [ ] Press and hold Shift, Control, Option on the left side of the keyboard.
- [ ] Now press and hold the Power button as well.
- [ ] Hold all the keys down for 10 seconds.
- [ ] Release all the keys and turn on your MacBook.

Reset PRAM/NVRAM

PRAM (parameter random access memory) and NVRAM (non-volatile random access memory) hold information about the configuration of a Mac.
https://www.makeuseof.com/tag/reset-macs-smc-pram/

From command line: ```sudo nvram -c```
From https://apple.stackexchange.com/questions/354627/resetting-pram-through-terminal

- [ ] Shut down your Mac.
- [ ] Press the power button.
- [ ] Before the grey screen appears, press the Command, Option, P, and R keys at the same time.
- [ ] Hold the keys until your computer restarts and you hear the startup sound a second time.
- [ ] On Macs with the T2 Security Chip, hold the keys until the Apple logo appears and disappears for the second time.
- [ ] Release the keys.

Startup key combinations

https://support.apple.com/en-us/HT201255

Disable DEP notifications

On Big Sur, to Disable MDM (Device Enrollment) notifications:

Turning off Device Enrollment Notifications on MacBook Pro - Ask Different
https://apple.stackexchange.com/questions/297293/turning-off-device-enrollment-notifications-on-macbook-pro

Disable Device Enrollment Notification on Mac.md
https://gist.github.com/sghiassy/a3927405cf4ffe81242f4ecb01c382ac

Disable Device Enrollment Program (DEP) notification on macOS Catalina.md
https://gist.github.com/henrik242/65d26a7deca30bdb9828e183809690bd

Not sure if necessary, but also add to hosts:
0.0.0.0 iprofiles.apple.com
0.0.0.0 mdmenrollment.apple.com
0.0.0.0 deviceenrollment.apple.com
0.0.0.0 gdmf.apple.com

- [ ] Restart in Recovery Mode (Command+R)
- [ ] From Utilities: Startup Security Utility
- [ ] A 3-choices popup appears: select (No security). Note: not the case for me, but does not appear to be essential
- [ ] Restart again in Recovery Mode (Command+R)
- [ ] Run “mount” in Terminal from Utilities
- [ ] Write down the disk associated with /Volumes/Macintosh HD (mine was /dev/disk2s5)
- [ ] umount /Volumes/Macintosh\ HD
- [ ] mkdir /Volumes/Macintosh\ HD
- [ ] then: mount -t apfs -rw /dev/disk2s5 /Volumes/Macintosh\ HD
- [ ] cd /Volumes/Macintosh\ HD/System/Library/LaunchAgents
- [ ] mkdir disabled
- [ ] mv com.apple.ManagedClientAgent.* disabled/
- [ ] mv com.apple.mdmclient.* disabled/
- [ ] cd ../LaunchDaemons
- [ ] mkdir disabled
- [ ] mv com.apple.ManagedClient.* disabled/
- [ ] mv com.apple.mdmclient.* disabled/
- [ ] csrutil authenticated-root disable (this will turn off Signed System Volume SSV, preventing FileVault)
- [ ] bless —folder /Volumes/Macintosh\ HD/System/Library/CoreServices —bootefi —create-snapshot
- [ ] reboot
- [ ] if you reset PRAM, you need to boot again into recovery and disable authenticated-root. It is not going to boot otherwise, since the startup disk has been tampered with

QuickLook tools/plugins

https://github.com/sindresorhus/quick-look-plugins
brew cask install qlcolorcode qlstephen qlmarkdown quicklook-json qlimagesize suspicious-package quicklookase qlvideo

See also https://www.quicklookplugins.com/

Remove duplicates / empty folders

Find duplicates:
Disk Drill https://www.cleverfiles.com/disk-drill-mac.html

Remove empty folders:
Find Empty Folders http://www.tempel.org/FindEmptyFolders
From command line: ```find . -type d -empty -delete```

Raspberry Pi Time Machine

https://gregology.net/2018/09/raspberry-pi-time-machine/

ssh pi@rpi-capsule.local
afp://rpi-capsule

Security powertools

https://objective-see.com/products.html

Knock Knock: startup explorer
Task manager: explore dylibs, files, network

Show/hide files on Mac

Reveal in Finder / Open dialog:
Press Command+Shift+Period

Reveal permanently in Finder:
> defaults write com.apple.Finder AppleShowAllFiles true
> killall Finder

Hide/Reveal in Finder, method 1:
> mv filename .filename
> mv .filename filename

Hide/Reveal in Finder, method 2:
> chflags hidden filename
> chflags nohidden filename

Hide/Reveal in Finder, method 3:
> SetFile -a V filename
> SetFile -a v filename

If you fail to reveal:
xattr -d com.apple.FinderInfo filename

Security through obscurity, unicode lookalikes:
https://gist.github.com/StevenACoffman/a5f6f682d94e38ed804182dc2693ed4b

Rectangle window move/resize

https://rectangleapp.com/

Things 3

[Add entries]

Email: add-to-things-4u8xhujspb4368kfcu6@things.email
URLs: https://support.culturedcode.com/customer/en/portal/articles/2803573

[Export database db]

https://github.com/AlexanderWillner/things.sh
https://github.com/AlexanderWillner/KanbanView
https://gist.github.com/RaVbaker/7004732
https://sqlitebrowser.org/dl/

[Alternatives]

Microsoft TODO https://todo.microsoft.com/
Notion https://www.notion.so/
