<h1 align="center">
  <div>
    <img src="https://raw.githubusercontent.com/adrg/adrg.github.io/master/assets/projects/xdg/logo.svg" alt="xdg logo"/>
  </div>
</h1>

<h4 align="center">Go implementation of the XDG Base Directory Specification and XDG user directories.</h4>

<p align="center">
    <a href="https://github.com/adrg/xdg/actions?query=workflow%3ACI">
        <img alt="Build status" src="https://github.com/adrg/xdg/workflows/CI/badge.svg">
    </a>
    <a href="https://app.codecov.io/gh/adrg/xdg">
        <img alt="Code coverage" src="https://codecov.io/gh/adrg/xdg/branch/master/graphs/badge.svg?branch=master">
    </a>
    <a href="https://pkg.go.dev/github.com/adrg/xdg">
        <img alt="pkg.go.dev documentation" src="https://img.shields.io/badge/go.dev-reference-007d9c?logo=go&logoColor=white">
    </a>
    <a href="https://opensource.org/licenses/MIT" rel="nofollow">
        <img alt="MIT license" src="https://img.shields.io/github/license/adrg/xdg">
    </a>
    <br />
    <a href="https://goreportcard.com/report/github.com/adrg/xdg">
        <img alt="Go report card" src="https://goreportcard.com/badge/github.com/adrg/xdg">
    </a>
    <a href="https://github.com/avelino/awesome-go#configuration">
        <img alt="Awesome Go" src="https://awesome.re/mentioned-badge.svg">
    </a>
    <a href="https://github.com/adrg/xdg/graphs/contributors">
        <img alt="GitHub contributors" src="https://img.shields.io/github/contributors/adrg/xdg" />
    </a>
    <a href="https://github.com/adrg/xdg/issues">
        <img alt="GitHub open issues" src="https://img.shields.io/github/issues-raw/adrg/xdg">
    </a>
    <a href="https://ko-fi.com/T6T72WATK">
        <img alt="Buy me a coffee" src="https://img.shields.io/static/v1.svg?label=%20&message=Buy%20me%20a%20coffee&color=579fbf&logo=buy%20me%20a%20coffee&logoColor=white">
    </a>
</p>

Provides an implementation of the [XDG Base Directory Specification](https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html).
The specification defines a set of standard paths for storing application files,
including data and configuration files. For portability and flexibility reasons,
applications should use the XDG defined locations instead of hardcoding paths.
The package also includes the locations of well known [user directories](https://wiki.archlinux.org/index.php/XDG_user_directories).

The current implementation supports most flavors of Unix, Windows, Mac OS and Plan 9.  
Full documentation can be found at https://pkg.go.dev/github.com/adrg/xdg.

## Installation
    go get github.com/adrg/xdg

## Default locations

The package defines sensible defaults for XDG variables which are empty or not
present in the environment.

### XDG Base Directory

<details open>
    <summary><strong>Unix-like operating systems</strong></summary>
    <br/>

| <a href="#xdg-base-directory"><img width="400" height="0"></a> | <a href="#xdg-base-directory"><img width="500" height="0"></a><p>Unix</p> | <a href="#xdg-base-directory"><img width="600" height="0"></a><p>macOS</p>                                            | <a href="#xdg-base-directory"><img width="500" height="0"></a><p>Plan 9</p> |
| :------------------------------------------------------------: | :-----------------------------------------------------------------------: | :-------------------------------------------------------------------------------------------------------------------: | :-------------------------------------------------------------------------: |
| <kbd><b><samp>XDG_DATA_HOME</samp></b></kbd>                   | <kbd>~/.local/share</kbd>                                                 | <kbd>~/Library/Application&nbsp;Support</kbd>                                                                         | <kbd>$home/lib</kbd>                                                        |
| <kbd><b><samp>XDG_DATA_DIRS</samp></b></kbd>                   | <kbd>/usr/local/share</kbd><br/><kbd>/usr/share</kbd>                     | <kbd>/Library/Application&nbsp;Support</kbd>                                                                          | <kbd>/lib</kbd>                                                             |
| <kbd><b><samp>XDG_CONFIG_HOME</samp></b></kbd>                 | <kbd>~/.config</kbd>                                                      | <kbd>~/Library/Application&nbsp;Support</kbd>                                                                         | <kbd>$home/lib</kbd>                                                        |
| <kbd><b><samp>XDG_CONFIG_DIRS</samp></b></kbd>                 | <kbd>/etc/xdg</kbd>                                                       | <kbd>~/Library/Preferences</kbd><br/><kbd>/Library/Application&nbsp;Support</kbd><br/><kbd>/Library/Preferences</kbd> | <kbd>/lib</kbd>                                                             |
| <kbd><b><samp>XDG_STATE_HOME</samp></b></kbd>                  | <kbd>~/.local/state</kbd>                                                 | <kbd>~/Library/Application&nbsp;Support</kbd>                                                                         | <kbd>$home/lib/state</kbd>                                                  |
| <kbd><b><samp>XDG_CACHE_HOME</samp></b></kbd>                  | <kbd>~/.cache</kbd>                                                       | <kbd>~/Library/Caches</kbd>                                                                                           | <kbd>$home/lib/cache</kbd>                                                  |
| <kbd><b><samp>XDG_RUNTIME_DIR</samp></b></kbd>                 | <kbd>/run/user/UID</kbd>                                                  | <kbd>~/Library/Application&nbsp;Support</kbd>                                                                         | <kbd>/tmp</kbd>                                                             |

</details>

<details open>
    <summary><strong>Microsoft Windows</strong></summary>
    <br/>

| <a href="#xdg-base-directory"><img width="400" height="0"></a> | <a href="#xdg-base-directory"><img width="700" height="0"></a><p>Folder IDs</p> | <a href="#xdg-base-directory"><img width="900" height="0"></a><p>Default paths</p> |
| :------------------------------------------------------------: | :-----------------------------------------------------------------------------: | :--------------------------------------------------------------------------------: |
| <kbd><b><samp>XDG_DATA_HOME</samp></b></kbd>                   | <kbd>FOLDERID_LocalAppData</kbd>                                                | <kbd>%LOCALAPPDATA%</kbd>                                                          |
| <kbd><b><samp>XDG_DATA_DIRS</samp></b></kbd>                   | <kbd>FOLDERID_RoamingAppData</kbd><br/><kbd>FOLDERID_ProgramData</kbd>          | <kbd>%APPADATA%</kbd><br/><kbd>%ProgramData%</kbd>                                 |
| <kbd><b><samp>XDG_CONFIG_HOME</samp></b></kbd>                 | <kbd>FOLDERID_LocalAppData</kbd>                                                | <kbd>%LOCALAPPDATA%</kbd>                                                          |
| <kbd><b><samp>XDG_CONFIG_DIRS</samp></b></kbd>                 | <kbd>FOLDERID_ProgramData</kbd><br/><kbd>FOLDERID_RoamingAppData</kbd>          | <kbd>%ProgramData%</kbd><br/><kbd>%APPDATA%</kbd>                                  |
| <kbd><b><samp>XDG_STATE_HOME</samp></b></kbd>                  | <kbd>FOLDERID_LocalAppData</kbd>                                                | <kbd>%LOCALAPPDATA%</kbd>                                                          |
| <kbd><b><samp>XDG_CACHE_HOME</samp></b></kbd>                  | <kbd>FOLDERID_LocalAppData\cache</kbd>                                          | <kbd>%LOCALAPPDATA%\cache</kbd>                                                    |
| <kbd><b><samp>XDG_RUNTIME_DIR</samp></b></kbd>                 | <kbd>FOLDERID_LocalAppData</kbd>                                                | <kbd>%LOCALAPPDATA%</kbd>                                                          |

</details>

### XDG user directories

<details open>
    <summary><strong>Unix-like operating systems</strong></summary>
    <br/>

| <a href="#xdg-base-directory"><img width="500" height="0"></a> | <a href="#xdg-base-directory"><img width="500" height="0"></a><p>Unix</p> | <a href="#xdg-base-directory"><img width="500" height="0"></a><p>macOS</p>                                            | <a href="#xdg-base-directory"><img width="500" height="0"></a><p>Plan 9</p> |
| :------------------------------------------------------------: | :-----------------------------------------------------------------------: | :-------------------------------------------------------------------------------------------------------------------: | :-------------------------------------------------------------------------: |
| <kbd><b><samp>XDG_DESKTOP_DIR</samp></b></kbd>                 | <kbd>~/Desktop</kbd>                                                      | <kbd>~/Desktop</kbd>                                                                                                  | <kbd>$home/desktop</kbd>                                                    |
| <kbd><b><samp>XDG_DOWNLOAD_DIR</samp></b></kbd>                | <kbd>~/Downloads</kbd>                                                    | <kbd>~/Downloads</kbd>                                                                                                | <kbd>$home/downloads</kbd>                                                  |
| <kbd><b><samp>XDG_DOCUMENTS_DIR</samp></b></kbd>               | <kbd>~/Documents</kbd>                                                    | <kbd>~/Documents</kbd>                                                                                                | <kbd>$home/documents</kbd>                                                  |
| <kbd><b><samp>XDG_MUSIC_DIR</samp></b></kbd>                   | <kbd>~/Music</kbd>                                                        | <kbd>~/Music</kbd>                                                                                                    | <kbd>$home/music</kbd>                                                      |
| <kbd><b><samp>XDG_PICTURES_DIR</samp></b></kbd>                | <kbd>~/Pictures</kbd>                                                     | <kbd>~/Pictures</kbd>                                                                                                 | <kbd>$home/pictures</kbd>                                                   |
| <kbd><b><samp>XDG_VIDEOS_DIR</samp></b></kbd>                  | <kbd>~/Videos</kbd>                                                       | <kbd>~/Movies</kbd>                                                                                                   | <kbd>$home/videos</kbd>                                                     |
| <kbd><b><samp>XDG_TEMPLATES_DIR</samp></b></kbd>               | <kbd>~/Templates</kbd>                                                    | <kbd>~/Templates</kbd>                                                                                                | <kbd>$home/templates</kbd>                                                  |
| <kbd><b><samp>XDG_PUBLICSHARE_DIR</samp></b></kbd>             | <kbd>~/Public</kbd>                                                       | <kbd>~/Public</kbd>                                                                                                   | <kbd>$home/public</kbd>                                                     |

</details>

<details open>
    <summary><strong>Microsoft Windows</strong></summary>
    <br/>

| <a href="#xdg-base-directory"><img width="500" height="0"></a> | <a href="#xdg-base-directory"><img width="600" height="0"></a><p>Folder IDs</p> | <a href="#xdg-base-directory"><img width="900" height="0"></a><p>Default paths</p> |
| :------------------------------------------------------------: | :-----------------------------------------------------------------------------: | :--------------------------------------------------------------------------------: |
| <kbd><b><samp>XDG_DESKTOP_DIR</samp></b></kbd>                 | <kbd>FOLDERID_Desktop</kbd>                                                     | <kbd>%USERPROFILE%\Desktop</kbd>                                                   |
| <kbd><b><samp>XDG_DOWNLOAD_DIR</samp></b></kbd>                | <kbd>FOLDERID_Downloads</kbd>                                                   | <kbd>%USERPROFILE%\Downloads</kbd>                                                 |
| <kbd><b><samp>XDG_DOCUMENTS_DIR</samp></b></kbd>               | <kbd>FOLDERID_Documents</kbd>                                                   | <kbd>%USERPROFILE%\Documents</kbd>                                                 |
| <kbd><b><samp>XDG_MUSIC_DIR</samp></b></kbd>                   | <kbd>FOLDERID_Music</kbd>                                                       | <kbd>%USERPROFILE%\Music</kbd>                                                     |
| <kbd><b><samp>XDG_PICTURES_DIR</samp></b></kbd>                | <kbd>FOLDERID_Pictures</kbd>                                                    | <kbd>%USERPROFILE%\Pictures</kbd>                                                  |
| <kbd><b><samp>XDG_VIDEOS_DIR</samp></b></kbd>                  | <kbd>FOLDERID_Videos</kbd>                                                      | <kbd>%USERPROFILE%\Videos</kbd>                                                    |
| <kbd><b><samp>XDG_TEMPLATES_DIR</samp></b></kbd>               | <kbd>FOLDERID_Templates</kbd>                                                   | <kbd>%APPDATA%\Microsoft\Windows\Templates</kbd>                                   |
| <kbd><b><samp>XDG_PUBLICSHARE_DIR</samp></b></kbd>             | <kbd>FOLDERID_Public</kbd>                                                      | <kbd>%PUBLIC%</kbd>                                                                 |

</details>

### Non-standard directories

<details open>
    <summary><strong>Unix-like operating systems</strong></summary>
    <br/>

| <a href="#xdg-base-directory"><img width="400" height="0"></a> | <a href="#xdg-base-directory"><img width="600" height="0"></a><p>Unix</p>                                                                                                                                        | <a href="#xdg-base-directory"><img width="600" height="0"></a><p>macOS</p>                                                               | <a href="#xdg-base-directory"><img width="400" height="0"></a><p>Plan 9</p> |
| :------------------------------------------------------------: | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: | :--------------------------------------------------------------------------------------------------------------------------------------: | :-------------------------------------------------------------------------: |
| <kbd><b><samp>Application&nbsp;directories</samp></b></kbd>    | <kbd>$XDG_DATA_HOME/applications</kbd><br/><kbd>~/.local/share/applications</kbd><br/><kbd>/usr/local/share/applications</kbd><br/><kbd>/usr/share/applications</kbd><br/><kbd>$XDG_DATA_DIRS/applications</kbd> | <kbd>/Applications</kbd>                                                                                                                 | <kbd>$home/bin</kbd>                                                        |
| <kbd><b><samp>Font directories</samp></b></kbd>                | <kbd>$XDG_DATA_HOME/fonts</kbd><br/><kbd>&#126;/.fonts</kbd><br/><kbd>~/.local/share/fonts</kbd><br/><kbd>/usr/local/share/fonts</kbd><br/><kbd>/usr/share/fonts</kbd><br/><kbd>$XDG_DATA_DIRS/fonts</kbd>       | <kbd>~/Library/Fonts</kbd><br/><kbd>/Library/Fonts</kbd><br/><kbd>/System/Library/Fonts</kbd><br/><kbd>/Network/Library/Fonts</kbd>      | <kbd>$home/bin</kbd><br/><kbd>/bin</kbd>                                    |

</details>

<details open>
    <summary><strong>Microsoft Windows</strong></summary>
    <br/>

| <a href="#xdg-base-directory"><img width="400" height="0"></a> | <a href="#xdg-base-directory"><img width="300" height="0"></a><p>Folder IDs</p> | <a href="#xdg-base-directory"><img width="1300" height="0"></a><p>Default paths</p>                                                     |
| :------------------------------------------------------------: | :-----------------------------------------------------------------------------: | :-------------------------------------------------------------------------------------------------------------------------------------: |
| <kbd><b><samp>Application&nbsp;directories</samp></b></kbd>    | <kbd>FOLDERID_Programs</kbd><br/><kbd>FOLDERID_CommonPrograms</kbd>             | <kbd>%APPDATA%\Microsoft\Windows\Start&nbsp;Menu\Programs</kbd><br/><kbd>%ProgramData%\Microsoft\Windows\Start&nbsp;Menu\Programs</kbd> |
| <kbd><b><samp>Font directories</samp></b></kbd>                | <kbd>FOLDERID_Fonts</kbd><br/><kbd>-</kbd>                                      | <kbd>%SystemRoot%\Fonts</kbd><br/><kbd>%LOCALAPPDATA%\Microsoft\Windows\Fonts</kbd>                                                     |

</details>

## Usage

#### XDG Base Directory

```go
package main

import (
	"log"

	"github.com/adrg/xdg"
)

func main() {
	// XDG Base Directory paths.
	log.Println("Home data directory:", xdg.DataHome)
	log.Println("Data directories:", xdg.DataDirs)
	log.Println("Home config directory:", xdg.ConfigHome)
	log.Println("Config directories:", xdg.ConfigDirs)
	log.Println("Home state directory:", xdg.StateHome)
	log.Println("Cache directory:", xdg.CacheHome)
	log.Println("Runtime directory:", xdg.RuntimeDir)

	// Non-standard directories.
	log.Println("Application directories:", xdg.ApplicationDirs)
	log.Println("Font directories:", xdg.FontDirs)

	// Obtain a suitable location for application config files.
	// ConfigFile takes one parameter which must contain the name of the file,
	// but it can also contain a set of parent directories. If the directories
	// don't exist, they will be created relative to the base config directory.
	configFilePath, err := xdg.ConfigFile("appname/config.yaml")
	if err != nil {
		log.Fatal(err)
	}
	log.Println("Save the config file at:", configFilePath)

	// For other types of application files use:
	// xdg.DataFile()
	// xdg.StateFile()
	// xdg.CacheFile()
	// xdg.RuntimeFile()

	// Finding application config files.
	// SearchConfigFile takes one parameter which must contain the name of
	// the file, but it can also contain a set of parent directories relative
	// to the config search paths (xdg.ConfigHome and xdg.ConfigDirs).
	configFilePath, err = xdg.SearchConfigFile("appname/config.yaml")
	if err != nil {
		log.Fatal(err)
	}
	log.Println("Config file was found at:", configFilePath)

	// For other types of application files use:
	// xdg.SearchDataFile()
	// xdg.SearchStateFile()
	// xdg.SearchCacheFile()
	// xdg.SearchRuntimeFile()
}
```

#### XDG user directories

```go
package main

import (
	"log"

	"github.com/adrg/xdg"
)

func main() {
	// XDG user directories.
	log.Println("Desktop directory:", xdg.UserDirs.Desktop)
	log.Println("Download directory:", xdg.UserDirs.Download)
	log.Println("Documents directory:", xdg.UserDirs.Documents)
	log.Println("Music directory:", xdg.UserDirs.Music)
	log.Println("Pictures directory:", xdg.UserDirs.Pictures)
	log.Println("Videos directory:", xdg.UserDirs.Videos)
	log.Println("Templates directory:", xdg.UserDirs.Templates)
	log.Println("Public directory:", xdg.UserDirs.PublicShare)
}
```

## Stargazers over time

[![Stargazers over time](https://starchart.cc/adrg/xdg.svg)](https://starchart.cc/adrg/xdg)

## Contributing

Contributions in the form of pull requests, issues or just general feedback,
are always welcome.  
See [CONTRIBUTING.MD](CONTRIBUTING.md).

**Contributors**:
[adrg](https://github.com/adrg),
[wichert](https://github.com/wichert),
[bouncepaw](https://github.com/bouncepaw),
[gabriel-vasile](https://github.com/gabriel-vasile),
[KalleDK](https://github.com/KalleDK),
[nvkv](https://github.com/nvkv),
[djdv](https://github.com/djdv).

## References

For more information see:
* [XDG Base Directory Specification](https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html)
* [XDG user directories](https://wiki.archlinux.org/index.php/XDG_user_directories)
* [Windows Known Folders](https://docs.microsoft.com/en-us/windows/win32/shell/knownfolderid)

## License

Copyright (c) 2014 Adrian-George Bostan.

This project is licensed under the [MIT license](https://opensource.org/licenses/MIT).
See [LICENSE](LICENSE) for more details.
