---
topic: SMB
type: protocol
site: https://tool.io/
sort: network
project: cheatsheet
date: 2023/04/21
---

# Protocol SMB
[Readme](../README.md)
## Information

> SMB = Server Message Block

- Network protocol 
  - TCP/IP
  - NetBIOS
  - NetBEUI
  - IPX/SPX
- Response-request protocol
- A client-server communication protocol 
- Sharing access to files, printers, serial ports and other resources

## Working

![SMB working](../Images/SMB_Working.png)

## Commands
### Default commands

| What                    | Command            |
| ----------------------- | :----------------- |
| List files              | ```ls```           |
| List all info over file | ```allinfo file``` |
| Enable recurse mode     | ```recurse```      |
| Upload file/folder      | ```mput file```    |
| Download file/folder    | ```mget file```    |
| Delete file             | ```del file```     |

### Other commands
| What                       | Command               |
| -------------------------- | :-------------------- |
| Get info over command      | ```? command```       |
| Run command in local shell | ```! shell-command``` |