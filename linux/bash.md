---
topic: bash
type: language
site: https://www.gnu.org/software/bash/
status: core
included_topics:
  - cli
history:
  found: 2019/04/21
  tried: 2019/04/21
  used: 2023/04/21
  core: 2023/04/21
  hold:
os:
  - linux
---

# Bash
[Readme](../README.md)
- [Bash](#bash)
  - [Terminal short cuts](#terminal-short-cuts)
  - [Default commands](#default-commands)
  - [File manipulation](#file-manipulation)
  - [Networking](#networking)
  - [Ssh](#ssh)
  - [Devices](#devices)
  - [Less used ones](#less-used-ones)
  - [Wildcards](#wildcards)
  - [Piping and reforming](#piping-and-reforming)
  - [Groups and Users](#groups-and-users)
  - [File permissions](#file-permissions)
    - [File/folder permissions](#filefolder-permissions)
    - [Chmod options](#chmod-options)
  - [Scripts](#scripts)
    - [If statements](#if-statements)
    - [Arguments](#arguments)
    - [EXIT CODES](#exit-codes)

## Terminal short cuts

| Shortcut   | Meaning               |
| ---------- | :-------------------- |
| ctrl+R     | Reverse search        |
| ctrl+D     | Leave Terminal        |
| ctrl+c     | exit command          |
| ctrl+z     | force exit            |
| ctrl+l     | clear                 |
| ctrl+(a/e) | cursor begin/end line |
| ctrl+u     | remove typed line     |
| ctrl+w     | remove word before    |

## Default commands

| What                                                                            | Command                                                                                                                                                                                                      |
| ------------------------------------------------------------------------------- | :----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Get path                                                                        | ```pwd```                                                                                                                                                                                                    |
| Move                                                                            | ```mv source destination```                                                                                                                                                                                  |
| List files                                                                      | ```ls```  <br>  ```ls -iahl```                                                                                                                                                                               |
| Find file <br> newer than <br> larger then <br>  run command on files           | ```find folder -type f -name '*.txt'```   <br> ```find folder -newermt $(date +%Y%m%d -d '1 day ago') ```   <br> ```find folder find -size +5M```<br> ```find folder -name '*.csv' -exec command '{}' \; ``` |
| Get lines <br> get lines starting with<br>using [piping](#piping-and-reforming) | ```grep 'toFind' source```<br>```grep '^[1-3]' source``` <br> ```command  \| grep 'toFind'```                                                                                                                |
| Disk usage                                                                      | ```du folder```                                                                                                                                                                                              |
| Echo                                                                            | ```echo -n "text"```                                                                                                                                                                                         |
| Get manual                                                                      | ```man commandName    ```                                                                                                                                                                                    |
| Hard link                                                                       | ```ln  destination source```                                                                                                                                                                                 |
| Soft link                                                                       | ```ln -s destination source```                                                                                                                                                                               |
| Swap user                                                                       | ```su username```                                                                                                                                                                                            |
| Run command as user                                                             | ```su username --session-command='whoami'```                                                                                                                                                                 |
| System information                                                              | ```uname -a``` <br>   ```neofetch```                                                                                                                                                                         |

## File manipulation

| What                                                      | Command                                                                 |
| --------------------------------------------------------- | :---------------------------------------------------------------------- |
| Create new empyt file                                     | ```touch destination```                                                 |
| Read file                                                 | ```cat source"```                                                       |
| Read file scroable                                        | ```more source"```    <br>     ```less source"```                       |
| Get bottom of file                                        | ```tail -n 5 source"```                                                 |
| Get top of file                                           | ```head -n 5 source"```                                                 |
| Get type of file                                          | ```file source```                                                       |
| Differnce between files                                   | ```diff source1 source2```                                              |
| Files in folder_a and not in folder_b                     | ```comm -23 <(ls folder_a \| sort) <(ls folder_b \| sort)```            |
|                                                           |
| Lines in file <br> words in file  <br> characters in file | ```wc -l source ```  <br> ```wc -w source ``` <br>  ```wc -c source ``` |
| Open file for img                                         | ```xdg-open file```                                                     |
| Cut                                                       | ```cut -d ";" -f 1 source```                                            |
| Sort rows                                                 | ```sort -k 3 --field-separator=',' source```                            |



## Networking

| What                     | Command                              |
| ------------------------ | :----------------------------------- |
| Find own IP              | ```ip address show``` <br>```ip a``` |
| Download from web        | ```wget siteName    ```              |
| Get from web (dont save) | ```curl siteName  ```                |



## Ssh

| What                       | Command                                                              |
| -------------------------- | :------------------------------------------------------------------- |
| Remote login               | ``` ssh user@adress```  <br>  ```ssh -i ~/.ssh/id_ed25519 -l user``` |
| Run local script remote    | ``` ssh address -l user 'bash -s' < local_source.sh```               |
| Find terminals for X11     | ``` ls /usr/bin/  \|  grep term ```                                  |
| Remote login X11 untrusted | ``` ssh -X  user@adress```                                           |
| Remote login X11 trusted   | ``` ssh -Y  user@adress```                                           |
| Open new terminal          | ``` lxterminal &```                                                  |
| Cp files over ssh          | ``` scp user@adress:/var/source destination```                       |

## Devices

| What                  | Command                        |
| --------------------- | :----------------------------- |
| Find location of disk | ```findmnt```                  |
| Mount                 | ```mount /dev/sda1 /mnt/usb``` |
| Unmount               | ```umount /dev/sda1```         |

## Less used ones
| What                | Command                                             |
| ------------------- | :-------------------------------------------------- |
| Fix apt command     | ```dpkg --configure -a```                           |
| Save correct keymap | ```localectl set-keymap --no-convert  be-latin1 ``` |
| Get date            | ```date +"%Y-%m-%d"```                              |

## Wildcards

| WildCard            | Notation |
| ------------------- | :------- |
| Multiple Characters | *        |
| One Characters      | ?        |
| Number between      | [1-3]    |
| Number not between  | [!1-3]   |
| Start of line       | ^        |



## Piping and reforming

| What                                        | Command                                             |
| ------------------------------------------- | :-------------------------------------------------- |
| Write  to file (override) <br> write append | ```command > file```   <br>  ```command >> file ``` |
| Write output <br> write errors              | ```command > file```   <br>  ```command 2> file```  |
| Write to void                               | ```command >/dev/null  ```                          |
| Pipe                                        | ```command \| command2  ```                         |
| Use and pass                                | ```command \| tee command2  \|  command3 ```        |
| Command in command                          | ```command $(command2) arg2  ```                    |
| Get part of output                          | ```command  \| awk '{print $x}'```                  |

## Groups and Users   

| What                                | Command                                                                                     |
| ----------------------------------- | :------------------------------------------------------------------------------------------ |
| Groups of user                      | ```groups username```                                                                       |
| Add group                           | ```addgroup groupname```                                                                    |
| Delete group                        | ```groupdel groupname```                                                                    |
| Add user <br> user no primary group | ```useradd -d homedir -m username``` <br> ```useradd -d homedir -m -g groupname username``` |
| Remove user                         | ```userdel username```                                                                      |
| Add user to group                   | ```usermod -a -G groupname username```                                                      |
| Reload groups without logout        | ```newgrp -```                                                                              |
| Lock user                           | ```passwd -l username```                                                                    |
| Unlock user                         | ```passwd -u username```                                                                    |

## File permissions

| What                           | Command                      |
| ------------------------------ | :--------------------------- |
| Change owner of file/dir       | ```chown username source```  |
| Change group of file/dir       | ```chgrp groupname source``` |
| Change permissions of file/dir | ```chmod +x source```        |



### File/folder permissions
- 3 bits (rwx)for user, group and other
  - r: read
  - w: wite
  - x: execute

| Command | file     | folder                                         |
| ------- | :------- | :--------------------------------------------- |
| r       | Read     | Read                                           |
| w       | write    | write                                          |
| x       | excecute | ls folder content (needed for other 2 actions) |



### Chmod options

```chown WOP source```
| What      | Meaning                                              | Command               |
| --------- | :--------------------------------------------------- | :-------------------- |
| Who       | user<br>group<br>other<br>all                        | u<br>g<br>o<br>a      |
| Operator  | add<br>remove<br>set                                 | +<br>-<br>=           |
| Privilege | Read<br>write<br>execute <br>sticky bit<br>SUID/SGID | r<br>w<br>x<br>t<br>s |

- Sticky bit
  
    Setting this makes it so only the create of a file may remove it.

- SUID/SGID (switch user ID/switch group ID)

    This will give everyone permission to execute the file with the permissions of the user who set the +s switch.


## Scripts

**This is very space sensitive**

**Pick " OVER ' for strings**

| What            | Command                                                                                                                                                                                                   |
| --------------- | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Start of script | ```#!/bin/bash```                                                                                                                                                                                         |
| Run script      | ```./script.sh```                                                                                                                                                                                         |
| New var         | ```varname=2``` <br> ```varname=2``````varname=$(commando)```                                                                                                                                             |
| Input           | ```read -p "output" varname```                                                                                                                                                                            |
| If              | ```if [ "$name" = "inside String" ];then ```<br>&nbsp;&nbsp;```       //extra code```<br>```elif [];then```<br>&nbsp;&nbsp;```//extra code```<br>```else```<br>&nbsp;&nbsp;```//extra code```<br>```fi``` |


### If statements

| What                     | Command   |
| ------------------------ | :-------- |
| Equal to                 | -eq       |
| Not equal to             | -ne       |
| Less than                | -lt       |
| Less than or equal to    | -le       |
| Greater than             | -gt       |
| Greater than or equal to | -gt       |
| Exist                    | -e "file" |
| File exist               | -f "file" |
| Dir exist                | -d "file" |
| Read permission          | -r "file" |
| Write permission         | -w "file" |
| Execute permission       | -x "file" |


### Arguments
| What                               | Command            |
| ---------------------------------- | :----------------- |
| Number of used agrs                | $#                 |
| Naam van script                    | ${0}               |
| Functions                          | function fname(){} |
| PID van process                    | $$                 |
| Alle variables                     | $*                 |
| Set  (to change behaviors in bash) | set 'commando'     |

### EXIT CODES
| What    | Exit code |
| ------- | :-------- |
| correct | 0         |
| error   | 1         |

