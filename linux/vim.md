---
topic: vim
type: tool
site: https://www.vim.org/
status: core
included_topics: 
 - cli
history:
  found: 2022/04/21
  tried: 2022/04/21
  used: 2022/04/21
  core: 2023/01/1
  hold: 
os:
  - linux
  - mac
---


# vim
[Readme](README.md)

- [vim](#vim)
	- [Command mode](#command-mode)
		- [Bookmarks](#bookmarks)
		- [Move](#move)
		- [Select](#select)
		- [Modify selected](#modify-selected)
		- [Insert mode enter options](#insert-mode-enter-options)
		- [special insert](#special-insert)
	- [insert mode](#insert-mode)

## Command mode

| What                | Keys                |
| ------------------- | :------------------ |
| Exit vim            | ```:q```            |
| Exit no save        | ```:q!```           |
| Save                | ```:w```            |
| Save exit           | ```:wq```           |
| Show line number    | ```:set number```   |
| Move to line number | ```:30```           |
| Save exit           | ```ZZ```            |
| Repeat last         | ```command	@:```    |
| Repeat more         | ```@@```            |
| Read only           | ```read fileName``` |
| Del line            | ```dd```            |
| Undo                | ```u```             |
| Redo                | ```ctrl+r```        |
| End of file         | ```G```             |
| Begin of file       | ```gg```            |
| Reload file         | ```:e!```           |
| Open tab            | ```:tabe file```    |
| Change tab          | ```:tabn```         |
| Prev tab            | ```:tabp```         |

### Bookmarks

| What | Keys              |
| ---- | :---------------- |
| Set  | ```m {a-z A-Z}``` |
| List | ```:marks ```     |
| Go   | ```'{a-z A-Z}```  |

### Move

| what      | previous | next     |
| --------- | :------- | :------- |
| Sentence  | ```(```  | ```)```  |
| Paragraph | ```{```  | ```}```  |
| Section   | ```[[``` | ```]]``` |

### Select

| What                                                 | Keys                                     |
| ---------------------------------------------------- | :--------------------------------------- |
| Per caracter                                         | ```v```                                  |
| Per line                                             | ```V```                                  |
| Escape                                               | ```esc```                                |
| Find  <br>next<br>previous                           | ```/toSearch``` <br> ```n```<br> ```N``` |
| Replace  <br>/g is for all<br>/c is for conformation | ```:%s/orignal/new/gc```                 |
| Open manual                                          | ```shift+k```                            |

### Modify selected

| What           | Keys      |
| -------------- | :-------- |
| Switch case    | ```~```   |
| Del            | ```d```   |
| Change         | ```c```   |
| Select         | ```v/V``` |
| Yank           | ```yy```  |
| Past           | ```p```   |
| Filter command | ```!```   |


### Insert mode enter options

| What           | Keys    |
| -------------- | :------ |
| After cursor   | ```a``` |
| End of line    | ```A``` |
| Before cursor  | ```i``` |
| New line below | ```o``` |
| New line above | ```O``` |

### special insert

| What           | Keys                 |
| -------------- | :------------------- |
| File           | ```:r [filename]```  |
| Output command | ```:r! [filename]``` |


man command					 shift+k
move to line				 :30		move line 30




## insert mode

- exit by hitting 	 'esc'

| What               | Kes          |
| ------------------ | :----------- |
| Predict            | ```ctrl n``` |
| Use last predicted | ```ctrl p``` |
