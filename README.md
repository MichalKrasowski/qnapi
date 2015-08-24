# QNapi

QNapi is free software for automatic fetching subtitles for given movie file.
It uses online databases such as NapiProjekt, OpenSubtitles and Napisy24.
It is based on Qt5 library, so it can be launched on any supported operating
system, including Windows, OSX and Linux.

## Binary packages

Latest binary packages are available at http://qnapi.github.io/#download

## Building from source

#### Prerequisites

* C++ compiler installed (`clang++`, `g++` or *MinGW* for Windows), present in `PATH`
* Qt5 installed with `qmake` present in `PATH` (you can find one at http://www.qt.io/download-open-source/)

#### Binary prerequisities

QNapi depends on these binary executables:

* 7zip (7z, 7za) - to unpack subtitles, which are commonly compressed with 7z
* ffprobe (from ffmpeg) - to retrieve movie info such as dimensions or frame rate

Linux/UNIX users will have such binaries as separate packages.

Statically compiled 7zip binaries are provided in this repository for Windows/OSX
users at `win32/content/7za.exe` and `macx/content/7za`, respectively.

> **Important!** For Windows or OSX users it is required to manually download and unpack ffprobe binary.
>
> * Windows - `ffprobe.exe` static binary is available at http://ffmpeg.zeranoe.com/builds/win32/static/ and should be unpacked to `win32/content/`
> * OSX - `ffprobe` static binary is available at https://evermeet.cx/pub/ffprobe/ and should be unpacked to `macx/content`


#### Cloning the source code

First, you have to clone project source code using git client:

`$ git clone --recursive https://github.com/QNapi/qnapi.git`

#### Compiling

To compile the application, you have to execute two following commands in `qnapi` root directory:

`$ qmake`

This will produce `Makefile`.

`$ make` (or `mingw32-make` on Windows)

This will compile the sources and build executable binary (or app bundle on OSX).

> **Important!** Windows users have to execute one more command:
>
> `$ make install` (or `mingw32-make install`)
>
> This one will copy all binaries, libraries and other dependencies to `win32/out` directory.

#### Running

By default, output binaries are placed by `make` in different locations, depending on your operating system:

* Linux - `qnapi` in root project directory
* OSX - `macx/QNapi.app` bundle
* Windows - `win32/out/qnapi.exe` executable

After you locate your binaries, you can run the application.

> ##### 7zip note #####
> For proper subtitle extraction after download, *7zip* executable is required to be passed in application's settings.
> Linux users have to install 7zip binary package from distribution repositories or compile on its own.
> For Windows and OSX there are pre-build binaries included in this repository, in `win32` and `macx` directories appropriately and should be automatically detected by the application.

## Making redistributable package

### OSX

#### Prerequisites

You need `appdmg` script installed. You can found it at https://github.com/LinusU/node-appdmg

#### Building .dmg image

To build .dmg image for OSX with nice, drag&drop installer, you have to execute:

`$ make appdmg`

`QNapi-x.y.z.dmg` will appear in `macx` directory when command is completed.

### Windows

#### Prerequisites

You need to have **NSIS** 2.x installed. You can found it at http://nsis.sourceforge.net

#### Building Windows installer

Installer script is placed at `win32/QNapi-setup.nsi`. You can build binary exe package using NSIS user interface (by `right mouse button -> compile NSIS script`) or from command line:

`$ C:\Path\To\makensis.exe QNapi-setup.nsi`

After a while, `QNapi-x.y.z-setup.exe` file will appear in `win32` directory.
