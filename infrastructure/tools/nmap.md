# nmap
[Readme](../README.md)

- [nmap](#nmap)
  - [Commands](#commands)
    - [Target Specification](#target-specification)
    - [Scan Techniques](#scan-techniques)
    - [Host Discovery](#host-discovery)
    - [Port Specification](#port-specification)
    - [Service and Version Detection](#service-and-version-detection)
    - [OS Detection](#os-detection)
    - [Timing and Performance](#timing-and-performance)
      - [Timing and Performance Switches](#timing-and-performance-switches)
    - [NSE Scripts](#nse-scripts)
      - [Useful NSE Script Examples](#useful-nse-script-examples)
    - [Firewall / IDS Evasion and Spoofing](#firewall--ids-evasion-and-spoofing)
    - [Outputs](#outputs)
    - [Helpful Nmap Output examples](#helpful-nmap-output-examples)
    - [Miscellaneous Options](#miscellaneous-options)
    - [Other Useful Nmap Commands](#other-useful-nmap-commands)

## Commands

### Target Specification

| What                     | Switch          | Example                            |
| :----------------------- | :-------------- | :--------------------------------- |
| Scan a single IP         |                 | ```nmap 192.168.1.1```             |
| Scan specific IPs        |                 | ```nmap 192.168.1.1 192.168.2.1``` |
| Scan a range             |                 | ```nmap 192.168.1.1-254```         |
| Scan a domain            |                 | ```nmap scanme.nmap.org```         |
| Scan using CIDR notation |                 | ```nmap 192.168.1.0/24```          |
| Scan targets from a file | ``` -iL```      | ```nmap -iL targets.txt```         |
| Scan 100 random hosts    | ``` -iR```      | ```nmap -iR 100```                 |
| Exclude listed hosts     | ``` –exclude``` | ```nmap –exclude 192.168.1.1```    |

### Scan Techniques

| What                                                   | Switch    | Example                    |
| :----------------------------------------------------- | :-------- | :------------------------- |
| TCP SYN port scan (Default)                            | ```-sS``` | ```nmap 192.168.1.1 -sS``` |
| TCP connect port scan (Default without root privilege) | ```-sT``` | ```nmap 192.168.1.1 -sT``` |
| UDP port scan                                          | ```-sU``` | ```nmap 192.168.1.1 -sU``` |
| TCP ACK port scan                                      | ```-sA``` | ```nmap 192.168.1.1 -sA``` |
| TCP Window port scan                                   | ```-sW``` | ```nmap 192.168.1.1 -sW``` |
| TCP Maimon port scan                                   | ```-sM``` | ```nmap 192.168.1.1 -sM``` |

### Host Discovery

| What                                            | Switch    | Example                              |
| :---------------------------------------------- | :-------- | :----------------------------------- |
| No Scan. List targets only                      | ```-sL``` | ```nmap 192.168.1.1-3 -sL```         |
| Disable port scanning. Host discovery only.     | ```-sn``` | ```nmap 192.168.1.1/24 -sn```        |
| Disable host discovery. Port scan only.         | ```-Pn``` | ```nmap 192.168.1.1-5 -Pn```         |
| TCP SYN discovery on port x. Port 80 by default | ```-PS``` | ```nmap 192.168.1.1-5 -PS22-25,80``` |
| TCP ACK discovery on port x. Port 80 by default | ```-PA``` | ```nmap 192.168.1.1-5 -PA22-25,80``` |
| UDP discovery on port x. Port 40125 by default  | ```-PU``` | ```nmap 192.168.1.1-5 -PU53```       |
| ARP discovery on local network                  | ```-PR``` | ```nmap 192.168.1.1-1/24 -PR```      |
| Never do DNS resolution                         | ```-n```  | ```nmap 192.168.1.1 -n```            |

### Port Specification

| What                                                                  | Switch           | Example                                   |
| :-------------------------------------------------------------------- | :--------------- | :---------------------------------------- |
| Port scan for port x                                                  | ```-p```         | ```nmap 192.168.1.1 -p 21```              |
| Port range                                                            | ```-p```         | ```nmap 192.168.1.1 -p 21-100```          |
| Port scan multiple TCP and UDP ports                                  | ```-p```         | ```nmap 192.168.1.1 -p U:53,T:21-25,80``` |
| Port scan all ports                                                   | ```-p```         | ```nmap 192.168.1.1 -p```-                |
| Port scan from service name                                           | ```-p```         | ```nmap 192.168.1.1 -p http,https```      |
| Fast port scan (100 ports)                                            | ```-F```         | ```nmap 192.168.1.1 -F```                 |
| Port scan the top x ports                                             | ```–top-ports``` | ```nmap 192.168.1.1 –top-ports 2000```    |
| Leaving off initial port in range makes the scan start at port 1      | ```-p-65535```   | ```nmap 192.168.1.1 -p-65535```           |
| Leaving off end port in range makes the scan go through to port 65535 | ```-p0-```       | ```nmap 192.168.1.1 -p0-```               |

### Service and Version Detection

| What                                                                       | Switch                       | Example                                         |
| :------------------------------------------------------------------------- | :--------------------------- | :---------------------------------------------- |
| Attempts to determine the version of the service running on port           | ```-sV```                    | ```nmap 192.168.1.1 -sV```                      |
| Intensity level 0 to 9. Higher number increases possibility of correctness | ```-sV –version-intensity``` | ```nmap 192.168.1.1 -sV –version-intensity 8``` |
| Enable light mode. Lower possibility of correctness. Faster                | ```-sV –version-light```     | ```nmap 192.168.1.1 -sV –version-light```       |
| Enable intensity level 9. Higher possibility of correctness. Slower        | ```-sV –version-all```       | ```nmap 192.168.1.1 -sV –version-all```         |
| Enables OS detection, version detection, script scanning, and traceroute   | ```-A```                     | ```nmap 192.168.1.1 -A```                       |

### OS Detection

| What                                                                                                 | Switch                 | Example                                   |
| :--------------------------------------------------------------------------------------------------- | :--------------------- | :---------------------------------------- |
| Remote OS detection using TCP/IP stack fingerprinting                                                | ```-O```               | ```nmap 192.168.1.1 -O```                 |
| If at least one open and one closed TCP port are not found it will not try OS detection against host | ```-O –osscan-limit``` | ```nmap 192.168.1.1 -O –osscan-limit```   |
| Makes Nmap guess more aggressively                                                                   | ```-O –osscan-guess``` | ```nmap 192.168.1.1 -O –osscan-guess```   |
| Set the maximum number x of OS detection tries against a target                                      | ```-O –max-os-tries``` | ```nmap 192.168.1.1 -O –max-os-tries 1``` |
| Enables OS detection, version detection, script scanning, and traceroute                             | ```-A```               | ```nmap 192.168.1.1 -A```                 |

### Timing and Performance

| What                                                                                       | Switch    | Example                    |
| :----------------------------------------------------------------------------------------- | :-------- | :------------------------- |
| Paranoid (0) Intrusion Detection System evasion                                            | ```-T0``` | ```nmap 192.168.1.1 -T0``` |
| Sneaky (1) Intrusion Detection System evasion                                              | ```-T1``` | ```nmap 192.168.1.1 -T1``` |
| Polite (2) slows down the scan to use less bandwidth and use less target machine resources | ```-T2``` | ```nmap 192.168.1.1 -T2``` |
| Normal (3) which is default speed                                                          | ```-T3``` | ```nmap 192.168.1.1 -T3``` |
| Aggressive (4) speeds scans; assumes you are on a reasonably fast and reliable network     | ```-T4``` | ```nmap 192.168.1.1 -T4``` |
| Insane (5) speeds scan; assumes you are on an extraordinarily fast network                 | ```-T5``` | ```nmap 192.168.1.1 -T5``` |

#### Timing and Performance Switches

| What                                                          | Switch                                                          | Example          |
| :------------------------------------------------------------ | :-------------------------------------------------------------- | :--------------- |
| Give up on target after this long                             | ```–host-timeout time```                                        | ```1s; 4m; 2h``` |
| Specifies probe round trip time                               | ```–min-rtt-timeout/max-rtt-timeout/initial-rtt-timeout time``` | ```1s; 4m; 2h``` |
| Parallel host scan group sizes                                | ```–min-hostgroup/max-hostgroup size```                         | ```50; 1024```   |
| Probe parallelization                                         | ```–min-parallelism/max-parallelism numprobes```                | ```10; 1```      |
| Specify the maximum number of port scan probe retransmissions | ```–max-retries tries```                                        | ```3```          |
| Send packets no slower than number per second                 | ```–min-rate number```                                          | ```100```        |
| Send packets no faster than number per second                 | ```–max-rate number```                                          | ```100```        |

### NSE Scripts

> NSE = Nmap Scripting Engine

| What                                                                    | Switch                | Example                                                                       |
| :---------------------------------------------------------------------- | :-------------------- | :---------------------------------------------------------------------------- |
| Scan with default NSE scripts. Considered useful for discovery and safe | ```-sC```             | ```nmap 192.168.1.1 -sC```                                                    |
| Scan with default NSE scripts. Considered useful for discovery and safe | ```–script default``` | ```nmap 192.168.1.1 –script default```                                        |
| Scan with a single script. Example banner                               | ```–script```         | ```nmap 192.168.1.1 –script=banner```                                         |
| Scan with a wildcard. Example http                                      | ```–script```         | ```nmap 192.168.1.1 –script=http*```                                          |
| Scan with two scripts. Example http and banner                          | ```–script```         | ```nmap 192.168.1.1 –script=http,banner```                                    |
| Scan default, but remove intrusive scripts                              | ```–script```         | ```nmap 192.168.1.1 –script “not intrusive”```                                |
| NSE script with arguments                                               | ```–script-args```    | ```nmap –script snmp-sysdescr –script-args snmpcommunity=admin 192.168.1.1``` |

#### Useful NSE Script Examples

| What                                           | Example                                                                                                                   |
| :--------------------------------------------- | :------------------------------------------------------------------------------------------------------------------------ |
| http site map generator                        | ```nmap -Pn –script=http-sitemap-generator scanme.nmap.org```                                                             |
| Fast search for random web servers             | ```nmap -n -Pn -p 80 –open -sV -vvv –script banner,http-title -iR 1000```                                                 |
| Brute forces DNS hostnames guessing subdomains | ```nmap -Pn –script=dns-brute domain.com```                                                                               |
| Safe SMB scripts to run                        | ```nmap -n -Pn -vv -O -sV –script smb-enum*,smb-ls,smb-mbenum,smb-os-discovery,smb-s*,smb-vuln*,smbv2* -vv 192.168.1.1``` |
| Whois query                                    | ```nmap –script whois* domain.com```                                                                                      |
| Detect cross site scripting vulnerabilities    | ```nmap -p80 –script http-unsafe-output-escaping scanme.nmap.org```                                                       |
| Check for SQL injections                       | ```nmap -p80 –script http-sql-injection scanme.nmap.org```                                                                |

### Firewall / IDS Evasion and Spoofing

| What                                                                                            | Switch             | Example                                                                          |
| :---------------------------------------------------------------------------------------------- | :----------------- | :------------------------------------------------------------------------------- |
| Requested scan (including ping scans) use tiny fragmented IP packets. Harder for packet filters | ```-f```           | ```nmap 192.168.1.1 -f```                                                        |
| Set your own offset size                                                                        | ```–mtu```         | ```nmap 192.168.1.1 –mtu 32```                                                   |
| Send scans from spoofed IPs                                                                     | ```-D```           | ```nmap -D 192.168.1.101,192.168.1.102,192.168.1.103,192.168.1.23 192.168.1.1``` |
| Above example explained                                                                         | ```-D```           | ```nmap -D decoy-ip1,decoy-ip2,your-own-ip,decoy-ip3,decoy-ip4 remote-host-ip``` |
| Scan Facebook from Microsoft (-e eth0 -Pn may be required)                                      | ```-S```           | ```nmap -S www.microsoft.com www.facebook.com```                                 |
| Use given source port number                                                                    | ```-g```           | ```nmap -g 53 192.168.1.1```                                                     |
| Relay connections through HTTP/SOCKS4 proxies                                                   | ```–proxies```     | ```nmap –proxies http://192.168.1.1:8080, http://192.168.1.2:8080 192.168.1.1``` |
| Appends random data to sent packets                                                             | ```–data-length``` | ```nmap –data-length 200 192.168.1.1```                                          |

### Outputs

| What                                                                   | Switch               | Example                                             |
| :--------------------------------------------------------------------- | :------------------- | :-------------------------------------------------- |
| Normal output to the file normal.file                                  | ```-oN```            | ```nmap 192.168.1.1 -oN normal.file```              |
| XML output to the file xml.file                                        | ```-oX```            | ```nmap 192.168.1.1 -oX xml.file```                 |
| Grepable output to the file grep.file                                  | ```-oG```            | ```nmap 192.168.1.1 -oG grep.file```                |
| Output in the three major formats at once                              | ```-oA```            | ```nmap 192.168.1.1 -oA results```                  |
| Grepable output to screen. -oN -, -oX – also usable                    | ```-oG –```          | ```nmap 192.168.1.1 -oG –```                        |
| Append a scan to a previous scan file                                  | ```–append-output``` | ```nmap 192.168.1.1 -oN file.file –append-output``` |
| Increase the verbosity level (use -vv or more for greater effect)      | ```-v```             | ```nmap 192.168.1.1 -v```                           |
| Increase debugging level (use -dd or more for greater effect)          | ```-d```             | ```nmap 192.168.1.1 -d```                           |
| Display the reason a port is in a particular state, same output as -vv | ```–reason```        | ```nmap 192.168.1.1 –reason```                      |
| Only show open (or possibly open) ports                                | ```–open```          | ```nmap 192.168.1.1 –open```                        |
| Show all packets sent and received                                     | ```–packet-trace```  | ```nmap 192.168.1.1 -T4 –packet-trace```            |
| Shows the host interfaces and routes                                   | ```–iflist```        | ```nmap –iflist```                                  |
| Resume a scan                                                          | ```–resume```        | ```nmap –resume results.file```                     |


### Helpful Nmap Output examples

| What                                                                    | Example                                                                                      |
| :---------------------------------------------------------------------- | :------------------------------------------------------------------------------------------- |
| Scan for web servers and grep to show which IPs are running web servers | ```nmap -p80 -sV -oG – –open 192.168.1.1/24 \| grep open```                                  |
| Generate a list of the IPs of live hosts                                | ```nmap -iR 10 -n -oX out.xml \| grep “Nmap” \| cut -d ” ” -f5 > live-hosts.txt```           |
| Append IP to the list of live hosts                                     | ```nmap -iR 10 -n -oX out2.xml \| grep “Nmap” \| cut -d ” ” -f5 >> live-hosts.txt```         |
| Compare output from nmap using the ndif                                 | ```ndiff scanl.xml scan2.xml```                                                              |
| Convert nmap xml files to html files                                    | ```xsltproc nmap.xml -o nmap.html```                                                         |
| Reverse sorted list of how often ports turn up                          | ```grep ” open ” results.nmap \| sed -r ‘s/ +/ /g’ \| sort \| uniq -c \| sort -rn \| less``` |

### Miscellaneous Options

| What                 | Switch   | Example                            |
| :------------------- | :------- | :--------------------------------- |
| Enable IPv6 scanning | ```-6``` | ```nmap -6 2607:f0d0:1002:51::4``` |
| nmap help screen     | ```-h``` | ```nmap -h```                      |

### Other Useful Nmap Commands

| What                                                | Example                                               |
| :-------------------------------------------------- | :---------------------------------------------------- |
| Discovery only on ports x, no port scan             | ```nmap -iR 10 -PS22-25,80,113,1050,35000 -v -sn```   |
| Arp discovery only on local network, no port scan   | ```nmap 192.168.1.1-1/24 -PR -sn -vv```               |
| Traceroute to random targets, no port scan          | ```nmap -iR 10 -sn -traceroute```                     |
| Query the Internal DNS for hosts, list targets only | ```nmap 192.168.1.1-50 -sL –dns-server 192.168.1.1``` |
