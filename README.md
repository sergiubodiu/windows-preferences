Modern software development relies heavily on a way to manage dependencies, i.e. to keep track of required software libraries and their versions. Examples are apt-get for Linux, homebrew for MacOSX, Maven for Java and pip for Python.

Git for Windows is based on MSYS2 which bundles Arch Linux' Pacman tool for dependency management.
How to use pacman

   pacman -h  # There is a man page for pacman. 

### Install/upgrade packages

To install a package, run

    pacman -S <package-name>

To ensure that the newest package version is installed, it is recommended to pass the -y option, too, which asks Pacman to download the newest package list:

    pacman -Sy <package-name>

To upgrade all packages to their newest versions, call

    pacman -Syu

Updating msys2-runtime, pacman and bash

    As pacman.exe is itself an MSYS2 executable, it is strongly suggested to update msys2-runtime and pacman packages individually if they need to be updated, and let pacman quit immediately afterwards.

Likewise, if you run pacman from a bash -- an MSYS2 program, too -- you should quit the shell immediately (it might show an infinite stream of heap messages instead of quitting, requiring to be force-quit).
Remove packages

    pacman -R <package-name>

### List packages

To list the installed packages, call

    pacman -Q

To list the contents of a package, call

    pacman -Ql <package-name>

To find out what package a file belongs to, call

    pacman -Qo <file-name>

### Troubleshooting Issues
This issue is discusses many times. You need firs update pacman mirrors:

    pacman -Sy && pacman -S pacman-mirrors

Synchronizing package databases...
    pacman -Syw base

### Proxy 

    Located the proxy.pac file in use at my company

    In that file, identified the fall-thru proxy (i.e. domains not redirected elsewhere), defined as

return "PROXY wwwproxy:8080";

Added this to my MSYS2 shell environment:

```
export http_proxy=<myusername>:<mypassword>@proxy-host-name:8080
export https_proxy=$http_proxy
export ftp_proxy=$http_proxy
export rsync_proxy=$http_proxy
export no_proxy="localhost,127.0.0.1,localaddress,.localdomain.com"
```

