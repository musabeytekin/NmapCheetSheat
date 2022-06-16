# Nmap

## Basic Scanning

- Single ip: 
```bash
nmap 192.168.1.10
```
- Multiple ip:
```bash
nmap 192.168.1.10 192.168.1.11
```
- Ip Range:
```bash
nmap 192.168.1.10-256
```
- Network Scan:
```bash
nmap 192.168.1.0/24
```
- Domain Scan:
```bash
nmap testdomain.com
```
- Scan targets in given file:
```bash
nmap -iL targets.txt
```

- scanning with excluded ip:
```bash
nmap --exclude 192.168.1.24 
```

- Scan without DNS resolution:
```bash
nmap 192.168.1.10 -n
```

- Without port scanning and name resolution: ⭐️⭐️
```bash
nmap 192.168.1.10 -sn
```

- Ping scan with ARP packets:
```bash
nmap 192.168.1.10 -PR 
```

- No ping, port scan only: ⭐️⭐️
```bash
nmap 192.168.1.10 -Pn
```

- Ping scan with TCP ACK flag: ⭐️⭐️
```bash
nmap 192.168.1.10 -PA
```

- TCP port scan: ⭐️⭐️
```bash
nmap 192.168.1.10 -sT
```

- TCP port scanning with SYN flag: ⭐️⭐️
```bash
nmap 192.168.1.10 -sS
```

- TCP port scanning with ACK flag: ⭐️⭐️
```bash
nmap 192.168.1.10 -sA
```

- UDP port scanning:
```bash
nmap 192.168.1.10 -sA
```

- Scanning of specific port range: ⭐️⭐️
```bash
nmap 192.168.1.10 0-100
```

- Scanning specific UDP and TCP ports: 
```bash
nmap 192.168.1.10 -p U:63 T:21-25,80
```

- Scanning all ports: ⭐️⭐️
```bash
nmap 192.168.1.10 -p-
```

- Port scan by service name:
```bash
nmap 192.168.1.10 -p http,ftp
```

- Quick scan of 100 ports:
```bash
nmap 192.168.1.10 -F
```

- Scanning the top 1000 ports: 
```bash
nmap 192.168.1.10 --top-ports 1000
```

## Version Detection

- version scan of the service running on the port(simple): ⭐️⭐️
```bash
nmap 192.168.1.10 -sV
```

- Highest (9th) level version scan: ⭐️⭐️
```bash
nmap 192.168.1.10 -sV --version-all
```

- 8th precision version scan from 0-9 (High number = correct result):
```bash
nmap 192.168.1.10 -sV --version-intensity 8
```

- light and fast version scan:
```bash
nmap 192.168.1.10 --version-light
```

## OS Detection

- simple OS detection (with tcp/ip fingerprint):
```bash
nmap 192.168.1.10 -O 
```

- Scanning ports with tcp ports:
```bash
nmap 192.168.1.10 -O --osscan-limit
```

- Scanning with more aggressive predictions: ⭐️⭐️
```bash
nmap 192.168.1.10 -O --osscan-guess 
```

- One-time OS scan:
```bash
nmap 192.168.1.10 -O --max-os-tries 1
```

- OS, version and vulnerability scanning: ⭐️⭐️
```bash
nmap 192.168.1.10 -A
```

## Time and Performance adjusted scanning

- (Paranoid) IDS dodge and slowest scan. Use in an external (WAN) network:
```bash
nmap 192.168.1.10 -T0
```

- (Sneaky) IDS dodge and slow browsing:
```bash
nmap 192.168.1.10 -T1
```

- (Polite) Faster but less detectable scanning:
```bash
nmap 192.168.1.10 -T2
```

- (Normal) Scan at default speed:
```bash
nmap 192.168.1.10 -T3
```

- (Aggressive) Fast and aggressive scanning: ⭐️⭐️
Usage in local (LAN) network:
```bash
nmap 192.168.1.10 -T4
```

- (Insane) Fastest scan.Usage in local (LAN) network:
```bash
nmap 192.168.1.10 -T5
```

## Scanning with NSE(Nmap Script Engine)

- Scanning with top scripts: ⭐️⭐️
```bash
nmap 192.168.1.10 -sC
```

- Scanning with specific scripts: ⭐️⭐️
```bash
nmap 192.168.1.10 --script http-sql-injection
```

- Scanning all specific ports:
```bash
nmap 192.168.1.10 --script smb*
```

- Script scanning with arguments:
```bash
nmap --script snmp-sysdescr --script-args snmpcommunity=admin 192.168.1.10 
```

- Scanning all scripts: ⭐️⭐️
```bash
nmap 192.168.1.10 --script vuln
```

- Update Script Database: 
```bash
nmap --script-updatedb
```
- Get help about a script:
```bash
nmap --script-help snmp-sysdescr
```

- Auto Vulnerable detection:
```bash
nmap --script vuln 192.168.1.10
```
- Auto Vulnerable detection:
```bash
nmap --script vulners 192.168.1.10
```

- Vulscan scripts:
```bash
nmap --script vulscan/vulscan.nse
```

## Output Scanning

- normal output: ⭐️⭐️
```bash
nmap 192.168.1.10 -oN output.txt 
```

- XML output:
```bash
nmap 192.168.1.10 -oX output.xml
```

- Grep file output:
```bash
nmap 192.168.1.10 -oG output.grep
```

- Output in triple format:
```bash
nmap 192.168.1.10 -oA output
```

- More detailed scanning. As the number of -v is increased, the monthly purchase becomes stronger: ⭐️⭐️
```bash
nmap 192.168.1.10 -v 
nmap 192.168.1.10 -vvv 
```

- More error detailed scanning , As the number of -v is increased, the monthly purchase becomes stronger:
```bash
nmap 192.168.1.10 -d 
nmap 192.168.1.10 -dd
```

- show only open ports:
```bash
nmap 192.168.1.10 --open
```

- View all sent and received packets:
```bash
nmap 192.168.1.10 --packet-trace
```

- View the destination's ethernet and routes:
```bash
nmap 192.168.1.10 --iflist
```

- Resume scanning from file:
```bash
nmap 192.168.1.10 --resume output.txt
```


