# Nmap – Network Scanning Tool & Reconnaissance
## Ethical Hacking & Cybersecurity Guide
## Cybersecurity • Network Scanning • Ethical Hacking

### Introduction : 
Nmap (Network Mapper) is a powerful open-source tool used for network discovery and security auditing. 
It helps identify live hosts, open ports, services, and operating systems on a network.

Network scanning is important because it helps organizations understand their attack surface.
By scanning systems ethically, defenders can fix vulnerabilities before attackers exploit them.

Real-world ethical use cases include SOC monitoring, VAPT assessments, penetration testing, and academic learning.

## Installation Guide
### Linux (Kali / Ubuntu)

> sudo apt update

> sudo apt install nmap

### Windows
```
 Download installer from:
 https://nmap.org/download.html
```

### macOS
```
brew install nmap
```

### Nmap Basics :

Nmap basic syntax:
nmap [options] target

Targets can be IP addresses, ranges, or domain names. Nmap identifies port states such as
open, closed, and filtered.

### Scan Types

| Details | Commands |
| TCP Connect Scan | nmap -sT 192.168.1.1 |
| SYN Scan | nmap -sS 192.168.1.1 |
| UDP Scan | nmap -sU 192.168.1.1 |
| Ping Scan | nmap -sn 192.168.1.0/24 |
