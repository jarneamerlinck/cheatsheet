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
| What               | Keys                |
| ------------------ | :------------------ |
| Detach session     | ```PREFIX d```      |
| Move in window     | ```PREFIX arrows``` |
| Move other window  | ```PREFIX n/p```    |
| List windows       | ```PREFIX w```      |
| List sessies       | ```PREFIX s```      |
| Show plane numbers | ```PREFIX q```      |
| Set clock          | ```PREFIX t```      |
| Commands           | ```PREFIX :```      |
| Zoom               | ```PREFIX z```      |
|                    |
| Start copy         | ```PREFIX [```      |
| Move to start      | ```ctrl  space```   |
| Move to end        | ```alt  w```        |
| Past               | ```PREFIX ]```      |

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
