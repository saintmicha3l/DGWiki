# Linux Tools

Below you will find a large collection of Linux-based tools that are **not typically preinstalled** on Kali, ParrotOS, BlackArch, or similar penetration-testing distributions.  
All tools listed are commonly used in **authorized penetration tests, red team engagements, malware research, reverse engineering, and Capture The Flag (CTF) environments**.

> Use only on systems you own or have explicit permission to test.

---

## Reconnaissance & OSINT

- [Amass](https://github.com/owasp-amass/amass) – Attack surface mapping and asset discovery  
- [theHarvester](https://github.com/laramies/theHarvester) – Emails, subdomains, and hosts enumeration  
- [Recon-ng](https://github.com/lanmaster53/recon-ng) – Modular reconnaissance framework  
- [SpiderFoot](https://github.com/smicallef/spiderfoot) – Automated OSINT collection  
- [Maltego CE](https://github.com/paterva/maltego-trx) – Graph-based OSINT analysis  
- [Subfinder](https://github.com/projectdiscovery/subfinder) – Passive subdomain enumeration  
- [Assetfinder](https://github.com/tomnomnom/assetfinder) – Domain discovery  
- [DNSGen](https://github.com/ProjectAnte/dnsgen) – Subdomain mutation  
- [GitLeaks](https://github.com/gitleaks/gitleaks) – Secret scanning for Git repos  
- [TruffleHog](https://github.com/trufflesecurity/trufflehog) – Credential discovery in Git  
- [Metagoofil](https://github.com/laramies/metagoofil) – Metadata extraction from public files  

---

## Web Application Testing

- [Burp Suite Community](https://github.com/PortSwigger) – Web proxy and testing platform  
- [OWASP ZAP](https://github.com/zaproxy/zaproxy) – Web application scanner  
- [FFUF](https://github.com/ffuf/ffuf) – Fast web fuzzer  
- [Wfuzz](https://github.com/xmendez/wfuzz) – Web brute forcing  
- [Feroxbuster](https://github.com/epi052/feroxbuster) – Recursive content discovery  
- [Gobuster](https://github.com/OJ/gobuster) – Directory and DNS brute forcing  
- [Nikto](https://github.com/sullo/nikto) – Web server vulnerability scanning  
- [WhatWeb](https://github.com/urbanadventurer/WhatWeb) – Web technology fingerprinting  
- [SQLmap](https://github.com/sqlmapproject/sqlmap) – SQL injection exploitation  
- [XSStrike](https://github.com/s0md3v/XSStrike) – Advanced XSS scanner  
- [Dalfox](https://github.com/hahwul/dalfox) – XSS discovery and exploitation  
- [Arjun](https://github.com/s0md3v/Arjun) – HTTP parameter discovery  
- [ParamSpider](https://github.com/devanshbatham/ParamSpider) – URL parameter mining  

---

## Passwords, Hashes & Credentials

- [Hashcat](https://github.com/hashcat/hashcat) – GPU-accelerated password cracking  
- [Hydra](https://github.com/vanhauser-thc/thc-hydra) – Network login brute forcing  
- [Medusa](https://github.com/jmk-foofus/medusa) – Parallel brute-force tool  
- [John the Ripper](https://github.com/openwall/john) – Password cracker  
- [CrackMapExec](https://github.com/Porchetta-Industries/CrackMapExec) – Active Directory exploitation  
- [Impacket](https://github.com/fortra/impacket) – Windows protocol abuse toolkit  
- [RsaCtfTool](https://github.com/Ganapati/RsaCtfTool) – RSA cryptography attacks  
- [CeWL](https://github.com/digininja/CeWL) – Custom wordlist generation  
- [Pipal](https://github.com/digininja/pipal) – Password analysis  

---

## Exploitation Frameworks & Toolkits

- [Metasploit Framework](https://github.com/rapid7/metasploit-framework) – Exploitation platform  
- [Empire](https://github.com/BC-SECURITY/Empire) – Post-exploitation framework  
- [Sliver](https://github.com/BishopFox/sliver) – Modern C2 framework  
- [Covenant](https://github.com/cobbr/Covenant) – .NET command-and-control  
- [Nishang](https://github.com/samratashok/nishang) – PowerShell exploitation  
- [SearchSploit](https://github.com/offensive-security/exploitdb) – Local exploit search  
- [RouterSploit](https://github.com/threat9/routersploit) – Embedded device exploitation  

---

## Reverse Engineering & Binary Exploitation

- [Ghidra](https://github.com/NationalSecurityAgency/ghidra) – Reverse engineering framework  
- [Radare2](https://github.com/radareorg/radare2) – Binary analysis toolkit  
- [Cutter](https://github.com/rizinorg/cutter) – GUI for reverse engineering  
- [pwntools](https://github.com/Gallopsled/pwntools) – CTF exploitation framework  
- [pwndbg](https://github.com/pwndbg/pwndbg) – GDB exploit development plugin  
- [GEF](https://github.com/hugsy/gef) – GDB Enhanced Features  
- [Binwalk](https://github.com/ReFirmLabs/binwalk) – Firmware analysis  
- [apktool](https://github.com/iBotPeaches/Apktool) – Android app reverse engineering  
- [jadx](https://github.com/skylot/jadx) – Dex to Java decompiler  

---

## Malware Analysis & Forensics

- [YARA](https://github.com/VirusTotal/yara) – Malware pattern matching  
- [CAPA](https://github.com/mandiant/capa) – Malware capability detection  
- [Volatility](https://github.com/volatilityfoundation/volatility3) – Memory forensics  
- [FLOSS](https://github.com/mandiant/flare-floss) – String deobfuscation  
- [Cuckoo Sandbox](https://github.com/cuckoosandbox/cuckoo) – Automated malware analysis  
- [REMnux](https://github.com/REMnux/distro) – Malware analysis distro tooling  
- [PEStudio](https://github.com/erocarrera/pefile) – PE file inspection  

---

## Networking, Traffic & Wireless

- [Bettercap](https://github.com/bettercap/bettercap) – Network attack framework  
- [Wireshark](https://github.com/wireshark/wireshark) – Packet analysis  
- [Tcpdump](https://github.com/the-tcpdump-group/tcpdump) – CLI packet capture  
- [Aircrack-ng](https://github.com/aircrack-ng/aircrack-ng) – Wireless auditing  
- [Kismet](https://github.com/kismetwireless/kismet) – Wireless reconnaissance  
- [Responder](https://github.com/lgandx/Responder) – LLMNR/NBT-NS poisoning  

---

## Payloads, Shells & Post-Exploitation

- [PEASS-ng](https://github.com/carlospolop/PEASS-ng) – Privilege escalation enumeration  
- [LinEnum](https://github.com/rebootuser/LinEnum) – Linux privilege escalation  
- [Linux Exploit Suggester](https://github.com/mzet-/linux-exploit-suggester) – Kernel exploit suggestions  
- [GTFOBins](https://github.com/GTFOBins/GTFOBins.github.io) – Living-off-the-land binaries  
- [Chisel](https://github.com/jpillora/chisel) – TCP tunneling  
- [Socat](https://github.com/3ndG4me/socat) – Socket relay  

---

## Wordlists & Supporting Data

- [SecLists](https://github.com/danielmiessler/SecLists) – Payloads, wordlists, fuzzing data  
- [PayloadsAllTheThings](https://github.com/swisskyrepo/PayloadsAllTheThings) – Exploitation payloads  
- [FuzzDB](https://github.com/fuzzdb-project/fuzzdb) – Attack patterns and payloads
- [Probable‑Wordlists](https://github.com/berzerk0/Probable-Wordlists)  
- [Weakpass Wordlists](https://github.com/weakpass/weakpass)
- [CrackStation Wordlist (Mirrors & Metadata)](https://github.com/brannondorsey/naive-hashcat)
- [Common Usernames](https://github.com/insidetrust/statistically-likely-usernames)

---

