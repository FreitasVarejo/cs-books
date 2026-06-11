Q: Qual é a principal função de um sistema de gerenciamento de pacotes no Linux?
A) Compilar automaticamente o código-fonte de aplicativos recém-baixados
B) Rastrear pacotes instalados, dependências de bibliotecas e a localização exata dos arquivos
C) Isolar aplicativos em ambientes virtualizados para evitar acesso à rede
D) Gerenciar a fila de impressão e dispositivos de hardware externos
A: B) Rastrear pacotes instalados, dependências de bibliotecas e a localização exata dos arquivos

---

Q: Qual das seguintes opções descreve corretamente o Flatpak?
A) Uma ferramenta legada usada apenas em distribuições Red Hat antigas
B) Um substituto para o gerenciador de inicialização GRUB
C) Um sistema que combina gerenciamento de pacotes e isolamento (sandboxing) de aplicativos
D) Um utilitário de linha de comando para descompactar arquivos .tar.gz
A: C) Um sistema que combina gerenciamento de pacotes e isolamento (sandboxing) de aplicativos

---

Q: Qual é a convenção de nomenclatura padrão para um pacote RPM?
A) PACKAGE-NAME_VERSION-RELEASE_ARCHITECTURE.rpm
B) PACKAGE-NAME-VERSION-RELEASE.ARCHITECTURE.rpm
C) PACKAGE-NAME.ARCHITECTURE.VERSION-RELEASE.rpm
D) PACKAGE-NAME-RELEASE-VERSION.ARCHITECTURE.rpm
A: B) PACKAGE-NAME-VERSION-RELEASE.ARCHITECTURE.rpm

---

Q: O que o campo "RELEASE" (também chamado de build number) em um nome de pacote RPM geralmente representa?
A) O tipo de processador para o qual o pacote foi compilado
B) A arquitetura neutra do pacote
C) Uma modificação de programa menor que o número da versão, muitas vezes incluindo a versão da distribuição
D) O número de vezes que o pacote foi baixado do repositório
A: C) Uma modificação de programa menor que o número da versão, muitas vezes incluindo a versão da distribuição

---

Q: Em pacotes RPM, o que significa quando a arquitetura (ARCHITECTURE) é descrita como "noarch"?
A) O pacote contém apenas o código-fonte original
B) O pacote não requer nenhum arquivo de biblioteca compartilhada
C) O pacote não foi compilado com sucesso e contém erros
D) O pacote é arquiteturalmente neutro e pode rodar em diferentes tipos de CPU
A: D) O pacote é arquiteturalmente neutro e pode rodar em diferentes tipos de CPU

---

Q: Qual ferramenta pode ser usada no CentOS ou Fedora para baixar um arquivo RPM diretamente de um repositório sem instalá-lo imediatamente?
A) apt-get download
B) yumdownloader
C) zypper fetch
D) rpm-download
A: B) yumdownloader

---

Q: Qual das seguintes opções do comando `rpm` é usada para atualizar um pacote APENAS se uma versão anterior já estiver instalada?
A) -i (--install)
B) -U (--upgrade)
C) -F (--freshen)
D) -e (--erase)
A: C) -F (--freshen)

---

Q: Ao instalar um pacote RPM, qual combinação de flags exibe uma barra de progresso visual com marcas de hash (#) e saída detalhada?
A) rpm -Uvh
B) rpm -ivp
C) rpm -Uqc
D) rpm -eha
A: A) rpm -Uvh

---

Q: Se você tentar remover um pacote RPM usando `rpm -e` e houver falha de dependências (outros pacotes dependem dele), o que acontecerá?
A) O `rpm` removerá os pacotes dependentes automaticamente
B) O pacote será removido, mas o sistema emitirá um aviso após o fato
C) O `rpm` emitirá uma mensagem de erro e não removerá o pacote
D) O `rpm` ignorará a dependência e forçará a remoção
A: C) O `rpm` emitirá uma mensagem de erro e não removerá o pacote

---

Q: Qual comando lista TODOS os pacotes RPM atualmente instalados no sistema?
A) rpm -ql
B) rpm -qa
C) rpm -qi
D) rpm -qR
A: B) rpm -qa

---

Q: Você precisa verificar quais dependências um pacote RPM exige. Qual comando realiza essa tarefa?
A) rpm -qd
B) rpm -qc
C) rpm -qR
D) rpm -qp
A: C) rpm -qR

---

Q: O administrador precisa saber quais arquivos de configuração pertencem ao pacote "zsh". Qual comando RPM é apropriado?
A) rpm -qc zsh
B) rpm -qR zsh
C) rpm -qa zsh
D) rpm -qf zsh
A: A) rpm -qc zsh

---

Q: Qual comando deve ser usado para obter informações detalhadas (como versão e licença) de um arquivo de pacote RPM não instalado chamado "software.rpm"?
A) rpm -qi software.rpm
B) rpm -qip software.rpm
C) rpm -qa software.rpm
D) rpm -qf software.rpm
A: B) rpm -qip software.rpm

---

Q: Qual comando RPM indica a qual pacote instalado pertence o arquivo "/usr/bin/zsh"?
A) rpm -qf /usr/bin/zsh
B) rpm -ql /usr/bin/zsh
C) rpm -qc /usr/bin/zsh
D) rpm -qi /usr/bin/zsh
A: A) rpm -qf /usr/bin/zsh

---

Q: Ao executar `rpm -V` em um pacote instalado, a saída exibe a letra "5" para um arquivo específico. O que isso significa?
A) O tamanho do arquivo foi alterado
B) As permissões do arquivo foram alteradas
C) O digest (hash) do arquivo foi alterado
D) O arquivo está faltando no sistema
A: C) O digest (hash) do arquivo foi alterado

---

Q: Ao extrair arquivos manualmente de um pacote RPM sem instalá-lo, qual sequência de comandos é comumente usada?
A) rpm2cpio pacote.rpm | tar -xvf -
B) rpm2cpio pacote.rpm | cpio -idv
C) rpm -x pacote.rpm > arquivos.cpio
D) cpio -i pacote.rpm | rpm2cpio
A: B) rpm2cpio pacote.rpm | cpio -idv

---

Q: Qual arquivo de configuração principal contém as diretivas de como o utilitário `yum` opera no sistema?
A) /etc/yum.repos.d/
B) /etc/yum/sources.list
C) /etc/yum.conf
D) /var/cache/yum/config
A: C) /etc/yum.conf

---

Q: Qual subcomando do YUM pesquisa as descrições e nomes de pacotes no repositório por uma palavra-chave específica?
A) yum search
B) yum find
C) yum query
D) yum locate
A: A) yum search

---

Q: Qual comando YUM atualiza o pacote especificado e ao mesmo tempo remove pacotes obsoletos?
A) yum update
B) yum upgrade
C) yum dist-upgrade
D) yum freshen
A: B) yum upgrade

---

Q: Um usuário tenta executar um comando, mas o arquivo está ausente. Qual comando YUM pode ser usado para descobrir qual pacote fornece o arquivo ausente (ex: libgimpui-2.0.so.0)?
A) yum search libgimpui-2.0.so.0
B) yum which libgimpui-2.0.so.0
C) yum whatprovides libgimpui-2.0.so.0
D) yum info libgimpui-2.0.so.0
A: C) yum whatprovides libgimpui-2.0.so.0

---

Q: Qual comando exibe informações detalhadas de um pacote específico, de forma semelhante ao comando `rpm -qi`, mas usando o YUM?
A) yum details
B) yum show
C) yum info
D) yum inspect
A: C) yum info

---

Q: Como você pode adicionar um novo repositório ao sistema sem editar os arquivos .repo manualmente no YUM?
A) Usando o comando `yum add-repo`
B) Usando o comando `yum-config-manager --add-repo`
C) Usando o comando `yum --install-repo`
D) Usando o comando `rpm -i --repo`
A: B) Usando o comando `yum-config-manager --add-repo`

---

Q: Ao usar o `yum-config-manager`, como você desabilita o repositório nomeado "updates"?
A) yum-config-manager --disable updates
B) yum-config-manager --remove updates
C) yum disable updates
D) yum-config-manager updates=0
A: A) yum-config-manager --disable updates

---

Q: O `dnf` é um substituto moderno para o `yum`. Em qual distribuição Linux ele é usado por padrão?
A) Debian
B) openSUSE
C) Ubuntu
D) Fedora
A: D) Fedora

---

Q: Qual é a ferramenta de gerenciamento de pacotes por linha de comando nativa de distribuições baseadas em SUSE, como openSUSE?
A) yum
B) dnf
C) zypper
D) apt
A: C) zypper

---

Q: Qual comando atualiza os metadados do repositório local no ZYpp para conhecer os pacotes mais recentes disponíveis?
A) zypper update
B) zypper refresh
C) zypper sync
D) zypper fetch
A: B) zypper refresh

---

Q: No ZYpp (`zypper`), qual comando procura pacotes instalados que correspondam à palavra "firefox"?
A) zypper find -i firefox
B) zypper se -i firefox
C) zypper query firefox
D) zypper ls firefox
A: B) zypper se -i firefox

---

Q: Como o `zypper` instala um pacote local que está no formato RPM, resolvendo automaticamente suas dependências pelos repositórios configurados?
A) zypper install --local pacote.rpm
B) zypper in /caminho/completo/pacote.rpm
C) zypper rpm pacote.rpm
D) zypper add pacote.rpm
A: B) zypper in /caminho/completo/pacote.rpm

---

Q: Qual das opções descreve corretamente a convenção de nomenclatura padrão para um pacote Debian?
A) PACKAGE-NAME_VERSION-RELEASE_ARCHITECTURE.deb
B) PACKAGE-NAME-VERSION-RELEASE.ARCHITECTURE.deb
C) PACKAGE-NAME.ARCHITECTURE.VERSION-RELEASE.deb
D) PACKAGE-NAME_ARCHITECTURE_VERSION.deb
A: A) PACKAGE-NAME_VERSION-RELEASE_ARCHITECTURE.deb

---

Q: Em sistemas Debian e Ubuntu, qual comando exibe todo o conteúdo (arquivos e caminhos) dentro de um arquivo `.deb` antes da instalação?
A) dpkg -L pacote.deb
B) dpkg -l pacote.deb
C) dpkg -c pacote.deb
D) dpkg -I pacote.deb
A: C) dpkg -c pacote.deb

---

Q: Qual opção do `dpkg` é usada para exibir informações sobre um arquivo de pacote `.deb` não instalado?
A) -I (--info)
B) -l (--list)
C) -s (--status)
D) -S (--search)
A: A) -I (--info)

---

Q: Ao administrar um sistema Debian, qual comando exibe todos os pacotes atualmente instalados no sistema usando a base de dados do `dpkg`?
A) dpkg --show-all
B) dpkg --get-selections
C) dpkg --list-all
D) dpkg -S \*
A: B) dpkg --get-selections

---

Q: Se você precisa descobrir qual pacote Debian instalado possui o arquivo de configuração `/etc/hosts`, qual comando você utilizaria?
A) dpkg -l /etc/hosts
B) dpkg -c /etc/hosts
C) dpkg -S /etc/hosts
D) dpkg -L /etc/hosts
A: C) dpkg -S /etc/hosts

---

Q: Qual opção do comando `dpkg` remove um pacote e, ao mesmo tempo, apaga todos os seus arquivos de configuração associados?
A) -r (--remove)
B) -P (--purge)
C) -e (--erase)
D) -d (--delete)
A: B) -P (--purge)

---

Q: Qual é a função do comando `dpkg-reconfigure` em um sistema Debian?
A) Reinstala o pacote baixando-o do servidor online
B) Repara pacotes quebrados instalando dependências ausentes
C) Executa novamente o script de pós-instalação para restaurar ou alterar as configurações padrão de um pacote instalado
D) Altera a arquitetura do pacote de 32 bits para 64 bits
A: C) Executa novamente o script de pós-instalação para restaurar ou alterar as configurações padrão de um pacote instalado

---

Q: Por que o comando `apt-get` é frequentemente preferido em relação ao `dpkg` para a instalação de novos softwares?
A) O `apt-get` converte arquivos RPM para DEB em tempo real
B) O `apt-get` resolve automaticamente e baixa dependências ausentes de repositórios online
C) O `apt-get` opera de forma totalmente isolada em "sandboxes"
D) O `apt-get` funciona em qualquer distribuição Linux, incluindo Red Hat
A: B) O `apt-get` resolve automaticamente e baixa dependências ausentes de repositórios online

---

Q: Qual comando da suíte APT é usado especificamente para realizar operações e consultas no índice de pacotes local, como buscar ou visualizar detalhes sem instalar nada?
A) apt-get
B) apt-file
C) apt-cache
D) dpkg-query
A: C) apt-cache

---

Q: Como você atualiza o índice local de pacotes usando as fontes listadas em `/etc/apt/sources.list`?
A) apt-get upgrade
B) apt-get update
C) apt-cache refresh
D) dpkg --update
A: B) apt-get update

---

Q: Qual ação do `apt-get` atualiza todo o sistema, mas monitora ativamente as dependências e permite remover pacotes obsoletos para resolver conflitos?
A) apt-get upgrade
B) apt-get install --all
C) apt-get dist-upgrade
D) apt-get update
A: C) apt-get dist-upgrade

---

Q: Qual comando permite recuperar o pacote de código-fonte de um software especificado nos repositórios Debian?
A) apt-cache fetch
B) apt-get source
C) apt-file source
D) dpkg -s
A: B) apt-get source

---

Q: Qual diretório local é utilizado pelo APT como cache para armazenar temporariamente os arquivos `.deb` baixados?
A) /var/lib/dpkg/archives
B) /etc/apt/cache
C) /var/cache/apt/archives
D) /tmp/apt-packages
A: C) /var/cache/apt/archives

---

Q: Em um arquivo `/etc/apt/sources.list`, qual seção indica repositórios contendo softwares mais recentes que não estão no repositório principal estável?
A) security
B) universe
C) backports
D) main
A: C) backports

---

Q: Qual ferramenta do APT pode procurar por um arquivo específico dentro de todos os pacotes do repositório, mesmo que os pacotes NÃO estejam instalados no sistema?
A) dpkg-query
B) apt-cache
C) apt-file
D) apt-get find
A: C) apt-file

---

Q: Antes de usar o `apt-file` para pesquisar em arquivos, o que você deve fazer para garantir resultados precisos?
A) Executar `apt-file update`
B) Executar `apt-get update`
C) Instalar o pacote `dpkg-dev`
D) Reiniciar o daemon do `apt`
A: A) Executar `apt-file update`

---

Q: Qual comando exibe informações detalhadas de um pacote no Debian, utilizando os dados de cache do repositório, incluindo suas dependências reversas?
A) apt-get info
B) apt-cache showpkg
C) dpkg -s
D) apt-file list
A: B) apt-cache showpkg

---

Q: Qual é a convenção típica de nomenclatura para um arquivo de biblioteca compartilhada (shared object) no Linux?
A) libLIBRARYNAME.so.VERSION
B) LIBRARYNAME.lib.VERSION
C) libLIBRARYNAME.a.VERSION
D) lib.LIBRARYNAME.VERSION.dll
A: A) libLIBRARYNAME.so.VERSION

---

Q: Arquivos de biblioteca com a extensão `.a` representam qual tipo de biblioteca?
A) Bibliotecas de link dinâmico
B) Bibliotecas estáticas que são integradas ao programa durante a compilação
C) Módulos de bibliotecas do kernel que são carregados sob demanda
D) Bibliotecas de sistema exclusivas do Windows emuladas no Linux
A: B) Bibliotecas estáticas que são integradas ao programa durante a compilação

---

Q: Qual comando exibe as bibliotecas compartilhadas exatas exigidas por um executável específico para rodar (ex: `/bin/echo`)?
A) ldconfig
B) ld
C) ldd
D) lsof
A: C) ldd

---

Q: O sistema usa um catálogo armazenado no arquivo `/etc/ld.so.cache` para encontrar bibliotecas rapidamente. Qual comando atualiza este cache de bibliotecas?
A) ldd --update
B) ldconfig
C) update-lib
D) refresh-cache
A: B) ldconfig

---

Q: Qual variável de ambiente é usada para especificar uma lista de diretórios a serem pesquisados por bibliotecas compartilhadas antes de verificar os diretórios padrão do sistema?
A) LIBRARY_PATH
B) LD_LIBRARY_PATH
C) PATH
D) LD_CACHE_DIR
A: B) LD_LIBRARY_PATH

---

Q: O que é o PID no contexto do gerenciamento de processos do Linux?
A) O identificador exclusivo do pacote
B) A prioridade interativa do processo
C) O Identificador de Processo atribuído pelo sistema a um programa em execução
D) O caminho do dispositivo de inicialização primário
A: C) O Identificador de Processo atribuído pelo sistema a um programa em execução

---

Q: O que define um processo "Zombie" no Linux?
A) Um processo que está pausado aguardando entrada do usuário
B) Um processo filho que terminou, mas seu pai ainda não processou o código de retorno
C) Um daemon de sistema que reinicia repetidamente devido a um erro
D) Um processo executando incondicionalmente em segundo plano
A: B) Um processo filho que terminou, mas seu pai ainda não processou o código de retorno

---

Q: Ao inspecionar processos usando a sintaxe estilo Unix, qual combinação de flags para o comando `ps` exibe TODOS os processos do sistema (equivalente a `-A`) e de forma estendida?
A) ps -ef
B) ps aux
C) ps -u
D) ps -t
A: A) ps -ef

---

Q: Qual comando fornece uma visão contínua, dinâmica e em tempo real da carga do sistema, CPU, memória e processos ativos?
A) free
B) uptime
C) top
D) ps
A: C) top

---

Q: Dentro do ambiente interativo do `top`, qual tecla é usada para matar (kill) um processo específico?
A) q
B) k
C) r
D) d
A: B) k

---

Q: Dentro do ambiente interativo do `top`, qual tecla muda a prioridade (renice) de um processo específico?
A) q
B) k
C) r
D) p
A: C) r

---

Q: No utilitário `top`, como um usuário altera a frequência (intervalo) em que a exibição se atualiza?
A) Pressionando `u` ou `i`
B) Pressionando `d` ou `s`
C) Pressionando `<` ou `>`
D) Pressionando `c` ou `f`
A: B) Pressionando `d` ou `s`

---

Q: Como você seleciona campos de classificação diferentes para a exibição no `top` (como classificar por uso de Memória em vez de CPU)?
A) Pressionando `F` ou `O`
B) Pressionando `c` ou `m`
C) Pressionando `l` ou `t`
D) Pressionando `z` ou `b`
A: A) Pressionando `F` ou `O`

---

Q: Qual comando de linha leve extrai especificamente a carga média do sistema (load average) e o tempo de atividade, sem mostrar uma lista contínua de processos?
A) free
B) uptime
C) lsof
D) dmesg
A: B) uptime

---

Q: O que é o GNU Screen?
A) Um ambiente gráfico de área de trabalho completo
B) Um visualizador de arquivos paginado em modo de texto
C) Um multiplexador de terminal que permite gerenciar várias janelas de shell a partir de uma sessão
D) Um utilitário de captura de tela de interface de linha de comando
A: C) Um multiplexador de terminal que permite gerenciar várias janelas de shell a partir de uma sessão

---

Q: Dentro do utilitário `screen`, qual é a combinação de teclas de prefixo padrão antes de invocar um comando, como alternar entre janelas?
A) Ctrl+B
B) Ctrl+C
C) Ctrl+Z
D) Ctrl+A
A: D) Ctrl+A

---

Q: Se você estiver executando uma sessão no `screen` e desejar "desanexar" (detach) a sessão deixando-a rodar no servidor em segundo plano, qual tecla você pressiona após o prefixo (Ctrl+A)?
A) C
B) D
C) K
D) \
A: B) D

---

Q: Qual das seguintes alternativas é uma alternativa moderna e popular ao GNU Screen e utiliza Ctrl+B como sua tecla de prefixo padrão?
A) xargs
B) nohup
C) tmux
D) byobu
A: C) tmux

---

Q: Em ambientes de terminal, qual metacaractere anexado ao final de um comando orienta o shell a iniciar e executar esse comando no plano de fundo imediatamente?
A) | (pipe)
B) >
C) &
D) ;
A: C) &

---

Q: Você está executando um processo demorado no primeiro plano (foreground) e percebe que ele está bloqueando seu shell. Qual combinação de teclas pausa a execução e devolve o controle do prompt?
A) Ctrl+C
B) Ctrl+D
C) Ctrl+Z
D) Ctrl+X
A: C) Ctrl+Z

---

Q: Depois de suspender um processo usando Ctrl+Z, qual comando orienta esse processo a retomar e continuar sua execução no plano de fundo?
A) fg
B) bg
C) jobs
D) nohup
A: B) bg

---

Q: Qual comando permite visualizar a lista de processos que estão atualmente em execução em plano de fundo (background) ou pausados pelo shell local?
A) ps
B) top
C) jobs
D) list
A: C) jobs

---

Q: Qual utilitário traz o trabalho (job) ativo no plano de fundo número 1 de volta para o primeiro plano (foreground) do terminal?
A) fg 1
B) bg 1
C) jobs -f 1
D) resume 1
A: A) fg 1

---

Q: Qual é a faixa de valores aceitos para a prioridade (niceness) de um processo padrão no Linux?
A) 0 a 100
B) -20 a 19
C) 1 a 99
D) -19 a 20
A: B) -20 a 19

---

Q: No Linux, qual valor de niceness corresponde à "maior" prioridade de agendamento de CPU?
A) 19
B) 0
C) 100
D) -20
A: D) -20

---

Q: Ao iniciar um novo aplicativo usando o comando `nice` sem especificar explicitamente um valor, qual nível de niceness é aplicado por padrão?
A) Ele diminui a prioridade atual adicionando 10
B) Ele define a prioridade para o máximo (-20)
C) Ele herda o valor exato do shell sem alterá-lo
D) Ele atribui a prioridade para o menor (19)
A: A) Ele diminui a prioridade atual adicionando 10

---

Q: Quem pode alterar a prioridade de um processo existente para um valor de niceness negativo (maior prioridade)?
A) Qualquer usuário que seja dono do processo
B) Apenas o usuário root
C) Apenas membros do grupo wheel
D) O sistema não permite valores negativos
A: B) Apenas o usuário root

---

Q: Qual utilitário é utilizado para alterar a prioridade de agendamento de um processo QUE JÁ ESTÁ em execução?
A) nice
B) top
C) renice
D) pkill
A: C) renice

---

Q: Sinais no Linux controlam o comportamento dos processos. Qual é o valor numérico do sinal KILL, que termina incondicionalmente um processo sem chance de limpeza?
A) 1 (HUP)
B) 9 (KILL)
C) 15 (TERM)
D) 18 (TSTP)
A: B) 9 (KILL)

---

Q: Qual é o sinal padrão emitido pelo comando `kill` se nenhum sinal específico for explicitamente indicado?
A) SIGKILL (9)
B) SIGINT (2)
C) SIGTERM (15)
D) SIGQUIT (3)
A: C) SIGTERM (15)

---

Q: Qual sinal é frequentemente usado para notificar um daemon (como um servidor web) para recarregar com segurança seus arquivos de configuração sem derrubar o processo principal?
A) SIGHUP (1)
B) SIGSEGV (11)
C) SIGCONT (19)
D) SIGSTOP (17)
A: A) SIGHUP (1)

---

Q: Qual é a principal diferença entre os comandos `kill` e `killall`?
A) `kill` requer o nome do processo, enquanto `killall` requer o PID
B) `kill` afeta apenas o primeiro plano, `killall` afeta apenas o plano de fundo
C) `kill` atua sobre IDs de processos (PIDs) exatos, enquanto `killall` atua sobre todos os processos que correspondem ao nome do comando especificado
D) `kill` envia SIGTERM, enquanto `killall` envia SIGKILL unicamente
A: C) `kill` atua sobre IDs de processos (PIDs) exatos, enquanto `killall` atua sobre todos os processos que correspondem ao nome do comando especificado

---

Q: Qual comando de sinalização procura processos com base em expressões e nomes, enviando sinais aos processos correspondentes, de forma semelhante ao `killall`?
A) pgrep
B) pkill
C) kill-name
D) signals
A: B) pkill

---

Q: Se um administrador não deseja terminar um processo imediatamente, mas quer obter a lista de PIDs correspondentes ao comando "ssh", qual utilitário deve ser usado?
A) pkill
B) pidof
C) pgrep
D) ls-pid
A: C) pgrep

---

Q: O comando `killall` permite o término de processos por nome. O que a opção `-I` geralmente faz ao usar esse comando em distribuições padrão (se disponível)?
A) Ignora processos que não são do usuário root
B) Pergunta (Modo Interativo) antes de matar cada processo
C) Força um SIGKILL incondicional
D) Opera desconsiderando a distinção entre maiúsculas e minúsculas no nome (Ignore case)
A: B) Pergunta (Modo Interativo) antes de matar cada processo

---

Q: Qual sinal é enviado para um processo ativo para pausá-lo (permitindo sua continuação no fundo), e é o sinal subjacente ao atalho de teclado Ctrl+Z?
A) SIGINT (2)
B) SIGTERM (15)
C) SIGTSTP (18)
D) SIGSTOP (17)
A: C) SIGTSTP (18)

---

Q: O comando `ps -C bash` é usado para qual finalidade específica?
A) Exibir todos os processos do sistema limitados apenas ao usuário 'bash'
B) Exibir apenas processos cujo comando exato seja 'bash'
C) Alterar as configurações principais do aplicativo 'bash'
D) Mudar a formatação de exibição do utilitário `ps`
A: B) Exibir apenas processos cujo comando exato seja 'bash'

---

Q: Um processo em execução possui um valor "NI" (Niceness) e um "PR" (Priority). No utilitário `top`, se o valor NI aumentar, o que geralmente acontece com sua prioridade para o kernel?
A) A prioridade do processo ao acessar CPU aumenta
B) A prioridade do processo não se altera
C) A prioridade do processo ao acessar CPU diminui
D) O processo é enviado instantaneamente para o estado Zombie
A: C) A prioridade do processo ao acessar CPU diminui

---

Q: Nas colunas padrão do comando `top`, o que a coluna VIRT representa?
A) A quantidade de memória RAM física (excluindo Swap) em uso pelo processo
B) A quantia total de memória virtual reservada para o processo (incluindo Swap)
C) A porcentagem de espaço de disco sendo gravado
D) A prioridade dinâmica na memória cache
A: B) A quantia total de memória virtual reservada para o processo (incluindo Swap)

---

Q: Em relação a gerenciamento de bibliotecas, quando um programa utiliza um recurso de vinculação dinâmica (dynamic linking), a biblioteca não é inserida diretamente no binário do executável. Quando a biblioteca é efetivamente carregada na memória?
A) Ao instalar o pacote RPM correspondente
B) Quando o arquivo de configuração `.conf` for modificado
C) Pelo linker dinâmico (`ld.so`) durante a execução do programa
D) Após um comando de `reboot` pelo Kernel
A: C) Pelo linker dinâmico (`ld.so`) durante a execução do programa

---

Q: Ao extrair e verificar propriedades de um pacote RPM sem instalá-lo (`rpm -qlp arquivo.rpm`), qual caractere na opção `-p` é fundamental?
A) O caractere p informa que a saída deve ser enviada para um pipe
B) O caractere p refere-se a 'package' (arquivo de pacote local, não na base instalada)
C) O caractere p sinaliza para ignorar as permissões
D) O caractere p executa a ação de purgar arquivos associados
A: B) O caractere p refere-se a 'package' (arquivo de pacote local, não na base instalada)

---

Q: Ao instalar novos pacotes via Debian (`apt-get install`), uma fase vital ocorre onde a pós-instalação configura o software recém-extraído. Qual utilitário APT refaz exatamente essa fase em pacotes já instalados?
A) dpkg-reconfigure
B) apt-cache rebuild
C) apt-get redo
D) debconf-show
A: A) dpkg-reconfigure

---

Q: No diretório `/etc/apt/sources.list`, componentes descrevem categorias de software disponíveis. O que a categoria "security" designa?
A) Aplicativos em versões de teste intensivo
B) Atualizações restritas para evitar vulnerabilidades do sistema
C) Versões do kernel desatualizadas e banidas
D) Ferramentas apenas de compilação sem pacotes binários
A: B) Atualizações restritas para evitar vulnerabilidades do sistema

---

Q: Como você lista o conjunto de arquivos não apenas do diretório atual, mas também descompacta o arquivo `emacs.cpio` recriando seus subdiretórios localmente no diretório de trabalho?
A) cpio -idv < emacs.cpio
B) cpio -o > emacs.cpio
C) rpm2cpio emacs.cpio | tar
D) dpkg -x emacs.cpio .
A: A) cpio -idv < emacs.cpio

---

Q: No utilitário `tmux` (que atua como uma alternativa ao GNU Screen), como os comandos são normalmente iniciados após iniciar uma sessão?
A) Pressionando Alt+T, seguido de uma tecla de atalho
B) Pressionando Ctrl+B, seguido de uma tecla de atalho
C) Pressionando Esc, seguido de uma tecla de atalho
D) Pressionando Ctrl+A, seguido de uma tecla de atalho
A: B) Pressionando Ctrl+B, seguido de uma tecla de atalho

---

Q: Qual ambiente de desktop usa por padrão o Kwin como seu Gerenciador de Janelas e os componentes chamados Plasmoids?
A) GNOME
B) XFCE
C) LXDE
D) KDE Plasma
A: D) KDE Plasma

---

Q: Qual organização ou grupo fornece especificações vitais para a interoperabilidade da área de trabalho, como "entradas de desktop" (arquivos .desktop)?
A) freedesktop.org
B) GNU Project
C) Linux Foundation
D) LPI
A: A) freedesktop.org

---

Q: No contexto do utilitário GNU `screen`, o que a opção `screen -ls` executa?
A) Instala o shell na memória do servidor
B) Lista todas as sessões multiplexadas do screen que estão atualmente ativas (desanexadas ou não)
C) Lista os arquivos de um diretório usando um renderizador melhorado
D) Deleta a última sessão anexada forçadamente
A: B) Lista todas as sessões multiplexadas do screen que estão atualmente ativas (desanexadas ou não)

---

Q: Qual das seguintes opções de filtragem ao utilitário `ps` limita a saída exclusivamente aos processos iniciados pelo usuário real ou efetivo de nome 'Christine'?
A) ps -N Christine
B) ps -u Christine
C) ps -p Christine
D) ps -g Christine
A: B) ps -u Christine

---

Q: O comando `ps` aceita vários estilos de parâmetros por razões históricas. O parâmetro que NÃO possui um traço (por exemplo, `ps aux`) origina-se de qual formato legado?
A) Formato BSD
B) Formato Unix SysV
C) Formato longo do GNU
D) Formato POSIX
A: A) Formato BSD

---

Q: Qual comando de gerenciamento pode relatar o local exato (caminhos absolutos) e listar todos os nomes dos arquivos de biblioteca instalados em um sistema RPM usando seu próprio repositório cache local?
A) rpm -qc
B) rpm -qa
C) rpm -ql
D) rpm -i
A: C) rpm -ql

---

Q: No arquivo de banco de dados RPM, pacotes dependentes são cruciais. Se você tentar instalar `gimp-2.8.rpm` e encontrar o erro "Failed dependencies", o que o RPM fará automaticamente?
A) Falhará a instalação e fará um aborto sem procurar os pacotes na internet
B) Fará um download oculto resolvendo a biblioteca
C) Ignorará e instalará o pacote mesmo com quebras do sistema
D) Pedirá que você execute o `apt-get` local
A: A) Falhará a instalação e fará um aborto sem procurar os pacotes na internet

---

Q: No gerenciador APT do Debian, as operações efetuadas na memória cache de pesquisa de pacotes são tratadas por qual comando independente do apt-get?
A) apt-cache
B) dpkg-query
C) apt-search
D) deb-find
A: A) apt-cache

---

Q: No Linux, qual componente atua resolvendo localmente as dependências de biblioteca compartilhada exigidas para execução do programa em tempo real?
A) initrd
B) bootloader
C) linker dinâmico / dynamic linker
D) flatpak
A: C) linker dinâmico / dynamic linker

---

Q: Ao instalar novos aplicativos via `apt-get install`, uma fase de verificação verifica as assinaturas do pacote para garantir validade e autenticidade. Como um sistema Linux baseado em Debian tipicamente gerencia e atualiza essas assinaturas globalmente?
A) Utilizando pacotes com certificados e comandos em segundo plano
B) O `dpkg` compila uma verificação baseada unicamente no kernel
C) Através de chaves PGP baixadas em anexo nos tarballs do repositório
D) Via `rpm -V` embutido
A: A) Utilizando pacotes com certificados e comandos em segundo plano

---
