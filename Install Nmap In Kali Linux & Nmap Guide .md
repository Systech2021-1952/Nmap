# Nmap – Network Scanning Tool & Reconnaissance
## Ethical Hacking & Cybersecurity Guide
## Cybersecurity • Network Scanning • Ethical Hacking

### Introduction : 
- Nmap (Network Mapper) is a powerful open-source tool used for network discovery and security auditing. 
It helps identify live hosts, open ports, services, and operating systems on a network.

- Network scanning is important because it helps organizations understand their attack surface.
By scanning systems ethically, defenders can fix vulnerabilities before attackers exploit them.

- Real-world ethical use cases include SOC monitoring, VAPT assessments, penetration testing, and academic learning.

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

Nmap basic syntax :

nmap [options] target

- Targets can be IP addresses, ranges, or domain names. Nmap identifies port states such as
open, closed, and filtered.

### Scan Types

| TCP Connect Scan |nmap -sT 192.168.1.1 |
|-----|-----|
| SYN Scan | nmap -sS 192.168.1.1 |
| UDP Scan | nmap -sU 192.168.1.1 |
| Ping Scan | nmap -sn 192.168.1.0/24 |

### Port Scanning Techniques

| Default scan | nmap target |
| ----- | ----- |
| Specific ports | nmap -p 80,443 target |
| All ports | nmap -p- target |
| Fast scan  | nmap -F target |

### Service & Version Detection

| Service detection   | nmap -sV target |
|-----|-----|
| OS detection       |  nmap -O target |
| Aggressive scan     | nmap -A target |

### Nmap Scripting Engine (NSE)

- NSE allows Nmap to run scripts for vulnerability detection, brute force testing, and information
gathering. Scripts are grouped into categories like safe, auth, vuln, and discovery.

> Run default scripts : nmap -sC target

> Run vuln scripts    : nmap --script vuln targe


### Output & Reporting

|Normal output      |  nmap target |
|-----|-----|
| Save normal output  | nmap -oN output.txt target |
| Grepable output     | nmap -oG output.gnmap target |
| XML output         |  nmap -oX output.xml target |

### Performance & Evasion

- Nmap timing templates (-T0 to -T5) control scan speed. Slower scans are stealthier, while faster
scans are noisy. Firewall and IDS awareness is important and should be studied only at a high
level and ethically.

### Defensive Perspective

- Defenders detect Nmap scans using IDS/IPS, SIEM logs, and firewall alerts. Systems can be
hardened by closing unused ports, applying patches, and monitoring traffic. Blue teams must
understand scanning to defend effectively.

### Ethical & Legal Disclaimer

- WARNING: Nmap must be used ONLY on systems you own or have written permission to test.
Unauthorized scanning is illegal and punishable by law. Ethical hackers must always follow legal
and professional guidelines.

### Conclusion

- This guide introduced Nmap from both offensive and defensive perspectives. Students should
continue practicing in legal labs and controlled environments to build strong ethical hacking
skills




