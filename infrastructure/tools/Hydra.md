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