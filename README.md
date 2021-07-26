
# handicraft

> A tool to automate the setup of Minecraft launchers, loaders and mods

[![python-39-blue](https://img.shields.io/badge/python-v3.9-blue)](https://www.python.org/) [![semantic-release](https://img.shields.io/badge/%20%20%F0%9F%93%A6%F0%9F%9A%80-semantic--release-e10079.svg)](https://github.com/semantic-release/semantic-release)

[![Buy me a coffee](https://www.buymeacoffee.com/assets/img/guidelines/download-assets-sm-2.svg)](https://www.buymeacoffee.com/Ratser)

Tired of having to manually deal with the setup of all the necessary stuff to join your friend's Minecraft server? Not anymore!

Customize which components to download and install. Define which type of launcher to setup and use. Also, through a CurseForge Minecraft Instance configuration file you can select which loaders or mods to use.
Forge? Fabric? No problem!

 Share your configuration files with your friends so you can all get the same components!

![Handicraft](https://raw.githubusercontent.com/RatserX/ratserx.github.io/master/public/images/minecraft-instance-analyzer.gif)

## Prerequisites

*  [Python 3](https://www.python.org/downloads/) - Python is an interpreted, high-level and general-purpose programming language. The project already contains the Python Embeddable Package for 64-bits, so it is not mandatory on Windows.

**IMPORTANT: Check the options "Install launcher for all users (recommended)" and "Add Python to PATH", then select the "Install Now" button. Alternatively, select the "Customize installation" button, check the option "for all users (requires elevation)" when installing the Optional Features and continue the installation.**

*  [Visual C++ Redistributable for Visual Studio 2015](https://www.microsoft.com/en-us/download/details.aspx?id=48145) - The Visual C++ Redistributable Packages install run-time components that are required to run C++ applications built using Visual Studio 2015. This is only required on Windows since the embedded distribution does not include the Microsoft C Runtime.

## Installation

1.  [Download](https://github.com/RatserX/handicraft/archive/main.zip) the main project.
2. Extract the package.
3. Run as administrator either `main.bat` on Windows, `main.sh` on Linux or manually run the required commands for every other case.
```shell
pip3 install -r "requirements.txt"
python "./src/main.py"
```
5. Follow the program instructions.

## Customization

#### Structure

###### /public/

| Path | Type | Description |
| ------------ | ------------ | ------------ |
| `configuration/` | **Required** | Directory that contains all the configuration files. |
| `data/` | **Required** | Directory that stores the downloaded files. |
| `log/` | **Required** | Directory that contains log files. |
| `profile/` | **Optional** | Directory that stores CurseForge Minecraft Instance files, usually named `minecraftinstance.json`. |

###### /public/configuration/

| Path | Type | Description |
| ------------ | ------------ | ------------ |
| `autorun.json` | **Optional** | Allows you to automatically run the program by defining a valid launcher or profile key. In case this file is deleted, the program will ask you for input. |
| `launcher.json` | **Required** | Allows you to handle the setup of launchers independently for each platform (Windows, MacOS, Linux). |
| `profile.json` | **Required** | Allows you to handle the setup of loaders and mods based on a CurseForge Minecraft Instance profile. |

#### Configuration

###### autorun.json

| Key | Type | Description |
| ------------ | ------------ | ------------ |
| `launcher` | **Required** | Defines the launcher key to be automatically used. |
| `profile` | **Required** | Defines the profile key to be automatically used. |

###### launcher.json

| Key | Type | Description |
| ------------ | ------------ | ------------ |
| `[key]` | **Required** | Defines the launcher key. |
| └ `name` | **Required** | . |
| └ `platform` | **Optional** | . |
| └─ `(linux/osx/windows)` | **Optional** | . |
| └── `data` | **Optional** | . |
| └── `tasks` | **Optional** | Defines which tasks are supposed to run. Allowed tasks are: *call, cd, clear, exit, java, modal, unzip, wget*. |

###### profile.json

| Key | Type | Description |
| ------------ | ------------ | ------------ |
| `[key]` | **Required** | Defines the profile key. |
| └ `name` | **Required** | . |
| └ `location` | **Required** | Defines the location of CurseForge Minecraft Instance profiles. |
| └ `tasks` | **Required** | Defines which tasks are supposed to run. Allowed tasks are: *backup, clear, exit, java, modal, remove, wget*. |

#### Task

| Item | Parameter | Type | Description |
| ------------ | ------------ | ------------ | ------------ |
| `backup` |  |  | Creates a backup of a file or directory. |
|  | `path` | **Required** | Operation path. |
| `clear` |  |  | Clears a path from its content. |
|  | `path` | **Required** | Operation path. |
| `call` |  |  | Runs an executable file. |
|  | `file` | **Required** | Operation file. |
|  | `key` | **Required** | Operation key. |
|  | `timeout` | **Optional** | Timeout until the subprocess is killed. If null, the subprocess runs asynchronously. If less than 0, the subprocess runs until it is done. |
|  | `parameters` | **Optional** | Additional parameters. |
| `cd` |  |  | Changes the current directory. |
|  | `path` | **Required** | Operation path. |
| `dialog` |  |  | Changes the current directory. |
|  | `caption` | **Required** | Title or caption. |
|  | `header` | **Required** | Highlight or header. |
|  | `messages` | **Optional** | Body or messages. |
| `exit` |  |  | Exits a running subprocess. |
|  | `key` | **Required** | Operation key. |
| `java` |  |  | Runs a java file. |
|  | `file` | **Required** | Operation file. |
|  | `key` | **Required** | Operation key. |
|  | `timeout` | **Optional** | Timeout until the subprocess is killed. If null, the subprocess runs asynchronously. If less than 0, the subprocess runs until it is done. |
| `remove` |  |  | Removes a specific file or directory. |
|  | `path` | **Required** | Operation path. |
| `unzip` |  |  | Tries to exit a running subprocess. |
|  | `file` | **Required** | Operation file. |
| `wget` |  |  | Downloads a file from the internet. |
|  | `url` | **Required** | Operation url. |
|  | `file` | **Required** | Operation file. |
|  | `pattern` | **Optional** |  Match the url with a specific pattern. |
|  | `repl` | **Optional** | Text to replace the matched pattern with. |

© RatserX
