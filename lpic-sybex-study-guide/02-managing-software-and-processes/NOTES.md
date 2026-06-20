# Chapter 2: Managing Software and Processes

## 2.0 Looking at Package Concepts

- **Package:** bundle of compiled applications
- **Package Manager:** system that track packages
  1. Tracks where packages files are located for each aplication
  2. Tracks the required library files for each aplication
  3. Tracks for version controls and fetch updates

## 2.1 Using RPM (RedHat)

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

### Using YUM

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

### Using ZYpp

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

## 2.2 Using Debian Packages

- **.deb packages**
  - Alternatives for .rpm packages
  - filename format: `PACKAGE-NAME-VERSION-RELEASE_ARCHITECTURE`.deb

- **dpkg** Command Set
  - CLI Tool for handling .deb packages
  - command syntax: `dpkg [ OPTIONS] ACTION PACKAGE-FILE`

## 2.3 Managing Shared Libraries

## 2.4 Managing Processes

- Linux assign each process a **process ID (PID)**
  - When Linux boots, it starts a **init process**, that starts the GUI, text consoles, etc

1. **Processo init:** quando linux boota, ele primeiro inicia esse processo

- Ele incia a GUI, consoles e etc.

1. **Processos Sleeping:** quando o processor sofreu swap para a memória virutal
2. **Processos zumbis:** quando um processo acabou mas seu processo pai não ack

- Só é terminando quando o pai ack

#### ps

```shell
$ ps -ef
UID  PID PPID C STIME TTY      TIME CMD
root 1      0 0 10:18 ?    00:00:03 /sbin/init splash
root 2      0 0 10:18 ?    00:00:00 [kthreadd]
root 4      2 0 10:18 ?    00:00:00 [kworker/0:0H]
root 5      2 0 10:18 ?    00:00:00 [kworker/u2:0]
root 6      2 0 10:18 ?    00:00:00 [mm_percpu_wq]
root 7      2 0 10:18 ?    00:00:00 [ksoftirqd/0]
root 8      2 0 10:18 ?    00:00:00 [rcu_sched]
root 9      2 0 10:18 ?    00:00:00 [rcu_bh]
```

- `UID:` ID do usuário que iniciou o processo
- `PID:` ID do processo
- `PPID:` ID do processo pai
- `C:` utilização da CPU ao longo do tempo de vida
- `STIME:` Tempo de sistema quando o processo foi iniciado
- `TTY:` O **dispositvo de terminal** que iniciou o processo
- `TIME:` O tempo cumulativo de CPU do processo
- `CMD:` O **programa** que iniciou o processo
  - Processor com `[]` entre o `CMD` estão **sleeping**

- Groups and users are real or effective:
  1. **Real group/users:** this is the group/user the account is associated
  2. **Effective group/users:** this is a temporary group/user the account is using (SUID, GUID)

#### top

Enquanto o ps fornece um "instantâneo" (snapshot) estático, o comando top exibe uma visão dinâmica e em tempo real dos processos, do uso da CPU, memória e da carga do sistema

```bash
$ top
top - 11:19:00 up  1:00,  3 users,  load average: 1.06, 0.64, 0.34
Tasks: 217 total,   2 running, 182 sleeping,   0 stopped,   0 zombie
%Cpu(s): 99.0 us,  1.0 sy,  0.0 ni,  0.0 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem :  4039720 total,  2040584 free,  1020624 used,   978512 buff/cache
KiB Swap:   483800 total,   483800 free,        0 used.  2722572 avail Mem

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND
 2966 root      20   0   41700   1924   1484 R  91.8   0.0   1:07.56 stress-ng-m+
 2481 Christi+  20   0 2997472 275884 104796 S   3.9   6.8   0:25.75 gnome-shell
```

1. **Summary Area (Cabeçalho):** informações gerais do sistema

- Linha 1 (Uptime & Load): Mostra a hora atual, o tempo que o sistema está ligado (up), usuários logados e o Load Average (Carga Média) referentes aos últimos 1, 5 e 15 minutos
  - `$ uptime` para ver as Load Avareges
- Linha 2 (Tasks): Total de processos e a quantidade de cada estado
- Linha 3 (%Cpu): Utilizaçõa de CPU
  - us: Userspace
  - sy: System
  - id: Idle
  - wa: Waiting (tempo de I/O, etc)
- Linhas 4 e 5 (Mem & Swap): Uso da memória RAM (física) e Swap (virtual) exibindo o total, o que está livre (free), o que está sendo usado (used) e o que está em cache (buff/cache).

1. **Task Area (Coluna de procesos):**

- `PR:` A prioridade do processo
- `NI:` Valor nice do processo
- `VIRT:` Quantidade de memória virtual sendo usada
- `RES:` Quantidade de memória física sendo usada
- `SHR:` Quantidade de memória compartilhada
- `S:` Status do processo (D = interruptible sleep, I = idle, R = running, S = sleeping, T =
  traced or stopped, and Z = zombie)
- `TIME+:` O tempo cumulativo de CPU que o pr ocesso usou desde que foi iniciado
  Sua seção sobre o `ps` está excelente, muito bem resumida e alinhada com o que é cobrado na prova.

Quando o `top` estiver rodando, você pode pressionar atalhos no teclado para alterar o comportamento em tempo real:

- **`k`**: Mata (Kill) um processo (ele pedirá o PID e o sinal, sendo SIGTERM/15 o padrão).
- **`r`**: Muda a prioridade (Renice) de um processo (ele pedirá o PID e o novo valor de nice).
- **`u`**: Filtra para mostrar apenas processos de um **usuário específico**.
- **`M`**: Ordena a lista pelo uso de **Memória** (`%MEM`).
- **`P`**: Ordena a lista pelo uso da **CPU** (`%CPU` - Padrão).
- **`c`**: Alterna entre mostrar apenas o nome do comando ou o caminho absoluto (comando completo com parâmetros).
- **`q`**: Sai do `top`.

[Vou pular tmux e screen porque já uso tmux]

### Understanding Foreground and Background Processes

- **Background mode:** maneira de rodar um probrama sem mostrar na CLI
  - Coloque o símbolo `&` no final de um comando na CLI

1. **Job number:** índice associado pelo SHELL
2. **PID:** índice associado pelo LINUX

```bash
 $ bash CriticalBackups.sh &
 [2] 1540
 $
 $ jobs -l
 [1]- 1539 Running sleep 3000 &
 [2]+ 1540 Running bash CriticalBackups.sh &
```

#### fg

É possível trazer um processo em background mode para o foreground usando `fg`

```bash
$ jobs -l
 [1]- 1539 Running sleep 3000 &
 [2]+ 1540 Running bash CriticalBackups.sh &
 $
 $ fg %2
 bash CriticalBackups.sh
```

#### bg

Para enviar um processo do foreground mode para background é possível

1. Usar Ctrl+Z para pausar o processo
2. usar o commando `bg`

```bash
$ bash CriticalBackups.sh
 ^Z
 [2]+ Stopped bash CriticalBackups.sh
 $
 $ bg %2
 [2]+ bash CriticalBackups.sh &
 $
 $ jobs -l
 [1]- 1539 Running sleep 3000 &
 [2]+ 1540 Running bash CriticalBackups.sh &
```

#### kill

Comando para parar um processo em background

```bash
[1]- 1539 Running sleep 3000 &
[2]+ 1540 Running bash CriticalBackups.sh &
$
$ kill %1
[1]- Terminated sleep 3000
$
$ jobs -l
[2]+ 1540 Running bash CriticalBackups.sh &
$
```

#### nohup

- Comando feito para fazer um processo background que continua mesmo se der log off
- O processo passa a não receber mais input de STDIN
- Normalmente encaminha STDOUT e STDERR para `$HOME/nohup.out`

```bash
$ nohup bash CriticalBackups.sh &
[1] 2090
$ nohup: ignoring input and appending output to 'nohup.out'
$
```

#### nice -n VALUE COMMAND

Os comandos `nice` e `renice` permitem controlar a prioridade para CPU **(niceness level)**

- VALUE: inteiro de -20 a 19
  - Quanto menor o valor maior a prioridade
  - Valor padrão é zero
  - Apenas **super admin** podem dar nice value abaixo de 0

#### renice PRIORITY [-p PIDS] [-u USERS] [-g GROUPS]

### Sending Signals to Processes

- **HUP (1):** Hangs up (Muitas vezes usado para pedir que daemons recarreguem seus arquivos de configuração).
- **INT (2):** Interrupts (Interrompe o processo). É o sinal gerado ao pressionar `Ctrl+C` no terminal.
- **QUIT (3):** Stops running (Para a execução do processo).
- **KILL (9):** Unconditionally terminates (Termina incondicionalmente). O modo força bruta. O processo é assassinado pelo kernel e não tem chance de fechar arquivos ou salvar dados. Só use como último recurso.
- **SEGV (11):** Segments violation (Sinal de erro quando o processo tenta acessar uma memória inválida).
- **TERM (15):** Terminates if possible. É o **sinal padrão** caso nenhum número seja especificado. Pede educadamente para o processo terminar, permitindo que ele limpe seus dados e feche corretamente.
- **STOP (17):** Stops unconditionally (Pausa incondicionalmente, mas não termina).
- **TSTP (18):** Stops or pauses. Permite que o processo continue rodando em background. É o sinal gerado pelo atalho `Ctrl+Z`.
- **CONT (19):** Resumes execution. Despausa e retoma a execução de um processo parado por STOP ou TSTP.

_(Dica: Frequentemente, os sinais recebem o prefixo "SIG", como SIGTERM, SIGKILL, SIGSTOP, etc)._

### Ferramentas para envio de sinais

Além de parar trabalhos em background com `%Job_Number`, o Linux fornece comandos específicos para sinalizar processos usando diferentes critérios:

#### `kill`

Envia sinais a um processo baseando-se em seu **PID** (ou **Job ID**, usando `%`). O sinal padrão enviado é o 15 (TERM).

```bash
# Envia o sinal padrão (15 TERM)
$ kill 2305

# Especificando um sinal diferente (Ex: 9 KILL)
$ kill -9 2305
# ou
$ kill -s KILL 2305
```

**Atenção:** Se esquecer de colocar o `%` ao tentar matar um Job ID, o sistema tentará matar o PID 1 (o que pode derrubar/travar o sistema se executado como root).

#### `killall`

Envia o sinal para todos os processos que corresponderem exatamente ao **nome** do programa passado como argumento.

```bash
# Encerra todas as instâncias do programa 'stress-ng'
$ killall stress-ng
```

#### `pkill`

Funciona junto com o utilitário de busca `pgrep`. Ele não precisa do PID ou do nome exato do comando; em vez disso, usa critérios de pesquisa avançados (como nome do terminal, dono do processo ou correspondência de string) e envia o sinal a todos os processos que derem "match".

```bash
# Envia sinal (TERM) para todos os processos rodando no terminal tty3
$ sudo pkill -t tty3

# Envia sinal para todos os processos do usuário 'carol'
$ pkill -u carol
```
