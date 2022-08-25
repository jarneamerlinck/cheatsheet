# Package managers
[Readme](../README.md)
## Packman
### Commands

| What                                 | Command                   |
| ------------------------------------ | :------------------------ |
| Update official packages             | ```sudo pacman -Syu```    |
| Update all packages                  | ```yay -Syu```            |
| Install package from official repo   | ```sudo pacman -S pkg ``` |
| Install package from unofficial repo | ```yay -S pkg ```         |

### Important

- "yay" should not be used by an superuser or sudo.
- "yay" installs AUR-packages that everyone can upload. So be aware of the posibility that you could be installing a virius. Run it trought the MAKEPGK file for security.

## Apt
### Commands
| What                                                      | Command                                 |
| --------------------------------------------------------- | :-------------------------------------- |
| Update the repo's                                         | ```sudo apt update```                   |
| Upgrade  all packages                                     | ```sudo apt upgrade```                  |
| Install an package                                        | ```sudo apt install pkg```              |
| Remove an package                                         | ```sudo apt remove pkg```               |
| Purge an package                                          | ```sudo apt purge pkg```                |
| Try to fix apt                                            | ```dpkg --configure -a```               |
| Add repo                                                  | ```sudo add-apt-repository repo_name``` |
| Remove installed dependencies that are no longer required | ```sudo apt autoremove```               |

### Nala
Please don't use apt anymore Nala is better. Below after install to swap apt to nala 
```bash
apt() { 
  command nala "$@"
}
sudo() {
  if [ "$1" = "apt" ]; then
    shift
    command sudo nala "$@"
  else
    command sudo "$@"
  fi
}



```
| What                  | Command                                                                                                                                                                                                                                                                                                                                                                       |
| --------------------- | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| install               | ```echo "deb http://deb.volian.org/volian/ scar main" \| sudo tee /etc/apt/sources.list.d/volian-archive-scar-unstable.list```<br>```wget -qO - https://deb.volian.org/volian/scar.key  \| sudo tee /etc/apt/trusted.gpg.d/volian-archive-scar-unstable.gpg```<br>```sudo apt update && sudo apt install nala```  <br>  ```sudo apt update && sudo apt install nala-legacy``` |
| Fetch                 | ```sudo nala fetch```                                                                                                                                                                                                                                                                                                                                                         |
| Upgrade  all packages | ```sudo nala upgrade```                                                                                                                                                                                                                                                                                                                                                       |
| Install an package    | ```sudo nala install pkg```                                                                                                                                                                                                                                                                                                                                                   |
| Remove an package     | ```sudo nala remove pkg```                                                                                                                                                                                                                                                                                                                                                    |
| Purge an package      | ```sudo nala purge pkg```                                                                                                                                                                                                                                                                                                                                                     |
| show history          | ```sudo nala history```                                                                                                                                                                                                                                                                                                                                                       |
| undo history item 1   | ```sudo sudo nala history undo 1```                                                                                                                                                                                                                                                                                                                                           |




## Dnf
### Commands
| What                                                      | Command                     |
| --------------------------------------------------------- | :-------------------------- |
| Check for updates                                         | ```sudo dnf check-update``` |
| Upgrade  all packages                                     | ```sudo dnf upgrade```      |
| Seach an package                                          | ```sudo dnf search pkg```   |
| Install an package                                        | ```sudo dnf install pkg```  |
| Remove an package                                         | ```sudo dnf remove pkg```   |
| Remove installed dependencies that are no longer required | ```sudo dnf autoremove```   |



