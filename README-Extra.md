## Footprinting and Reconnaissance
### Tools
- Windows CLI tools
```console
$ Ping <ip>
$ nslookup <domain.com>
$ tracert  <ip>
```

<details>
    <summary> 1)Windows CLI tools </summary>

```bash
$ ping <ip>
 or 
$ ping www.domain.com
```
````console
$ ping <host-ip> -f -l 1300
````
```bash
$ nslookup <domain.com>
```
```bash
$ tracert <doamin>

$ traceroute <host-ip>
```
</details>

### Reconnasiance/Footprinting
<details>
  <summary>Recon</summary>

- -r range , Scan Entire Network for ALive host using ARP
```console
$ netdiscover -r 192.168.29.1/24
```
</details>



## Scanning Networks
<details>
    <summary>Scanning Networks</summary
- Port Scanning using Hping3:

```bash
hping3 --scan 1-3000 -S 10.10.10.10
```
--scan parameter defines the port range to scan and –S represents SYN flag.

- Pinging the target using HPing3:
```
hping3 -c 3 10.10.10.10
```
-c 3 means that we only want to send three packets to the target machine.

- UDP Packet Crafting
```
hping3 10.10.10.10 --udp --rand-source --data 500
```
- TCP SYN request
```
hping3 -S 10.10.10.10 -p 80 -c 5
```
-S will perform TCP SYN request on the target machine, -p will pass the traffic through which port is assigned, and -c is the count of the packets sent to the Target machine.

- HPing flood
```
hping3 10.10.10.10 --flood
``` 
</details>
