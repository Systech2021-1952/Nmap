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
-----

### CHAPTER 5: PORT SCANNING TECHNIQUES
Port Scanning Techniques — Detailed

- ### Scan Types (-s flags)
Scan Types — -s flags

|Command / Flag |Description (EN) |Tanglish |
|---|---|---|
|nmap -sS <target> |TCP SYN Scan (Stealth) — DEFAULT as root |Stealth scan — half-open, fast, less detectable |
|nmap -sT <target> |TCP Connect Scan — full 3-way handshake |Full connection — root illama use pannum |
|nmap -sU <target> |UDP Scan — slower but important |UDP ports check — DNS, SNMP, DHCP etc |
|nmap -sA <target> |TCP ACK Scan — firewall rule mapping |Firewall rules map pannurathu ku |
|nmap -sW <target> |TCP Window Scan — like ACK scan |Window size analyze pannitu port state check |
|nmap -sM <target> |TCP Maimon Scan — FIN/ACK probe |FIN+ACK probe — BSD systems detect pannumnmap -sN <target> TCP Null Scan — no flags set Flag illama packet anuppu — firewall bypass |
|nmap -sF <target> |TCP FIN Scan — only FIN flag |Only FIN flag — stealth technique |
|nmap -sX <target> |Xmas Scan — FIN+PSH+URG flags |3 flags on — Christmas tree scan nu solluvaangnmap -sY <target> SCTP INIT Scan SCTP protocol use panni scan |
|nmap -sZ <target> |SCTP COOKIE-ECHO Scan |SCTP COOKIE-ECHO use panni scan |
|nmap -sI zombie <target> |Idle/Zombie Scan — untraceable |Zombie computer use panni anonymous scan |
|nmap -sO <target> |IP Protocol Scan |IP protocols support check pannum |

- ### Port Specification
Enna ports scan pannanum nu specify panrathu

|Command |Description (EN) |Tanglish |
|---|---|---|
|nmap -p 80 <target> |Scan only port 80 |Port 80 matum scan pannu |
|nmap -p 80,443,22 |Scan specific ports |Specific ports list kuduthu scan pannu |
|nmap -p 1-1000 <target> |Scan port range |1 to 1000 1 to 1000 ports scan — range specify |
|nmap -p- <target> |Scan all 65535 ports |Ellaa 65535 ports scan — time edukum |
|nmap --top-ports 100 |Scan top 100 most common ports |Most common 100 ports matum scan |
|nmap --top-ports 1000 |Scan top 1000 most common ports |Common 1000 ports — good balance |
|nmap -p U:53,T:80 |Scan UDP port 53 and TCP port 80 |UDP 53 and TCP 80 — combined scan |
|nmap -F <target> |Fast scan — top 100 ports only |Fast scan — 100 ports matum | 
|nmap -r <target> |Scan ports in order (not random) |Ports order-aa scan — randomize panna maata |
---
### CHAPTER 6: SERVICE & VERSION DETECTION
Service mattum Version kandupidikkirathu

After finding open ports, the next step is to identify WHAT services are running and WHICH VERSION. This information
is critical for finding vulnerabilities.

- → Open ports kandupidichaa aprom enna service run aagudu, enna version use pannudu — intha info vulnerability find
pannurathu ku romba important!

|Command |Description (EN) |Tanglish |
|---|---|---|
|nmap -sV <target> |Detect service versions on open ports |Open ports-la enna service, enna version |
|nmap -sV --version-intensity 0 |Lightest version probe |Miga light — fast aana less accurate |
|nmap -sV --version-intensity 5 |Default intensity (0-9) |Default intensity — balance |
|nmap -sV --version-intensity 9 |Most aggressive version detection |Max intensity — slow aana accurate |
|nmap -sV --version-light |Intensity 2 — lighter scan |Quick version check |
|nmap -sV --version-all |Intensity 9 — try all probes |Ellaa probes try pannu — thorough check |
|nmap -sV --version-trace |Show version scan activity |Version scan steps debug panni paarrukk |
|nmap -A <target> |Aggressive: OS+Version+Script+Traceroute |All-in-one: OS, version, scripts, tracerout |

★ PRO TIP: nmap -sV -sC -O --open → Most useful combo for real pentesting!

#### → Real pentest-la use pannurathu ku best combo — open ports, versions, OS ellaam oru command-la!
-----
### CHAPTER 7: OS DETECTION
Operating System kandupidikkirathu

Nmap can fingerprint the Operating System of a remote host by analyzing how the target responds to specially crafted TCP/IP packets. This technique is called 'OS Fingerprinting'.

→ Remote computer enna OS use pannuduchu (Windows, Linux, Mac) nu Nmap kandupidikkalaam. Special TCP/IP packets anuppi response analyze pannum — 'OS Fingerprinting' nu solluvaanga.

|Command |Description (EN) |Tanglish |
|---|---|---|
|nmap -O <target> |Enable OS detection |OS detection enable pannu — needs roo |
|nmap -O --osscan-limit |Only do OS scan if open+closed TCP port found|Open and closed port both irundhaa matun |
|map -O --osscan-guess |Guess OS more aggressively |Exact match illana best guess pannidu |
|nmap -O --max-os-tries 1 |Limit OS detection retries |OS detection attempts 1-ku limit pannu |
|nmap -A <target> |OS + Version + Scripts + Traceroute |Ellaam oru command-la — all-in-one |
|nmap -O --fuzzy |Submit guesses if no perfect match |Perfect match illa pattaalum guess panni |

NOTE: OS detection requires at least one open and one closed port on the target. It also requires root/administrator privileges to run.

→ OS detection pannum pothu root/admin privilege venum. Target-la oru open port, oru closed port irukkanum — illana
accurate-aa detect panna mudiyaathu.
-----
### CHAPTER 8: NMAP SCRIPTING ENGINE (NSE)
NSE — Advanced Scripting Power

NSE (Nmap Scripting Engine) is one of Nmap's most powerful features. It allows users to write and run scripts that automate complex tasks — from version detection to vulnerability scanning. Scripts are written in Lua and located at /usr/share/nmap/scripts/

→ NSE Nmap-oda super power! Lua scripting language-la ezhudha padda scripts use panni vulnerability check, brute force,
malware detect ellaam pannalathu! Scripts /usr/share/nmap/scripts/ folder-la irukkum.

## NSE Basic Usage
NSE use pannurathu — basics

|Command |Description (EN) |Tanglish |
|---|---|---|
|nmap -sC <target> |Run default scripts (safe category) |Default scripts run — safe category |
|nmap --script=default |Same as -sC |-sC ku same — default scripts |
|nmap --script=vuln <target> |Run all vulnerability scripts |Vulnerability scripts run — CVE check pan |
|nmap --script=safe <target> |Run only safe scripts |Only safe scripts — target-ku damage illai |
|nmap --script=intrusive |Run intrusive scripts (careful!) |Intrusive scripts — careful use pannunga! |
|nmap --script=malware |Detect malware infections |Malware detect pannurathu ku |
|nmap --script=auth |Test authentication/bypass |Authentication test pannurathu ku |
|nmap --script=brute |Brute force scripts |Password brute force — authorized matum |
|nmap --script=exploit |Exploitation scripts |Exploit scripts — authorized systems matum |
|nmap --script=discovery |Network discovery scripts |Network discovery automate pannurathu |
|nmap --script=fuzzer |Fuzzing scripts |Fuzzing use panni vulnerabilities find pannu |
|nmap --script=dos |DoS testing (dangerous!) |DoS test — very careful! Authorized matum |
|nmap --script=external |Scripts using external resources |External APIs use panni check pannum |
|nmap --script=version |Version detection scripts |Version detect panna extra scripts | 

- ### Popular NSE Scripts
Most used NSE scripts

|Script Name |Description (EN) |Tanglish |
|---|---|---|
|--script=http-title |Get HTTP page titles |Website title kandupidi |
|--script=http-headers |Show HTTP response headers |HTTP headers paarrukku |
|--script=http-methods |List allowed HTTP methods |HTTP methods list pannum |
|--script=ssl-cert |Get SSL certificate info |SSL certificate details paarrukku |













