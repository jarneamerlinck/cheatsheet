---
topic: snapper
type: tool
site: https://snapper.io/manpages/snapper.html
status: core
included_topics:
  - cli
history:
  found: 2024/09/01
  found: 2024/09/01
  found: 2024/09/01
  found: 2024/09/11
  hold:
os:
  - linux
---

# Snapper
[Readme](../README.md)

> Snapper is a snapshot tool for linux (best for with btrfs)

| What                             | Command                                                                       |
| -------------------------------- | :---------------------------------------------------------------------------- |
| List all snapshots (of /)                       | ```snapper list``` |
| List all snapshots of a specific subvolume                       | ```snapper -c home list``` |
| Create new snapshot (for subvolume)                      | ```snapper -c home create``` |
| Create new snapshot (for subvolume)                      | ```snapper -c home create``` |
| Restore snapshot n (for subvolume)                      | ```snapper -c home undochange n..0``` |
