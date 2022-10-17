### Conda
[Readme](../README.md) &nbsp; [Python](Python.md)

- [Quick guide](#quick-guide)
- [Channels and packages](#channels-and-packages)
- [Working with conda environments](#working-with-conda-environments)
- [Environment management](#environment-management)
- [Exporting environments](#exporting-environments)
- [Importing environments](#importing-environments)

## Quick guide

| What                                   | Command                             |
| -------------------------------------- | :---------------------------------- |
| Verify conda install and check version | ```conda info```                    |
| Update conda in base environment       | ```conda update -n base conda```    |
| Create a new environment               | ```conda create --name ENVNAME```   |
| Activate environment                   | ```conda activate ENVNAME```        |
| Get help for any command               | ```conda COMMAND --help```          |
| Get info for any package               | ```conda search PKGNAME --info```   |
| Run commands w/o user prompt           | ```conda COMMAND ARG --yes```       |
| Installing multiple packages           | ```conda install PKG1 PKG2 --yes``` |
| Remove all unused files                | ```conda clean --all```             |
| Examine conda configuration            | ```conda config --show```           |

## Channels and packages

| What                                     | Command                                              |
| ---------------------------------------- | :--------------------------------------------------- |
| Install packages from specified channel  | ```conda install -c CHANNELNAME PKG1 PKG2```         |
| List installed packages                  | ```conda list```                                     |
| Uninstall package                        | ```conda uninstall PKGNAME```                        |
| Update all packages                      | ```conda update --all```                             |
| Install specific version of package      | ```conda install PKGNAME=3.1.4```                    |
| Install a package from specific channel  | ```conda install CHANNELNAME::PKGNAME```             |
| Install package with AND logic           | ```conda install “PKGNAME>2.5,<3.2”```               |
| Install package with OR logic            | ```conda install “PKGNAME [version=’2.5 \| 3.2’]”``` |
| List installed packages with source info | ```conda list --show-channel-urls```                 |
| View channel sources                     | ```conda config --show-sources```                    |
| Add channel                              | ```conda config --add channels CHANNELNAME```        |
| Set default channel for pkg fetching     | ```conda config --set channel_priority strict```     |

## Working with conda environments

| What                                | Command                                      |
| ----------------------------------- | :------------------------------------------- |
| List all environments and locations | ```conda env list```                         |
| Update all packages in environment  | ```conda update --all --name ENVNAME```      |
| Install packages in environment     | ```conda install --name ENVNAME PKG1 PKG2``` |
| Remove package from environment     | ```conda uninstall PKGNAME --name ENVNAME``` |
| Reactivate base environment         | ```conda activate base```                    |

## Environment management

| What                                    | Command                                              |
| --------------------------------------- | :--------------------------------------------------- |
| List packages + source channels         | ```conda list -n ENVNAME --show-channel-urls```      |
| Uninstall package from specific channel | ```conda remove -n ENVNAME -c CHANNELNAME PKGNAME``` |
| Create environment with Python version  | ```conda create -n ENVNAME python=3.10```            |
| Clone environment                       | ```conda create --clone ENVNAME -n NEWENV```         |
| List revisions made to environment      | ```conda list -n ENVNAME --revisions```              |
| Restore environment to a revision       | ```conda install -n ENVNAME --revision NUMBER```     |
| Delete environment by name              | ```conda remove -n ENVNAME --all```                  |

## Exporting environments

| What                                  | Command                                       |
| ------------------------------------- | :-------------------------------------------- |
| Cross-platform compatible             | ```conda env export --from-history>ENV.yml``` |
| Platform + package specific           | ```conda env export ENVNAME>ENV.yml```        |
| Platform + package + channel specific | ```conda list --explicit>ENV.txt```           |

## Importing environments

| What             | Command                                          |
| ---------------- | :----------------------------------------------- |
| From a .yml file | ```conda env create -n ENVNAME --file ENV.yml``` |
| From a .txt file | ```conda create -n ENVNAME --file ENV.txt```     |
