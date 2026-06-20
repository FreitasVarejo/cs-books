Q: No gerenciamento de processos do Linux, o que significa a sigla PID?
A) Priority Identification Descriptor
B) Process Identifier
C) Program Installation Directory
D) Primary Interrupt Device
A: B) Process Identifier

---

Q: Qual é o primeiro processo iniciado pelo kernel do Linux, responsável por gerar todos os outros processos do sistema?
A) bash
B) grub
C) init (ou systemd)
D) kthreadd
A: C) init (ou systemd)

---

Q: O que caracteriza um processo no estado "Zombie" (Z) no Linux?
A) Um processo que está consumindo 100% da CPU e não responde a sinais
B) Um daemon em segundo plano que reinicia automaticamente após falhar
C) Um processo filho que já terminou sua execução, mas cujo processo pai ainda não leu seu código de saída
D) Um processo que foi movido da memória RAM para a área de Swap
A: C) Um processo filho que já terminou sua execução, mas cujo processo pai ainda não leu seu código de saída

---

Q: Quando você visualiza a lista de processos, nota alguns cujos comandos estão entre colchetes, como `[kthreadd]`. O que isso geralmente indica?
A) Que o processo foi iniciado por um usuário sem privilégios
B) Que o processo está em estado Zombie
C) Que é um processo de nível de kernel ou que está "sleeping" (movido para o disco/swap)
D) Que o processo está consumindo mais de 50% de memória física
A: C) Que é um processo de nível de kernel ou que está "sleeping" (movido para o disco/swap)

---

Q: Na saída do comando `ps -ef`, o que a coluna "PPID" representa?
A) Priority Process Identifier
B) Parent Process ID (ID do processo pai)
C) Primary Partition ID
D) Process Page Index Directory
A: B) Parent Process ID (ID do processo pai)

---

Q: Qual é a diferença fundamental entre as informações exibidas pela coluna "TIME" e a coluna "STIME" na saída padrão do `ps`?
A) STIME é o tempo total na CPU; TIME é o horário em que o processo parou
B) TIME é o tempo cumulativo de uso da CPU pelo processo; STIME é a hora exata em que o processo foi iniciado
C) TIME indica há quanto tempo o usuário está logado; STIME indica o tempo restante para o timeout do processo
D) STIME é o tempo gasto na memória Swap; TIME é o tempo gasto na memória RAM
A: B) TIME é o tempo cumulativo de uso da CPU pelo processo; STIME é a hora exata em que o processo foi iniciado

---

Q: Qual opção de sintaxe do comando `ps` (estilo Unix) é utilizada para exibir TODOS os processos em execução no sistema, de forma equivalente a `ps -e`?
A) ps -A
B) ps -u
C) ps aux
D) ps -U
A: A) ps -A

---

Q: Você precisa listar todos os processos no sistema, mas deseja excluir um grupo específico de processos da sua seleção. Qual flag do comando `ps` inverte a seleção?
A) ps -r
B) ps -x
C) ps -N
D) ps -i
A: C) ps -N

---

Q: Qual parâmetro do `ps` permite exibir apenas os processos que estão vinculados a um comando específico pelo nome, como o bash?
A) ps -c bash
B) ps -C bash
C) ps --cmd bash
D) ps -p bash
A: B) ps -C bash

---

Q: Como você filtra a saída do `ps` para exibir exclusivamente processos vinculados ao terminal `tty3`?
A) ps -tty 3
B) ps -t tty3
C) ps --terminal=3
D) ps -T 3
A: B) ps -t tty3

---

Q: O comando `ps` suporta três estilos de sintaxe devido a mesclagens históricas. Qual destas é considerada a sintaxe estilo BSD?
A) ps -ef
B) ps --user root
C) ps aux
D) ps -U root
A: C) ps aux

---

Q: Na saída do utilitário `top`, o "Load Average" exibe três valores numéricos. O que esses números representam?
A) A porcentagem de uso da CPU no último 1 minuto, 5 minutos e 15 minutos
B) O uso em Megabytes de memória RAM ativa, Swap e Cache
C) O número médio de processos na fila de execução ou esperando processamento nos últimos 1, 5 e 15 minutos
D) O tempo máximo de resposta de rede do servidor em milissegundos
A: C) O número médio de processos na fila de execução ou esperando processamento nos últimos 1, 5 e 15 minutos

---

Q: Ao monitorar a saúde do sistema através do "Load Average", qual dos três valores fornecidos é o mais crítico para indicar uma sobrecarga sustentada e prolongada?
A) A média de 1 minuto
B) A média de 5 minutos
C) A média de 15 minutos
D) O pico instantâneo de uso da RAM
A: C) A média de 15 minutos

---

Q: Qual utilitário fornece uma visão dinâmica e em tempo real dos processos ativos, atualizando-se continuamente em vez de fornecer apenas um instantâneo estático?
A) ps
B) top
C) uptime
D) jobs
A: B) top

---

Q: Dentro do ambiente interativo do comando `top`, qual tecla de atalho é usada para alterar a prioridade ("renice") de um processo em execução?
A) k
B) p
C) n
D) r
A: C) r

---

Q: Você está visualizando os processos através do comando `top` e percebe um processo travado. Qual tecla permite enviar um sinal (por padrão, SIGTERM) para encerrar (kill) o processo diretamente pela interface do `top`?
A) q
B) k
C) x
D) d
A: B) k

---

Q: Qual tecla interativa do `top` permite alterar o intervalo de atualização da tela (que por padrão é de 3 segundos)?
A) d (ou s)
B) u
C) i
D) c
A: A) d (ou s)

---

Q: No utilitário `top`, qual tecla interativa permite alternar entre a exibição apenas do nome do comando e a exibição do caminho absoluto/linha de comando completa?
A) W
B) l
C) c
D) M
A: C) c

---

Q: Qual tecla interativa do `top` permite selecionar um campo específico (como %MEM ou %CPU) pelo qual você deseja ordenar a lista de processos?
A) F (ou O)
B) R
C) M
D) u
A: A) F (ou O)

---

Q: Na área de tarefas do comando `top`, a coluna "VIRT" (Virtual Memory) indica o quê?
A) O tamanho da memória física (RAM) residente em uso pelo processo
B) O espaço de memória em cache
C) A quantidade total de memória virtual (RAM + Swap) consumida pelo processo
D) A quantidade de memória de vídeo dedicada
A: C) A quantidade total de memória virtual (RAM + Swap) consumida pelo processo

---

Q: Qual coluna no comando `top` mostra especificamente a quantidade de Memória Física (RAM) não trocada (não-swap) que o processo está utilizando no momento?
A) VIRT
B) SHR
C) RES
D) NI
A: C) RES

---

Q: Na área de resumo da CPU do utilitário `top`, o status `%Cpu(s): id` indica o quê?
A) A porcentagem de tempo que a CPU está ociosa (idle)
B) O tempo gasto processando interrupções de hardware
C) A porcentagem de CPU aguardando operações de I/O
D) O tempo da CPU consumido por processos de usuário
A: A) A porcentagem de tempo que a CPU está ociosa (idle)

---

Q: No cabeçalho `%Cpu(s)` do `top`, o indicador `wa` alerta sobre:
A) Processos em modo zumbi
B) O tempo que a CPU gasta esperando (waiting) por operações de leitura/escrita em disco (I/O)
C) O atraso de latência da rede primária
D) O número de usuários ativos aguardando resposta
A: B) O tempo que a CPU gasta esperando (waiting) por operações de leitura/escrita em disco (I/O)

---

Q: Qual comando de linha única extrai as métricas de tempo de atividade (uptime) do sistema e a média de carga (load average), de forma muito mais leve que o `top`?
A) free
B) uptime
C) ps -l
D) lsof
A: B) uptime

---

Q: Qual comando é mais indicado para fornecer uma visão isolada e rápida do uso atual da memória física (RAM) e da memória de troca (Swap) no sistema?
A) free
B) dmesg
C) vmstat
D) lsblk
A: A) free

---

Q: Como você executa um utilitário (como `sleep 3000`) diretamente em segundo plano (background) a partir do prompt do shell?
A) Adicionando o caractere `|` ao final do comando
B) Adicionando o caractere `&` ao final do comando
C) Pressionando `Ctrl+C` antes do comando
D) Colocando o comando entre aspas simples
A: B) Adicionando o caractere `&` ao final do comando

---

Q: Se você iniciar um script demorado no primeiro plano (foreground) e desejar pausá-lo (suspendê-lo) temporariamente para liberar o prompt do terminal, qual atalho de teclado você deve usar?
A) Ctrl+Z
B) Ctrl+C
C) Ctrl+D
D) Ctrl+X
A: A) Ctrl+Z

---

Q: Após pausar um processo em execução no terminal com `Ctrl+Z`, qual comando você digita para instruí-lo a continuar sua execução silenciosamente em segundo plano (background)?
A) fg
B) jobs
C) bg
D) nohup
A: C) bg

---

Q: Qual utilitário do shell lista todos os processos atualmente ativos em segundo plano (background) ou pausados (stopped) que foram iniciados a partir do seu terminal atual?
A) top
B) bg
C) jobs
D) list-bg
A: C) jobs

---

Q: Se a saída do comando `jobs` exibir o processo `+ Stopped  vim texto.txt`, qual comando você utilizaria para trazer esse processo específico de volta à edição no terminal principal (foreground)?
A) fg 2
B) bg 2
C) resume 2
D) vim -f 2
A: A) fg 2

---

Q: O GNU Screen e o tmux pertencem a qual categoria de ferramentas de terminal?
A) Editores de texto não-interativos
B) Emuladores de interface gráfica (GUI)
C) Multiplexadores de terminal (Terminal Multiplexers)
D) Sistemas de inicialização do kernel
A: C) Multiplexadores de terminal (Terminal Multiplexers)

---

Q: Ao usar o `screen`, qual é a combinação de teclas padrão (prefixo) necessária antes de executar qualquer subcomando interno (como criar nova janela)?
A) Ctrl+B
B) Ctrl+C
C) Ctrl+A
D) Alt+S
A: C) Ctrl+A

---

Q: Dentro de uma sessão do `screen`, você precisa "desanexar" (detach) a janela atual, deixando o processo rodando no servidor, para voltar ao prompt original. Qual tecla você pressiona LOGO APÓS o prefixo `Ctrl+A`?
A) d
B) x
C) k
D) \
A: A) d

---

Q: Qual das seguintes ferramentas é considerada uma alternativa mais moderna ao GNU Screen e utiliza por padrão a tecla de prefixo `Ctrl+B`?
A) xterm
B) konsole
C) byobu
D) tmux
A: D) tmux

---

Q: Em uma sessão do utilitário `screen`, qual atalho (após o prefixo) é utilizado para dividir a janela atual horizontalmente em dois painéis?
A) Shift+| (Pipe)
B) Shift+S
C) Tab
D) c
A: B) Shift+S

---

Q: Em uma sessão do `screen`, após criar painéis divididos, qual atalho (após o prefixo) pula o foco do cursor para a próxima janela/painel?
A) Tab
B) c
C) K
D) \
A: A) Tab

---

Q: Qual comando lista todas as sessões multiplexadas do `screen` que estão atualmente rodando no sistema, permitindo que você as identifique para reconectar?
A) screen -list (ou screen -ls)
B) screen --show
C) jobs -s
D) top -screen
A: A) screen -list (ou screen -ls)

---

Q: O conceito de "Niceness" no Linux refere-se à prioridade de um processo. Qual é o intervalo de valores de niceness permitidos?
A) 0 a 100
B) -10 a 10
C) -20 a 19
D) 1 a 99
A: C) -20 a 19

---

Q: Na escala de niceness do Linux, qual valor representa a prioridade MÁXIMA de acesso à CPU?
A) 19
B) 100
C) 0
D) -20
A: D) -20

---

Q: Se você iniciar um programa utilizando o comando `nice` sem especificar um valor numérico (`nice ./script.sh`), qual ajuste de niceness o sistema aplica por padrão?
A) O niceness é subtraído em 5 pontos
B) O niceness é definido como 0
C) O niceness aumenta em 10 pontos (reduzindo a prioridade)
D) O niceness é definido para o máximo, -20
A: C) O niceness aumenta em 10 pontos (reduzindo a prioridade)

---

Q: Quem tem permissão no sistema Linux para atribuir um valor de niceness negativo (prioridade mais alta) a um processo?
A) Apenas o usuário root
B) O usuário dono do processo e o root
C) Qualquer usuário pertencente ao grupo "users"
D) O kernel define isso de forma estritamente autônoma
A: A) Apenas o usuário root

---

Q: Qual utilitário é especificamente projetado para alterar o valor de niceness (prioridade) de um processo que JÁ ESTÁ em execução?
A) nice
B) renice
C) chpri
D) topnice
A: B) renice

---

Q: Na coluna de um processo na exibição do `top`, você vê o campo "PR" e o campo "NI". O que o campo "NI" representa?
A) Prioridade em Tempo Real (Real-time Priority)
B) Valor de Nice configurado (Niceness)
C) Número de Interrupções de hardware
D) Network Interface atrelada ao processo
A: B) Valor de Nice configurado (Niceness)

---

Q: Se um usuário comum (sem privilégios administrativos) tenta executar o comando `renice -5 -p 1234` em um de seus próprios processos, qual será o resultado?
A) O comando será bem-sucedido e a prioridade aumentará
B) O comando falhará com erro de "Permission denied" (Permissão negada)
C) O processo 1234 será morto imediatamente
D) O comando aguardará a aprovação via polkit
A: B) O comando falhará com erro de "Permission denied" (Permissão negada)

---

Q: Qual sinal (signal) padrão é emitido aos processos quando utilizamos o comando `kill` sem especificar explicitamente uma flag numérica ou nome de sinal?
A) SIGKILL (9)
B) SIGHUP (1)
C) SIGTERM (15)
D) SIGINT (2)
A: C) SIGTERM (15)

---

Q: Você precisa finalizar um processo de maneira incondicional, pois ele travou e está ignorando o SIGTERM. Qual sinal no Linux força o encerramento sem permitir que o processo reaja ou limpe seus dados?
A) SIGQUIT (3)
B) SIGINT (2)
C) SIGSTOP (17)
D) SIGKILL (9)
A: D) SIGKILL (9)

---

Q: O comando `kill` aceita PIDs (Process IDs), mas também pode encerrar tarefas listadas pelo comando `jobs`. Como você direciona o `kill` para encerrar o "Job 2" da sua sessão de shell atual?
A) kill j2
B) kill %2
C) kill -job 2
D) kill #2
A: B) kill %2

---

Q: Qual sinal é frequentemente utilizado pelos administradores de sistemas para instruir um daemon (como o Apache ou Nginx) a recarregar seus arquivos de configuração com segurança, sem interromper o serviço principal?
A) SIGCONT (19)
B) SIGSEGV (11)
C) SIGTSTP (18)
D) SIGHUP (1)
A: D) SIGHUP (1)

---

Q: Qual sinal de controle corresponde à ação de teclado `Ctrl+C` disparada em um terminal, sinalizando para o processo atual que ele deve ser interrompido?
A) SIGINT (2)
B) SIGQUIT (3)
C) SIGSTOP (17)
D) SIGTERM (15)
A: A) SIGINT (2)

---

Q: Qual é a principal diferença funcional entre os comandos `kill` e `killall`?
A) O `kill` encerra instâncias de segundo plano; o `killall` encerra instâncias em primeiro plano
B) O `kill` aceita o número PID; o `killall` permite matar todos os processos que correspondam exatamente ao nome do comando fornecido
C) O `kill` envia SIGTERM; o `killall` só pode enviar SIGKILL
D) O `killall` não exige privilégios de root, enquanto o `kill` exige
A: B) O `kill` aceita o número PID; o `killall` permite matar todos os processos que correspondam exatamente ao nome do comando fornecido

---

Q: O administrador precisa encerrar todos os processos associados a um terminal travado (`tty3`). Utilizando a família de ferramentas pgrep/pkill, qual comando atende diretamente a esse requisito?
A) pkill -tty 3
B) pkill -t tty3
C) killall tty3
D) kill -tty 3
A: B) pkill -t tty3

---

Q: Em vez de encerrar um processo, você apenas quer saber os PIDs associados a um comando cujo nome contém a string "ssh". Qual comando procura na tabela de processos por correspondência de strings e retorna apenas os PIDs?
A) pgrep
B) pidof
C) pkill
D) killall -q
A: A) pgrep

---

Q: Se um processo estiver pausado (em estado T) devido à recepção de um sinal SIGSTOP ou SIGTSTP, qual sinal deve ser enviado a ele para que ele retome sua execução normal?
A) SIGHUP (1)
B) SIGCONT (19)
C) SIGINT (2)
D) SIGRESUME
A: B) SIGCONT (19)

---

Q: Qual sinal causa o evento associado a "Segmentation violation" (Falha de Segmentação), indicando que um programa tentou acessar uma área de memória restrita?
A) SIGQUIT (3)
B) SIGSEGV (11)
C) SIGSTOP (17)
D) SIGTERM (15)
A: B) SIGSEGV (11)

---

Q: Você percebe na saída do comando `ps` que um processo está com o status 'D'. O que este estado específico significa no Linux?
A) Daemon (Processo em execução contínua no fundo)
B) Defunct (Processo completamente morto e sem pai)
C) Uninterruptible sleep (Geralmente esperando por I/O e imune a sinais até concluir)
D) Detached (Sessão de tela desconectada)
A: C) Uninterruptible sleep (Geralmente esperando por I/O e imune a sinais até concluir)

---

Q: O comando `killall` tem uma opção que permite alterar sua correspondência para ignorar diferenças entre maiúsculas e minúsculas (case-insensitive) ao matar por nome de programa. Qual é essa opção?
A) -i
B) -c
C) -I
D) -u
A: C) -I

---

Q: Um processo zumbi (Z) não pode ser morto através do comando `kill -9`. Qual é a ação corretiva correta para remover um zumbi preso se o seu processo pai continuar ativo sem ler seu status?
A) Enviar o sinal SIGCONT ao processo zumbi
B) Matar ou reiniciar o processo PAI desse zumbi
C) Executar o utilitário `zombie-cleaner`
D) Alterar a prioridade do zumbi para 19 via `renice`
A: B) Matar ou reiniciar o processo PAI desse zumbi

---

Q: O ambiente de multiplexação `screen` suporta diversas opções de linha de comando. Qual opção permite que um usuário reconecte a uma sessão "desanexada" (detached) específica do `screen` previamente iniciada?
A) screen -r
B) screen -a
C) screen -c
D) screen -reconnect
A: A) screen -r

---

Q: Ao executar `top`, a tecla 'i' oculta quais tipos de processos da visualização interativa?
A) Processos zumbis (zombie)
B) Processos com niceness negativo
C) Processos de sistema do usuário root
D) Processos ociosos ou adormecidos (idle/sleeping)
A: D) Processos ociosos ou adormecidos (idle/sleeping)

---

Q: O utilitário `free` possui um argumento para simplificar a leitura de valores grandes convertendo bytes para Megabytes ou Gigabytes dinamicamente. Qual é este formato "human-readable"?
A) free -a
B) free -h
C) free -m
D) free --convert
A: B) free -h

---

Q: Qual das seguintes colunas é apresentada nativamente pela saída estendida (`ps -ef`) e informa o "Terminal" ao qual o processo está anexado?
A) PPID
B) TIME
C) TTY
D) STIME
A: C) TTY

---

Q: Ao observar as métricas de um processo, você vê as informações de "Real User" e "Effective User". O que o "Effective User" dita sobre o processo?
A) É o ID permanente gravado no arquivo `/etc/passwd` atrelado à conta original
B) É a conta de usuário temporária sendo usada no momento pela execução, muitas vezes alterada por programas com SUID
C) Refere-se estritamente ao administrador (root) do sistema
D) Identifica o autor do programa compilado
A: B) É a conta de usuário temporária sendo usada no momento pela execução, muitas vezes alterada por programas com SUID

---

Q: O atalho `Ctrl+A` e depois `\` (barra invertida) é digitado durante o uso do GNU Screen. Qual é o resultado dessa ação na sessão ativa?
A) Divide a tela horizontalmente
B) Bloqueia a sessão de terminal requerendo senha
C) Encerra e mata incondicionalmente todos os processos das janelas ativas e a sessão do screen
D) Copia todo o texto da tela para a área de transferência
A: C) Encerra e mata incondicionalmente todos os processos das janelas ativas e a sessão do screen

---

Q: Você tem múltiplos trabalhos (jobs) no background do seu shell. Ao executar o utilitário `jobs`, você nota um caractere `+` (mais) ao lado do número do trabalho "Job 2". O que esse `+` indica?
A) Que o trabalho concluiu sua execução e está pronto para fechar
B) Que é o "trabalho atual" (current job), e será o padrão se os comandos `fg` ou `bg` forem usados sem argumentos numéricos
C) Que o trabalho tem prioridade de niceness positiva
D) Que o trabalho falhou com erro fatal
A: B) Que é o "trabalho atual" (current job), e será o padrão se os comandos `fg` ou `bg` forem usados sem argumentos numéricos

---

Q: O que a flag `-u` seguida de um nome (ex: `ps -u christine`) especificamente ordena ao utilitário `ps` listar?
A) Apenas processos executados pelo Effective User (UID ou username) fornecido
B) Apenas processos iniciados com o comando `su` por aquele usuário
C) Apenas processos em que aquele usuário alterou a niceness
D) O número total de usuários logados além daquele especificado
A: A) Apenas processos executados pelo Effective User (UID ou username) fornecido

---

Q: Na saída completa de `ps -ef`, a coluna C representa a utilização histórica da CPU ao longo da vida do processo. No `top`, qual tecla interativa permite exibir o tempo cumulativo (Cumulative CPU time) ou tempo de CPU relativo?
A) S
B) C
C) T
D) H
A: A) S

---

Q: Dentro do GNU Screen, caso você queira fechar e matar especificamente a "janela atual" na qual você está operando, sem encerrar o programa Screen como um todo, qual atalho (após o prefixo) você deve acionar?
A) K
B) D
C) \
D) X
A: A) K

---

Q: O atalho de sistema para suspender/pausar e colocar em segundo plano um processo (enviando um SIGTSTP) é:
A) Ctrl+P
B) Ctrl+Z
C) Ctrl+B
D) Ctrl+D
A: B) Ctrl+Z

---

Q: O que ocorrerá se você tentar renicear (diminuir a prioridade, com valores maiores) os processos de outros usuários sendo você um usuário comum (não-root)?
A) O comando funcionará, desde que o novo valor de niceness seja entre 1 e 19
B) O processo mudará temporariamente e retornará à sua niceness base em 10 segundos
C) A alteração de niceness será solicitada ao usuário dono do processo via D-Bus
D) Ocorrerá erro "Permission denied"; usuários comuns só podem alterar a niceness dos seus próprios processos
A: D) Ocorrerá erro "Permission denied"; usuários comuns só podem alterar a niceness dos seus próprios processos

---

Q: Utilizando `ps` na sintaxe BSD (como `ps aux`), o que indica a coluna `STAT` se o valor estiver marcado como "S"?
A) O processo é Compartilhado (Shared)
B) O processo está Dormindo (Sleeping/Interruptible)
C) O processo parou via Sinal (Stopped)
D) O processo é de raiz do Sistema (System)
A: B) O processo está Dormindo (Sleeping/Interruptible)

---

Q: No utilitário `top`, um administrador pressiona a tecla `u` minúscula. O que o `top` fará em seguida?
A) Desfará (Undo) a última modificação de configuração feita no top
B) Mostrará um prompt pedindo a digitação de um nome de usuário, exibindo então apenas os processos desse usuário
C) Alterará a contagem do tempo de sistema (Uptime) de formato detalhado para simplificado
D) Encerra o top imediatamente e atualiza os pacotes do usuário
A: B) Mostrará um prompt pedindo a digitação de um nome de usuário, exibindo então apenas os processos desse usuário

---

Q: Se um processo recebe o sinal `SIGKILL` e não pode capturá-lo, interceptá-lo ou ignorá-lo, o que acontece com os arquivos não salvos abertos por esse processo?
A) O kernel pausa o kill por 5 segundos para auto-salvamento
B) Eles são gravados automaticamente no diretório /tmp
C) Provavelmente ocorrerá perda de dados não salvos, já que o processo não consegue limpar seus encerramentos
D) O processo entra em loop infinito impedindo a perda de dados
A: C) Provavelmente ocorrerá perda de dados não salvos, já que o processo não consegue limpar seus encerramentos

---

Q: Como o utilitário `killall` difere do utilitário `pkill` em relação à forma de correspondência do nome do programa no sistema de arquivos do Linux?
A) `killall` exige correspondência exata de nome do comando em muitos sistemas, enquanto `pkill` utiliza expressões regulares expandidas (regex) para correspondência parcial
B) `pkill` é um comando depreciado para envio de SIGKILL apenas, enquanto `killall` suporta enviar qualquer sinal
C) `killall` só permite matar programas cujos arquivos fonte sejam em scripts bash, enquanto `pkill` mata binários
D) Nenhuma diferença, eles são nomes alternativos (aliases) para exatamente o mesmo binário
A: A) `killall` exige correspondência exata de nome do comando em muitos sistemas, enquanto `pkill` utiliza expressões regulares expandidas (regex) para correspondência parcial

---

Q: O comando `pkill -u emma bash` fará exatamente o quê?
A) Forçará a exclusão da conta do usuário emma usando scripts do bash
B) Matará todos os processos com nome 'bash' que pertençam efetivamente ao usuário 'emma'
C) Mudará a shell padrão da usuária emma para bash sem confirmação
D) Envia o sinal SIGINT para todos os usuários exceto emma
A: B) Matará todos os processos com nome 'bash' que pertençam efetivamente ao usuário 'emma'

---

Q: No utilitário `top`, qual tecla escreve as definições visuais e de filtros que você configurou (como exibir linha de comando cheia ou ordem de cpu) em um arquivo de configuração (`~/.toprc`) para que sejam preservadas no próximo uso?
A) S
B) C
C) W (maiúsculo)
D) s (minúsculo)
A: C) W (maiúsculo)

---

Q: Qual das seguintes linhas representa o formato correto para suspender um processo cujo ID é 4015 usando o comando `kill` explícito com código numérico?
A) kill -Z 4015
B) kill -17 4015
C) kill -18 4015
D) kill -19 4015
A: C) kill -18 4015 (ou kill -17 / SIGSTOP, dependendo do contexto. Mas o SIGTSTP padrão gerado pelo shell suspende e pode ser continuado, logo 18 ou 17 são sinais Stop) _Correção para a Flashcard seguir o padrão absoluto LPI_: No material LPI, SIGSTOP incondicional é 17 e TSTP é 18. Ambos suspendem. Faremos a pergunta mais clara.

Q: O sinal SIGSTOP (Sinal numérico 17) atua interrompendo incondicionalmente um processo sem encerrá-lo. Qual das opções exibe a chamada válida para emitir este sinal ao processo 500?
A) kill -17 500
B) kill -STOP 500
C) kill -s SIGSTOP 500
D) Todas as opções acima são sintaxes perfeitamente válidas do comando kill
A: D) Todas as opções acima são sintaxes perfeitamente válidas do comando kill

---

Q: O comando `uptime` lista a carga média. Qual é a melhor descrição prática para uma carga de "1.00" em um sistema com exato 1 núcleo de processamento lógico (1 CPU)?
A) O processador está 1% em uso
B) O processador falhou em processar e derrubou 100 pacotes
C) A CPU foi perfeitamente 100% utilizada ao longo desse tempo para lidar com exato 1 processo constantemente ativo na fila
D) A máquina está bloqueada aguardando 1 hora de I/O
A: C) A CPU foi perfeitamente 100% utilizada ao longo desse tempo para lidar com exato 1 processo constantemente ativo na fila

---

Q: Para iniciar uma nova janela no terminal multiplexador GNU Screen, qual tecla você aciona no teclado diretamente APÓS o atalho de prefixo `Ctrl+A`?
A) N (Next)
B) W (Window)
C) C (Create)
D) M (Multiplex)
A: C) C (Create)

---

Q: Em ferramentas como `ps`, a coluna `CMD` ou `COMMAND` mostra o nome do programa. Quando visualizamos a listagem, o que os processos envolvidos por parênteses ou colchetes, como `[ksoftirqd/0]`, têm em comum?
A) Foram agendados pela ferramenta `cron`
B) São processos mortos não expurgados
C) São threads e processos pertencentes diretamente ao Kernel, não residindo no espaço do usuário (userspace)
D) São softwares de terceiros instalados no diretório `/opt`
A: C) São threads e processos pertencentes diretamente ao Kernel, não residindo no espaço do usuário (userspace)

---

Q: Qual das seguintes ferramentas fornece na tela a contagem total e segregada do espaço de Memória Compartilhada e "Buff/Cache" em MB ou GB instantaneamente, separada de detalhes de PID?
A) pgrep
B) ps
C) free
D) jobs
A: C) free

---

Q: Ao criar processos em background colocando um `&` ao final da linha, você também recebe a saída padrão (STDOUT) desse processo no terminal. Qual é a prática comum para enviar processos para o background e garantir que suas saídas de texto não poluam o seu terminal visualmente?
A) Utilizar redirecionamento de streams combinando `>`, `2>` ou `&>` para um arquivo de log ou `/dev/null`
B) Alterar a niceness do processo para 19
C) Executar o comando `bg -quiet` antes de dispará-los
D) Fechar o terminal imediatamente e abrir um novo
A: A) Utilizar redirecionamento de streams combinando `>`, `2>` ou `&>` para um arquivo de log ou `/dev/null`

---

Q: Como você executa o comando `top` para exibir e classificar dinamicamente todos os processos, mas pede para ele sair (quit) sozinho após exatamente 5 atualizações em lote (iterações)?
A) top -q 5
B) top -n 5
C) top --limit 5
D) top -p 5
A: B) top -n 5

---

Q: Se você usar a tecla `h` minúscula enquanto opera o `top`, qual será a funcionalidade exibida?
A) Mostra/Esconde as threads individuais pertencentes a processos em execução (Toggle showing of threads)
B) Pede Help (Ajuda) mostrando um manual da tela
C) Halt (Pausa incondicional do top até ser chamado)
D) Hexadecimal view para uso de memória
A: A) Mostra/Esconde as threads individuais pertencentes a processos em execução (Toggle showing of threads)

---

Q: Como as métricas de tempo de execução são avaliadas na prioridade `NI` (niceness) quando uma máquina lida com alta contenção computacional?
A) Prioridades positivas recebem a maior fatia de ciclos incondicionalmente
B) A máquina abandona processos cujo Niceness supera 10
C) Processos com menor valor Nice (ex: -10) ganham fatias de processamento maiores/mais frequentes do agendador em relação aos processos com Nice maior (ex: 5)
D) O Kernel aplica Niceness unicamente na limitação de uso de HD
A: C) Processos com menor valor Nice (ex: -10) ganham fatias de processamento maiores/mais frequentes do agendador em relação aos processos com Nice maior (ex: 5)

---

Q: Você tem um processo PID 5550 pertencente à root rodando com Niceness 0. Qual das opções abaixo pode abaixar a prioridade dele para que não compita tanto com os recursos da máquina?
A) renice -10 -p 5550
B) renice 15 -p 5550
C) chpri 10 5550
D) nice --10 5550
A: B) renice 15 -p 5550

---

Q: Enquanto navega no Linux, qual sinal no Terminal interrompe a entrada de arquivos, sinalizando um "End Of File" (EOF) para aplicações interativas lendo da entrada padrão (STDIN), em oposição ao SIGINT do Ctrl+C?
A) Ctrl+Z
B) Ctrl+X
C) Ctrl+D
D) Ctrl+V
A: C) Ctrl+D

---

Q: O comando `ps -e` e `ps -A` possuem funções idênticas. Qual é o propósito desses sinalizadores baseados no padrão UNIX System V?
A) Executam uma contagem apenas do "Effective user"
B) Mostram "All/Every" (Todos) os processos na máquina de qualquer usuário/terminal
C) Exibem processos formatados estritamente em Árvore
D) Param a máquina para debug de Arquitetura
A: B) Mostram "All/Every" (Todos) os processos na máquina de qualquer usuário/terminal

---

Q: Utilizando o comando `ps`, o que a inclusão do flag `-f` na sintaxe de `ps -ef` habilita na exibição?
A) Filtra a visão por arquivos abertos (Files)
B) Realiza formatação "Full-format" (Formato longo), mostrando UID, PPID, C, e tempo exato
C) Força (Force) a exibição ignorando privilégios root
D) Segue o formato das "Forests" organizando processos visualmente na hierarquia
A: B) Realiza formatação "Full-format" (Formato longo), mostrando UID, PPID, C, e tempo exato

---

Q: O GNU Screen e o tmux permitem que um usuário desconecte a sessão do terminal preservando o estado e reanexando de outro local seguro. Se um programa demorado falhar com erro interno após desconexão no screen, a sessão do multiplexador continuará sendo registrada pelo sistema hospedeiro?
A) Não, se houver erro interno o multiplexador cessa a sessão do usuário incondicionalmente
B) Sim, contanto que o shell de dentro do screen continue ativo, você poderá retornar ao screen e ler os erros remanescentes da saída do erro padrão da tarefa no terminal virtualizado
C) Não, multiplexadores param no momento exato em que são desconectados
D) Sim, mas as mensagens são automaticamente limpas por falta de buffer físico
A: B) Sim, contanto que o shell de dentro do screen continue ativo, você poderá retornar ao screen e ler os erros remanescentes da saída do erro padrão da tarefa no terminal virtualizado

---

Q: Você está em um shell e digita `pkill -u root nginx`. Qual impacto exato este comando terá?
A) Irá alterar a niceness do usuário nginx e seus respectivos daemons para zero
B) Mandará o sinal TERM para encerrar instâncias da aplicação 'nginx' mas apenas as que pertencerem ou estiverem rodando pelos privilégios do 'root'
C) Executará nginx forçando permutas para permissão do root
D) Matará de forma abrupta a conta inteira do usuário root
A: B) Mandará o sinal TERM para encerrar instâncias da aplicação 'nginx' mas apenas as que pertencerem ou estiverem rodando pelos privilégios do 'root'

---

Q: Você percebe que o sistema de correio não reiniciou perfeitamente. Como administrador, você emite o comando `kill -1 %3`. O que ocorre?
A) O utilitário kill usa o PID 3 para desligamento forçado
B) Ele mata o usuário de ID 3 que rodou o arquivo 1
C) Envia um sinal `SIGHUP` (sinal 1) especificamente ao trabalho de terminal (Job) de número 3
D) A prioridade do Job 3 é trocada para Niceness +1
A: C) Envia um sinal `SIGHUP` (sinal 1) especificamente ao trabalho de terminal (Job) de número 3

---

Q: Qual das combinações interativas dentro do utilitário `top` inverte as cores no terminal de exibição?
A) y
B) x
C) z
D) I (I maiúsculo)
A: C) z

---

Q: Em um cenário operacional onde você não tem certeza de como a aplicação se chama perfeitamente no executável principal do sistema, mas sabe que lida com java. Qual a ação mais eficaz para listar os identificadores de CPU (PIDs)?
A) killall java
B) bg java
C) pgrep java
D) ping java
A: C) pgrep java

---

Q: Além do comando top, o comando de listagem instantânea `ps` consegue classificar sua base e resultados através da flag long option especial "--sort". Para ordenar pelo uso mais intensivo da CPU pelos comandos em lista no Linux, deve-se usar:
A) ps -el --sort=pcpu
B) ps -el --sort=c
C) ps -el -H
D) ps --ordercpu
A: A) ps -el --sort=pcpu

---

Q: Como classificar a saída de ps em ordem descrescente (o maior gasto de memória primeiro)?
A) Preceder a flag da ordenação por `+`, por exemplo, `--sort=+pmem`
B) Preceder a flag de campo por `-`, por exemplo, `--sort=-pmem`
C) Colocar a flag `--reverse`
D) O sistema unix base faz reverse apenas com `sort -r` como canos externos (pipes)
A: B) Preceder a flag de campo por `-`, por exemplo, `--sort=-pmem`

---

Q: Qual tecla interativa do `top` permite alternar o status das linhas que exibem métricas específicas de memória RAM e Memória Swap (Toggle the MEM and SWAP lines)?
A) R
B) t
C) m
D) S
A: C) m

---

Q: Durante o uso do terminal `tmux`, caso não conheça a listagem de clientes locais já abertos nesse servidor pela sua conta local ou global, qual comando em prompt fornece uma lista de sessões de painéis ativos com tmux?
A) jobs tmux
B) tmux ls (ou tmux list-sessions)
C) pgrep tmux
D) screen -t
A: B) tmux ls (ou tmux list-sessions)

---

Q: Pela interpretação de "signals", quando o próprio sistema entra em shutdown para reinicializar ordenadamente com `reboot` ou `systemctl`, que sinal ele primeiro envia amplamente às instâncias abertas garantindo encerramento brando na limpeza de seus descritores?
A) 9 (SIGKILL)
B) 11 (SIGSEGV)
C) 15 (SIGTERM)
D) 17 (SIGSTOP)
A: C) 15 (SIGTERM)

---

Q: Se, por infelicidade em debug, você mandar um kill incondicional (9 - SIGKILL) para a "mãe" dos processos de sessão de terminal sob as quais todas as suas aplicações e o console bash foram ramificados. O que ocorre com os programas filhos?
A) Passarão as referências parentais para PID 1 e permanecerão órfãos abertos dependendo do contexto da shell pai ou morrerão pelas ramificações
B) Serão automaticamente movidos para a máquina do Root
C) Ocorrerá erro "Permission Denied" nativo
D) A prioridade do Niceness será inflacionada
A: A) Passarão as referências parentais para PID 1 e permanecerão órfãos abertos dependendo do contexto da shell pai ou morrerão pelas ramificações

---

Q: O status 'T' na listagem "STAT" do `ps` ou "S" da tela de tarefas do `top` marca um programa como "Stopped" ou "Traced". Que tipo de ação ou sinal leva um programa em execução normalmente para este estado "T"?
A) Erros graves em memória via SIGSEGV
B) O processo excedeu sua prioridade mínima de execução
C) O recebimento do sinal Ctrl+Z em terminal ou explícito envio de SIGSTOP ou SIGTSTP por gerenciadores de jobs
D) Operações intensas aguardando a finalização da varredura na rede (I/O sleep)
A: C) O recebimento do sinal Ctrl+Z em terminal ou explícito envio de SIGSTOP ou SIGTSTP por gerenciadores de jobs

---

Q: Considere que o processo executado localmente via `sleep 10 &` assumiu a numeração `45678`. O formato representa "[Nº do Job] PID". Se você digitar `kill -9 45678`, você obteve êxito?
A) Não, porque programas de background recusam SIGKILL por defeito numérico
B) Sim, envia o sinal numérico 9 (SIGKILL) perfeitamente validado no ID do processo mapeado pelo sistema
C) Não, porque a sintaxe requer `kill -9 %1` rigorosamente
D) Ocorrerá formatação de processo zumbi ativando logs
A: B) Sim, envia o sinal numérico 9 (SIGKILL) perfeitamente validado no ID do processo mapeado pelo sistema

---

Q: No utilitário de leitura `top`, o campo `%Cpu(s): 0.0 st` (steal time) refere-se especificamente a métricas em qual contexto frequente de sistemas modernos?
A) Latência estrita por roubo computacional via DNS spoofing
B) Porcentagem e penalidade de ciclos de CPU "roubados" involuntariamente pela plataforma host / hypervisor quando a máquina monitorada trata-se especificamente de uma Máquina Virtual (Virtual Machine) operando em provedores
C) Medição exclusiva de disco magnético de rotação lenta (slow tracking)
D) Uso de ciclos de rede para protocolo SSH
A: B) Porcentagem e penalidade de ciclos de CPU "roubados" involuntariamente pela plataforma host / hypervisor quando a máquina monitorada trata-se especificamente de uma Máquina Virtual (Virtual Machine) operando em provedores

---

Q: Você abriu uma sessão no `screen` na sua conta. Foi pra casa. Outro dia no laboratório quer assumir novamente. Ao digitar o comando de reconexão de sessão você é confrontado porque o screen entende que a sessão já encontra-se formalmente 'Anexada' (Attached) em outro terminal que se manteve sem logout na sua casa. Qual flag é utilizada para "forçar desanexo e anexar aqui" assumindo-a (detach and reattach here)?
A) screen -d -r (ou -dr)
B) screen -A -X
C) screen -f -r
D) screen -force
A: A) screen -d -r (ou -dr)

---

Q: Para encerrar o próprio GNU Screen local, e todo seu terminal associado de forma direta através do teclado caso apenas 1 painel virtual esteja em foco sob sua edição de shell, você utilizaria de que manobra?
A) Digitasse exit, ou Ctrl+D para dar logout na subshell atrelada ao terminal, consequentemente derrubando esse screen focado em fim limpo
B) Fecharia a aba gráfica da janela da UI
C) Apertaria Tab até desaparecer da lista multiplex
D) Deletaria via log local (PID /var)
A: A) Digitasse exit, ou Ctrl+D para dar logout na subshell atrelada ao terminal, consequentemente derrubando esse screen focado em fim limpo

---

Q: É possível na inicialização de um comando via `nice` alterar não apenas de +10, mas em outros parâmetros. Qual flag da ferramenta nice define explicitamente o incremento?
A) nice -priority=10
B) nice -n 10
C) nice --num 10
D) nice -p 10
A: B) nice -n 10

---

Q: Após o uso sistemático da CPU para um servidor Web (ex: PID 330) em ambiente crítico de pico com niceness 0 padrão, deseja-se dar uma preferência de velocidade muito grande para ele não travar, enviando niceness negativo forte (ex: -15). Qual usuário executa essa diretiva renice?
A) Qualquer utilizador via Polkit sem senha
B) Apenas utilizadores sudoers / administradores usando `sudo renice -n -15 -p 330`
C) Usuários no grupo www-data sem restrições
D) Apenas o kernel autonomamente via OOM Killer escalável
A: B) Apenas utilizadores sudoers / administradores usando `sudo renice -n -15 -p 330`

---

Q: O comando `ps -u userName` e `ps -U username` exibem, respectivamente:
A) Ambos emitem logs ignorados em U (unknown)
B) Processos do 'Effective user' vs Processos da propriedade 'Real user' original em listagens BSD e Unix-System-V
C) Identificam processos rodando em UEFI modes com flags de upper cases
D) Mostra Uptime cumulativo das requisições via portas
A: B) Processos do 'Effective user' vs Processos da propriedade 'Real user' original em listagens BSD e Unix-System-V

---

Q: Processos em execução consomem tempo cumulativo do agendador. Ao encerrá-los com KILL de emergência, qual processo especial de nível mais alto pode "herdar" a adoção de laços infantis criados subitamente e gerir seus códigos mortos de retornos isolando-os da criação dos "Zumbis perpétuos"?
A) Processo PID 0, reservado de swap
B) Processo init/systemd (Geralmente PID 1)
C) Cron daemon agendador de tempos
D) Kthreadd (Sempre PID 2 globalmente engrenado)
A: B) Processo init/systemd (Geralmente PID 1)

---

Q: O que indica a coluna `SHR` no utilitário `top`?
A) Shell Runtime, em minutos formatados
B) Total em kilobits do HD alocado para Share Pools no disco C:
C) "Shared Memory" (Memória Compartilhada), quantificando blocos de RAM compartilháveis/acessíveis simultaneamente por outros processos interligados na base do Sistema Operacional (ex: bibliotecas em comum dll/.so)
D) Shortened, significando programas pausados
A: C) "Shared Memory" (Memória Compartilhada), quantificando blocos de RAM compartilháveis/acessíveis simultaneamente por outros processos interligados na base do Sistema Operacional (ex: bibliotecas em comum dll/.so)

---
