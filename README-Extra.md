## Footprinting and Reconnaissance
<details>
    <summary> Reconnasiance/Footprinting</summary>
<details>
    <summary> 1) Windows CLI tools </summary>

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


### 2)Edit,Debug and monitor
<details>
    <summary> 2)Firebug </summary>
- Firebug extension Integrated with Firefox
</details>

### 3)Mirroring website:
<details>
    <summary> Mirroring</summary>
    
- Windows: HTTrack

- Linux: wget
```bash
 $ wget <url-of-website>
``` 
#### Note:- check wget -h for options

</details>

### 4)Advance route tracing 
#### Tool: Path Analyzer Pro

<details>
    <summary> 5)Information Gathering Using Metasploit</summary>

#### Extract accurate information about a network using Metasploit Framework.

```bash
$ service postgresql start
```
```bash
In msf type 
$db_status
```
If error then exit and type below commands
- To initialize database
```
$ msfdb init
```
```
$ service postgresql start
```
relaunch metasploit Framework
```
$ msfconsole
$ db_status
$ nmap -Pn -sS -A -oX <output_file> <subnet(xx.xx.xx.x/24)>
```
you can use different options and also remove some options
```
$ hosts
```
to get host information

```
$ use auxilliary/scanner/smb/smb_version
or 
$ use /scanner/smb/smb_version
$ show options
$ set RHOSTS xx.xx.xx.8-16
$ set THREADS 1000
$ run 
```
- Now you can see the os_flavor 
- Hence Extracted information about network using metasploit
</details>
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
