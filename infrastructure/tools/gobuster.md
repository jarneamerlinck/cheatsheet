---
topic: gobuster
type: tool
site: https://github.com/OJ/gobuster
status: tried
included_topics: 
 - cli
 - hacking
language:
 - bash
history:
  found: 2023/04/21
  tried: 2023/04/21
  used: 
  core: 
  hold: 
os:
  - linux
  - windows
  - mac
---

# gobuster

> gobuster is 

## tool notes
# GoBuster
[Readme](../../README.md)

- [GoBuster](#gobuster)
  - [Available Modes](#available-modes)
  - [Global flags](#global-flags)
  - [DNS Mode Options](#dns-mode-options)
  - [DIR Mode Options](#dir-mode-options)
  - [vhost Mode Options](#vhost-mode-options)

## Available Modes

| What                                                                 | Switch      | Example                                                                |
| :------------------------------------------------------------------- | :---------- | :--------------------------------------------------------------------- |
| The classic directory brute-forcing mode                             | ```dir```   | ```gobuster dir -u https://example.com -w ~/wordlists/shortlist.txt``` |
| DNS subdomain brute-forcing mode                                     | ```dns```   | ```gobuster dns -d example.com -t 50 -w common-names.txt```            |
| Enumerate open S3 buckets and look for existence and bucket listings | ```s3```    | ```gobuster vhost -u https://example.com -w common-vhosts.txt```       |
| Irtual host brute-forcing mode (not the same as DNS!)                | ```vhost``` | ```gobuster s3 -w bucket-names.txt```                                  |

## Global flags

| What                                                 | Switch    | long Switch             |
| :--------------------------------------------------- | :-------- | :---------------------- |
| Don't display progress                               | ```-z```  | ```--no-progress```     |
| Output file to write results to (defaults to stdout) | ```-o```  | ```--output string```   |
| Don't print the banner and other noise               | ```-q```  | ```--quiet```           |
| Number of concurrent threads (default 10)            | ```-t```  | ```--threads int```     |
| Show IP addresses                                    | ```-i```  | ```--show-ips```        |
| DNS resolver timeout (default 1s)                    |           | ```--delay duration```  |
| Verbose output (errors)                              | ```-v```  | ```--verbose```         |
| Path to the wordlist                                 | ```-w ``` | ```--wordlist string``` |

## DNS Mode Options

| What                                                         | Switch   | long Switch              |
| :----------------------------------------------------------- | :------- | :----------------------- |
| Help for dns                                                 | ```-h``` | ```--help```             |
| The target domain                                            | ```-d``` | ```--domain string```    |
| Use custom DNS server (format server.com or server.com:port) | ```-r``` | ```--resolver string```  |
| Show CNAME records (cannot be used with '-i' option)         | ```-c``` | ```--show-cname```       |
| Show IP addresses                                            | ```-i``` | ```--show-ips```         |
| DNS resolver timeout (default 1s)                            |          | ```--timeout duration``` |

## DIR Mode Options

| What                                                                                                                   | Switch   | long Switch                    |
| :--------------------------------------------------------------------------------------------------------------------- | :------- | :----------------------------- |
| Help for dir                                                                                                           | ```-h``` | ```--help```                   |
| Append / to each request                                                                                               | ```-f``` | ```--add-slash```              |
| Cookies to use for the requests                                                                                        | ```-c``` | ```--cookies string```         |
| Expanded mode, print full URLs                                                                                         | ```-e``` | ```--expanded```               |
| File extension(s) to search for                                                                                        | ```-x``` | ```--extensions string```      |
| Follow redirects                                                                                                       | ```-r``` | ```--follow-redirect```        |
| Specify HTTP headers, -H 'Header1: val1' -H 'Header2: val2'                                                            | ```-H``` | ```--headers stringArray```    |
| Include the length of the body in the output                                                                           | ```-l``` | ```--include-length```         |
| Skip TLS certificate verification                                                                                      | ```-k``` | ```--no-tls-validation```      |
| Don't print status codes                                                                                               | ```-n``` | ```--no-status```              |
| Password for Basic Auth                                                                                                | ```-P``` | ```--password string```        |
| Proxy to use for requests \[http(s)://host:port\]                                                                      | ```-p``` | ```--proxy string```           |
| Positive status codes (will be overwritten with status-codes-blacklist if set) (default "200,204,301,302,307,401,403") | ```-s``` | ```--status-codes string```    |
| String Negative status codes (will override status-codes if set)                                                       | ```-b``` | ```--status-codes-blacklist``` |
| HTTP Timeout (default 10s)                                                                                             |          | ```--timeout duration```       |
| The target URL                                                                                                         | ```-u``` | ```--url string```             |

## vhost Mode Options

| What                                                        | Switch   | long Switch                 |
| :---------------------------------------------------------- | :------- | :-------------------------- |
| Help for vhost                                              | ```-h``` | ```--help```                |
| Cookies to use for the requests                             | ```-c``` | ```--cookies string```      |
| Follow redirects                                            | ```-r``` | ```--follow-redirect```     |
| Specify HTTP headers, -H 'Header1: val1' -H 'Header2: val2' | ```-H``` | ```--headers stringArray``` |
| Skip TLS certificate verification                           | ```-k``` | ```--no-tls-validation```   |
| Password for Basic Auth                                     | ```-P``` | ```--password string```     |
| Proxy to use for requests \[http(s)://host:port\]           | ```-p``` | ```--proxy string```        |
| HTTP Timeout (default 10s)                                  |          | ```--timeout duration```    |
| The target URL                                              | ```-u``` | ```--url string```          |
| Set the User-Agent string (default "gobuster/3.1.0")        | ```-a``` | ```--useragent string```    |
| Username for Basic Auth                                     | ```-U``` | ```--username string```     |
