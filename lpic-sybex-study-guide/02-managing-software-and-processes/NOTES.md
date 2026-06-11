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

- **RPM command set:** rpm `ACTION` [ `OPTION` ] `PACKAGE-FILE`
  1. -e --erase Removes the specified package
  2. -F --freshen Upgrades a package only if an earlier version already exists
  3. -i --install Installs the specified package
  4. -q --query Queries whether the specified package is installed
  5. -U --upgrade Installs or upgrades the specified package
  6. -V --verify Verifies whether the package files are present and the package’s integrity

- Extracting Data from RPMs

```console
$ rpm2cpio emacs-24.3-22.el7.x86_64.rpm > emacs.cpio
$
```

## 2.3 Using YUM

- RPM não tem inteligência para:
  - Não acessa diretamente a internet para a instalação de dependências
  - Instalar dependências de um pacote

- **Repository:** online linux distro clearinghouse
  - Each linux distribution keep an online list of tested and compatible packages

- YUM: user tool to
