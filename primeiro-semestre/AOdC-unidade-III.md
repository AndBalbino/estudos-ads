## 1. Unidade de controle (UC)
A UC tem como principal objetivo gerenciar todas as etapas de processamento de uma instrução sincronizando os submódulos internos do processador por intermédio da geração de sinais de controle.
Mas como a UC consegue fazer isso?

A resposta inicia na fase da implementação da UC, concebida pela metodologia conhecida como implementação por hardware (hardwired). Nesta técnica, as etapas de processamento de uma instrução são mapeadas pelos circuitos de eletrônica digital, em que um conjunto de portas lógicas consegue decodificar a instrução em questão, gerando os sinais de controle.
quais etapas de instrução são essas? Uma instrução, para que se possa aproveitar melhor os recursos computacionais e, também, para que os submódulos sejam mais simples, rápidos e otimizados, é quebrada em várias micro instruções (ou micro-operações). A execução de cada micro-operação ficará sob a responsabilidade de um módulo de hardware específico.
Essa divisão da instrução em etapas menores favorece o pipeline, por meio do qual consegue-se antecipar, mais facilmente, o início de uma nova instrução.

### Micro-operações:
Sabemos que cada instrução é dividida em várias operações mais simples denominadas como micro-operações. Mas, não somente a fase de execução propriamente dita é dividida em micro-operações, também, todas as etapas de execução da instrução, ou seja, todo o ciclo de instrução.

</span>
<div align-"center">
<img src="https://user-images.githubusercontent.com/113153237/221052719-991724e3-d87f-4568-bbf1-1ab64e919218.png" width= "500px" />
</div>
*Divisão das etapas de execução em micro-operações, sendo que cada micro-operação é executada em um pulso de máquina.*

Na figura acima podem ser notadas as micro-operações em todo o ciclo de instrução. A etapa de busca da instrução poderá ser, então, dividida em micro-operações, tais como:

- instanciação do registrador MAR (Memory Address Register), com o valor contido em PC (Program Counter);
- ativação do sistema de memória, para acessar o endereço cuja localização está constando no MAR. O valor retornado pela memória será salvo no registrador MBR (Memory Buffer Register);
- incrementação do valor do registrador PC. Essa micro-operação poderá ser realizada concomitantemente à micro-operação descrita anteriormente;
- cópia do valor buscado da memória, que foi salvo no registrador MBR para o registrador IR (Instruction Register).

Ainda em relação à figura acima, o mesmo processo de divisão de uma fase dentro do ciclo de instrução pode ser aplicado ao ciclo indireto. **O ciclo indireto ocorre na fase de busca dos operandos**. Nessa ocasião, o ciclo pode ser dividido nas micro-operações abaixo listadas:

- registrador MAR recebe o campo do IR, que contém o endereço de memória, o qual contém a referência para que seja acessada a informação requerida;
- acessa-se a memória na posição MAR para coletar a referência de memória e armazená-la no MBR;
- atualiza-se o campo de IR para que se possa, na próxima fase, acessar a localização definitiva de memória que contém a informação a ser manipulada.

 Essa divisão em micro-operações em muito facilita a técnica de pipeline, sendo que o tempo para a execução de uma micro-operação é muito menor em relação ao tempo para processar toda a instrução. Por consequência, os módulos responsáveis pela execução da micro-operação tornam-se disponíveis mais rapidamente, favorecendo, portanto, o início de execução da micro-operação referente à instrução seguinte.
 
 ## Ciclos de interrupção, execução e instrução:
 
 A interação entre os dispositivos de E/S (entrada e saída ou I/O – input/output) é feita mediante o envio de sinais de interrupção. Uma interrupção é tratada de acordo com uma sequência de instruções análoga à de um processo (programa em execução). Sendo assim, o processo sob processamento deverá ser interrompido para que sejam carregadas, no pipeline, as instruções relativas à interrupção. No entanto, se uma interrupção, em nível do ciclo de instruções, comporta-se como um processo, então ela também é quebrada em micro-operações? A resposta é sim. Não somente o código, relativo à interrupção em si, é dividido em micro-operações, mas, também, a troca de contexto. Salvar contexto denota a operação de armazenar, na memória (estrutura em pilha), informações tais como o valor do registrador PC, para que, ao término da interrupção, seja possível retornar exatamente ao ponto de parada do programa. As micro-operações para o atendimento da interrupção podem ser expressas na sequência de micro-operações descritas a seguir:

- registrador MBR recebe o valor do PC para que seja empilhado;
- registrador MAR é instanciado com a localização do topo do segmento de pilha (stack segment);
- PC é setado com o endereço da rotina de tratamento da interrupção;
- a memória é acessada para efetivar o empilhamento do PC (contido no MBR).

Na implementação do tratamento de interrupção, o seu término é marcado por uma instrução do tipo IRET (Interrupt Return). As micro-operações relativas ao IRET são parecidas à sequência acima, porém ocorre o desempilhamento do registrador PC.
Cada instrução pertence a um grupo distinto e apresenta uma funcionalidade também distinta. Então, é de se esperar que a sequência de micro-operações varie de instrução para instrução – mesmo entre instruções da mesma classe (mesmo formato de instrução).
Até o momento, foram referenciadas etapas fixas.
Tomemos, para ilustrar a divisão da etapa de execução em micro-operações, duas instruções hipotéticas quaisquer: a primeira trata de uma escrita na memória do tipo STORE posição, e, a segunda, um desvio condicional do tipo JZ offset (jump caso zero).

Para a instrução do tipo STORE posição, vamos supor que o valor a ser salvo na memória, encontra-se no registrador acumulador. Nesse caso, a instrução poderá ser decomposta nas seguintes micro-operações:

- salvar o valor do acumulador no registrador MBR;
- carregar, no registrador MAR, o campo de endereço presente no registrador IR;
- acessar a memória para efetivar a gravação.

Já com relação à instrução JZ offset, vamos supor que a operação de comparação (ou subtração), que servirá de base à instrução de desvio condicional já tenha ocorrido. Dessa forma, a instrução JZ offset poderá ser decomposta nas seguintes micro-operações:

- carregar, em algum registrador R, o valor contido no IR (offset);
- somar, ao registrador R, o valor de PC;
- caso flag Z seja igual a zero, então PC recebe o valor de R.

Apesar de, em ambos os exemplos, as instruções terem sido divididas, coincidentemente, em quatro micro-operações, na realidade, o número de micro-operações pode se diferenciar nas diferentes instruções.

Convém lembrar que o número de micro-operações está relacionado à implementação do processador (organização). Sendo assim, processadores da mesma família (apresentando a mesma arquitetura) podem variar em relação ao número e à forma das micro-operações.

Para controlar a sequência de operações das micro-operações, a unidade de controle manipula um registrador especial para tal função: o ICC (instruction cycle code). Esse registrador é instanciado ao longo da execução das micro-operações para armazenar o estado corrente e, consequentemente, determinar a próxima micro-operação a ser realizada. A figura a seguir ilustra um fluxograma da execução das micro-operações a partir do valor instanciado no registrador ICC.

</span>
<div align-"center">
<img src="https://user-images.githubusercontent.com/113153237/221058336-030c8b0d-a4c8-4eba-be0c-746ad66efcb4.png" width= "500px" />
</div>
*Fluxograma da execução das micro-operações a partir do valor instanciado no registrador ICC.*

Na figura acima, as ações são representadas pelos retângulos, e os hexágonos representam as tomadas de decisão em função do valor do registrador ICC. Na figura, foram convencionados os seguintes valores para ICC: 00 = busca; 01 = indireto; 10 = execução; 11 = interrupção. Dessa forma, foram representadas todas as etapas inerentes ao ciclo de instrução. Com base no valor do ICC, o hardware pode acionar os submódulos correspondentes e rotear as informações por entre eles.

## 2. Função do computador e interconexão

O computador tem por finalidade executar instruções pertencentes a um programa (programas do usuário, do próprio sistema operacional ou referentes ao tratamento das interrupções). Todas as instruções estão dentro de uma das seguintes classes: processador-memória, processador-E/S, processamento propriamente dito e controle.

Então, as micro-operações devem, também, abranger as funcionalidades básicas do computador. Segundo Stallings (2010), as funcionalidades das micro-operações estão classificadas da seguinte forma:

- movimentações de dados do tipo registrador-registrador;
- movimentações de dados entre registrador e barramento (para interfacear, por exemplo, o sistema de memória);
- efetuar operações lógicas ou aritméticas.

 Essas funcionalidades das micro-operações são evocadas para o tratamento das interrupções e, por diversas vezes, acessam os barramentos do sistema para completar as suas ações. 
 
 ### Interrupções: sequenciais, múltiplas e aninhadas:
 
 Interrupções são eventos utilizados para interfacear os dispositivos de E/S com o processador. Elas podem ocorrer a partir da evocação do dispositivo (por exemplo, quando é pressionada uma tecla do teclado) ou a evocação pode partir do software (por exemplo, o programa necessita salvar uma informação em um arquivo).

Em ambos os casos, elas deverão ser tratadas, interrompendo o fluxo de processamento dos aplicativos abertos.
A figura abaixo ilustra o tratamento das etapas de execução de uma instrução envolvendo a manipulação de interrupções.

</span>
<div align-"center">
<img src="https://user-images.githubusercontent.com/113153237/221060310-75f3a2ff-f867-47e0-9a95-653549490b8e.png" width= "500px" />
</div>
*Sequência de etapas para execução das instruções, sendo que, após cada instrução, há a verificação da existência de solicitações de interrupções.*

Na figura acima, nota-se que, após a execução de uma instrução ser completada, há a verificação, se há alguma interrupção enfileirada pendente a ser executada. Nesse caso, ela entraria como um processo normal, ou seja, as instruções vinculadas ao tratamento da interrupção entrariam no fluxo do pipeline.

Quando um fluxo de execução é adicionado ao pipeline, o que acontece quando alguma outra interrupção ocorre? Quando esse cenário ocorre, temos duas maneiras de realizar o tratamento: na primeira forma, assim que o tratamento da interrupção for iniciado, poderemos desabilitar novas interrupções ou permitir que as próprias interrupções sejam interrompidas para o atendimento de outras. A figura abaixo mostra a diferença entre esses dois enfoques.

</span>
<div align-"center">
<img src="https://user-images.githubusercontent.com/113153237/221060687-b4085a84-ea28-4ff8-af7c-be3d6ff48ce9.png" width= "500px" />
</div>
*Tratamento de interrupções com a desabilitação de novas interrupções (a) e tratamento de novas interrupções de forma aninhada (b).*

Em relação à figura acima, temos o tratamento de interrupções sequencialmente (a). Nesse tipo de enfoque, ocorre a desabilitação de interrupções, para que as novas que ocorrerem sejam apenas enfileiradas, de modo que o tratamento ocorra somente após o término da atual. Por sua vez, no tratamento aninhado (b), uma interrupção poderá ser descontinuada, para que seja tratada uma com maior prioridade.

Em ambos os casos (sequencial ou aninhado), ocorrerá a interrupção da execução dos processos do usuário para que as interrupções sejam tratadas pelo pipeline.

### Barramentos: de endereço, dados e controle:

Existem instruções que dependem de uma estrutura de comunicação com os demais módulos do computador (memória e dispositivos de E/S), para que possam ser processadas. Essa estrutura de comunicação é provida pelos barramentos.

</span>
<div align-"center">
<img src="https://user-images.githubusercontent.com/113153237/221423145-fc67f32b-b8c8-4e9e-aca8-ea7aed318ae5.png" width= "500px" />
</div>
*Interfaces requeridas pelos módulos do computador (a) e a estrutura básica de um barramento (b).*

**SCSI:** *Sigla de **Small Computer System Interface**, é uma tecnologia que permite ao usuário **conectar uma larga gama de periféricos**, tais como discos rígidos, unidades CD-ROM.*

Na figura acima, as interfaces dos módulos do computador, em (a), correspondem, em suma, às linhas de dados, endereços e de sinais de controle. Sendo assim, um barramento deve ter, em sua funcionalidade básica, vias para o tráfego de tais sinais (exibidos em (b), destacados em vermelho):

- **vias de dados:** as vias de dados são **responsáveis pelo tráfego, em paralelo, das informações a serem processadas, armazenadas ou enviadas aos dispositivos de E/S**;
- **vias de endereçamento:** tem por objetivo **transmitir endereços de memória ou de módulos de E/S;**
- **vias de sinais de controle:** como sinais de controle podemos ter (STALLINGS, 2010):

- **leitura/escrita de memória:** define a operação a ser realizada quando o acesso à memória for solicitado;

- **leitura/escrita de E/S:** define a operação a ser realizada quando o acesso a algum dispositivo de E/S for solicitado;

- **ACK de transferência (acknowledgment):** o ACK é um sinal de reconhecimento cuja função é avisar o término, de forma satisfatória, da operação de transferência;

- **solicitação de barramento:** sinal gerado por algum módulo para que use o barramento;

- **concessão de barramento:** resposta à solicitação de barramento, outorgando ao módulo, o direito do uso do barramento;

- **requisição de interrupção:** sinal que indica a pendência de alguma interrupção;

- **ACK de interrupção:** reconhecimento da interrupção que estava pendente;

- **clock:** pulsos de sincronização;

- **reset:** efetua a reinicialização dos módulos.

Em alguns modelos de barramentos, como o PCI (Peripheral Component Interconnect), as vias de endereçamento e de dados são multiplexadas. Em canais multiplexados (circuito combinacional dedicado, ou seja, composto de portas lógicas principalmente portas **AND**, possuindo duas ou mais entradas e somente uma única saída.), as vias podem atender às funcionalidades de transporte de forma alternada, ou seja, em certos momentos, transmite-se endereços e, em outros, os dados são trafegados.

**PCI:** *PCI é um barramento para conectar periféricos em computadores baseados na arquitetura IBM PC. O barramento PCI suporta as funções encontradas em um barramento de processador mas em um formato padronizado que é independente de qualquer barramento particular nativo do processador.*

 **Métricas e conceitos associados aos barramentos:**

- **largura do barramento:** referencia-se à quantidade de vias paralelas para o tráfego de informações. A largura do barramento está associada ao tamanho da palavra usada pelo sistema computacional em questão – por exemplo, uma largura de 64 bits ou de 32 bits;
- **topologia:** a topologia está associada ao arranjo físico para a ligação dos módulos. Como topologias mais comuns, encontramos: barramento, anel e linha ponto a ponto;
- **frequência de trabalho:** relativo à frequência, em Hertz (Hz), do sinal de clock usado para a sincronização dos módulos;
- **vazão, largura de banda ou throughput:** a largura de banda é o índice que indica a quantidade de bits transferidos dentro do intervalo de um segundo (bps);
- **sistema de coordenação:** indica como é realizada a coordenação pelo uso do barramento. O sistema pode ser centralizado onde há um árbitro de barramento, cuja função é receber as requisições e, usando um critério de tempo e/ou prioridade, fornecer, a um módulo requisitante, a permissão de uso do barramento. Um mecanismo bastante usado para solicitar e obter acesso ao barramento é denominado “handshake”. Por sua vez, denomina-se controle distribuído quando não há um coordenador. Nesse caso, os próprios módulos decidem entre si qual será o detentor de uso do barramento. Para tanto, usa-se a troca de mensagens ou a passagem de “tokens”. Em sistemas ponto a ponto, podemos, ainda, encontrar solicitações baseadas em “daisy-chain”.

**Handshake:** *Handshake ou aperto de mão é o processo pelo qual duas ou mais máquinas afirmam que reconheceram umas às outras e estão prontas para iniciar a comunicação. O handshake é utilizado em protocolos de comunicação, tais como: FTP, TCP, HTTP, SMB, SMTP, POP3 etc.*

Um computador pode ser dotado de barramentos de vários níveis, atendendo a um conjunto de módulos ou dispositivos. A utilização de uma hierarquia de barramentos permite uma utilização mais eficiente evitando-se que um tipo de fluxo não impacte negativamente em algum outro. Como exemplo, podemos ver a topologia das máquinas usuais atuais, na figura a seguir, em dois níveis de abstração: a configuração de uma máquina dita como convencional (a); e uma configuração de alto desempenho (b).
 
 
</span>
<div align-"center">
<img src="https://user-images.githubusercontent.com/113153237/221424598-0f72e828-fa82-40d2-ab42-08c91ab23a59.png" width= "500px" />
</div>
*Configurações de um barramento: em (a), tem-se uma configuração básica e, em (b), uma configuração de alto desempenho.* 

Na figura acima, temos uma dissociação dos barramentos em função do tipo de comunicação requerida. Nota-se que o barramento do sistema tem por objetivo interligar apenas o processador ao sistema de memória (memória principal e memória cache) devido à alta demanda de uso. Os demais módulos estão sendo interligados por barramento de alta velocidade ou barramento de expansão. No caso, nota-se, na porção denotada por (b), que houve uma incorporação de um barramento de alto desempenho, atendendo os dispositivos mais críticos (como a placa de vídeo). Nesse caso, o tráfego do barramento de expansão fica dissociado em relação ao tráfego do barramento de alta velocidade.
Podemos encontrar essa hierarquia de barramentos nos chipsets (conjunto de circuitos integrados controladores do barramento) atuais. Em tais chipsets podemos encontrar a “ponte norte” (northbridge) como elementos de interligação do processador com o sistema de memória e a placa de vídeo (por exemplo, AGP ou PCI Express). Por sua vez, os demais módulos (placa de vídeo onboard, controladoras de disco, etc.) são interligados pela “ponte sul” (southbridge).

**Chipsets:** *Comumente encontrados em textos de tecnologia e descritivos de equipamentos eletrônicos, são **responsáveis por conectar vários componentes de um aparelho, ligando, em um computador, a placa mãe ao processador.** Em geral, o termo “set” significa um conjunto, nesse caso, de microchips.*

**Northbridge:** *A ponte norte ou northbridge, faz o controle dos componentes denominados rápidos; como é o caso da placa de vídeo, memória RAM e do processador.*

**Southbridge:** *Ponte sul ou southbridge controla os componentes, como portas USB e paralelas, slots PCI e ISA e, os discos rígidos, que são classificados como componentes lentos.*

- [Tudo sobre Chipsets](https://www.clubedohardware.com.br/artigos/placas-mae/tudo-o-que-voc%C3%AA-precisa-saber-sobre-chipsets-r34158/?nbcpage=1) 

Já que existe uma grande preocupação no transporte de informações entre o processador e a memória, dedicando, para isso, um barramento (ponte norte), então a memória também deve ser eficiente para que o tempo de resposta diante das requisições do processador seja mínimo. 

## 3. Visão geral do sistema de memória
### Características dos Sistemas de Memória:
Inicialmente, pode-se falar que as características da memória variam em função da sua funcionalidade e de sua localização. Porém algumas métricas e conceitos podem ser aplicados em qualquer que seja o nível de memória dentro de sua hierarquia. Com isso, segundo (STALLINGS, 2010), uma memória em específico pode ser classificada de acordo com a sua unidade de transferência, método de acesso, desempenho e tecnologia de fabricação.

Define-se unidade de transferência como sendo a forma com que a informação é tratada. A informação pode ser tratada como sendo uma palavra de bits ou um bloco (contendo várias palavras). A palavra geralmente relaciona-se com a largura do barramento (por exemplo, 64 bits) para que as informações não precisem passar por um processo de serialização ou paralelização, ou, ainda, não sejam necessários vários pulsos (ciclos) de clock para ler ou gravar informações frente à memória.

Alguns níveis de memória, por exemplo, a memória externa (discos rígidos), manipulam blocos de informações. Nesse tipo de memória, consegue-se gravar ou ler todo o bloco, gastando-se apenas um ciclo de memória. **Essa quantidade de bits que poderão ser gravados ou recuperados de uma só vez se denomina unidade de transferência**.

Além da unidade de transferência, um outro aspecto a ser considerado relaciona-se com as unidades endereçáveis. A quantidade de unidades endereçáveis é proporcional à quantidade de bits que compõem o endereço. Por exemplo, em um sistema cujo tamanho da palavra é de 16 bits, teremos 2^16 linhas de endereçamento de memória (unidades endereçáveis). Caso a largura da memória seja também de 16 bits então, teremos: 2^16 = 65.536 (64 k) unidades endereçáveis. Cada unidade compreende 16 bits (2 bytes), então a capacidade total da memória é de 64k * 2 bytes = 128 k bytes.

Um outro aspecto a ser considerado relaciona-se ao método de acesso. Método de acesso refere-se a como o item deverá ser localizado na memória. Podemos classificar o método de acesso em quatro tipos:

- **acesso sequencial:** para acessarmos uma informação (no caso denominado como registro), devemos percorrer, sequencialmente, todos os registros anteriores até chegarmos no demandado. Como exemplo de memória que utiliza o acesso sequencial, poderemos relacionar as unidades de fitas magnéticas;
- **acesso direto:** esse método de acesso é utilizado, por exemplo, nas unidades de discos. Para se acessar um registro, primeiro pode-se posicionar o dispositivo de leitura e gravação em uma região específica para que, em seguida, seja possível realizar um acesso sequencial dentro dessa região. Como é necessário um acesso sequencial, não se pode precisar o tempo gasto para acessar um item;
- **acesso aleatório:** em memórias com acesso aleatório, como as memórias principais (memórias RAM – Random Access Memory), a unidade endereçável pode ser acessada diretamente. Dessa forma, o tempo de acesso é constante e determinista, independentemente da posição na qual se encontra o item a ser manipulado;
- **memória associativa:** na técnica de memória associativa, usada, por exemplo, em alguns modelos de memória cache, o item não tem um endereçamento explícito, ou seja, pode estar posicionado em qualquer linha da memória. O processo de busca do item é realizado paralelamente em todas as linhas, comparando-se os seus conteúdos com um padrão de bits que representa a informação demandada.

A tecnologia empregada para o sistema de memória tem um forte impacto sobre a forma de manipulação das informações, custos e a performance computacional. Além de impactar diretamente na volatilidade da memória, as tecnologias de fabricação influenciam na densidade de bits (número de bits armazenados por uma área). Podemos falar sobre dois grandes tipos principais: as memórias do tipo DRAM (Dynamic RAM) e as SRAM (Static RAM).

As **memórias DRAM** são baseadas na utilização de capacitores como elementos básicos de armazenamento. Porém, os capacitores se descarregam com o tempo, sendo necessário um ciclo de realimentação para reativar a sua carga (refresh). Durante o ciclo de refresh, a memória fica bloqueada para leituras e escritas, deixando-a mais lenta em relação à SRAM.

Por sua vez, as **memórias SRAM** usam componentes semicondutores para o armazenamento de bits. Isso faz com que as memórias se tornem mais rápidas em relação à DRAM (pois, além da tecnologia mais rápida, não é necessário o ciclo de refresh). Porém, ocupa um espaço muito maior para armazenar cada bit da informação.

O desempenho de uma memória está relacionado a três métricas:

- **tempo de acesso:** o tempo de acesso ou latência representa o tempo, desde a chegada da requisição ao sistema de memória, para que a informação fique disponível para a transferência;
- **tempo de ciclo de memória:** período no qual possa ser tratada uma segunda solicitação sem causar interferências ou danos às informações manipuladas na requisição anterior;
- **taxa de transferência:** tempo gasto para a completa transferência dos n bits demandados.

Essas métricas, conceitos e tecnologias podem ser empregados no sistema de memória, variando dentro de seu nível hierárquico. 

### Hierarquia de memória e princípios da memória cache:
Tudo a ser processado (as informações e as próprias instruções) deverá ser carregado para os registradores do processador. E, também, os arquivos executáveis que se encontram no disco rígido precisam ser transferidos para a memória principal para que sejam executados. Diante dessas afirmativas, temos a seguinte constituição da hierarquia de memória:

- **registradores:** nível mais alto da hierarquia de memória. São os elementos de memória internamente ao processador, baseados em componentes semicondutores;
- **memória cache:** nível imediatamente abaixo dos registradores. Por se tratar de uma memória de alta velocidade, tem como objetivo diminuir os acessos à memória principal. A memória cache pode, ainda, apresentar três níveis: L1 (level 1), L2 e L3. O nível L1, localizado dentro do núcleo do processador, é sincronizado com a mesma frequência do núcleo. Geralmente o nível L1 é dividido entre L1 de instruções e L1 de dados. O nível L2 encontra-se fora do núcleo, porém dentro do encapsulamento do processador. Trabalha com a metade da frequência do núcleo. Por último, a cache L3 está localizada na placa-mãe, operando na mesma frequência do barramento. A cache é implementada, assim como os registradores, com componentes baseados em semicondutores;
- **memória principal:** componente de memória responsável por conter os processos em execução. Junto com a memória secundária, forma a memória virtual (TANENBAUM, 2013). A memória principal é implementada, geralmente, por componentes capacitivos;
- **memória secundária:** representa o nível mais baixo da memória (mais distante do processador). A memória secundária pode ser exemplificada pelo disco rígido – dispositivo que usa o meio magnético como forma de armazenamento.

Na medida em que se aumenta o nível, ou seja, aproxima-se do processador, tem-se o incremento da performance computacional, diminuição da densidade (capacidade de armazenamento de menos bits por área de superfície), menor capacidade de armazenamento, maior custo por bit.

Dentre os níveis da hierarquia de memória, daremos maior foco, nesse momento, à memória cache devido a sua importância para o aumento da performance computacional do sistema.

Como mencionado antes, o objetivo da cache é diminuir o número de acessos à memória principal. Com isso, atenuam-se os atrasos frente à busca ou gravação das informações junto ao sistema de memória.

O funcionamento da memória cache segue dois princípios: o princípio da localidade espacial e o princípio da localidade temporal. De acordo com Hennessy (2014), eles se definem da seguinte forma:

- **princípio da localidade espacial:** quando um processo usa alguma informação, a probabilidade de usar outras informações próximas é alta;princípio da localidade espacial: quando um processo usa alguma informação, a probabilidade de usar outras informações próximas é alta;
- **princípio da localidade temporal:** a chance de uma informação utilizada recentemente ser utilizada em um futuro próximo é elevada.
 
Então, a memória cache, usando os princípios dessas duas localidades, armazena as informações “estratégicas” – tentando-se, dessa forma, evitar acessos desnecessários à memória principal.

## 4. Elementos do projeto da memória cache
### Mapeamento associativo e direto:
Convém mencionar que a cache manipula blocos de informações (compostos por vários dados ou várias instruções vizinhas).
O **modelo de mapeamento** refere-se à **localização do bloco dentro da cache.** No **mapeamento associativo, um bloco não tem uma posição específica dentro da cache, ou seja, poderá estar em qualquer linha endereçável.** 
No mapeamento associativo, cada bloco da memória principal pode ser carregado em qualquer linha da cache. Com essa estratégia, a cache torna-se mais poderosa, pois permite-se uma maior reutilização das informações armazenadas. Porém o custo por bit é muito dispendioso pelo fato de que, em cada linha, deve ser associado um circuito de comparação. A função desse circuito de comparação consiste em procurar o item solicitado pelo processador comparando-se o endereço requisitado pelo processador com o conteúdo armazenado – **figura abaixo, item (a).**

Para localizar um item solicitado pelo processador, o sistema de gerenciamento da memória cache acompanha o seguinte fluxo:

- ao receber a demanda realizada pelo processador, todos os circuitos comparadores realizam a comparação do valor recebido do processador com todos os conteúdos localizados no campo “tag”;
- o comparador que retornar “true” como resultado da comparação envia um sinal a um circuito de seleção para que o campo “valor” seja acessado;
- será, também, acessado o campo “válido” da linha selecionada para que, caso o conteúdo seja válido, o conteúdo seja despachado para o processador, denotando, nesse caso, o evento “hit” (hit = conteúdo encontrado na cache). Caso o item não seja encontrado, ocorrerá o evento “miss”, fazendo com que seja ativado o nível de memória imediatamente inferior.

Convém salientar que esse procedimento é executado no caso de leituras na cache. A posição do item no processo de gravação em memória associativa segue apenas dois critérios:

- caso exista alguma posição vaga, escreva o item nesta posição;
- caso contrário, executa-se a política de troca de bloco, que será descrita adiante.

Por sua vez, o mapeamento direto vem em direção contrária aos custos e da complexidade do hardware. **No mapeamento direto, cada bloco da memória principal é mapeado  apenas uma linha de cache. No mapeamento direto, o acesso repetido a diferentes blocos de memória mapeados na mesma linha de cache resultará em uma alta taxa de acerto.** – figura a seguir, item (b). A sua estratégia de busca segue os seguintes passos:

- ao receber o endereço do processador, acessa-se a linha que corresponda à operação de resto da divisão do endereço pela quantidade de linhas da cache. Em termos práticos, a operação de divisão é realizada, simplesmente, coletando-se os n bits menos significativos do endereço. Por exemplo, supondo que o processador gerou o endereço 35 e que a cache possua oito linhas. Nesse caso, obtém-se a linha da cache pelos log2^8 = 3 bits menos significativos. O valor 35(10) poderá ser expresso como  . Nesse caso, a linha a ser acessada é a 3 (011(2) = 3(10)). Como todo bloco a ser alocado nesta linha contém os mesmos n bits menos significativos, então, o campo “tag” precisará armazenar apenas os (k–n) bits mais significativos, sendo k o tamanho da palavra manipulada pelo processador;
- na mesma linha, acessa-se o campo “válido”. Caso o item seja válido, então ocorre o evento “hit”, caso contrário, o evento “miss” (de forma análoga ao que foi descrito anteriormente).

- **O cache miss, ou falha de cache, acontece quando o sistema de cache não encontra os dados solicitados armazenados em sua memória. Contrariamente, o cache hit, ou êxito de cache, acontece quando o cache localiza em sua memória os dados requeridos, respondendo à solicitação com sucesso.**

No caso do mapeamento direto, quando é preciso escrever o item na cache, ocorre a substituição do conteúdo original pelo novo, demandado pelo processador.

O mapeamento direto tem uma grande desvantagem quando, por exemplo, dois itens que possuam o mesmo padrão de localização, estejam sendo demandados de forma alternada – como por exemplo, dois itens acessados durante um laço de repetição. Neste caso, sempre ocorrerá o evento “miss” pois um item sempre substituirá o outro.

Para atenuar esse problema, existe um terceiro mapeamento que, na verdade, é a fusão dos dois primeiros: trata-se do conjunto associativo. No conjunto associativo, item (c) da figura abaixo, ocorre uma replicação das colunas do mapeamento direto. Nessa abordagem, ao receber uma demanda do processador, a sistema de cache acessa a linha correspondente como no mapeamento direto. Com a linha selecionada, aplica-se, para a leitura ou para a escrita do bloco, os passos como descritos no mapeamento associativo. Esse tipo de mapeamento é o mais usado nos processadores atuais. Por exemplo, o Intel Core i7 Haswell utiliza a configuração “8-way set associative” (replicação de colunas com fator 8) em suas caches L1 e L2 (TELES, 2004).

</span>
<div align-"center">
<img src="https://user-images.githubusercontent.com/113153237/221438154-aa372908-4e07-495b-b586-09880de3f272.png" width= "500px" />
</div>
*Formas de mapeamento da memória cache, sendo que em (a) temos o mapeamento associativo, em (b), o mapeamento direto e, por fim, em (c), o conjunto associativo.*

Na figura acima, você pode notar o campo **“tag” que corresponde à referência do endereço do bloco armazenado.** O campo **“válido” tem por objetivo informar se o conteúdo da linha não pertence a algum processo já finalizado ou algum valor aleatório produzido no momento da iniciação do sistema.**

### Política de escrita: 
Ao se falar sobre política de escrita, podemos referenciar a dois aspectos: quando um item novo precisa ser gravado ou quando o item é alterado na memória cache.

Quando um item novo é demandado pelo processador e acontece um evento do tipo “miss”, então significa que o bloco precisa ser lido dos níveis inferiores de memória e gravado na cache. Sendo assim, os mapeamentos associativos e o conjunto associativo executam o seguinte algoritmo:

- caso exista posição disponível, salve o item nesta posição;
- caso contrário, algum bloco previamente carregado deverá deixar a cache. Mas qual item escolher? Adota-se um critério de escolha retirando-se, por exemplo, o bloco que teve o acesso mais remotamente (LRU – Least Recently Used), o bloco usado com menos frequência (LFU – Least Frequently Used) ou o bloco mais antigo (FIFO – First In/First Out).

**LRU:** O LRU (Least Recently Used, menos utilizado recentemente) escolhe preferencialmente páginas antigas e menos usadas para remoção.
**LFU:**  É um tipo de algoritmo de cache usado para gerenciar a memória em um computador. As características padrão deste método envolvem o sistema manter o controle do número de vezes que um bloco é referenciado na memória.
**FIFO:** Em Ciência da Computação, algoritmo de fila simples, FIFO (do inglês: first in, first out, "primeiro a entrar, primeiro a sair", "PEPS") ou FCFS (do inglês: first come, first served, "primeiro a chegar, primeiro a ser servido") é um algoritmo de escalonamento para estruturas de dados do tipo fila. onde o primeiro elemento a ser inserido, será o primeiro a ser retirado, ou seja, adiciona-se itens no fim e remove-se do início. 

O outro aspecto relacionado à política de escrita refere-se quando há a atualização no valor do conteúdo do bloco presente na cache. Nesse caso, o sistema de memória pode adotar dois critérios:

- **write back:** nesse tipo de política, qualquer alteração na cache é repassada aos níveis inferiores de memória, deixando todos os **níveis sincronizados com o mesmo valor de conteúdo;**
- **write through:** na estratégia de write through, ocorre a **atualização do nível inferior de memória apenas quando o item deixa a cache para ceder espaço a um novo item demandado pelo processador.**

- Exemplo:
Abstraia um ambiente que apresenta apenas um processador que tenha um núcleo. Neste caso, não há nenhuma possibilidade de que o valor de um bloco seja alterado por outros nós de processamento. Sendo assim, neste ambiente não é necessário o write through. Agora abstraia um ambiente que um certo item possa ser buscado por vários núcleos. O write through ajuda a manter a coerência dos valores armazenados na hierarquia de memória. 






