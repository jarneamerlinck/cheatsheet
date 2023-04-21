---
topic: Hydra
type: tool
site: https://github.com/vanhauser-thc/thc-hydra
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

# Hydra
[Readme](../../README.md)

- [Hydra](#hydra)
	- [Global flags](#global-flags)
	- [Examples](#examples)


## Global flags

| What      | Switch   |
| :-------- | :------- |
| User      | ```-l``` |
| Word list | ```-P``` |
| Threads   | ```-t``` |
| Output    | ```-o``` |
| Verbose    | ```-vV``` |

## Examples

| What                 | Command                                                                              |
| :------------------- | :----------------------------------------------------------------------------------- |
| password hack on ftp | ```hydra -t 4 -l user_name -P /usr/share/wordlists/rockyou.txt -vV 10.10.10.6 ftp``` |