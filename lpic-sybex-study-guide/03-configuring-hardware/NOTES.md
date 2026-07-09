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

1. **Character Device Files:** Escrevem dados serializados, um byte de cada vez (USB, Terminais)
2. **Block Device Files:** Escrevem dados em blocos (HHDs, SSDs)

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

### Hardware Modules

**Kernel modules:** drivers individuais que podem associar ao kernel em tempo de execução

Podem vir com **código fonte** ou como **arquivo binário pré compilado**

Usam extensão `.ko`

Devem oucupar o diretório `/lib/modules`

Os modulos carregados em boot time estão em `/etc/modules`

#### lsmod

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
snd_seq_device 14497 3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer 29482 2 snd_pcm,snd_seq
```
