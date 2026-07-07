Q: Qual firmware moderno substituiu amplamente o tradicional BIOS na maioria dos computadores compatíveis com IBM?
A) FTP
B) PXE
C) UEFI
D) NFS
A: C) UEFI

---

Q: Durante a inicialização de uma máquina com firmware UEFI, qual é o local comum onde o sistema procura os aplicativos EFI (EFI applications) e os carregadores de inicialização?
A) No MBR do primeiro disco
B) No diretório raiz do sistema /root
C) Na partição EFI System Partition (ESP), frequentemente montada em /boot/efi
D) No diretório virtual /sys/firmware
A: C) Na partição EFI System Partition (ESP), frequentemente montada em /boot/efi

---

Q: Em sistemas mais antigos ou naqueles configurados em modo legado (Legacy BIOS), onde o firmware procura pelo código binário inicial do carregador de inicialização (bootloader)?
A) Na partição EFI
B) No Master Boot Record (MBR) do primeiro dispositivo de armazenamento configurado no BIOS
C) Em um servidor remoto PXE incondicionalmente
D) No diretório /boot/grub do sistema de arquivos ext4
A: B) No Master Boot Record (MBR) do primeiro dispositivo de armazenamento configurado no BIOS

---

Q: Na arquitetura do Linux, qual é o propósito principal do diretório virtual `/dev`?
A) Armazenar os binários de dispositivos recém-compilados pelos desenvolvedores
B) Servir como o ponto de montagem principal para o sistema de arquivos virtual sysfs
C) Hospedar arquivos de dispositivos virtuais (device nodes) que o kernel utiliza para interagir com o hardware
D) Guardar as chaves de criptografia públicas de cada dispositivo PCI
A: C) Hospedar arquivos de dispositivos virtuais (device nodes) que o kernel utiliza para interagir com o hardware

---

Q: Qual das seguintes opções descreve melhor a finalidade do padrão PnP (Plug-and-Play) no gerenciamento de hardware?
A) Otimizar os drivers de vídeo para que forneçam maior taxa de quadros (FPS) automaticamente
B) Permitir que placas e dispositivos negociem com o sistema para determinar e alocar automaticamente endereços exclusivos, como portas de E/S e canais IRQ, evitando conflitos
C) Baixar da internet e compilar de forma autônoma drivers para novos dispositivos no momento da conexão
D) Fazer o bypass completo da CPU para qualquer hardware recém-inserido
A: B) Permitir que placas e dispositivos negociem com o sistema para determinar e alocar automaticamente endereços exclusivos, como portas de E/S e canais IRQ, evitando conflitos

---

Q: Qual tipo de interface de hardware comunica-se com a placa-mãe utilizando especificamente interrupções (IRQs), portas de E/S (I/O ports) e canais DMA?
A) USB
B) GPIO
C) Placas de rede sem fio externas
D) PCI
A: D) PCI

---

Q: Qual é a principal diferença de desempenho e comportamento entre a utilização de Canais DMA (Direct Memory Access) e Portas de E/S (I/O Ports) para a transferência de dados de dispositivos?
A) O DMA transfere os dados para o disco rígido contornando a memória RAM; as portas de I/O enviam dados para o monitor
B) Portas de I/O exigem que o processador (CPU) atue ativamente para transferir dados, o que é mais lento. O DMA permite que os dispositivos de hardware enviem os dados diretamente para a memória do sistema sem bloquear a CPU
C) O DMA só é utilizado em dispositivos USB 3.0, enquanto portas de E/S são exclusivas para placas PCI antigas
D) Não há diferença prática; ambos os métodos bloqueiam a CPU por períodos equivalentes
A: B) Portas de I/O exigem que o processador (CPU) atue ativamente para transferir dados, o que é mais lento. O DMA permite que os dispositivos de hardware enviem os dados diretamente para a memória do sistema sem bloquear a CPU

---

Q: Em qual pseudo-sistema de arquivos residente em memória as informações detalhadas de processos e também parâmetros de configuração de hardware do kernel (como listas de interrupções e mapeamentos de E/S) são acessadas tradicionalmente?
A) /dev
B) /sys
C) /proc
D) /etc/hardware
A: C) /proc

---

Q: Se um administrador suspeitar de um conflito de interrupções de hardware, qual arquivo virtual ele deve inspecionar para listar as interrupções de hardware (IRQs) solicitadas e o uso atual por dispositivos?
A) /proc/ioports
B) /sys/bus/irq
C) /dev/irq
D) /proc/interrupts
A: D) /proc/interrupts

---

Q: Um administrador precisa descobrir quais endereços específicos de memória na máquina estão designados para que a CPU se comunique ativamente com o hardware (as portas I/O designadas). Onde essa informação fica armazenada em tempo real?
A) /proc/ioports
B) /proc/dma
C) /proc/interrupts
D) /sys/devices/ports
A: A) /proc/ioports

---

Q: O diretório `/sys` hospeda o sistema de arquivos virtual `sysfs`. Qual é a finalidade principal do sysfs introduzida no Kernel Linux 2.6?
A) Substituir o carregador de inicialização GRUB por um sistema de arquivos montável
B) Hospedar scripts de compilação automáticos do kernel
C) Exportar informações organizadas hierarquicamente sobre dispositivos de hardware conectados, seus drivers e o modelo de barramentos do kernel para o userspace
D) Armazenar logs persistentes do sistema (substituindo o /var/log)
A: C) Exportar informações organizadas hierarquicamente sobre dispositivos de hardware conectados, seus drivers e o modelo de barramentos do kernel para o userspace

---

Q: Qual utilitário de linha de comando analisa o hardware da máquina e exibe uma lista detalhada de todos os dispositivos diretamente conectados ao barramento PCI do sistema?
A) lsusb
B) lsmod
C) lspci
D) lshw
A: C) lspci

---

Q: Após plugar um novo teclado e um mouse, qual comando pode ser usado para inspecionar imediatamente todos os controladores USB e os dispositivos fixados a eles de maneira direta?
A) lspci
B) dmesg --usb
C) lsmod
D) lsusb
A: D) lsusb

---

Q: Qual utilitário é utilizado para exibir o status de todos os módulos de kernel atualmente carregados na memória do Linux?
A) sysmod
B) lsmod
C) modprobe
D) lspci -m
A: B) lsmod

---

Q: Para adicionar (carregar) ativamente um novo módulo de hardware no kernel em tempo de execução e, crucialmente, resolver e carregar todas as dependências adicionais automaticamente, qual comando deve ser utilizado?
A) insmod
B) lsmod
C) modprobe
D) rmmod
A: C) modprobe

---

Q: Um administrador tenta descarregar o módulo do bluetooth executando `modprobe -r bluetooth`, porém o sistema retorna o erro: "modprobe: FATAL: Module bluetooth is in use". Qual é a causa mais provável?
A) O usuário não invocou o comando como root
B) O módulo falhou em compilar a dependência de PnP
C) Um outro dispositivo, driver ou módulo carregado possui dependência ativa ou está utilizando o módulo de bluetooth no momento
D) O hardware bluetooth não está presente fisicamente na máquina
A: C) Um outro dispositivo, driver ou módulo carregado possui dependência ativa ou está utilizando o módulo de bluetooth no momento

---

Q: Qual daemon e gerenciador de subsistemas do Linux lida dinamicamente com as mudanças de estado de hardware, detectando quando um dispositivo é conectado e criando os respectivos "device nodes" em `/dev`?
A) init
B) udev
C) dbus
D) hald
A: B) udev

---

Q: O `dbus` (Desktop Bus) é muito mencionado ao lado de ferramentas de detecção de hardware. Qual é a sua responsabilidade primária neste contexto?
A) Atuar como barramento de hardware físico, equivalente ao USB, para periféricos internos
B) Servir como o driver genérico para teclados e mouses plug and play
C) Fornecer um sistema de Comunicação Interprocessos (IPC) que permite que os processos do sistema notifiquem imediatamente as aplicações de desktop e do usuário quando um hardware muda de estado
D) Montar partições UEFI durante o processo de boot
A: C) Fornecer um sistema de Comunicação Interprocessos (IPC) que permite que os processos do sistema notifiquem imediatamente as aplicações de desktop e do usuário quando um hardware muda de estado

---

Q: Uma máquina possui dois discos SATA em operação. Qual arquivo de dispositivo bruto (raw device file) o Linux normalmente criará em `/dev` para representar e endereçar o SEGUNDO disco rígido conectado ao sistema?
A) /dev/hdb
B) /dev/sda2
C) /dev/sdb
D) /dev/sdb1
A: C) /dev/sdb

---

Q: Qual tipo de dispositivo de armazenamento de dados utiliza internamente um circuito integrado de memória, sem conter peças mecânicas ou pratos giratórios?
A) HDD (Hard Disk Drive)
B) SCSI Magnético
C) SSD (Solid-State Drive)
D) SATA
A: C) SSD (Solid-State Drive)

---

Q: Na listagem do comando `lspci`, o administrador repara no código `03:00.0` antes do nome do dispositivo RAID. O que este código geralmente representa?
A) O identificador geográfico do slot e a designação do barramento da placa
B) A versão de firmware injetada na placa
C) O código de erro da inicialização do driver
D) O número exato da porta de I/O em formato hexadecimal
A: A) O identificador geográfico do slot e a designação do barramento da placa

---

Q: Se um servidor baseado na arquitetura x86 com firmware BIOS legado não consegue completar a inicialização (boot) após o administrador desconectar o teclado. Como este problema específico pode ser mitigado?
A) Adicionando "keyboard=ignore" aos parâmetros do kernel no GRUB
B) Desativando a checagem de erros do teclado (Halt on keyboard error) no utilitário de configuração local do próprio BIOS
C) Instalando e habilitando o driver udev-keyboard-stub no Linux
D) Trocando a porta do teclado de USB para PS/2
A: B) Desativando a checagem de erros do teclado (Halt on keyboard error) no utilitário de configuração local do próprio BIOS

---

Q: Um administrador de sistema adicionou um segundo disco rígido SATA a uma máquina que estava operando normalmente. Ao tentar inicializá-la novamente, o sistema exibe erro de bootloader e falha na inicialização. Qual é a causa mais provável abordada neste material?
A) Os discos SATA são mutuamente exclusivos e não suportam configurações de múltiplos discos em hardware padrão
B) A presença de um disco secundário obriga a transição de BIOS para UEFI
C) A ordem dos dispositivos de boot (Boot Device Order) no utilitário do BIOS/UEFI foi desconfigurada e o sistema está tentando ler o setor de boot do disco novo e vazio
D) O kernel do Linux perdeu as permissões PnP
A: C) A ordem dos dispositivos de boot (Boot Device Order) no utilitário do BIOS/UEFI foi desconfigurada e o sistema está tentando ler o setor de boot do disco novo e vazio

---

Q: Uma partição designada como `/dev/sda3` refere-se a quê especificamente no modelo de nomenclatura do kernel Linux?
A) Aos 3 primeiros setores montados do disco secundário SCSI
B) À terceira partição do primeiro disco rígido detectado (tipo SCSI/SATA/USB)
C) À primeira partição do terceiro disco rígido
D) A um dispositivo RAID de três vias ativo
A: B) À terceira partição do primeiro disco rígido detectado (tipo SCSI/SATA/USB)

---

Q: Em muitos sistemas mais antigos, qual daemon de abstração de hardware atuava fortemente em conformidade com o D-Bus para enumerar dispositivos para os programas de desktop, mas que hoje é considerado legado e substituído na prática pelo Udev?
A) acpid
B) hald (Hardware Abstraction Layer daemon)
C) systemd-hw
D) initrd
A: B) hald (Hardware Abstraction Layer daemon)

---

Q: Qual das seguintes opções de hardware embutido na placa-mãe, também chamados de periféricos integrados (integrated peripherals), pode frequentemente ser habilitada ou totalmente desabilitada utilizando a interface de configuração do BIOS ou UEFI?
A) Placas de som on-board e controladores de rede (NICs) embutidos
B) Frequência do monitor principal
C) Partições LVM nativas
D) A resolução do servidor X11
A: A) Placas de som on-board e controladores de rede (NICs) embutidos

---

Q: Em relação ao gerenciamento de módulos no kernel Linux, em qual arquivo ou subsistema virtual o comando `lsmod` procura suas informações para listar o que está ativo?
A) Ele analisa ativamente o arquivo de configuração `/etc/modprobe.conf`
B) Ele extrai suas saídas formatadas a partir da leitura do arquivo `/proc/modules`
C) Ele executa uma requisição D-Bus para o HAL
D) Ele compila o binário `/boot/vmlinuz` para extrair descritores
A: B) Ele extrai suas saídas formatadas a partir da leitura do arquivo `/proc/modules`

---

Q: Ao tentar solucionar problemas de conexão com uma placa-mãe USB, um administrador quer revisar o log do _Kernel Ring Buffer_ para ver se a porta USB foi detectada durante a última inserção pelo subsistema PnP. Qual comando visualizará essa saída?
A) dmesg
B) lsmod
C) lsof
D) modprobe --log
A: A) dmesg

---

Q: O `modprobe` pode ser configurado para incluir ou ignorar certos módulos através de arquivos de configuração em disco, além da resolução de dependências. Qual é o diretório padrão onde essas configurações de arquivos `.conf` customizadas do modprobe residem?
A) /usr/share/modules/
B) /etc/modprobe.d/
C) /proc/sys/modules/
D) /var/lib/modprobe/
A: B) /etc/modprobe.d/

---

Q: O conceito de "Mass Storage Devices" no currículo LPIC inclui uma variedade de opções de discos e arranjos. Qual tecnologia utiliza arranjos de múltiplos discos independentes organizados logicamente para aumentar a tolerância a falhas ou o desempenho do sistema de arquivos de hardware de uma só vez?
A) Arquitetura PATA
B) Tecnologia RAID
C) Particionamento MBR de alta velocidade
D) D-Bus
A: B) Tecnologia RAID

---

Q: O que define um módulo de hardware no Linux?
A) Um binário autônomo e isolado do Kernel, armazenado em `/bin`, usado para rodar GUI
B) Uma extensão compilada dinamicamente, geralmente com a extensão `.ko`, que pode ser carregada em demanda no kernel para adicionar suporte a um novo dispositivo de hardware
C) Uma placa aceleradora física baseada em slots PCI-E de 16x
D) O chip contendo as informações ROM do BIOS
A: B) Uma extensão compilada dinamicamente, geralmente com a extensão `.ko`, que pode ser carregada em demanda no kernel para adicionar suporte a um novo dispositivo de hardware

---

Q: Durante a inicialização (boot), os controladores de disco (como um RAID MegaRAID SAS) precisam ser reconhecidos e seus módulos engatados. Qual comando, ao listar dispositivos PCI, exibiria informações detalhadas incluindo qual módulo (Kernel driver in use) gerencia esse controlador RAID?
A) lsusb -verbose
B) lspci -k
C) lsmod -a
D) modprobe -raid
A: B) lspci -k

---

Q: Com a migração da arquitetura clássica para sysfs e udev, o conteúdo do `/dev` sofreu uma importante modificação de comportamento. Como esse diretório é gerenciado em distribuições modernas?
A) Ele é um sistema de arquivos puramente estático populado manualmente via comando MAKEDEV durante a instalação
B) O diretório é hospedado na nuvem e lido via protocolo NFS
C) Ele é montado de forma virtual como devtmpfs e populado de forma completamente dinâmica no espaço de usuário (userspace) pelo udev conforme hardwares são detectados
D) Seus arquivos estão permanentemente amarrados e salvos na partição lógica `/boot/efi`
A: C) Ele é montado de forma virtual como devtmpfs e populado de forma completamente dinâmica no espaço de usuário (userspace) pelo udev conforme hardwares são detectados

---

Q: O que o termo "Hotplug" representa em administração de hardware no Linux?
A) O aumento excessivo da temperatura da CPU quando DMA falha
B) A capacidade de conectar e desconectar dispositivos no sistema operacional de forma segura e com reconhecimento imediato enquanto a máquina já está em funcionamento
C) Plugar um cabo de rede em um equipamento que requer inicialização (cold boot)
D) A técnica de particionar e criptografar a MBR em movimento
A: B) A capacidade de conectar e desconectar dispositivos no sistema operacional de forma segura e com reconhecimento imediato enquanto a máquina já está em funcionamento

---

Q: Se um administrador desejar visualizar exatamente todos os canais de Acesso Direto à Memória (DMA) que estão ativamente em uso por dispositivos em seu computador no momento, qual arquivo ele deve inspecionar?
A) /sys/dma/status
B) /proc/dma
C) /etc/dma.conf
D) /dev/dma_ports
A: B) /proc/dma

---

Q: Você possui uma unidade de disco com um ambiente em falha. Qual ferramenta do Linux deve ser usada para inspecionar, criar ou gerenciar as partições lógicas de um disco rígido SCSI antes de adicionar sistemas de arquivo em cima dessas partições?
A) fdisk (ou gdisk/parted)
B) fsck
C) mount
D) lvm_disk
A: A) fdisk (ou gdisk/parted)

---

Q: Como é chamado o utilitário nativo projetado especificamente para converter múltiplas partições físicas de disco em agrupamentos de Volumes Lógicos altamente flexíveis (LVM) em níveis de abstração?
A) mkfs
B) lspci
C) parted
D) pvcreate / vgcreate / lvcreate
A: D) pvcreate / vgcreate / lvcreate

---

Q: O diretório `/dev` separa componentes em Block Devices (dispositivos de bloco) e Character Devices (dispositivos de caractere). Qual das opções ilustra melhor um "Dispositivo de Bloco"?
A) Uma placa de captura de som
B) O console do terminal TTY
C) Um disco rígido formatado, pois lê e grava informações em buffers de blocos regulares
D) Um mouse USB enviando eventos contínuos
A: C) Um disco rígido formatado, pois lê e grava informações em buffers de blocos regulares

---

Q: É prático saber visualizar as árvores e raízes (hubs) dos dispositivos USB em uma topologia lógica hierárquica. Qual parâmetro de `lsusb` ativa esta visão em árvore no prompt?
A) lsusb -t
B) lsusb -r
C) lsusb --tree
D) lsusb -hier
A: A) lsusb -t

---

Q: O utilitário `fsck` tem papel fundamental sobre as unidades de armazenamento de massa após elas estarem particionadas e ativadas no sistema. Qual é esse papel?
A) Ele anexa novos discos SCSI ativamente no diretório /dev automaticamente
B) É responsável por particionar o disco magnético de rotação
C) É utilizado para checar e reparar danos na integridade dos sistemas de arquivos montados ou desmontados em partições
D) Configura as IRQs para que a placa controladora atue via PnP
A: C) É utilizado para checar e reparar danos na integridade dos sistemas de arquivos montados ou desmontados em partições

---
