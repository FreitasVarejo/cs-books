# Chapter 3: Configuring Hardware

## 3.1 Configuring the Firmware and Core Hardware

### Firmware

Dispositivos de hardware responsáveis por iniciar o OS

- BIOS (Basic Input/Output System)
  - Firmware de baixo nível de sistemas antigos
  - Tem menu interativo de seleção de dispositivo de boot
  - **LIMITAÇÃO:** não consegue lidar com discos rígidos maiores que 2.2TB
  - Divisível em dois processor:
    - 1. Boot loader: código que inicializa o hardware e carrega o kernel, presente em disco
    - 1. MBR: código que contém a tabela de partições do disco rígido que contém o bootloader

- UEFI (Unified Extensible Firmware Interface)
  - Firmware de baixo nível de sistemas modernos
  - Tem menu interativo de seleção de dispositivo de boot
  - Suporta discos rígidos maiores que 2.2TB
  - Divisível em dois processor:
    - 1. Boot loader: código que inicializa o hardware e carrega o kernel, presente em disco
    - 1. GPT: código que contém a tabela de partições do disco rígido que contém o bootloader

### `/dev` Directory

**Device Files:** tudo no linux é um arquivo, incluindo comunicação entre dispositivos de hardware, isso inclui arquivos de escrita/leitura de dispositivos de hardware.

- 1. **Character Device Files:** Escrevem dados serializados, um byte de cada vez (USB, Terminais)
- 1. **Block Device Files:** Escrevem dados em blocos (HHDs, SSDs)
  - Uma partição de disco é um bloco de dados que pode ser lido/escrito em blocos de 512 bytes
  - Nem todos os block devices são discos, por exemplo, o RAM disk é um block device que usa a memória RAM como disco.

```bash
$ ls -al sd* tty*
brw-rw---- 1 root disk 8, 0 Feb 16 17:49 sda
brw-rw---- 1 root disk 8, 1 Feb 16 17:49 sda1
crw-rw-rw- 1 root tty 5, 0 Feb 16 17:49 tty
crw--w---- 1 root tty 4, 0 Feb 16 17:49 tty0
crw--w---- 1 gdm tty 4, 1 Feb 16 17:49 tty1
```

**Device Mapper:** o kernel mapaia blocos físicos para blocos virtuais. Usado para criar drivers lógicos (Logical Volume Manager), partições e encriptar blocos.

### `/proc` Directory

Diretório virual que contém arquivos de configuração e status do hardware e do kernel

> **Interrupt Requests(IRQ):** Sinalizam quando um hardware precisa enviar algo ao kernel em `/proc/interrupts`.

> **I/O Ports:** Sinalizam quando um hardware precisa enviar algo ao kernel em `/proc/ioports`.

> **Direct Memory Access:** mais rápido que IRQ, envia dados do disco para memória sem oucupar a CPU. Presente em `/proc/dma`

### Working with Devices

#### lsmod (List Modules)

Lista todos os kernel modules instalados no kernel.

```bash
$ lsmod
Module Size Used by
vboxsf 39706 1
snd_intel8x0 38153 2
snd_ac97_codec 130285 1 snd_intel8x0
ac97_bus 12730 1 snd_ac97_codec
snd_pcm 102099 2 snd_ac97_codec,snd_intel8x0
snd_page_alloc 18710 2 snd_intel8x0,snd_pcm
snd_seq_midi 13324 0
snd_seq_midi_event 14899 1 snd_seq_midi
snd_rawmidi 30144 1 snd_seq_midi
snd_seq 61560 2 snd_seq_midi_event,snd_seq_midi
snd_seq_device 14497 3 snd_seq,snd_rawmidi,snd_seq_midik
snd_timer 29482 2 snd_pcm,snd_seq
```

#### lsblk (List Block Devices)

```bash
$ lsblk
NAME MAJ:MIN RM SIZE RO TYPE MOUNTPOINT
loop0 7:0 0 34.6M 1 loop /snap/gtk-common-themes/818
loop1 7:1 0 2.2M 1 loop /snap/gnome-calculator/222
loop2 7:2 0 34.8M 1 loop /snap/gtk-common-themes/1122
loop3 7:3 0 169.4M 1 loop /snap/gimp/113
loop4 7:4 0 2.3M 1 loop /snap/gnome-calculator/238
[...]
loop24 7:24 0 91M 1 loop /snap/core/6405
loop25 7:25 0 140.9M 1 loop /snap/gnome-3-26-1604/70
loop26 7:26 0 3.7M 1 loop /snap/gnome-system-monitor/51
sda 8:0 0 10G 0 disk
└─sda1 8:1 0 10G 0 part
 ├─ubuntu--vg-root 253:0 0 9G 0 lvm /
 └─ubuntu--vg-swap_1 253:1 0 976M 0 lvm [SWAP]
sr0 11:0 1 1024M 0 rom
$
```

1. **MOUNTPOINT** diretório onde o dispositivo está montado.

#### lspci (List PCI Devices)

```bash
$ lspci
00:00.0 Host bridge: Intel Corporation 440FX - 82441FX PMC [Natoma] (rev 02)
00:01.0 ISA bridge: Intel Corporation 82371SB PIIX3 ISA [Natoma/Triton II]
00:01.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:02.0 VGA compatible controller: InnoTek Systemberatung GmbH VirtualBox Graphics Adapter
00:03.0 Ethernet controller: Intel Corporation 82540EM Gigabit Ethernet Controller (rev 02)
00:04.0 System peripheral: InnoTek Systemberatung GmbH VirtualBox Guest Service
00:05.0 Multimedia audio controller: Intel Corporation 82801AA AC97 Audio Controller (rev 01)
00:06.0 USB controller: Apple Inc. KeyLargo/Intrepid USB
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 08)
00:0d.0 SATA controller: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [AHCI mode] (rev 02)
```

> Usado para debuggar problemas como uma placa PCI não sendo reconhecida pelo kernel.

#### lsusb

```bash
$ lsusb
 Bus 001 Device 003: ID abcd:1234 Unknown
 Bus 001 Device 002: ID 80ee:0021 VirtualBox USB Tablet
 Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

### Hardware Modules

- **Kernel modules:** drivers individuais que podem associar ao kernel em tempo de execução
  - Podem vir com **código fonte** ou como **arquivo binário pré compilado**
  - Usam extensão `.ko`
  - Devem oucupar o diretório `/lib/modules`
  - Em `/etc/modules` se lista os modulos que devem carregar no boot
  - Em `/lib/modules/$(uname -r)/modules.dep` se lista as dependências dos módulos.

#### lsmod (List Modules)

```bash
$ lsmod
Module Size Used by
vboxsf 39706 1
snd_intel8x0 38153 2
snd_ac97_codec 130285 1 snd_intel8x0
ac97_bus 12730 1 snd_ac97_codec
snd_pcm 102099 2 snd_ac97_codec,snd_intel8x0
snd_page_alloc 18710 2 snd_intel8x0,snd_pcm
snd_seq_midi 13324 0
snd_seq_midi_event 14899 1 snd_seq_midi
snd_rawmidi 30144 1 snd_seq_midi
snd_seq 61560 2 snd_seq_midi_event,snd_seq_midi
snd_seq_device 14497 3 snd_seq,snd_rawmidi,snd_seq_midi
[...]
```

1. **USED BY:** indica os outros módulos que estão usando este módulo.

#### modinfo

```bash
$ modinfo bluetooth
filename: /lib/modules/3.13.0-63-generic/kernel/net/bluetooth/bluetooth.ko
alias: net-pf-31license: GPL
version: 2.17
description: Bluetooth Core ver 2.17
author: Marcel Holtmann <marcel@holtmann.org>
srcversion: 071210642A004CFE1860F30
depends:
intree: Y
vermagic: 3.13.0-63-generic SMP mod_unload modversions
signer: Magrathea: Glacier signing key
sig_key: E2:53:28:1F:E2:65:EE:3C:EA:FC:AA:3F:29:2E:21:2B:95:F0:35:9A
sig_hashalgo: sha512
parm: disable_esco:Disable eSCO connection creation (bool)
parm: disable_ertm:Disable enhanced retransmission mode (bool)
$
```

## 3.2 Storage Basics

- Hard Disk Drive (HDD) vs Solid State Drive (SSD)
  - Linux trata ambos com mesma interface
  - HDD tem partes móveis, SSD tem circutios eletrônico

### Tipos de Discos

1. Parallel Advanced Technology Attachment (PATA)
   - Conhecido como IDE
   - Suporta até 2 dispositivos por canal
   - Antigo padrão de interface de disco rígido
   - Velocidade máxima de transferência: 133 MB/s

2. Serial Advanced Technology Attachment (SATA)
   - Suporta até 4 dispositivo por canal
   - Velocidade máxima de transferência: 600 MB/s (SATA III)

3. SMall Computer System Interface (SCSI)
   - Suporta até 16 dispositivos por canal
   - Usado mais em Data Centers
   - Velocidade máxima de transferência: 640 MB/s (SCSI-3)

- Raw Device: Quando um drive é conectado ao linusx ele ganha um arquivo em `/dev/`
  - `/dev/hdx`: para PATA
  - `/dev/sdx`: para SATA e SCSI
  - Para cada partição é criadao um arquivo adicional, eg: `/dev/sda1`, `/dev/sda2`

### Partição de Disco

1. Master Boot Record (MBR)
   - Suporta até 4 partições primárias
   - Tamanho máximo de partição: 2TB
   - Localizado no primeiro setor do disco
   - Contém o bootloader e a tabela de partições
   - Usado primariamente por BIOS

2. GUID Partition Table (GPT)
   - Suporta até 128 partições primárias
   - Tamanho máximo de partição: 9.4 ZB
   - Localizado no primeiro setor do disco
   - Contém o bootloader e a tabela de partições
   - Usado primariamente por UEFI

### Automatic Drive Detection

- **udev** é o sistema de gerenciamento de dispositivos do Linux, responsável por detectar e configurar automaticamente os dispositivos de hardware conectados ao sistema. Ele cria arquivos de dispositivo em `/dev/` e gerencia permissões e propriedades dos dispositivos

Ele divide os links em quatro categorias principais

1. /dev/disk/by-id: Identifica pelo fabricante, modelo e número de série
2. /dev/disk/by-label: Identifica pelo rótulo (nome) atribuído à partição
3. /dev/disk/by-path: Identifica pela porta física de hardware em que o disco está conectado
4. /dev/disk/by-uuid: Identifica pelo UUID (Universally Unique Identifier) de 128 bits, que é o identificador mais robusto
