---
topic: git_cheatsheet
type: tool
site: https://git-scm.com/
status: core
included_topics:
  - backend
  - CI/CD
  - cli
language:
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

# git_cheatsheet

> git_cheatsheet is 

## tool notes
# Git
[Readme](README.md)
- [Git](#git)
	- [Configs](#configs)
	- [Normal Commands](#normal-commands)
		- [Bisect](#bisect)
		- [Add Patch](#add-patch)
	- [Remotes](#remotes)
	- [Logs](#logs)
	- [Stash](#stash)
	- [Branches](#branches)
		- [Merge](#merge)
			- [Merge error](#merge-error)
			- [Merge Types](#merge-types)
				- [Explicit Merges](#explicit-merges)
				- [Implicit merge](#implicit-merge)
				- [Squash](#squash)
			- [Merge strategy](#merge-strategy)
				- [Recursive](#recursive)
				- [Resolve](#resolve)
				- [Octopus](#octopus)
				- [Ours](#ours)
				- [Subtree](#subtree)
			- [Merge strategy options for Recursive strategy](#merge-strategy-options-for-recursive-strategy)
				- [ours](#ours-1)
				- [theirs](#theirs)
				- [patience](#patience)
				- [ignore](#ignore)
				- [renormalize](#renormalize)
				- [no-normalize](#no-normalize)
				- [no-renames](#no-renames)
				- [rename-threshold=n](#rename-thresholdn)
				- [subtree](#subtree-1)
	- [Advanced commands](#advanced-commands)
		- [Interactive rebase](#interactive-rebase)
			- [Workflow](#workflow)
			- [Change author of commit](#change-author-of-commit)

## Configs
- add --global to make the settings apply for all git repo's on the system

| What                             | Command                                                         |
| -------------------------------- | :-------------------------------------------------------------- |
| Set username                     | ```git config user.name "John Doe"```                           |
| Set email                        | ```git config  user.email johndoe@example.com```                |
| Set editer                       | ```git config --global core.editor vim```                       |
| Set commit template              | ```git config commit.template ~/.gitmessage.txt```              |
| Set excludesfile                 | ```git config --global core.excludesfile ~/.gitignore_global``` |
| Set git protocol for github auth | ```gh config set -h github.com git_protocol https```            |


## Normal Commands

| What                                                          | Command                                                                        |
| ------------------------------------------------------------- | :----------------------------------------------------------------------------- |
| Add  <br> [Add part of file](#add-patch)<br> Add deleted file | ```git add file```   <br>```git add --patch filename``` <br>```git add -u  ``` |
| Commit                                                        | ```git commit file```                                                          |
| Delete file from git                                          | ```git rm file```                                                              |
| Push                                                          | ```git push```   <br>      ```git push remote_name```                          |
| Pull                                                          | ```git pull```   <br>      ```git pull remote_name```                          |
| Fetch                                                         | ```git fetch```  <br> ```git fetch --tags``` <br>  ```git fetch remote_name``` |
| Revert commit                                                 | ```git revert commit_hash```                                                   |

### Bisect
Steps
| step                   | Command                           |
| ---------------------- | :-------------------------------- |
| Start bisect           | ```git bisect start```            |
| Its bad here           | ```git bisect bad```              |
| Worked at              | ```git bisect good commit_name``` |
| Works in current state | ```git bisect good```             |
| State can't be tested  | ```git bisect skip```             |
| View bisect            | ```git bisect visualize```        |
| Save bisect            | ```git bisect log```              |
| *Exit* bisect          | ```git bisect reset```            |


### Add Patch
select a part of a file for the  next commit

>y:    stage this hunk for the next commit
>
>n:    do not stage this hunk for the next commit
>
>q:    quit; do not stage this hunk or any of the remaining hunks
>
>a:    stage this hunk and all later hunks in the file
>
>d:    do not stage this hunk or any of the later hunks in the file
>
>g:    select a hunk to go to
>
>s:    split the current hunk into smaller hunks
>
>e:    manually edit the current hunk
>
>?: print help

## Remotes
 

| What            | Command                                                                                                 |
| --------------- | :------------------------------------------------------------------------------------------------------ |
| Show remotes    | ```git remote -v```                                                                                     |
| Show one remote | ```git remote show shortname```                                                                         |
| Set remote      | ```git remote set shortname remote_url```                                                               |
| Rename remote   | ```git remote rename original_name new_name```                                                          |
| Remove remote   | ```git remote remove shortname```                                                                       |
| mirror an repo  | ```git clone url --mirror```  <br>  ```git remote add upstream url``` <br> ```git clone url --mirror``` |


## Logs

| What                        | Command                          |
| --------------------------- | :------------------------------- |
| Show logs                   | ```git log```                    |
| Show logs between 2 commits | ```git log commit_1..commit_2``` |
| Show x commits              | ```git log -n 2```               |
| Show commit in one line     | ```git log --oneline```          |
| Show graph                  | ```git log --graph```            |
| Show decorate               | ```git log --decorate```         |
| Show stats                  | ```git log --stat```             |
| Show patch                  | ```git log-p```                  |
| Seach for                   | ```git log --grep="pattern"```   |
| Seach for                   | ```git log --author="pattern"``` |
| Include file                | ```git log file```               |



## Stash

| What                                   | Command                               |
| -------------------------------------- | :------------------------------------ |
| Show stashes                           | ```git stash show"```                 |
| Stash uncommited changes               | ```git stash save "stash_name"```     |
| Stash uncommited changes and new files | ```git stash -u  save "stash_name"``` |
| Apply last stash and remove it         | ```git stash pop```                   |
| Apply last stash and keep it           | ```git stash apply ```                |
| Apply selected stash and remove it     | ```git stash pop stash@{2}```         |
| Apply last stash and keep it           | ```git stash apply stash@{2} ```      |

## Branches
| What                                       | Command                                                                              |
| ------------------------------------------ | :----------------------------------------------------------------------------------- |
| Show all branches                          | ```git branch -a```                                                                  |
| Enter branch (creates if not exist)        | ```git checkout branch_name```  <br>    ```git checkout branch_name origin_branch``` |
| Create branch with empty history           | ```git switch --orphan newBranchName```                                              |
| Remove branche                             | ```git branch -d branch_name```                                                      |
| Merge feature_branch into receiving_branch | ```git checkout receiving_branch```<br>```git merge feature_branch```                |
| Rebase                                     | ```git rebase -a```                                                                  |

### Merge
#### Merge error
- Look ```git status``` or ```git log --merge```
#### Merge Types
##### Explicit Merges 
Explicit merges are the default merge type. The 'explicit' part is that they create a new merge commit. This alters the commit history and explicitly shows where a merge was executed. The merge commit content is also explicit in the fact that it shows which commits were the parents of the merge commit. Some teams avoid explicit merges because arguably the merge commits add "noise" to the history of the project.
##### Implicit merge
rebase or fast-forward merge  without merge commit.
##### Squash
```git merge --squash feature/login```  

This will squash the entire banch in to the receiving one without commiting it. This is used in pull requests.


#### Merge strategy

##### Recursive

```git merge -s recursive branch1 branch2```

This operates on two heads. Recursive is the default merge strategy when pulling or merging one branch. Additionally this can detect and handle merges involving renames, but currently cannot make use of detected copies. This is the default merge strategy when pulling or merging one branch.

##### Resolve

```git merge -s resolve branch1 branch2```

This can only resolve two heads using a 3-way merge algorithm. It tries to carefully detect cris-cross merge ambiguities and is considered generally safe and fast.

##### Octopus

```git merge -s octopus branch1 branch2 branch3 branchN```

The default merge strategy for more than two heads. When more than one branch is passed octopus is automatically engaged. If a merge has conflicts that need manual resolution octopus will refuse the merge attempt. It is primarily used for bundling similar feature branch heads together.

##### Ours

```git merge -s ours branch1 branch2 branchN```

The Ours strategy operates on multiple N number of branches. The output merge result is always that of the current branch HEAD. The "ours" term implies the preference effectively ignoring all changes from all other branches. It is intended to be used to combine history of similar feature branches.

##### Subtree

```git merge -s subtree branchA branchB```

This is an extension of the recursive strategy. When merging A and B, if B is a child subtree of A, B is first updated to reflect the tree structure of A, This update is also done to the common ancestor tree that is shared between A and B.


merge                   $ git merge oldBranch

enter last branch             $ git checkout -

#### Merge strategy options for Recursive strategy



##### ours

```git merge -s recursive -X ours```
```git merge --strategy recursive --strategy-option ours``` 
Not to be confused with the Ours merge strategy. This option conflicts to be auto-resolved cleanly by favoring the 'our' version. Changes from the 'theirs' side are automatically incorporated if they do not conflict.

##### theirs

```git merge -s recursive -X theirs```
```git merge --strategy recursive --strategy-option theirs```
The opposite of the 'ours' strategy. the "theirs" option favors the foreign merging tree in conflict resolution.

##### patience

```git merge -s recursive -X patience```
```git merge --strategy recursive --strategy-option patience```
This option spends extra time to avoid mis-merges on unimportant matching lines. This options is best used when branches to be merged have extremely diverged.


##### ignore
- ignore-space-change
- ignore-all-space
- ignore-space-at-eol
- ignore-cr-at-eol

```git merge -s recursive -X ignore-space-change```
```git merge --strategy recursive --strategy-option ignore-space-change```

A set of options that target whitespace characters. Any line that matches the subset of the passed option will be ignored.

##### renormalize

```git merge -s recursive -X renormalize```
```git merge --strategy recursive --strategy-option renormalize```

This option runs a check-out and check-in on all of the tree git trees while resolving a three-way merge. This option is intended to be used with merging branches with differing checkin/checkout states.

##### no-normalize

```git merge -s recursive -X renormalize```
```git merge --strategy recursive --strategy-option renormalize```

Disables the renormalize option. This overrides the merge.renormalize configuration variable.

##### no-renames

```git merge -s recursive -X no-renames```
```git merge --strategy recursive --strategy-option no-renames```

This option will ignore renamed files during the merge.

##### rename-threshold=n

```git merge -s recursive -X rename-threshold=25```
```git merge --strategy recursive --strategy-option rename-threshold=25```
This is the default behavior. The recursive merge will honor file renames. The n parameter can be used to pass a threshold for rename similarity. The default n value is 100%.

##### subtree

```git merge -s recursive -X subtree```
```git merge --strategy recursive --strategy-option subtree```

This option borrows from the `subtree` strategy. Where the strategy operates on two trees and modifies how to make them match on a shared ancestor, this option instead operates on the path metadata of the tree to make them match.






## Advanced commands
### Interactive rebase

- change commits 

| What                     | Command                         |
| ------------------------ | :------------------------------ |
| Rebase to commit         | ```git rebase -i commit_hash``` |
| Continue to next commit | ```git rebase --continue```     |


#### Workflow


1. Rebase to commit before the earliest commit you want to change
2. Change `pick` to `edit` to all commits you want to edit
3. Edit commit and Continue to next commit with ```git rebase --continue```
4. Continue untill  the last commit you changed to edit
5. push to origin with ```git push --force-with-lease```


#### Change author of commit
- In rebase
  - ```git commit --amend --author="Author Name <email@address.com>" --no-edit```

