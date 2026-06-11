# Chapter 2: Managing Software and Processes

## 2.1 Looking at Package Concepts

- **Package:** bundle of compiled applications
- **Package Manager:** system that track packages
  1. Tracks where packages files are located for each aplication
  2. Tracks the required library files for each aplication
  3. Tracks for version controls and fetch updates

## 2.2 Using RPM (RedHat)

- **.rpm files extentions:** `PACKAGE-NAME`-`VERSION`-`RELEASE`.`ARCHITECTURE`.rpm

1. PACKAGE NAME: the name of the software
2. VERSION: the version of the software
3. RELEASE: smaller version difference than the VERSION
4. ARCHITECTURE: CPU difference (noarch, x84_64, arm)

- You need super admin for installing or update packages

Viewing RPM package files

```console
 # ls -1 *.rpm
 docker-1.13.1-94.gitb2f74b2.el7.centos.x86_64.rpm
 emacs-24.3-22.el7.x86_64.rpm
 openssh-7.4p1-16.el7.x86_64.rpm
 zsh-5.0.2-31.el7.x86_64.rpm
 #
```

- **RPM command syntax:** `rpm ACTION [ OPTION ] PACKAGE-FILE`
  1. -e --erase Removes the specified package
  2. -F --freshen Upgrades a package only if an earlier version already exists
  3. -i --install Installs the specified package
  4. -q --query Queries whether the specified package is installed
  5. -U --upgrade Installs or upgrades the specified package
  6. -V --verify Verifies whether the package files are present and the package’s integrity

Extracting Data from RPMs

```console
$ rpm2cpio emacs-24.3-22.el7.x86_64.rpm > emacs.cpio
$
```

## 2.3 Using YUM

- RPM não tem inteligência para:
  - Acessa diretamente a internet para a instalação de dependências
  - Instalar dependências de um pacote

- **Repository:** online Linux distro clearinghouse
  - Each Linux distribution keep an online list of tested and compatible packages

- YUM: user CLI tool to interact with repository.
  - Uses the `/etc/yum.repos.d` to list the directories it checks
  - Each file defines a repository requested

```console
$ ls /etc/yum.repos.d/
CentOS-Base.repo CentOS-CR.repo
CentOS-Debuginfo.repo CentOS-fasttrack.repo
CentOS-Media.repo CentOS-Sources.repo
CentOS-Vault.repo
```

- **Yum command syntax:** `yum [OPTIONS] [COMMAND] [PACKAGE..]`
  1. **check-update:** Checks the repository for updates to installed packages
  2. **deplist:** Displays dependencies for the specified package
  3. **groupinstall:** Installs the specified package group
  4. **install:** Installs the specified package
  5. **localinstall:** Installs a package from a specified RPM file
  6. **localupdate:** Updates the system from specified RPM files
  7. **provides:** Shows to what package a file belongs
  8. **reinstall:** Reinstalls the specified package
  9. **remove:** Removes a package from the system
  10. **update:** Updates the specified package(s) to the latest version in the repository
  11. **upgrade:** Updates specified package(s) but removes obsolete packages

## 2.4 Using ZYpp

1. **install:** Installs the specified package
2. **info:** Displays information about the specified package
3. **list-updates:** Displays all available package updates for installed packages from the
   repository
4. **lr:** Displays repository information
5. **packages:** Lists all available packages or lists available packages from a specified
   repository
6. **what-provides:** Shows to what package a file belongs
7. **refresh:** Refreshes a repository’s information
8. **remove:** Removes a package from the system
9. **search:** Searches for the specified package(s)
10. **update:** Updates the specified package(s) or if no package is specified, updates
11. **all:** currently installed packages to the latest version(s) in the repository
12. **verify:** Verifies that installed packages have their needed dependencies satisfied

## 2.5 Using Debian Packages

- **.deb packages**
  - Alternatives for .rpm packages
  - filename format: `PACKAGE-NAME-VERSION-RELEASE_ARCHITECTURE`.deb

- **dpkg** Command Set
  - CLI Tool for handling .deb packages
  - command syntax: `dpkg [ OPTIONS] ACTION PACKAGE-FILE`

## 2.6 Managing Shared Libraries

- Linux assign each process a **process ID**
  - When Linux boots, it starts a **init process**, that the GUI, text consoles, etc

- Viewing processes with `ps` command

```console
``$ ps -ef
UID PID PPID C STIME TTY TIME CMD
root 1 0 0 10:18 ? 00:00:03 /sbin/init splash
root 2 0 0 10:18 ? 00:00:00 [kthreadd]
root 4 2 0 10:18 ? 00:00:00 [kworker/0:0H]`
root 5 2 0 10:18 ? 00:00:00 [kworker/u2:0]
root 6 2 0 10:18 ? 00:00:00 [mm_percpu_wq]
root 7 2 0 10:18 ? 00:00:00 [ksoftirqd/0]
root 8 2 0 10:18 ? 00:00:00 [rcu_sched]
root 9 2 0 10:18 ? 00:00:00 [rcu_bh]
```

- **UID:**: the users responsible for the process
- **PID:** the process id
- **PPID:** the process id of the parent process
- **TTY:** the terminal that they started from
- **TIME:** the time of CPU used by the process
