<div align="center">

# [ NMAP ]

### COMPLETE STUDY GUIDE

**Beginner → Intermediate → Advanced**

---

## Network Mapper — The Complete Command Reference

*English + Tanglish (Tamil in English Script)*
### prashanth baskaran
</div>

<div align="center">
  
| TOPIC | DETAILS |
|-----|-----|
| Tool Name | Nmap (Network Mapper) |
| Purpose | Network Discovery & Security Auditing |
| Level | Beginner → Advanced |
| Language | English + Tanglish |
| Total Chapters | 10 Chapters + Quick Reference |
</div>

- ##### FOR EDUCATIONAL PURPOSES ONLY — USE ETHICALLY & LEGALLY

Ethical use pannunga — authorized systems-la matum use pannunga!

-----

## TABLE OF CONTENTS
-----

[1] What is Nmap?

 → Nmap enna?

[2] Installation & Setup

   → Install panni setup panrathu

[3] Basic Scanning (Beginner)

   → Basic scan — Beginners ku

[4] Host Discovery

 → Host kandupidikkirathu

[5] Port Scanning Techniques

 → Port scan techniques

[6] Service & Version Detection

 → Service version kandupidikkirathu

[7] OS Detection

 → Operating System detection

[8] Nmap Scripting Engine (NSE)

 → NSE — Advanced scripting

[9] Evasion & Firewall Bypass

 → Firewall bypass techniques

[10] Output & Reporting

 → Results save panrathu

[★] Quick Reference Card

 → Ellaa commands oru pagela

-----
### CHAPTER 1: WHAT IS NMAP?
Nmap enna? Enna pannum?

Nmap (Network Mapper) is a free, open-source tool used for network discovery and security auditing. It was created by
Gordon Lyon (Fyodor) in 1997. Nmap sends specially crafted packets to target hosts and analyzes the responses to
determine what hosts are available, what services they are running, what operating systems are in use, and what type of
firewalls are deployed

> → Nmap oru free open-source tool. Itha use panni network-la irukkira computers, ports, services ellaam kandupidikkalaam.
1997-la Gordon Lyon create pannaar. Packet anuppi response analyze pannitu information collect pannum.
> 
KEY USES: Port scanning, Host discovery, Service/version detection, OS fingerprinting, Vulnerability scanning (with
NSE scripts), Network inventory, Security auditing.
> → Nmap use pannuvom: port scan, host discover, service version check, OS kandupidi, vulnerability scan, network audit —
ellaamey Nmap-la possible!
>
### WHY LEARN NMAP?
Nmap ethukku karkanum?
Nmap is the #1 tool used by ethical hackers, penetration testers, network admins, and security researchers worldwide. It
is pre-installed in Kali Linux, Parrot OS, and many security distributions. CompTIA Security+, CEH, and OSCP
certifications all test Nmap knowledge.
> → Ethical hackers, pen testers, network admins — ellaarum Nmap use pannuvaanga. Kali Linux-la default-aa varum. CEH,
OSCP exams-la Nmap questions varum — must learn!
-----
### CHAPTER 2: INSTALLATION & SETUP
Install panni setup panrathu
#### Installing on Linux
Linux-la install panrathu

|Command|Description (EN)|Tanglish|
|---|---|---|
|sudo apt install nmap |Install Nmap on Debian/Ubuntu |Ubuntu/Kali-la install pannum|
|sudo yum install nmap |Install on RHEL/CentOS |CentOS-la install pannum|
|sudo pacman -S nmap |Install on Arch Linux |Arch Linux-la install pannum|
|nmap --version |Check installed version |Version check pannu|
|which nmap |Find nmap location |Nmap path kandupidi|

### Installing on Windows & Mac
Windows / Mac-la install panrathu
Windows: Download installer from https://nmap.org/download.html — includes Zenmap GUI. macOS: Use Homebrew →
brew install nmap OR download .dmg from nmap.org
> → Windows-la nmap.org-la irundhu installer download pannu — Zenmap GUI vaarum. Mac-la homebrew use panni 'brew
install nmap' nu type pannu.
---
### CHAPTER 3: BASIC SCANNING — BEGINNER LEVEL
Basic Scanning — Beginners ku

### The Most Basic Scans
Miga basic scan commands

|Command |Description (EN) |Tanglish|
|---|---|---|
|nmap <target> |Default scan (top 1000 ports, SYN scan as root) |Basic default scan — top 1000 ports check pannum|
|nmap 192.168.1.1 |Scan a single IP address |Oru IP address scan pannu|
|nmap google.com |Scan a domain/hostname |Domain name kuduthu scan pannu|
|nmap 192.168.1.1-50 |Scan IP range |IP range scan — 1 to 50 check pannum|
|nmap 192.168.1.0/24 |Scan entire subnet (CIDR) |Entire subnet scan — /24 = 256 hosts|
|nmap 192.168.1.1 192.168.1.5 |Scan multiple specific IPs |Multiple IP scan — space-la separate pannunga|
|nmap -iL targets.txt |Scan IPs from a file |File-la irukira IP list scan pannum|
|nmap --exclude 192.168.1.5 |Exclude specific host from scan |Oru host-a skip panni scan pannum|

- ### Understanding Ports
Ports pathi therinjukkanum

Ports are like doors on a computer. There are 65,535 total ports. Well-known ports (0-1023): 80=HTTP, 443=HTTPS,
22=SSH, 21=FTP, 25=SMTP, 3306=MySQL. Registered ports (1024-49151), Dynamic ports (49152-65535)
> → Ports computer-oda doors madhiri. M■■■■■■ 65,535 ports irukkum. 80=HTTP, 443=HTTPS, 22=SSH, 21=FTP — intha
ports ellaarum therinjukkanum!

- ### Port State Meanings
  Port state-oda artham

|State |Meaning (EN) |Tanglish|
|---|---|---|
|open |Port is accepting connections | Port open — service running irukkum |
|closed | Port reachable but no service | Port respond pannum but service illa
|filtered | Firewall blocking — no response | Firewall block pannuduchu — response varalai
|unfiltered | Port reachable but state unknown | Reachable but open/closed theriyala
|open filtered | — unclear | Open-aa filtered-aa confirm illa
|closed filtered | Either closed or filtered | Closed-aa filtered-aa confirm illa
---
### CHAPTER 4: HOST DISCOVERY
Network-la irukkira hosts kandupidikkirathu

#### Before scanning ports, Nmap tries to discover which hosts are online. This is called 'host discovery' or 'ping scan'. It's
the first step in any network recon.

- → Port scan pannum munnaadi, etha hosts online-la irukkaanga nu kandupidikkanam. Intha process-ku 'Host Discovery' nu
peru. Network recon-la first step idhu.

|Command |Description (EN) |Tanglish |
|---|---|---|
|nmap -sn 192.168.1.0/24 |ing scan — no port scan, just host discovery |Ports scan panna maatan — hosts matum ka |
|nmap -Pn 192.168.1.1 |Skip host discovery — treat host as online |Ping panna maatan — direct port scan pann |
|nmap -PS 192.168.1.1 |TCP SYN ping to port 80 |CP SYN ping — port 80-ku anuppu |
|nmap -PS22,80,443 |TCP SYN ping on multiple ports |Multiple ports-ku SYN ping anuppu |
|nmap -PA 192.168.1.1 |TCP ACK ping (bypass firewalls) |ACK ping — firewall bypass ku useful |
|nmap -PU 192.168.1.1 |UDP ping discovery |UDP protocol use panni ping pannu |
|nmap -PE 192.168.1.0/24 |ICMP echo request (traditional ping) |Traditional ICMP ping — normal ping madhiri |
|nmap -PP 192.168.1.0/24 |ICMP timestamp ping |ICMP timestamp request use pannu |
|nmap -PM 192.168.1.0/24 |ICMP address mask ping |ICMP address mask request use pannu |
|nmap -PR 192.168.1.0/24 |ARP ping (LAN — very fast) |LAN-la ARP use pannitu scan — mega fast! |
|nmap -n 192.168.1.1 |Skip DNS resolution (faster) |DNS lookup skip — scan faster aagum |
|nmap -R 192.168.1.0/24 |Always do DNS resolution |Ellaa hosts-ku DNS resolve pannu |























































