## 1. Memória interna 
O sistema de memória é essencial para um sistema computacional, pelo fato de ser o responsável por prover o processador com as informações por ele demandadas (instruções e dados). Ele pode ser dividido em níveis hierárquicos, desde os registradores (nível mais alto), até a memória secundária (nível mais baixo). Quanto mais alto o nível da memória, mais rápido é seu processamento, mais cara e menor a sua capacidade de armazenamento (PATTERSON; HENNESSY, 1998).
A memória interna do computador pode ser classificada em relação ao seu tipo, volatilidade e tecnologia de fabricação.

Quanto ao tipo de memória, podemos encontrar as de acesso aleatório (RAM – Random Access Memory) e as ROM (Read Only Memory). Em relação à **memória do tipo RAM, o seu acesso é não sequencial, ou seja, podemos acessar um certo conteúdo, em qualquer localização, por intermédio da passagem de um endereço.** Por exemplo, é possível ingressar no conteúdo de um vetor cuja célula é endereçada pelo índice. Por sua vez, as **memórias do tipo ROM são aquelas representadas por sua capacidade apenas de atender às requisições de leitura.**
Veremos, nessa seção, a memória interna em sua concepção mais física. Essa memória interna será classificada, aqui, como memória dinâmica (DRAM), memória estática (SRAM) e memória apenas de leitura (ROM). 

### Memória DRAM e SRAM – RAM dinâmica e estática:
Basicamente, um módulo de memória poder ser representado na figura abaixo:  

</span>
<div align-"center">
<img src="https://user-images.githubusercontent.com/113153237/221997506-9fa2a3bb-8b60-46ef-8c47-3d2f6634f004.png" width= "500px" />
</div>  
*Módulo básico de memória. Outros pinos poderão ser encontrados nas implementações reais de memória.Fonte: Elaborada pelo autor, 2018.*

Na figura acima, temos uma possível pinagem de um módulo de memória. Nesta memória hipotética, podemos encontrar os seguintes pinos:

- **endereço:** palavra produzida pelo processador que contém a localização da memória a ser acessada;
- **operação (W/R):** define a operação a ser realizada. Neste caso, a linha sobre o caracter “W” indica que, caso esse pino receber o valor zero, será realizada uma operação de escrita (“W”: write). Caso contrário, ou seja, se esse pino tiver o valor um, foi demandada uma operação de leitura (“R”: read);
- **habilitação:** esse pino, também chamado como “enable”, habilita a memória a proceder a operação. Esse pino existe, pois a pinagem relativa ao endereço é ligada ao barramento compartilhado. Sendo assim, no barramento trafegarão sinais envolvendo os dispositivos e E/S. Assim, o pino enable (quando ativado) informa, módulo de memória, que o sinal de endereço é destinado à própria memória;
- **dados:** os pinos “dados” representam as informações que serão entregues ou coletadas da memória. Você pode notar que, ao contrário dos demais, esses pinos são bidirecionais;
- **clock:** por fim, esse pino entrega o pulso de clock para a sincronização das ações realizadas pela memória para proceder a ação de leitura ou gravação das informações.

As memórias do tipo RAM podem ser diferenciadas em relação à tecnologia de fabricação e suas utilidades principais. Com os dois tipos de memória RAM, a dinâmica (DRAM), e a estática (SRAM), faremos uma pergunta de provocação: porque a DRAM é usada na memória principal e a SRAM é usada na cache (níveis L1 e L2, principalmente)? A resposta está relacionada com a tecnologia de fabricação.
A figura abaixo, ilustra a concepção básica de uma DRAM e de uma SRAM.

</span>
<div align-"center">
<img src="https://user-images.githubusercontent.com/113153237/221998169-ef1c5662-e0a3-46d6-a3c6-8549ade393d3.png" width= "500px" />
</div>  
*Estrutura básica de uma célula de memória. Em (a), tem-se uma célula da DRAM e, em (b), uma configuração básica da SRAM.Fonte: STALLINGS, 2010, p. 130.*
Na figura acima, observa-se, em (a), integrando uma célula de memória DRAM, um componente eletrônico denominado “capacitor”. Um capacitor tem a capacidade de armazenar energia temporariamente. No caso da memória, essa carga armazenada é o próprio bit armazenado. Porém, como mencionado, a carga do capacitor é temporária (mesmo que o circuito continue recebendo tensão de alimentação). Esse é o motivo deste tipo de memória ser chamada de dinâmica.

Em função da descarga do capacitor, antes dele perder a referência do bit armazenado, o circuito de memória precisa ser “relembrado” (refresh). De tempos em tempos, ocorre o evento de refresh da memória (o tempo é em função da taxa de refresh). Durante todo o ciclo de refresh, a memória fica bloqueada tanto para operações de escrita, quanto para operações de leitura. Esse bloqueio impacta, de forma negativa, diretamente na performance das operações de memória.

Por outro lado, memórias SRAM, item (b) da figura acima, a base para a sua implementação são componentes baseados em semicondutores (transistores). Ao contrário da memória DRAM, seu armazenamento ocorre de forma estática, enquanto houver alimentação suprindo-a de energia.

Em função da implementação com transistores ocupando mais espaço, a memória SRAM se torna menos densa em relação à DRAM (menos quantidade de bits por área). Além da densidade, podemos falar que a SRAM é mais rápida e apresenta um custo mais alto (STALLINGS, 2010).

A SRAM é mais cara, mais rápida, e ocupa mais espaço que a DRAM, o que faz com que a SRAM seja usada para criar uma memória mais próxima do processador, a cache. Enquanto que a DRAM é usada para fazer os módulos de RAM, fornecendo uma muito maior quantidade de RAM ao sistema.
Atualmente, encontramos memórias DRAM do tipo SDRAM (DRAM Síncrona – Synchronous DRAM), equipando os computadores. Uma SDRAM é uma memória híbrida, sincronizada pelo clock do sistema computacional, envolvendo a DRAM e a SRAM (TANENBAUM, 2013). A grande vantagem da SDRAM, frente à DRAM é a possibilidade de eliminação de sinais de sincronização entre a memória e o processador – a sincronização é feita somente com os pulsos de clock. Este artifício permite que a memória opere no modo rajada (burst), no qual a memória pode transmitir dados com endereçamentos subsequentes, sem a intervenção do processador em enviar os próprios endereços demandados. Com isso, permite-se um melhor aproveitamento do pipeline, pois há a maior probabilidade de deixá-lo cheio.

SDRAM ou memória dinâmica de acesso aleatório sincronizado, é um tipo de memória capaz de se sincronizar com o processador do computador para poupar tempo na execução de comandos e transmissão de dados, conseguindo assim melhorar o desempenho do computador.

**A evolução da memória SDRAM culminou nas memórias SDRAM DDR (SDRAM Taxa Dupla de Dados – SDRAM Dual Data Rate). Neste tipo de implementação, a memória consegue entregar dois dados a cada ciclo de clock, um na subida da onda de clock, e outro na descida.**

### Tipos de ROM e correção de erro:
Um outro tipo de memória interna, que encontramos nos computadores, é a memória tipo ROM. Esse tipo de memória, não volátil, é utilizada em ocasiões nas quais requer apenas operações de leitura, como por exemplo: bibliotecas de funções, para que sejam usadas frequentemente (tal como BIOS – Basic Input/Output System), tabelas de funções ou informações fixas a serem demandadas pelo sistema computacional.
**BIOS:** (do inglês Basic Input/Output System) e também conhecido como System BIOS, ROM BIOS ou PC BIOS, é firmware, gravado em uma memória não volátil, usado para realizar a inicialização do hardware durante o processo de inicialização (por meio do botão de inicialização da máquina) e para fornecer serviços de tempo de execução para sistemas operacionais e programas.

A memória ROM pode ser classificada em relação ao momento no qual poderá ser realizada a gravação, da seguinte forma (STALLINGS, 2010):

- **ROM – no tipo ROM original:** as instruções eram gravadas no momento da fabricação do chip;
- **PROM (ROM programável – Programmable ROM):** a escrita, neste caso, poderá ser realizada uma única vez. Para tanto, será necessário um ambiente de programação que possua uma interface física (por exemplo, usando um cabo serial) para que seja realizada a programação do dispositivo;
- **EPROM (PROM apagável – Erasable PROM):**  semelhante à PROM, porém permite várias gravações. Para se gravar um novo conjunto de informações (dados ou código), é necessário realizar a etapa de apagamento, submetendo o dispositivo a um banho de luz ultravioleta. Neste tipo de componente, existe, no invólucro, uma região translúcida para permitir que a luz ultravioleta atinja a região interna do componente;
- **EEPROM (PROM apagável eletricamente – Electrically Erasable PROM):** igualmente à EPROM, permite o apagamento das informações para que seja feita uma nova gravação. Porém, em vez de se utilizar luz ultravioleta, o processo de apagamento se faz mediante sinais elétricos.

Quando se fala em armazenamento de informações e transmissão de dados, na maioria das vezes, temos que nos preocupar com a corretude da informação armazenada/transmitida. Corretude, neste caso, significa detectar ou, até mesmo, corrigir os dados em caso de erros.

Erros (ou falhas) podem ser permanentes ou transientes. Falhas permanentes ocorrem por falha física do componente – ocasionadas por defeitos de fabricação ou deterioração do material pelo tempo de uso. Falhas transientes também podem ser causadas pelo desgaste do material em função do tempo do uso ou, ainda, por influência de interferências externas.

Independentemente da causa ou tipo de falha, temos a necessidade de verificar se a informação que foi armazenada ou transmitida encontra-se coerente com os dados originais.

Um dos mecanismos mais simples consiste no cálculo do bit de paridade. Chama-se **paridade par** quando se adiciona, à palavra, o bit 1 para que a quantidade total de bits com valor 1 seja par (ou paridade ímpar para completar a quantidade ímpar de bits iguais a 1).

Por exemplo, caso a palavra a ser armazenada seja 01101101 . Como, na palavra, temos 5 bits iguais a 1, adiciona-se um nono bit com valor 1 para completar a quantidade par – neste caso, armazena-se 01101101*1* . Por outro lado, caso tivéssemos a palavra 10001101 (que já apresenta um número par de bits iguais a um), adicionaríamos o bit zero, ficando 10001101*0*. O bit de paridade par é conseguindo aplicando-se o operador “ou exclusivo” (XOR) em todos os bits da palavra.

A função **XOR** retornará VERDADEIRO se um número ímpar dos argumentos fornecidos for logicamente verdadeiro; caso contrário, retornará FALSO.
Sendo uma operação lógica entre dois operandos que resulta em um valor lógico verdadeiro se e somente se os dois operandos forem diferentes, ou seja, se um for verdadeiro e o outro for falso. É conhecido também pelas abreviações XOR ou EXOR e ainda por XOU ou EOU.
Porém, caso a interferência atingisse dois bits e não somente um, o que aconteceria? Vejamos alterando-se dois bits do primeiro exemplo, passando de 01*10*1101 para 01*01*1101. . O bit de paridade par continuaria sendo um (01*01*1101*1*). Neste caso, a utilização de bit de paridade não é muito seguro. Dependendo do ambiente e necessidade, usa-se algum outro método de detecção de erros, com é o caso do código de Hamming.

[Código de Hammming, conceito básico](https://definirtec.com/codigo-de-hamming/)

O código de Hamming permite não somente a detecção da ocorrência de erros, mas, também, que os dados sejam corrigidos. A ideia central baseia-se na formação de subconjuntos com intersecções. A partir dos bits de paridade destas intersecções, consegue-se verificar a ocorrência e corrigir os erros ocorridos sobre a palavra de informação (STALLINGS, 2010). 

## 2. Sistemas de entrada e saída
Além do processador, memória e barramento, fazem parte, também, do computador, os sistemas de entrada e de saída (E/S – I/O – Input/Output). Sistemas de E/S tem por objetivo interfacear com dispositivos externos, tais como vídeo, teclado e disco rígido.

Você pode estar se perguntando: como o computador consegue manipular dados provenientes de um dispositivo que opera blocos (registros), como os discos rígidos, e também de dispositivos que transmitam suas informações de forma serial, como os dispositivos ligados a uma porta USB (Universal Serial Bus)? Podemos responder que os dispositivos não estão ligados diretamente ao barramento e, sim, são interfaceados por um módulo de E/S, também chamado de controlador de E/S.

### Estrutura do módulo de E/S:
Os módulos de E/S devem ser implementados de forma a exportar funcionalidades de interfaceamento entre o barramento e os próprios dispositivos de E/S, sob sua responsabilidade. A figura abaixo ilustra o interfaceamento básico de um módulo de E/S.

</span>
<div align-"center">
<img src="https://user-images.githubusercontent.com/113153237/222009270-e0ade590-d643-4dfc-8bb5-e945ab5204b9.png" width= "500px" />
</div>  

- Estrutura básica de um módulo de E/S, identificando seus componentes externos e suas interfaces para a interligação com o barramento.Fonte: STALLINGS, 2010, p. 130.  


Na figura acima podemos ver a estrutura básica de um módulo de E/S. Nela, notamos os pinos de interfaceamento com o barramento (linhas de dados, endereço e de controle) e o interfaceamento com os dispositivos propriamente ditos. Também identificamos as linhas de endereço que transmitem a identificação do módulo de E/S gerada pelo processador. A partir de seu conteúdo, o módulo verifica se a requisição é ou não direcionada a ele. Veremos, adiante, que um módulo pode ser identificado como um endereço de memória, ou como um identificador próprio de E/S. Por sua vez, os registradores de estado/controle armazenam as condições atuais do módulo, por exemplo, se ele se encontra ocupado (), pronto para receber novas demandas () ou, ainda, informar estados de erro. Por fim, as linhas de controle são responsáveis pelo envio das requisições realizadas pelo processador ou usados quando solicitadas operações envolvendo DMA (Direct Memory Access, em português, acesso direto à memória).
A unidade de lógica de E/S desempenha a função de gerenciamento dos dispositivos de E/S além de ser o módulo responsável pelo recebimento das requisições (pelas linhas de controle e de endereço) e instanciações ou recebimento das informações por meio dos registradores de dados e de estado/controle.

Como funcionalidades dos módulos de E/S podemos citar (STALLINGS, 2010):

- **controle e temporização:** o controle e temporização são funcionalidades fundamentais para permitir a sincronização de acesso e uso dos dispositivos sob a coordenação do módulo de E/S;
- **interação com o processador e com os dispositivos de E/S:** a interação com o processador permite o recebimento das demandas (representadas por sinais e de palavras de controle) e, também, permite o envio ou o recebimento das informações a serem manipuladas. Essa demanda é completada pela ativação dos dispositivos de E/S para a coleta ou envio dos dados perante o mundo externo;
- **detecção de erros:** já que os dispositivos de E/S envolvem armazenamento e transmissão, como mencionado anteriormente, necessitam, na maior parte dos casos, de mecanismos para detecção de erros;
- **bufferização das informações sob manipulação:** a técnica de armazenar temporariamente (bufferizar) uma informação, permite compatibilizar as taxas de transferência entre os dispositivos e os barramentos envolvidos, uma vez que os dispositivos de E/S tendem a ser mais lentos em relação ao barramento e ao processador.

Mais especificamente em relação à funcionalidade de controle e temporização, podemos nos atentar ao fato de que o mecanismo para acesso ao dispositivo de E/S é baseado no handshake. Tal mecanismo é dividido em duas fases: inicialmente, o processador consulta ao módulo de E/S para verificar a disponibilidade de um dispositivo. Caso haja uma resposta positiva, então, somente neste momento, é que o processador envia um comando de E/S para efetivar a transferência das informações.

Convém salientar que a comunicação entre o processador e o módulo de E/S requer o uso do barramento. Sendo assim, deve-se, ainda, seguir a sincronização imposta pelo árbitro do barramento, para consumar a comunicação entre o processador e o módulo de E/S.

Há uma diferença entre um canal de E/S (ou processador de E/S) e um controlador de E/S (ou controlador de dispositivo). Os canais de E/S, usados normalmente em computadores de maior porte (exemplo, os mainframes), são módulos com um grau de independência elevado e a sua complexidade permite que eles assumam grande parte do processamento inerente à coleta ou transmissão de informações junto aos dispositivos de E/S. Os controladores de E/S, encontrados geralmente nos computadores pessoais, são módulos primitivos e requerem maior controle por parte do processador (STALLINGS, 2010).

### Instrução de E/S e processamento de E/S:
Para que possamos manipular os módulos de E/S devemos, primeiro, saber o modo de manipulação do módulo em específico. Três formas são admitidas: **E/S programada, E/S controlada por interrupções e DMA (Acesso Direto à Memória – Direct Memory Access).** Nos dois primeiros modos, **o processador intermedeia a transferência de informações entre o módulo de E/S e a memória.** Já, no último modo **(DMA), a transferência para a memória é realizada diretamente pelo módulo de E/S.**

</span>
<div align-"center">
<img src="https://user-images.githubusercontent.com/113153237/222011218-9b2a50f2-a0c7-4b4c-beae-5802984bc394.png" width= "500px" />
</div>
