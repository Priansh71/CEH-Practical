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
