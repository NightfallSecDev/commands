### Use Nmap to scan multiple IPs
```bash
nmap -iL ips.txt 
```

```bash
nmap -iL ips.txt -p 80,443,22,21 -oN output.txt
```
```bash
nmap -iL ips.txt -p 1-65535 -oN full_output.txt
```
### Scan using Nmap Scripting Engine (NSE) for vulnerability checks
```bash
nmap -iL ips.txt --script=vuln -oN vuln_scan.txt
```
### Parallel Scan to Speed Up
```bash
nmap -iL ips.txt -p 80,443,22,21 -T4 -oN fast_output.txt
```
### Masscan for faster scanning 
```bash
masscan -iL ips.txt -p80,443,22 --rate 1000 -oG masscan_output.txt
```
```bash
masscan -p1-65535 -iL ips.txt --rate 1000
```

```bash
naabu -host hackerone.com
```
```bash
naabu -p 80,443,21-23,u:53 -host hackerone.com
```
```bash 
naabu -list hosts.txt
```