---
topic: Volatility
type: tool
site: https://github.com/volatilityfoundation/volatility3
status: tried
included_topics: 
 - cli
 - hacking
language:
 - python
 - bash
history:
  found: 2023/04/21
  tried: 
  used: 
  core: 
  hold: 
os:
  - linux
  - windows
  - mac
---

# Volatility
[Readme](../../README.md)

- [Volatility](#volatility)
  - [Install](#install)
  - [Global flags](#global-flags)
  - [Examples](#examples)

## Install
- `git clone https://github.com/volatilityfoundation/volatility3`
- `cd volatility3;pip install -e requirements-minimal.txt`
- 
## Global flags

| Description                                                                                           | Option   | Example                                              |
| ----------------------------------------------------------------------------------------------------- | -------- | ---------------------------------------------------- |
| This argument is where you provide the name and location of the memory dump that you wish to analyse. | ```-f``` | ```python3 vol.py -f /path/to/my/memorydump.vmem```  |
| This  argument increases the verbosity of Volatility. For debugging.                                  | ```-v``` | ```python3 vol.py -v```                              |
| This argument allows you to override the default location of where plugins are stored.                | ```-p``` | ```python3 vol.py -p /path/to/my/custom/plugins```   |
| This argument allows you to specify where extracted processes or DLLs are stored.                     | ```-o``` | ```python3 vol.py -o /output/extracted/files/here``` |


## Plugins

| Plugin            | Description                                                                                                           | Objective                                                                                                                                                                                                                                                                                                                                                       |
|-------------------|-----------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| windows.pslist    | This plugin lists all of the processes that were running at the time of the capture.                                  | To discover what processes were running on the system.                                                                                                                                                                                                                                                                                                          |
| windows.psscan    | This plugin allows us to analyse a specific process further.                                                          | To discover what a specific process was actually doing.                                                                                                                                                                                                                                                                                                         |
| windows.dumpfiles | This plugin allows us to export the process, where we can perform further analysis (i.e. static or dynamic analysis). | To export a specific binary that allows us further to analyse it through static or dynamic analysis.                                                                                                                                                                                                                                                            |
| windows.netstat   | This plugin lists all network connections at the time of the capture.                                                 | To  understand what connections were being made. For example, was a process  causing the computer to connect to a malicious server? We can use this  IP address to implement defensive measures on other devices. For  example, if we know an IP address is malicious, and another device is  communicating with it, then we know that device is also infected. |


