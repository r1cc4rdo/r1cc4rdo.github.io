**r1cc4rdo.github.io** :: [website](https://r1cc4rdo.github.io/) :: [repo](https://github.com/r1cc4rdo/r1cc4rdo.github.io) :: [help](https://pages.github.com/) :: [docs](https://help.github.com/en/categories/working-with-github-pages)

### Networking
* [FreePN](https://www.freepn.org/) VPN service
* Transfer files / drop / share: [wormhole.app](https://wormhole.app/) :: [drop.lol](https://drop.lol/) :: [sharedrop.io](https://www.sharedrop.io/) :: [WeTransfer](https://wetransfer.com/)
* [mitmproxy](https://mitmproxy.org): Man In The Middle Proxy
* NAT piercing / ssh tunnel: [patchbay](https://patchbay.pub/) :: [ngrok](https://ngrok.com/) :: [Spork](https://spork.sh/)
* [WiFi pentesting](WIFI.md)

### Tools
* [12ft Ladder](https://12ft.io/): Bypass paywalls. See also: [github](https://github.com/iamadamdev/bypass-paywalls-chrome)
* Bootable USB Creators: [YUMI](https://www.pendrivelinux.com/yumi-multiboot-usb-creator/), [Ventoy](https://ventoy.net/en/download.html), [UNetbootin](https://unetbootin.github.io/), [Rufus](https://rufus.ie/en/)
* [htmlq](https://github.com/mgdm/htmlq): like jq, but for HTML
* Paper backups: [paperback](https://github.com/cyphar/paperback) :: [paperback-cli](https://github.com/Wikinaut/paperback-cli)
* Wall art generator: [Rasterbator](https://rasterbator.net/)
* [Youtube Downloader](https://yt1s.com)

### HowTo

#### Copy with rsync
```
rsync -avzhP src dest

a archive
v verbose
z compress in flight 
h human-readable
P keep partially transferred files and show progress
```
Use ```—append``` to resume files. Will do checksum, and resend on failure.

Use ```-e “ssh -i path/to/key.pem”``` to provide an identity. See [link](https://unix.stackexchange.com/questions/127352/specify-identity-file-id-rsa-with-rsync)

#### Add local admin from Windows cmdline
```
net user USER PASS /add
net localgroup administrators USER /add
```
then login as COMPUTERNAME\USER
