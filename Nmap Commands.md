# Nmap Cheat Sheet

- Quick reference guide for common Nmap commands and scanning techniques.

## Basic Usage

| Purpose | Command |
|----------|----------|
| Scan a host | `nmap 192.168.1.1` |
| Scan a domain | `nmap scanme.nmap.org` |
| Multiple targets | `nmap 192.168.1.1 192.168.1.2` |
| Subnet scan | `nmap 192.168.1.0/24` |

## Port Scanning

| Purpose | Command |
|---------|---------|
| Specific ports | `nmap -p 80,443 target` |
| Port range | `nmap -p 1-1000 target` |
| All ports | `nmap -p- target` |
| Top 100 ports | `nmap --top-ports 100 target` |

## Scan Types

| Purpose | Command |
|----------|----------|
| SYN scan | `nmap -sS target` |
| TCP connect scan | `nmap -sT target` |
| UDP scan | `nmap -sU target` |
| Ping scan only | `nmap -sn target` |
| Aggressive scan | `nmap -A target` |

## Service & OS Detection

| Purpose | Command |
|----------|----------|
| Service version detection | `nmap -sV target` |
| OS detection | `nmap -O target` |
| Default scripts | `nmap -sC target` |
| Vulnerability scan | `nmap --script=vuln target` |

## Timing & Performance

| Purpose | Command |
|----------|----------|
| Slow scan | `nmap -T0 target` |
| Fast scan | `nmap -T4 target` |
| Aggressive timing | `nmap -T5 target` |

## Firewall Evasion

| Purpose | Command |
|----------|----------|
| Skip ping | `nmap -Pn target` |
| Fragment packets | `nmap -f target` |
| Decoy scan | `nmap -D RND:10 target` |

## Output Formats

| Purpose | Command |
|----------|----------|
| Normal output | `nmap -oN output.txt target` |
| XML output | `nmap -oX output.xml target` |
| All formats | `nmap -oA scan_results target` |

## Useful Real-World Commands

| Purpose | Command |
|----------|----------|
| Quick scan | `nmap -T4 -F target` |
| Full scan | `nmap -p- -T4 -A target` |
| Stealth + version detection | `nmap -sS -sV target` |

> Use Nmap responsibly and only on systems you own or have permission to test.

----
