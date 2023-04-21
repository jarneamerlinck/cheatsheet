---
topic: chezmoi
type: tool
site: https://www.chezmoi.io/
status: hold
included_topics: 
 - cli
history:
  found: 2022/04/21
  tried: 2022/04/21
  used: 2022/04/21
  core: 
  hold: 2023/04/21
os:
  - linux
---

# chezmoi

> chezmoi is 

## tool notes


# Chezmoi
[Readme](../README.md)
## workflow
![I²C working](../Images/chezmoi_workflow.png)

| What     | Command                                                      |
| -------- | :----------------------------------------------------------- |
| install  | ```sh -c "$(curl -fsLS chezmoi.io/get)"   ```                |
| init     | ```chezmoi init git@github.com:/jarneamerlinck/dotconfig ``` |
| add file | ```chezmoi add file```                                    |
| edit     | ```chezmoi edit file```                                   |
| apply    | ```chezmoi apply```                                       |
| update   | ```chezmoi update```                                      |