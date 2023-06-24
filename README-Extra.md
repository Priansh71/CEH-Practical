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


## Enumeration
<details>
    <summary>Enumeration</summary>

 ### 1) NetBios Enumeration
#### Tool: Global Network Inventory
- Audit Scan Mode >> Select IP range >> Authentication setting >> connect as windows 12(victim) server using credentials that is currently logged on
- The Scan Summary tab displays a brief summary of machine that has been scanned. It will shows you the Machine name, MAC Address, OS installed, and etc.
- User groups,Services,Installed Softwares etc can be seen in the scan summmary.
  
### 2) Network Resources
#### Tool: Advanced IP Scanner  
- Enumerate network resources using Advanced IP Scanner.
- Perform a system ard network scan, Enumerate user accounts, Execute remotepenetration, Gather information about local network
- Input range of IP
- Now you have the IP address, Name, MAC address, and Manufacturer information of the victim machine.

### 3) Network enum using superscan
#### Tool: Superscan
- Lists of computers that belong to a domain
- Lists Of shares on the individual hosts on the network
- Policies and passwords
- Enter hostname/IP/URL >> select Enumeration type >> and see the scan result for required information.

### 4) Resurces in Local machine
#### Tool: Hyena
- Click '+' node of local workstation to expand section.
- select different nodes to view their information
- Users, Services, User Rights, Scheduled jobs

 ### 5) SMB ENumeration
#### Tools: nbstat,nmap

- In windows 12
```bash
nmap -O <win-12-ip>
```

```bash
nbstat -A xx.xx.xx.xx  //perform nbstat scan on port 139 in cmd
net use
net use \\xx.xx.xx.xx\e ""\user:""
net use \\xx.xx.xx.16\e""/user:""  //create null session 
// xx.xx.xx.16 is windows server 16
```
- disconnect drive Z
-this creates a null session 
- confirm by using
```bash
net use // session with name e would have been created
```


##### Note: Your first target is the computer with a Windows OS on which you can see ports 139 and 445 open. Remember, this usually works only against Windows but may partially succeed if other OSs have these ports open. There may be more than one system with NetBIOS open. You see that ports 135. 139.445. etc. are open and port 139 is using NetBIOS.

  ### 6) Some other tools
#### Tools:
- NetBIOS Enumerator
- SoftPerfect Network Scanner

</details>
