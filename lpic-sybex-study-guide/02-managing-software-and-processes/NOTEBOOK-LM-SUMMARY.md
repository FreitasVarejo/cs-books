# NOTEBOOK LM SUMMARY CHAPTER 2

## Looking at Package Concepts

### Core Commands & Concepts

- **Package:** A bundle containing most of the files required to run a single application.
- **Package Management:** The system of tracking installed software via a database, which logs packages, exact files, library dependencies, and file locations.
- **Repository:** A central clearinghouse of software packages maintained by each Linux distribution, accessible via the Internet.

### Command Variants & Alternatives

- **Flatpak:** An alternative new trend in package management. Instead of just delivering files, Flatpak combines package management, software deployment, and application sandboxing. It provides all needed dependencies and runs the application in an isolated virtualized environment, protecting the rest of the system.

---

## Using RPM

### Core Commands & Concepts

- **RPM Naming Convention:** Packages follow the standard `NAME-VERSION-RELEASE.ARCHITECTURE.rpm`.
- **RELEASE (Build Number):** Represents a smaller program modification than a version number. Can include a VCS (Version Control System) string (e.g., `.gitb2f74b2`) or the distribution version (e.g., `el7` for Red Hat Enterprise Linux v7, `fc29` for Fedora).
- **Primary Commands:** `rpm`, `rpm2cpio`, `cpio`.

### Command Variants & Alternatives

- **`rpm2cpio` & `cpio` vs `rpm`:** While `rpm` installs and manages packages, sometimes you need to extract and review files without installing them. The `rpm2cpio` command converts the `.rpm` file into a `cpio` archive, which can then be piped into the `cpio` command to extract the raw files.

### Flags, Options & Configurations

#### `rpm` Command Actions (Table 2.1)

| Short / Long Flag  | Description & Behavior                                            | Example Syntax        |
| :----------------- | :---------------------------------------------------------------- | :-------------------- |
| `-e` / `--erase`   | Removes the specified package.                                    | `rpm -e zsh`          |
| `-F` / `--freshen` | Upgrades a package _only_ if an earlier version already exists.   | `rpm -F package.rpm`  |
| `-v` / `--verbose` | Provides detailed, verbose output.                                | `rpm -vh package.rpm` |
| `-h` / `--hash`    | Prints hash marks (`#`) to display the progress of the operation. | `rpm -vh package.rpm` |

#### `rpm` Query Action Options (Table 2.2)

| Short / Long Flag      | Description & Behavior                                                                                       | Example Syntax          |
| :--------------------- | :----------------------------------------------------------------------------------------------------------- | :---------------------- |
| `-a` / `--all`         | Lists all installed packages on the system.                                                                  | `rpm -qa`               |
| `-c` / `--configfiles` | Lists the names and absolute directory references of package configuration files.                            | `rpm -qc zsh`           |
| `-i` / `--info`        | Provides detailed information, including version, installation date, and signatures.                         | `rpm -qi zsh`           |
| `N/A` / `--provides`   | Shows what facilities the package provides.                                                                  | `rpm -q --provides zsh` |
| `-R` / `--requires`    | Displays various package requirements (dependencies).                                                        | `rpm -qR zsh`           |
| `-s` / `--state`       | Provides states of the different files in a package, such as normal (installed), not installed, or replaced. | `rpm -qs zsh`           |
| `-V` / `--verify`      | Verifies a package to check for missing files or modifications.                                              | `rpm -V emacs`          |

#### Verify Action Response Codes for `rpm` (Table 2.3)

| Code      | Description & Behavior                        |
| :-------- | :-------------------------------------------- |
| `?`       | Unable to perform verification tests.         |
| `5`       | Digest number has changed.                    |
| `c`       | File is a configuration file for the package. |
| `D`       | Device number (major or minor) has changed.   |
| `G`       | Group ownership has changed.                  |
| `L`       | Link path has changed.                        |
| `missing` | Missing file.                                 |
| `M`       | Mode (permission or file type) has changed.   |
| `P`       | Capabilities have changed.                    |
| `S`       | Size of file has changed.                     |
| `T`       | Time stamp (modification) has changed.        |
| `U`       | User ownership has changed.                   |

---

## Using YUM

### Core Commands & Concepts

- **Primary Command:** `yum`
- **Configuration File:** `/etc/yum.conf` (Contains directives determining how `yum` operates).
- **Repositories Directory:** `/etc/yum.repos.d/` (Location for adding third-party `.repo` configuration files).

### Command Variants & Alternatives

- **`dnf` vs `yum`:** `dnf` (dandified yum) is a newer RPM package management tool gaining popularity and is included as part of the Fedora distribution as a replacement for `yum`.

### Flags, Options & Configurations

#### `yum` Actions

| Action      | Description & Behavior                                                                | Example Syntax        |
| :---------- | :------------------------------------------------------------------------------------ | :-------------------- |
| `install`   | Installs the specified package and automatically resolves/installs dependencies.      | `yum install emacs`   |
| `update`    | Updates the specified package(s) to the latest version in the repository.             | `yum update emacs`    |
| `upgrade`   | Updates specified package(s) but automatically removes obsolete packages.             | `yum upgrade emacs`   |
| `reinstall` | Reinstalls a package, often used to quickly fix missing files identified by `rpm -V`. | `yum reinstall emacs` |

---

## Using ZYpp

### Core Commands & Concepts

- **Primary Command:** `zypper` (Used primarily in SUSE-based distributions).

### Command Variants & Alternatives

- **Command Shortcuts:** `zypper` allows the abbreviation of its actions (e.g., `in` for `install`, `re` for `remove`, `se` for `search`).

### Flags, Options & Configurations

#### `zypper` Command Actions

| Action (Short)   | Description & Behavior                                                                | Example Syntax              |
| :--------------- | :------------------------------------------------------------------------------------ | :-------------------------- |
| `help`           | Displays overall general help or help on a specified command.                         | `zypper help`               |
| `install` (`in`) | Installs the specified package.                                                       | `zypper in nmap`            |
| `info`           | Displays information about the specified package.                                     | `zypper info nmap`          |
| `list-updates`   | Displays all available package updates for installed packages.                        | `zypper list-updates`       |
| `lr`             | Displays repository information.                                                      | `zypper lr`                 |
| `packages`       | Lists all available packages or lists available packages from a specified repository. | `zypper packages`           |
| `what-provides`  | Shows to what package a file belongs.                                                 | `zypper what-provides file` |
| `refresh`        | Refreshes a repository’s information.                                                 | `zypper refresh`            |
| `remove` (`re`)  | Removes a package from the system.                                                    | `zypper re nmap`            |
| `search` (`se`)  | Searches for the specified package(s).                                                | `zypper se nmap`            |
| `update`         | Updates specified package(s) or all packages to the latest version.                   | `zypper update`             |
| `verify`         | Verifies that installed packages have their needed dependencies satisfied.            | `zypper verify`             |

---

## Using Debian Packages

### Core Commands & Concepts

- **Debian Naming Convention:** Standard package format is `PACKAGE-NAME-VERSION-RELEASE_ARCHITECTURE.deb`.
- **Primary Command:** `dpkg`

### Command Variants & Alternatives

- **`dpkg` vs APT suite:** `dpkg` works directly with local `.deb` files and cannot automatically resolve or download missing dependencies from the internet. The APT suite (`apt-get`, `apt`) operates on top of `dpkg` to fetch files from repositories and resolve dependencies automatically.

### Flags, Options & Configurations

#### The `dpkg` Command Actions (Table 2.6)

| Short / Long Flag          | Description & Behavior                                                    | Example Syntax          |
| :------------------------- | :------------------------------------------------------------------------ | :---------------------- |
| `-c` / `--contents`        | Displays the contents of a package file.                                  | `dpkg -c package.deb`   |
| `-C` / `--audit`           | Searches for broken installed packages and suggests how to fix them.      | `dpkg -C`               |
| `N/A` / `--configure`      | Reconfigures an installed package.                                        | `dpkg --configure pkg`  |
| `N/A` / `--get-selections` | Displays all currently installed packages on the system.                  | `dpkg --get-selections` |
| `-i` / `--install`         | Installs a `.deb` package; if already installed, upgrades it.             | `dpkg -i package.deb`   |
| `-I` / `--info`            | Displays information about an uninstalled package file.                   | `dpkg -I package.deb`   |
| `-l` / `--list`            | Lists all installed packages matching a specified pattern.                | `dpkg -l "*zsh*"`       |
| `-L` / `--listfiles`       | Prints out a list of every installed file associated with a package.      | `dpkg -L zsh`           |
| `-p` / `--print-avail`     | Displays information about an installed package.                          | `dpkg -p zsh`           |
| `-P` / `--purge`           | Removes an installed package _including_ its configuration files.         | `dpkg -P zsh`           |
| `-r` / `--remove`          | Removes an installed package but _leaves_ the configuration files intact. | `dpkg -r zsh`           |
| `-s` / `--status`          | Displays the status (installed/not installed) of the specified package.   | `dpkg -s zsh-common`    |
| `-S` / `--search`          | Locates the package that owns the specified files.                        | `dpkg -S /etc/hosts`    |

---

## Looking at the APT Suite

### Core Commands & Concepts

- **Sources List:** `/etc/apt/sources.list` (Defines the repositories).
- **Primary Commands:** `apt-cache`, `apt-get`, `dpkg-reconfigure`.

### Command Variants & Alternatives

- **`apt` vs `apt-get`/`apt-cache`:** The new `apt` tool combines the most commonly used features of both `apt-get` and `apt-cache`, providing improved user interface features and simpler commands for managing Debian packages.
- **`apt-get download`:** A specific action used to obtain copies of `.deb` package files directly from a repository to your local system without immediately installing them.

### Flags, Options & Configurations

| Command            | Option / Action | Description & Behavior                                                                           | Example Syntax          |
| :----------------- | :-------------- | :----------------------------------------------------------------------------------------------- | :---------------------- |
| `apt-cache`        | `showpkg`       | Displays detailed package information, dependencies, and reverse dependencies from the database. | `apt-cache showpkg zsh` |
| `dpkg-reconfigure` | _None_          | Re-runs the initial configuration prompts for an already installed package.                      | `dpkg-reconfigure pkg`  |

---

## Managing Shared Libraries

### Core Commands & Concepts

- **System Library:** A collection of shared functions (self-contained code modules).
- **Library Cache:** A catalog of library directories (`/etc/ld.so.cache`) used by the system to quickly find libraries when loading programs.
- **Dynamic Linker:** The system component responsible for locating a program's needed library functions, copying them into memory, and binding them.
- **Primary Locations:** `/lib*`, `/usr/lib*` (for system utilities), and configuration paths `/etc/ld.so.conf`, `/etc/ld.so.conf.d/`.
- **Environment Variable:** `LD_LIBRARY_PATH`.
- **Primary Commands:** `ldd`, `ldconfig`.

### Flags, Options & Configurations

| Command    | Flag / Option | Description & Behavior                                                                        | Example Syntax  |
| :--------- | :------------ | :-------------------------------------------------------------------------------------------- | :-------------- |
| `ldconfig` | `-v`          | Updates and displays the library cache catalog in verbose mode.                               | `ldconfig -v`   |
| `ldd`      | _None_        | Displays a list of the specific shared library files required for a given application to run. | `ldd /bin/echo` |

---

## Managing Processes

### Examining Process Lists

**Core Commands & Concepts**

- **Process:** A running program in Linux.
- **PID:** Process ID assigned by the system.
- **`init` / `systemd`:** The very first process started by the kernel, responsible for spawning all other processes.
- **Process States:** Running, Sleeping (Interruptible or Uninterruptible), Stopped, Zombie (terminated child process waiting for parent acknowledgement).
- **Primary Commands:** `ps`, `top`, `uptime`, `free`.

**Command Variants & Alternatives**

- **`ps` Syntax Styles:** Due to historical merges, the modern `ps` command accepts three syntax styles:
  - **Unix-style:** Preceded by a single dash (`-ef`, `-u`).
  - **BSD-style:** Not preceded by a dash (`aux`, `U`).
  - **GNU long options:** Preceded by a double dash (`--user`).
- **`top` vs `ps`:** `ps` provides a static snapshot of processes. `top` provides a real-time, dynamic, continuously updating view of system load, CPU, memory, and processes.
- **`uptime` & `free`:** Lightweight alternatives. `uptime` extracts just the system load averages and runtime from `top`. `free` extracts just the memory usage statistics.

**Flags, Options & Configurations: `ps` Program Selection Options (Table 2.8)**
| Option(s) | Description & Behavior | Example Syntax |
| :--- | :--- | :--- |
| `a` | Display every process on the system associated with a tty terminal. | `ps a` |
| `-A`, `-e` | Display every process on the system. | `ps -ef` |
| `-C CommandList` | Only display processes running a command in the CommandList. | `ps -C bash` |
| `-g`, `-group` | Only display processes whose current effective group is in GIDList. | `ps -g 1000` |
| `-G`, `-Group` | Only display processes whose current real group is in GIDList. | `ps -G 1000` |
| `-N` | Display every process except selected processes (inverts selection). | `ps -N` |
| `p`, `-p`, `--pid` | Only display PIDList processes. | `ps -p 1840` |
| `-r` | Only display selected processes that are in a state of running. | `ps -r` |
| `-t`, `--tty` | List every process associated with the specified tty terminals. | `ps -t tty3` |
| `-T` | List every process associated with the current tty terminal. | `ps -T` |
| `-u`, `--user` | Only display processes whose effective user (username or UID) is in UserList. | `ps -u Christine` |
| `-U`, `--User` | Only display processes whose real user (username or UID) is in UserList. | `ps -U Christine` |

**Flags, Options & Configurations: The `top` Interactive Commands (Table 2.9)**
| Command Key | Description & Behavior |
| :--- | :--- |
| `1` | Toggles the single CPU and Symmetric Multiprocessor (SMP) state. |
| `b` | Toggles the bolding of important numbers in the tables. |
| `I` | Toggles Irix/Solaris mode. |
| `z` | Configures color for the table / Toggles color and mono mode. |
| `l` | Toggles display of the load average information line. |
| `t` | Toggles display of the CPU information line. |
| `m` | Toggles display of the MEM and SWAP information lines. |
| `f` | Adds or removes different information columns. |
| `o` | Changes the display order of information columns. |
| `F` or `O` | Selects a field on which to sort the processes (`%CPU` by default). |
| `<` or `>` | Moves the sort field one column left (`<`) or right (`>`). |
| `R` | Toggles normal or reverse sort order. |
| `h` | Toggles showing of threads. |
| `c` | Toggles showing of the command name or the full command line. |
| `i` | Toggles showing of idle processes. |
| `S` | Toggles showing of the cumulative CPU time or relative CPU time. |
| `x` | Toggles highlighting of the sort field. |
| `y` | Toggles highlighting of running tasks. |
| `u` | Shows processes for a specific user. |
| `n` or `#` | Sets the number of processes to display. |
| `k` | Kills a specific process (requires ownership or root). |
| `r` | Changes the priority (`renice`) of a specific process. |
| `d` or `s` | Changes the update interval (default three seconds). |
| `W` | Writes current settings to a configuration file. |
| `q` | Exits the `top` command. |

---

### Employing Multiple Screens

**Core Commands & Concepts**

- **Terminal Multiplexer:** Utilities that allow you to open multiple window sessions side-by-side or in the background to perform multiple operations.
- **Primary Commands:** `screen`, `tmux`.

**Command Variants & Alternatives**

- **`screen` vs `tmux`:** Both are multiplexers. `screen` (GNU Screen) is older and historically ubiquitous. `tmux` is a modern alternative with a different default prefix key (`Ctrl+B` instead of `Ctrl+A`).

**Flags, Options & Configurations: The `screen` Utility Prefix Shortcut `Ctrl+A` Commands (Table 2.10)**
| Key / Combination | Description & Behavior |
| :--- | :--- |
| `\` | Kill all of a processes’ windows and terminate screen. |
| `Shift+|` | Split current screen window vertically into two focuses. |
| `Tab` | Jump to next window focus. |
| `D` | Detach from current screen window (leaves it running in background). |
| `K` | Kill current window. |
| `N` | Move to next screen window. |
| `P` | Move to previous screen window. |
| `Shift+S` | Split current screen window horizontally into two focuses. |
| `C` | Create a new window within a split focus. |

_(Note: For `tmux`, the default prefix is `Ctrl+B`, and detaching is `Ctrl+B` followed by `D`. Listing sessions is done via `tmux ls` or `screen -ls`)._

---

### Understanding Foreground and Background Processes

**Core Commands & Concepts**

- **Foreground vs Background:** Background mode allows long-running commands to execute without tying up the active command-line interface.
- **Primary Commands & Metacharacters:** `&`, `jobs`, `bg`, `fg`, `Ctrl+Z`.

**Flags, Options & Configurations**
| Command / Key | Description & Behavior | Example Syntax |
| :--- | :--- | :--- |
| `&` | Metacharacter appended to a command to immediately start it in the background. | `sleep 3000 &` |
| `Ctrl+Z` | Pauses (stops) a program currently running in the foreground and assigns it a job number. | `Ctrl+Z` |
| `bg` | Sends a paused job to continue executing in the background. | `bg 1` |
| `fg` | Brings a background job back to the foreground terminal session. | `fg 1` |
| `jobs` | Lists all active background/paused jobs and their job numbers. | `jobs -l` |

---

### Managing Process Priorities

**Core Commands & Concepts**

- **Niceness:** Determines when a process obtains CPU time. Ranges from `-20` (highest priority) to `19` (lowest priority). The default is `0`.
- **Root Privileges:** Only the root user can assign a negative (higher priority) niceness value.
- **Primary Commands:** `nice`, `renice`.

**Flags, Options & Configurations**
| Command | Flag / Option | Description & Behavior | Example Syntax |
| :--- | :--- | :--- | :--- |
| `nice` | `-n` | Starts a new application at a specified niceness level. If `-n` is omitted, some systems require syntax like `nice -10` or `nice --10` (for -10). | `nice -n 10 bash script.sh` |
| `renice` | `-p` | Changes the priority of an already running process by specifying its PID. | `renice 15 -p 1949` |

---

### Sending Signals to Processes

**Core Commands & Concepts**

- **Signals:** Standardized numeric and named messages sent by the kernel or users to control process behavior (e.g., terminating, pausing).
- **Primary Commands:** `kill`, `killall`, `pkill`, `pgrep`.

**Command Variants & Alternatives**

- **`kill` vs `killall` / `pkill`:** `kill` requires passing the exact PID (Process ID) or Job ID (prefixed with `%`). `killall` allows you to kill processes based on their exact command name (affecting all instances). `pkill` acts exactly like `pgrep`, matching process names by string and sending a signal to all matches.

**Flags, Options & Configurations: Linux Process Signals (Table 2.12)**
| Number | Name | Description & Behavior |
| :--- | :--- | :--- |
| `1` | `HUP` | Hangs up. Used to disconnect or gracefully restart certain daemons. |
| `2` | `INT` | Interrupts the process. |
| `3` | `QUIT` | Stops running. |
| `9` | `KILL` | Unconditionally terminates. Process cannot ignore this. Use as a last resort. |
| `11`| `SEGV` | Segments violation. |
| `15`| `TERM` | Terminates if possible. This is the default signal sent by kill commands. |
| `17`| `STOP` | Stops unconditionally, but doesn’t terminate. |
| `18`| `TSTP` | Stops or pauses, but continues to run in the background. |
| `19`| `CONT` | Resumes execution after a STOP or TSTP signal. |

**Command Options & Syntax**
| Command | Option / Action | Description & Behavior | Example Syntax |
| :--- | :--- | :--- | :--- |
| `kill` | `-SIGNAL` | Sends a specific signal number (e.g., `-9`) or name (e.g., `-KILL`) to a PID. | `kill -9 1840` |
| `killall`| _None_ | Sends the default `TERM` signal to all instances of a named program. | `killall stress-ng` |
| `pkill` | `-t` | Kills all processes associated with a specific terminal (tty). | `sudo pkill -t tty3` |
| `pgrep` | `-t` | Returns the PIDs of all processes associated with a specific terminal. | `pgrep -t tty3` |
