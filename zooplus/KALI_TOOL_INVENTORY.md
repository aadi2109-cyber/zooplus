# Kali Linux Tool Inventory

**Generated:** 2026-09-05
**System:** Kali GNU/Linux Rolling 2026.3 | Kernel 7.1.5+kali-amd64 | x86_64
**User:** kali (uid=1000, sudo, netdev, scanner, bluetooth)
**Shell:** zsh | Package managers: apt, dpkg

## Summary

- Total Debian packages installed: ~3425
- Relevant tools cataloged: ~100+
- Categories: 15

## Reconnaissance & OSINT

| Tool | Version | Path | Package | Root? |
|------|---------|------|---------|-------|
| nmap | 7.99 | /usr/bin/nmap | nmap | No |
| nikto | (no --version) | /usr/bin/nikto | nikto | No |
| theHarvester | (no --version) | /usr/bin/theHarvester | theHarvester | No |
| subfinder | (no --version) | /usr/bin/subfinder | subfinder | No |
| amass | (no --version) | /usr/bin/amass | amass | No |
| sublist3r | (no --version) | /usr/bin/sublist3r | sublist3r | No |
| shodan | CLI | /usr/bin/shodan | shodan | No |
| dnsrecon | CLI | /usr/bin/dnsrecon | dnsrecon | No |
| fierce | CLI | /usr/bin/fierce | fierce | No |
| dnsmap | CLI | /usr/bin/dnsmap | dnsmap | No |
| dnsenum | CLI | /usr/bin/dnsenum | dnsenum | No |
| recon-ng | 5.1.2 | /usr/bin/recon-ng | recon-ng | No |

## Web Security & Testing

| Tool | Version | Path | Package | Root? |
|------|---------|------|---------|-------|
| burpsuite | 2026.8-53343 | /usr/bin/burpsuite | burpsuite | No (GUI) |
| zap | CLI | /usr/bin/zap | zaproxy | No |
| wpscan | CLI | /usr/bin/wpscan | wpscan | No |
| nikto | CLI | /usr/bin/nikto | nikto | No |
| whatweb | CLI | /usr/bin/whatweb | whatweb | No |
| dirb | CLI | /usr/bin/dirb | dirb | No |
| dirbuster | 1.0-RC1 | /usr/bin/dirbuster | dirbuster | No (GUI) |
| gobuster | 3.8.2 | /usr/bin/gobuster | gobuster | No |
| ffuf | 2.1.0-dev | /usr/bin/ffuf | ffuf | No |
| wfuzz | CLI | /usr/bin/wfuzz | wfuzz | No |
| feroxbuster | 2.13.1 | /usr/bin/feroxbuster | feroxbuster | No |
| sqlmap | 1.10.8-stable | /usr/bin/sqlmap | sqlmap | No |

## Network Analysis & Scanning

| Tool | Version | Path | Package | Root? |
|------|---------|------|---------|-------|
| nmap | 7.99 | /usr/bin/nmap | nmap | Some scripts need root |
| masscan | CLI | /usr/bin/masscan | masscan | Yes (raw sockets) |
| unicornscan | 0.4.7 | /usr/bin/unicornscan | unicornscan | Yes |
| tcpreplay | CLI | /usr/bin/tcpreplay | tcpreplay | No |
| ngrep | CLI | /usr/bin/ngrep | ngrep | No |
| scapy | CLI | /usr/bin/scapy | python3-scapy | No |

## Packet Capture & Analysis

| Tool | Version | Path | Package | Root? |
|------|---------|------|---------|-------|
| wireshark | 4.6.6 | /usr/bin/wireshark | wireshark | No (GUI) |
| tshark | 4.6.6 | /usr/bin/tshark | wireshark | No (or root for raw) |
| tcpdump | 4.99.6 | /usr/bin/tcpdump | tcpdump | Yes (raw sockets) |
| dumpcap | 4.6.6 | /usr/bin/dumpcap | wireshark | Yes |

## Password Auditing

| Tool | Version | Path | Package | Root? |
|------|---------|------|---------|-------|
| john | 1.9.0-jumbo | /usr/sbin/john | john | No |
| hashcat | v7.1.2 | /usr/bin/hashcat | hashcat | GPU drivers |
| hydra | v9.7 | /usr/bin/hydra | hydra | No |
| medusa | CLI | /usr/bin/medusa | medusa | No |
| crunch | CLI | /usr/bin/crunch | crunch | No |
| hashid | CLI | /usr/bin/hashid | hashid | No |
| hash-identifier | CLI | /usr/bin/hash-identifier | hash-identifier | No |

## Exploitation Frameworks

| Tool | Version | Path | Package | Root? |
|------|---------|------|---------|-------|
| metasploit (msfconsole) | CLI | /usr/bin/msfconsole | metasploit-framework | Yes (often) |
| msfvenom | CLI | /usr/bin/msfvenom | metasploit-framework | Yes (often) |

## Wireless Security

| Tool | Version | Path | Package | Root? |
|------|---------|------|---------|-------|
| aircrack-ng | CLI | /usr/bin/aircrack-ng | aircrack-ng | Yes |
| airodump-ng | CLI | /usr/sbin/airodump-ng | aircrack-ng | Yes |
| aireplay-ng | CLI | /usr/sbin/aireplay-ng | aircrack-ng | Yes |
| airmon-ng | CLI | /usr/sbin/airmon-ng | aircrack-ng | Yes |
| wifite | CLI | /usr/sbin/wifite | wifite | Yes |
| kismet | 2025.09 | /usr/bin/kismet | kismet | Yes |

## Digital Forensics

| Tool | Version | Path | Package | Root? |
|------|---------|------|---------|-------|
| exiftool | CLI | /usr/bin/exiftool | libimage-exiftool-perl | No |
| binwalk | CLI | /usr/bin/binwalk | binwalk | No |
| scalpel | 1.60 | /usr/bin/scalpel | scalpel | No |
| testdisk | CLI | /usr/bin/testdisk | testdisk | No |
| photorec | CLI | /usr/bin/photorec | testdisk | No |

## Reverse Engineering & Binary Analysis

| Tool | Version | Path | Package | Root? |
|------|---------|------|---------|-------|
| radare2 | 6.0.5 | /usr/bin/radare2 | radare2 | No |
| r2 | 6.0.5 | /usr/bin/r2 | radare2 | No |
| gdb | CLI | /usr/bin/gdb | gdb | No |
| strings | CLI | /usr/bin/strings | binutils | No |
| objdump | CLI | /usr/bin/objdump | binutils | No |
| readelf | CLI | /usr/bin/readelf | binutils | No |
| nm | CLI | /usr/bin/nm | binutils | No |
| hexdump | CLI | /usr/bin/hexdump | bsdutils | No |
| xxd | CLI | /usr/bin/xxd | vim-common | No |
| file | CLI | /usr/bin/file | file | No |

## Samba / SMB Tools

| Tool | Version | Path | Package | Root? |
|------|---------|------|---------|-------|
| smbclient | 4.24.5 | /usr/bin/smbclient | samba | No |
| enum4linux | 0.9.1 | /usr/bin/enum4linux | enum4linux | No |
| nbtscan | CLI | /usr/bin/nbtscan | nbtscan | No |
| rpcclient | 4.24.5 | /usr/bin/rpcclient | samba | No |
| smbpasswd | CLI | /usr/bin/smbpasswd | samba | No |

## SNMP Tools

| Tool | Version | Path | Package | Root? |
|------|---------|------|---------|-------|
| snmpwalk | CLI | /usr/bin/snmpwalk | net-snmp | No |
| snmpcheck | CLI | /usr/bin/snmpcheck | snmpcheck | No |
| onesixtyone | 0.3.3 | /usr/bin/onesixtyone | onesixtyone | No |
| snmp-check | CLI | /usr/bin/snmp-check | snmp-check | No |

## SSL/TLS

| Tool | Version | Path | Package | Root? |
|------|---------|------|---------|-------|
| sslscan | CLI | /usr/bin/sslscan | sslscan | No |
| sslyze | CLI | /usr/bin/sslyze | sslyze | No |

## DNS Tools

| Tool | Version | Path | Package | Root? |
|------|---------|------|---------|-------|
| dig | CLI | /usr/bin/dig | dnsutils | No |
| host | CLI | /usr/bin/host | bind9-host | No |
| nslookup | CLI | /usr/bin/nslookup | dnsutils | No |

## Proxy / Network Relay

| Tool | Version | Path | Package | Root? |
|------|---------|------|---------|-------|
| proxychains | CLI | /usr/bin/proxychains | proxychains | No |
| openvpn | 2.7.5 | /usr/sbin/openvpn | openvpn | Yes |

## Response / Exploitation Helpers

| Tool | Version | Path | Package | Root? |
|------|---------|------|---------|-------|
| responder | CLI | /usr/sbin/responder | responder | Yes |
| bloodhound-python | CLI | /usr/bin/bloodhound-python | bloodhound-python | No |

## Development Tools

| Tool | Version | Path | Package | Root? |
|------|---------|------|---------|-------|
| python3 | 3.14.6 | /usr/bin/python3 | python3 | No |
| pip3 | 26.1.2 | /usr/bin/pip3 | python3-pip | No |
| gcc | 15.3.0 | /usr/bin/gcc | gcc | No |
| g++ | 15.3.0 | /usr/bin/g++ | g++ | No |
| gcc-14 | 14.4.0 | /usr/bin/gcc-14 | gcc-14 | No |
| g++-14 | 14.4.0 | /usr/bin/g++-14 | g++-14 | No |
| go | 1.26.7 | /usr/bin/go | golang | No |
| ruby | 3.3.8 | /usr/bin/ruby | ruby | No |
| nodejs | v26.8.1 | /usr/bin/nodejs | nodejs | No |
| npm | (local) | /home/kali/.local/bin/npm | npm | No |
| git | 2.53.0 | /usr/bin/git | git | No |
| make | 4.4.1 | /usr/bin/make | make | No |
| autoconf | CLI | /usr/bin/autoconf | autoconf | No |
| automake | CLI | /usr/bin/automake | automake | No |
| perl | CLI | /usr/bin/perl | perl | No |
| php | CLI | /usr/bin/php | php | No |
| java | CLI | /usr/bin/java | java | No |

## Shell / CLI Utilities

| Tool | Version | Path | Package | Root? |
|------|---------|------|---------|-------|
| curl | 8.21.0 | /usr/bin/curl | curl | No |
| wget | 1.25.0 | /usr/bin/wget | wget | No |
| jq | 1.8.2 | /usr/bin/jq | jq | No |
| grep | 3.12 | /usr/bin/grep | grep | No |
| sed | 4.9 | /usr/bin/sed | sed | No |
| awk | 5.3.2 | /usr/bin/awk | gawk | No |
| git | 2.53.0 | /usr/bin/git | git | No |

## File Utilities

| Tool | Version | Path | Package | Root? |
|------|---------|------|---------|-------|
| ssh-copy-id | CLI | /usr/bin/ssh-copy-id | openssh-client | No |
| telnet | CLI | /usr/bin/telnet | telnet | No |

## Symlinks / Duplicates

- `r2` -> `radare2` (same tool)
- `nc` -> `netcat` (netcat-openbsd variant)
- `nmap` and `ncat` are separate tools (ncat was NOT found)

## Prerequisites / Limitations

- Wireless tools (aircrack-ng, wifite, kismet) require root and wireless hardware with monitor mode support.
- msfconsole typically requires root for some auxiliary modules.
- hashcat may require GPU drivers for GPU acceleration.
- masscan, unicornscan require root for raw socket access.
- wireshark/tshark require group `wireshark` membership for non-root packet capture (kali user is NOT in wireshark group by default).
- shodan, theHarvester, holehe require API keys or internet access.
- proxychains requires `/etc/proxychains.conf` configuration.
- openvas/gvm requires database and service setup.
- burpsuite is a Java GUI application.

## Capabilities Not Available

- ncat (netcat-openbsd only, no traditional ncat)
- crackmapexec (not installed)
- autorecon (not installed)
- ghidra (not installed)
- chisel (not installed)
- proxifier (not installed)
- dirsearch (not installed)
- hakrawler (not installed)
- webtech (not installed)
- volatility / volatility3 (not found in PATH)
- docker / podman / kubernetes tools (not found in PATH)

## Refresh Procedure

To refresh this inventory after installing/removing tools:

1. Run: `dpkg-query -W | awk -F'\t' '{print $1}' | sort` to list all packages.
2. Run: `apt list --installed 2>/dev/null | grep -v Listing | awk -F'/' '{print $1}' | sort` for apt packages.
3. Check individual tools: `command -v <tool>` and `<tool> --version`.
4. Re-run the skill creation script or manually update the tables.