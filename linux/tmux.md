---
topic: tmux
type: tool
site: https://github.com/tmux/tmux/wiki
status: core
included_topics: 
 - cli
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

# Tmux
[Readme](../README.md)

- [Tmux](#tmux)
	- [Commands](#commands)
	- [Shortcuts](#shortcuts)
	- [tmux nesting](#tmux-nesting)
	- [Plugin keys](#plugin-keys)

## Commands

- ```ctrl+b``` = PREFIX


| What                 | Command                               |
| -------------------- | :------------------------------------ |
| Enter                | ```tmux new -s sesionName```          |
| Atach existing shell | ```tmux attach -t sesionName```       |
| Kill sesion          | ```tmux kill-session -t sesionName``` |
| List sessions        | ```tmux list-sessions```              |


## Shortcuts
| What                      | Keys                              |
| ------------------------- | :-------------------------------- |
| Detach session            | ```PREFIX d```                    |
| Move in window            | ```PREFIX arrows```               |
| Move other window         | ```PREFIX n/p```                  |
| List windows              | ```PREFIX w```                    |
| List sessies              | ```PREFIX s```                    |
| Show pane numbers         | ```PREFIX q```                    |
| Show clock in pane        | ```PREFIX t```                    |
| Commands                  | ```PREFIX :```                    |
| Zoom to pane              | ```PREFIX z```                    |
|                           |
| Start copy                | ```PREFIX [```                    |
| Move to start             | ```ctrl  space```                 |
| Move to end               | ```alt  w```                      |
| Past                      | ```PREFIX ]```                    |
|                           |
| New window                | ```PREFIX c```                    |
| Rename window             | ```PREFIX ,```                    |
| Close current window      | ```PREFIX &```                    |
|                           |
| Split pane horizontal     | ```PREFIX "```                    |
| Split pane vertically     | ```PREFIX %```                    |
| Current pane to window    | ```PREFIX !```                    |
| Close current pane        | ```PREFIX x```                    |
| Move between pane layouts | ```PREFIX space```                |
| Change size of pane       | ```PREFIX arrows``` (hold PREFIX) |



## tmux nesting
| What         | Keys                  |
| ------------ | :-------------------- |
| Send command | ```PREFIX command```  |
| Detach       | ```PREFIX PREFIX d``` |

## Plugin keys
| What               | Keys                 |
| ------------------ | :------------------- |
| Install/refresh    | ```PREFIX I```       |
| Update plugins     | ```PREFIX U```       |
| Remove not in list | ```PREFIX  alt  U``` |
