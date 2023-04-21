---
topic: FTP
type: protocol
site: https://en.wikipedia.org/wiki/File_Transfer_Protocol
sort: network
project: cheatsheet
date: 2023/04/21
---

# Protocol FTP
[Readme](../README.md)
## Information

> SMB = File Transfer Protocol

- Network protocol 
  - TCP/IP
- Active/passive
  - Active FTP connection, the client opens a port and listens. The server is required to actively connect to it
  - Passive FTP connection, the server opens a port and listens (passively) and the client connects to it
- A client-server protocol 
- Sharing access to files, printers, serial ports and other resources

## Working

![FTP working](../Images/FTP_Working.png)

## Commands
### Default commands

| What                 | Command            |
| -------------------- | :----------------- |
| List files           | ```list```         |
| change dir           | ```CWD dir```      |
| change to parent dir | ```CDUP```         |
| Create dir           | ```MKD dir```      |
| Remove dir           | ```RMD dir```      |
| Rename file          | ```rename old new``` |
| Delete file          | ```delete file```    |

### Transfer files

| What                             | Command                           |
| -------------------------------- | :-------------------------------- |
| Upload file/folder               | ```put file```                   |
| Append to serverfile file/folder | ```append local_file server_file``` |
| Download file/folder             | ```get file```                   |

### Other commands

| What                       | Command               |
| -------------------------- | :-------------------- |
| Get info over command      | ```?command```       |
| Run command in local shell | ```!shell-command``` |