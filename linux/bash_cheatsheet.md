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
  - [Wildcards en andere belangrijke tekens](#wildcards-en-andere-belangrijke-tekens)
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
| ctrl+D     | verlaten cat          |
| ctrl+c     | exit                  |
| ctrl+z     | force exit            |
| ctrl+l     | clear                 |
| ctrl+(a/e) | cursor begin/end line |
| ctrl+u     | remove typed line     |
| ctrl+w     | remove word er voor   |

## Default commands

| What                                                                            | Command                                                                                                                                                                                                      |
| ------------------------------------------------------------------------------- | :----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| get path                                                                        | ```pwd```                                                                                                                                                                                                    |
| move                                                                            | ```mv source destination```                                                                                                                                                                                  |
| list files                                                                      | ```ls```  <br>  ```ls -iahl```                                                                                                                                                                               |
| find file <br> newer than <br> larger then <br>  run command on files           | ```find folder -type f -name '*.txt'```   <br> ```find folder -newermt $(date +%Y%m%d -d '1 day ago') ```   <br> ```find folder find -size +5M```<br> ```find folder -name '*.csv' -exec command '{}' \; ``` |
| get lines <br> get lines starting with<br>using [piping](#piping-and-reforming) | ```grep 'toFind' source```<br>```grep '^[1-3]' source``` <br> ```command  \| grep 'toFind'```                                                                                                                |
| disk usage                                                                      | ```du folder```                                                                                                                                                                                              |
| echo                                                                            | ```echo -n "text"```                                                                                                                                                                                         |
| get manual                                                                      | ```man commandName    ```                                                                                                                                                                                    |
| hard link                                                                       | ```ln  destination source```                                                                                                                                                                                 |
| soft link                                                                       | ```ln -s destination source```                                                                                                                                                                               |
| swap user                                                                       | ```su username```                                                                                                                                                                                            |
| run command as user                                                             | ```su username --session-command='whoami'```                                                                                                                                                                 |
| system information                                                              | ```uname -a``` <br>   ```neofetch```                                                                                                                                                                         |

## File manipulation

| What                                                      | Command                                                                 |
| --------------------------------------------------------- | :---------------------------------------------------------------------- |
| create new empyt file                                     | ```touch destination```                                                 |
| read file                                                 | ```cat source"```                                                       |
| read file scroable                                        | ```more source"```    <br>     ```less source"```                       |
| get bottom of file                                        | ```tail -n 5 source"```                                                 |
| get top of file                                           | ```head -n 5 source"```                                                 |
| get type of file                                          | ```file source```                                                       |
| differnce between files                                   | ```diff source1 source2```                                              |
| files in folder_a and not in folder_b                     | ```comm -23 <(ls folder_a \| sort) <(ls folder_b \| sort)```            |
|                                                           |
| lines in file <br> words in file  <br> characters in file | ```wc -l source ```  <br> ```wc -w source ``` <br>  ```wc -c source ``` |
| open file for img                                         | ```xdg-open file```                                                     |
| cut                                                       | ```cut -d ";" -f 1 source```                                            |
| sort rows                                                 | ```sort -k 3 --field-separator=',' source```                            |



## Networking

| What                     | Command                 |
| ------------------------ | :---------------------- |
| find own IP              | ```ip address show```   |
| download from web        | ```wget siteName    ``` |
| get from web (dont save) | ```curl siteName  ```   |



## Ssh

| What                       | Command                                                              |
| -------------------------- | :------------------------------------------------------------------- |
| remote login               | ``` ssh user@adress```  <br>  ```ssh -i ~/.ssh/id_ed25519 -l user``` |
| run local script remote    | ``` ssh address -l user 'bash -s' < local_source.sh```               |
| find terminals for X11     | ``` ls /usr/bin/  \|  grep term ```                                  |
| remote login X11 untrusted | ``` ssh -X  user@adress```                                           |
| remote login X11 trusted   | ``` ssh -Y  user@adress```                                           |
| open new terminal          | ``` lxterminal &```                                                  |
| cp files over ssh          | ``` scp user@adress:/var/source destination```                       |

## Devices

| What                  | Command                        |
| --------------------- | :----------------------------- |
| find location of disk | ```findmnt```                  |
| mount                 | ```mount /dev/sda1 /mnt/usb``` |
| unmount               | ```umount /dev/sda1```         |

## Less used ones
| What                | Command                                             |
| ------------------- | :-------------------------------------------------- |
| fix apt command     | ```dpkg --configure -a```                           |
| save correct keymap | ```localectl set-keymap --no-convert  be-latin1 ``` |
| get date            | ```date +"%Y-%m-%d"```                              |

## Wildcards en andere belangrijke tekens

| WildCard            | Notation |
| ------------------- | :------- |
| multiple Characters | *        |
| one Characters      | ?        |
| number between      | [1-3]    |
| number not between  | [!1-3]   |
| start of line       | ^        |



## Piping and reforming

| What                                        | Command                                             |
| ------------------------------------------- | :-------------------------------------------------- |
| write  to file (override) <br> write append | ```command > file```   <br>  ```command >> file ``` |
| write output <br> write errors              | ```command > file```   <br>  ```command 2> file```  |
| write to void                               | ```command >/dev/null  ```                          |
| pipe                                        | ```command \| command2  ```                         |
| use and pass                                | ```command \| tee command2  \|  command3 ```        |
| command in command                          | ```command $(command2) arg2  ```                    |
| get part of output                          | ```command  \| awk '{print $x}'```                  |

## Groups and Users   

| What                                | Command                                                                                     |
| ----------------------------------- | :------------------------------------------------------------------------------------------ |
| groups of user                      | ```groups username```                                                                       |
| add group                           | ```addgroup groupname```                                                                    |
| delete group                        | ```groupdel groupname```                                                                    |
| add user <br> user no primary group | ```useradd -d homedir -m username``` <br> ```useradd -d homedir -m -g groupname username``` |
| remove user                         | ```userdel username```                                                                      |
| add user to group                   | ```usermod -a -G groupname username```                                                      |
| lock user                           | ```passwd -l username```                                                                    |
| unlock user                         | ```passwd -u username```                                                                    |

## File permissions

| What                           | Command                      |
| ------------------------------ | :--------------------------- |
| change owner of file/dir       | ```chown username source```  |
| change group of file/dir       | ```chgrp groupname source``` |
| change permissions of file/dir | ```chmod +x source```        |



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
| start of script | ```#!/bin/bash```                                                                                                                                                                                         |
| run script      | ```./script.sh```                                                                                                                                                                                         |
| new var         | ```varname=2``` <br> ```varname=2``````varname=$(commando)```                                                                                                                                             |
| input           | ```read -p "output" varname```                                                                                                                                                                            |
| if              | ```if [ "$name" = "inside String" ];then ```<br>&nbsp;&nbsp;```       //extra code```<br>```elif [];then```<br>&nbsp;&nbsp;```//extra code```<br>```else```<br>&nbsp;&nbsp;```//extra code```<br>```fi``` |


### If statements

| What                     | Command   |
| ------------------------ | :-------- |
| equal to                 | -eq       |
| not equal to             | -ne       |
| less than                | -lt       |
| less than or equal to    | -le       |
| greater than             | -gt       |
| greater than or equal to | -gt       |
| exist                    | -e "file" |
| file exist               | -f "file" |
| dir exist                | -d "file" |
| read permission          | -r "file" |
| write permission         | -w "file" |
| execute permission       | -x "file" |


### Arguments
| What                               | Command            |
| ---------------------------------- | :----------------- |
| number of used agrs                | $#                 |
| naam van script                    | ${0}               |
| functions                          | function fname(){} |
| PID van process                    | $$                 |
| alle variables                     | $*                 |
| set  (to change behaviors in bash) | set 'commando'     |

### EXIT CODES
| What    | Exit code |
| ------- | :-------- |
| correct | 0         |
| error   | 1         |

