# Chapter 3: Configuring Hardware

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
