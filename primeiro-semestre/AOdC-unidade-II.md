## 1. Introdução à arquitetura de computadores 
Para entender como o computador funciona, precisamos, antes, conhecer a sua organização e as funcionalidades de seus módulos. Com isso, será possível não somente entendermos, mas, também, propormos soluções de desenvolvimento de sistemas mais otimizados – aproveitando-se as particularidades de um sistema computacional.

### Visão de alto nível do computador:
Em relação aos computadores ditos como pessoais, seguimos o modelo do matemático John von Neumann (TANENBAUM, 2013). Nesse modelo, a filosofia básica de trabalho consiste no programa armazenado em uma estrutura de memória para que possa ser executado pelo processador. Além da memória, como elementos de sua organização, podemos encontrar a unidade de controle e a unidade lógica e aritmética.

Diante da herança frente ao modelo de von Neumann (TANENBAUM, 2013), pode-se dizer que os elementos básicos de um sistema computacional são (STALLINGS, 2010):

- **sistema de memória:** dividido, ainda, em **memória secundária** (por exemplo, disco rígido (HD), disquete e CD-ROM) a mais lenta chamadas também de “memórias de armazenamento em massa”, para armazenamento permanente de dados. Não podem ser endereçadas diretamente, a informação precisa ser carregada em memória principal antes de ser tratada pelo processador. Não são estritamente necessárias para a operação do computador. **Memória principal** também conhecida como memória central, é uma memória de rápido acesso e que armazena os dados /informações (programas, objetos, dados de entrada e saída I/O, dados do sistema operacional). **Memória cache** funciona como uma biblioteca de acesso rápido que existe dentro de computadores e dispositivos móveis. Ela tem o objetivo de guardar dados, informações e processos temporários acessados com frequência e assim agilizar o processo de uso no momento em que são requisitados pelo usuário. **Registradores** é a memória dentro da própria CPU que armazena "n" bits. Os registradores estão no topo da hierarquia de memória, sendo assim, é um tipo de memória mais rápida e financeiramente mais custosa;
- **unidade de processamento:** dentro do processador, encontramos a unidade de controle, a unidade lógica e aritmética, a rede de interconexão interna e os registradores (para o armazenamento de instruções, dados e informações de controle);
- **unidades de E/S (Entrada/Saída):** objetiva o interfaceamento com os dispositivos de entrada e de saída;
- **rede de interconexão:** tem a função de interconectar os módulos pertencentes ao sistema computacional.

### Memórias do computador  


</span>
<div align-"center">
<img src="https://user-images.githubusercontent.com/113153237/220212078-f209a234-645e-4fd2-b045-8eeecef05f89.png" width= "500px" />
</div>

### Hierarquia das memórias  


</span>
<div align-"center">
<img src="https://user-images.githubusercontent.com/113153237/220212854-5b851030-b9eb-4822-ba92-fd76e1fc24ef.png" width= "500px" />
</div>

### Sistemas de memórias e suas características  


</span>
<div align-"center">
<img src="https://user-images.githubusercontent.com/113153237/221450152-8f93a973-beb1-41a3-9175-ac0889285b00.png" width= "500px" />
</div>  
  
    
    
Além dos módulos em si, precisamos ter em mente que, para que eles atuem, é necessária toda uma sincronização de trabalho. **Essa sincronização é atingida pela geração de sinais de controle, os quais estão presentes dentro do processador para que este possa executar as instruções, e, também, estão presentes nos demais módulos que integram o computador.**

### Interconexão do computador, estrutura e função do processador:
Os caminhos que conectam os componentes de um sistema computacional é chamado de estrutura de interconexão. A estrutura de interconexão deve suportar os seguintes tipos de transferência: – Da memória para o processador. – Do processador para a memória.
A figura a seguir ilustra os módulos e a sua interconexão.
 
</span>
<div align-"center">
<img src="https://user-images.githubusercontent.com/113153237/220213916-647a26b7-f69d-41ed-ae82-916acdfa3eb4.png" width= "500px" />
</div>

Na figura acima, você pode notar a presença de canais de comunicação inter-relacionando os módulos do sistema computacional. Tais canais transportam informações envolvendo os dispositivos de E/S (interfaceados via *buffers*: **buffer de dados é uma região de memória física utilizada para armazenar temporariamente os dados enquanto eles estão sendo movidos de um lugar para outro**) além de transportarem dados e instruções entre a memória e o processador. Por sua vez, internamente à CPU são apresentados, além da unidade de execução, registradores de controle.
A estrutura apresentada na figura anterior permite que o processador desempenhe a sua função básica: executar instruções. Para que uma instrução seja executada, é necessário que esta seja carregada da memória para o processador. Sendo assim, para executar um programa completo, o processador deverá, em suma, realizar a busca da instrução e executá-la – linha a linha de código.

A execução representa o envio de informação e a ativação de módulos específicos, correspondentes a cada classe de instrução. Geralmente, os processadores manipulam quatro classes de instruções, enumeradas a seguir (STALLINGS, 2010):

- **processador-memória:** representa as instruções de transferência de dados entre o processador e a memória;
- **processador-E/S:** ao invés da transferência de informações envolvendo a memória, as instruções do processador-E/S intercambiam informações entre o processador e os módulos de E/S;
- **processamento:** compreende as instruções que realizam a execução propriamente dita. As informações a serem manipuladas deverão estar, necessariamente, carregadas nos registradores do processador;
- **controle:** as instruções de controle estão relacionadas aos desvios condicionais e não condicionais, alterando, dessa forma, a sequência do fluxo de processamento das instruções.

As instruções precisam, para que sejam decodificadas e executadas, estar carregadas nos registradores do processador. 

## 2. Organização dos registradores 
Todas as instruções e informações a serem processadas deverão, necessariamente, ser carregadas previamente no processador. Para tanto, o processador possui um conjunto de registradores de uso geral (GPR –  General Purpose Registers) e um conjunto de registradores para que sejam usados no controle do processamento.

### Registradores visíveis ao usuário: uso geral e dados
Registradores do tipo GPR têm a função de armazenar as informações sob processamento. Por exemplo, caso seja necessário executar uma operação de soma do tipo C = A + B, os valores de A e B deverão ser carregados previamente da memória e armazenados em registradores. Após o processo de execução ser completado, o resultado deverá ser armazenado também em registradores.
Podemos afirmar que quando as informações estão presentes em registradores, a chance de serem reaproveitadas em outras instruções próximas é alta. Sendo assim, os compiladores possuem estratégias de otimização para que se possa aproveitar ao máximo os valores previamente carregados nos registradores.
Um segundo aspecto refere-se à organização do hardware. Por exemplo, em computadores do tipo RISC (Reduced Instruction Set Computer), as operações que manipulam informações são do tipo registrador-registrador, ou seja, as fontes são oriundas de registradores e o resultado é salvo também em registrador (STALLINGS, 2010). Dessa forma, os circuitos internos de interfaceamento tornam-se mais simples e, consequentemente, não é necessário um módulo de seleção da fonte (chaveando-se entre a memória e o banco de registradores).
Convém mencionarmos que o processador Intel Core i7, apresenta, em cada núcleo, 16 registradores GPR (General Purpose Register) em seu banco de registradores.

### Registradores de estado e de controle:
Registradores de controle e estado: Usados pela unidade de controle para controlar a operação do processador e por programas privilegiados do Sistema Operacional para controlar a execução de programas.
Além dos registradores do tipo GPR, o processador mantém um conjunto de registradores destinados ao armazenamento de códigos de estado e de valores de configuração.
Alguns exemplos de registradores desse tipo, tais como:

- **PC (program counter):** o registrador PC, também chamado como IP (instruction pointer), **armazena o valor de endereço que contém a próxima linha de código (instrução) a ser executada.** A cada busca de instrução, o valor de PC é incrementado para que, no próximo ciclo, seja executada a instrução subsequente. Em instruções de desvio, o PC pode receber o valor do endereço que contempla a instrução após o salto (desvio);
- **IR (instruction register):** para que a instrução possa ser executada, ela precisa ser carregada para dentro do processador. O local para o armazenamento da palavra que contém a instrução é o registrador IR. Com base no valor armazenado, o processador realiza todas as etapas envolvidas na sua execução;
- **MAR (memory address register):** o registrador de endereço de memória contém o valor do endereço para o próximo acesso à memória. **Com o uso desse registrador, o processador informa, ao sistema de memória, o endereço sobre o qual será realizado o acesso (para a leitura ou para a escrita)**;
- **MBR (memory buffer register):** após o MAR configurado, ao efetivar o acesso à memória, o item manipulado (gravado ou lido da memória) é armazenado no MBR. Sendo assim, o MAR e o MBR fazem parte do interfaceamento entre o processador e a memória;
- **I/O AR (input-output address register):** de forma análoga ao interfaceamento entre processador e memória, existe o registrador I/O AR, que contém o endereço do dispositivo de E/S a ser acessado;
- **I/O BR (input-output buffer register):** o item manipulado entre o processador e o dispositivo de I/O é armazenado no registrador I/O BR.

Não poderíamos deixar de citar o registrador de flags. **Flags** são registradores onde cada bit significa um estado do processador. Esse flag é setado sempre quando houver "vai um" depois de uma adição ou quando há BORROW depois de uma subtração. Pode ser usado também em uma operação de deslocamento de bits, quando o bit mais ao extremo for deslocado para fora do dado.
O registrador de **flags é instanciado ao término, por exemplo, das operações aritméticas a fim de armazenar o estado final da operação, bem como informar se a operação resultou em algum valor negativo, nulo ou, ainda, se houve estouro de representação numérica (overflow).** Mas por que armazenar esse estado final da operação? Na maioria dos processadores, para se fazer uma operação de desvio, é necessário testar exatamente esse registrador de flags.

A figura a seguir ilustra a tradução de um desvio condicional a partir de uma linguagem de alto nível para um assembly (linguagem de máquina) hipotético.

</span>
<div align-"center">
<img src="https://user-images.githubusercontent.com/113153237/220216558-d29c3cbd-3fb8-4e02-a1c4-745d948dc226.png" width= "500px" />
</div>

Na parte (b) da figura acima, tem-se o código traduzido da parte (a) para o assembly de uma máquina hipotética. Suponha que os valores das variáveis (a) e (b) já estejam carregadas nos registradores reg1 e reg2, respectivamente. A linha um realiza a subtração desses dois registradores e armazenando o resultado no registrador reg3. Além do cálculo em si, a instrução de subtração também instancia os campos do registrador de flags. No nosso exemplo, daremos atenção ao campo **S** (sinal). Esse campo será instanciado em um caso a instrução de subtração retorne um valor negativo e, caso contrário, o campo será instanciado em zero.

O campo **S** será avaliado na instrução da linha dois: **js** (jump signal). Caso o campo **S** esteja sinalizado em um (resultado negativo), o fluxo de execução do código será desviado para o endereço apontado pelo rótulo **parte_else** (caso negativo, então, significa que a < b). Caso contrário (S = 0), assim, o trecho identificado como **<sequência_if...>** será executado.

Caso o fluxo tenha passado pela **<sequência_if...>**, a linha três, contendo um desvio incondicional (jmp = jump) será responsável por saltar o trecho **<sequência_else...>** para que o fluxo seja direcionado à primeira instrução fora do comando **if... else (<sequência_após_desvio...>)**.

Por fim, as linhas quatro e cinco representam os rótulos para nortear os desvios junto às instruções de desvios condicionais e não condicionais.
Cada família de processadores contém, em sua organização, o seu próprio mapeamento de registradores. A quantidade de registradores influenciará o formato com que as instruções são armazenadas na memória.

## 3.  Ciclo de Instrução 
Um ciclo de instrução é o período de tempo no qual um computador lê e processa uma instrução em linguagem de máquina da sua memória ou a sequência de ações que a CPU realiza para executar cada instrução em código de máquina num programa.

</span>
<div align-"center">
<img src="https://user-images.githubusercontent.com/113153237/220221764-297ca149-158a-4652-a70c-e515bbaedf6a.png" width= "500px" />
</div>

Como as intruções são armazenadas na memória. Vamos supor a operação de subtração codificada em assembly contida na figura anterior: “sub reg3, reg1,reg2”. Para começarmos a falar sobre a representação, lembre-se de que o computador armazena apenas números. Então, os dados são números (inclusive os caracteres são representados pelo valor contido na tabela ASCII) e as instruções não poderiam deixar de ser um valor numérico.

Vamos supor a operação de subtração codificada em assembly contida na figura anterior: “sub reg3, reg1,reg2”. Para começarmos a falar sobre a representação, lembre-se de que o computador armazena apenas números. Então, os dados são números (inclusive os caracteres são representados pelo valor contido na tabela ASCII) e as instruções não poderiam deixar de ser um valor numérico.
Cada instrução possui um código denominado (*opcode código de operação é a referência à instrução que um determinado processador possui para conseguir realizar determinadas tarefas. Suas especificações e formatos são definidos no conjunto de instruções da arquitetura do processador em questão).* Assim, é a partir do opcode que o processador reconhece quais os módulos deverão ser ativados e qual o caminho que aos dados deverão seguir dentro dele. A figura a seguir ilustra um possível formato para a instrução de subtração.

</span>
<div align-"center">
<img src="https://user-images.githubusercontent.com/113153237/220222102-d7155234-d5a8-46f8-83c8-1399f1b4fb7e.png" width= "500px" />
</div>
*Exemplo de formato de instrução de subtração de um processador hipotético de 16 bits.*

Na figura acima, supõe-se que a máquina hipotética em questão tem uma largura de palavra de 16 bits, sendo que o seu banco de registradores engloba oito registradores e possui 125 instruções em sua arquitetura de conjunto de instruções (ISA – Instruction Set Architecture). Fazendo as contas rapidamente, chegamos à conclusão de que serão necessários três bits (log28 = 3) para endereçar cada registrador e mais sete bits para mapear as instruções (log2125 ≈ 7).

Então, para mapear “sub reg3, reg1,reg2”, atribuindo aleatoriamente (para fins de ilustração) o valor 0110111 para o opcode da instrução de subtração, tem-se a palavra:  0110111 011 001 010 (lembrando que 011(2) = 3(10); 001(2) = 1(10); 010(2) = 2(10)).

Cada classe de instrução tem o seu formato de representação dentro da palavra de 16 bits. Sendo assim, os campos podem variar de tamanho e de representação, exceto o campo do opcode que, nesse caso, será mantido fixo (15 a nove bits).

O início do processo de execução da instrução consiste em sua busca a partir da memória. Como mencionado antes, o processador coleta toda palavra da memória (conjunto formado pelo opcode e seus operandos) e armazena no registrador IR, para que as informações sejam encaminhadas aos submódulos ao longo de sua organização. Nesse caso, existe um fluxo de informações e de sinais pelos caminhos do processador – caminhos estes chamados de datapath. 

**Datapath:** Um caminho de dados é uma coleção de unidades funcionais, como unidades lógicas aritméticas ou multiplicadores que realizam operações de processamento de dados, registradores e barramentos. Junto com a unidade de controle compõe a unidade central de processamento.


Os módulos e suas conexões, no datapath, são diagramados de acordo com as fases de execução das instruções. De acordo com (TANENBAUM, 2013), a execução de uma instrução poderá ser dividida nas seguintes etapas:

- busca, pelo processador, pela próxima instrução da memória e carrega no registrador RI;
- incremento do registrador PC, de modo a ser preparada a busca pela instrução subsequente (a modificação do valor de PC poderá ocorrer posteriormente caso a instrução seja de desvio);
- codificação do tipo da instrução carregada;
- carregamento dos operandos nos registradores (caso necessário);
- execução da instrução e registro do resultado;
- retorno ao início para recomeçar o ciclo em relação à próxima instrução.
 

Essa sequência de execução de uma instrução poderá ser manipulada de forma puramente sequencial ou, ainda, ser alvo de otimização de fluxo de processamento através da aplicação da técnica de pipeline. 

**Pipeline:** A segmentação de instruções é uma técnica de hardware que permite que a CPU realize a busca de uma ou mais instruções além da próxima a ser executada.

### Buscar, ler e interromper:
O que acontece no fluxo quando há a incidência de alguma interrupção? As interrupções causam um grande impacto na execução dos processos, pois elas devem ser atendidas quase que prontamente.
O impacto é causado pelo fato de que quando o sistema operacional escalona os processos (interrupções são também tratadas como processos), deve haver a troca de contexto. **Trocar um contexto significa que é necessário salvar todas as informações relevantes do processo (tais como o valor do registrador PC, as flags e algumas outras informações) para que, depois, quando o processo voltar à ativa, possa ser restaurado exatamente do mesmo ponto e com as mesmas configurações vigentes no momento de sua interrupção** (PATTERSON, 1998).

A figura abaixo ilustra o tratamento das etapas de execução de uma instrução envolvendo a manipulação de interrupções. Em **(a) tem-se o esquema básico de representação** e em **(b), um detalhamento das etapas propriamente ditas.**

</span>
<div align-"center">
<img src="https://user-images.githubusercontent.com/113153237/220782901-55340437-7881-43bc-a7cf-ec861f82a412.png" width= "500px" />
</div>
*Sequência de etapas para execução das instruções com a manipulação de interrupções: em (a), a representação básica, e em (b), o detalhamento das ações.*

Nota-se que, após a execução de uma instrução ser completada, verifica-se se há alguma interrupção enfileirada pendente a ser executada. Nesse caso, ela entraria como um processo normal, ou seja, as instruções vinculadas ao tratamento da interrupção entrariam no fluxo do pipeline(executa tarefas simultaneamente).
Quando um fluxo de execução é adicionado ao pipeline, o que acontece quando alguma outra interrupção ocorre? Quando esse cenário ocorre, temos duas maneiras de realizar o tratamento: na primeira forma, assim que o tratamento da interrupção for iniciado, poderemos desabilitar novas interrupções ou permitir que as próprias interrupções sejam interrompidas para o atendimento de outras. A figura abaixo mostra a diferença entre esses dois enfoques.

</span>
<div align-"center">
<img src="https://user-images.githubusercontent.com/113153237/220785209-db12778f-987c-41d5-bfde-9921efd0d4af.png" width= "500px" />
</div>
*Tratamento de interrupções com a desabilitação de novas interrupções (a) e tratamento de novas interrupções de forma aninhada (b).*

Em relação à figura acima, temos em (a) o tratamento de interrupções sequencialmente. Nesse tipo de enfoque, ocorre a desabilitação de interrupções para que as novas que ocorrerem sejam apenas enfileiradas, de modo que o tratamento ocorra somente após o término da atual. Por sua vez, em (b), no tratamento aninhado, uma interrupção poderá ser interrompida para que seja tratada uma com maior prioridade.

Em ambos os casos (sequencial ou aninhado), ocorrerá a interrupção da execução dos processos do usuário para que as interrupções sejam tratadas pelo pipeline.

### Fluxo de dados e estratégia de pipeline:
Para se executar uma instrução, tem-se que coletar as informações a serem manipuladas. Nem sempre uma informação é buscada de forma imediata, ou seja, às vezes é necessária mais de uma etapa para fazê-lo. 
Interfaceamento entre o processador e o sistema de memória é realizado pelos registradores MBR e MAR. Então, como acessar a memória para que seja buscada a instrução na posição apontada pelo registrador PC? A figura abaixo ilustra, em (a), esse processo.

</span>
<div align-"center">
<img src="https://user-images.githubusercontent.com/113153237/220791510-565ea165-31cb-4fd4-8e66-ff5c2955ace3.png" width= "500px" />
</div>

*Fluxo de dados na busca da instrução (a), na busca de operandos usando endereçamento indireto (b) e no ciclo de interrupção (c).*

Na figura acima, temos, em (a), a representação do fluxo de dados durante o processo de busca da instrução. Nota-se que, para que a instrução seja buscada junto à memória, o registrador MAR (memory address register) deverá receber o valor contido em PC (program counter). O valor de retorno do sistema de memória é salvo no registrador MBR (memory buffer register), que, no caso, contém a palavra referente à instrução. A finalização do fluxo ocorre no momento em que o valor de MBR é passado ao registrador IR (instruction register) – mesmo instante em que ocorre o incremento do PC para que, no próximo ciclo, seja buscada, a princípio, a instrução subsequente.
Ainda em relação à figura acima, o item (b) ilustra o fluxo de dados no momento da etapa de busca de operandos por ocasião do endereçamento indireto de memória. O valor buscado no sistema de memória (alocado em MBR) representa, na verdade, o endereço no qual se deseja o valor a ser manipulado. Diante disso, um novo ciclo é necessário para providenciar essa busca, sendo, então, para isso, necessária a transferência do valor inserido no MBR para o MAR.
Por fim, temos, em (c), o fluxo de dados inerente ao tratamento de uma interrupção. A transferência do valor de PC para o MBR relaciona-se com o salvamento de contexto, para que o ponto de processamento seja restaurado após a finalização da execução do código da interrupção. Sendo assim, o valor de PC será salvo em um segmento de pilha na memória, cujo ponteiro é passado pela unidade de controle ao MAR.

Qual a relação do fluxo de dados com o pipeline? A resposta reside no fato de que alterações no tempo de execução (havendo ou não a necessidade de ciclos extras de clock para a finalização de uma etapa) e de que alterações no chaveamento de comunicação entre os módulos alterará o modo de processamento e, consequentemente, impactará sobre o pipeline. 


No modelo de sistema computacional superescalar, as instruções poderão ser despachadas fora de ordem caso haja disponibilidade de hardware e de dados para a sua execução. Porém, nesse caso, além do fluxo de dados, o pipeline também precisará se preocupar com outros detalhes que afetarão o seu desempenho computacional. Tais detalhes são chamados como conflitos ou riscos (hazards). Os hazards podem ser classificados como estruturais, de dados ou de controle.

- **Clock:** Clock ou frequência é um termo utilizado para determinar a velocidade de um processador de um computador em Hertz (Hz). Basicamente, ele define a quantidade de ciclos que o componente consegue realizar a cada segundo.

Existem situações em pipelining em que a próxima instrução não pode ser executada no ciclo de clock seguinte.
Esses eventos são chamados de hazards (Riscos), e existem três tipos diferentes:

- **Hazards Estruturais:** Significa quando o hardware não pode admitir a combinação de instruções que queremos executar.
- **Hazards de Dados:** Ocorrem quando o pipeline precisa ser interrompido porque uma etapa precisa esperar até que outra seja concluída.
- **Hazards de Controle:** Decorre da necessidade de tomar uma decisão com base nos resultados de uma instrução enquanto outras estão sendo executadas.

Nos **hazards estruturais**, o pipeline é penalizado pela inexistência de recursos de hardware para que possa executar uma instrução. Como exemplo de hazard estrutural podemos citar o caso do pipeline que tenta buscar um certo operando, porém não é possível pois o sistema de memória está atendendo a gravação de resultado de uma instrução anterior.

Já os **hazards de dados** podem ser classificados em três categorias (PATTERSON, 2014):

- **leitura após escrita:**  no exemplo, **(i) R3 = R1 + R2; (ii) R2 = R4 + R5**, temos um hazard do tipo leitura após escrita, pois, caso a linha (ii) seja finalizada antes da carga de R2 na linha (i), teremos a manipulação de um valor errôneo na produção de R3;
- **escrita após leitura:** ocorre quando a produção da informação pela instrução i ocorre após a ocorrência da leitura pela instrução j (sendo i < j);
- **escrita após escrita:** quando a instrução k modifica o valor do resultado da instrução i, porém existe uma instrução intermediária j que deveria ler o valor produzido por i (com i ocorrendo antes do j, que ocorre antes de k).

Para melhor gerenciar os hazards estruturais e de dados, pode-se adotar uma solução baseada em Scoreboard ou Algoritmo de Tomasulo e suas variações, e renomeamento de registradores (PATTERSON, 2014).

- Artigo: [Algoritmo de tomasulo](https://www.ic.unicamp.br/~rodolfo/Cursos/mo401/2s2005/Trabalho/049239-tomasulo.pdf)

Por fim, os **hazards de controle** relacionam-se às instruções de desvio. Para evitar a paralização do pipeline enquanto a expressão lógica do desvio estiver em processamento, o processador tentará prever qual alternativa tomar. Para tanto, pode-se utilizar uma tabela ordenada pelos LSBs (less signitificant bit – bits menos significativos) contendo a resultado da expressão lógica da iteração anterior. Com esse valor, o processador antecipará a execução da próxima linha de instrução, efetivando o resultado apenas após a confirmação do caminho certo que deveria ser tomado (caso tenha tomado o caminho errado, descarta-se o resultado).

Assim como os hazards estruturais e de dados, existem, também, mecanismos para atenuar o impacto dos hazards de controle, dentre os quais podemos mencionar a   previsão dinâmica de desvios.


## 4. Aritmética do computador 

Tudo o que é armazenado e manipulado no computador consiste em informações numéricas. Mais especificamente, esses números seguem um modelo de representação binária. Em programação, existem os tipos de dados (por exemplo, em C/C++: char, int, float etc.) que possuem uma faixa de valores derivada de seu tamanho (em bits). Por exemplo, caso estejamos manipulando uma variável do tipo char, significa que poderemos representar valores de -128 a 127, ou seja, metade de sua capacidade de representação consistirá de valores positivos e metade de valores negativos. Mas por que esse valor? Nesse caso, quando se manipula tipos cuja largura é de 8 bits, tem-se 256 valores possíveis (2^8 = 256). No entanto, cabe o questionamento, como representar um valor em binário?

Todo valor, em qualquer base numérica, poderá ser fatorado. Por exemplo, o valor 876(10) poderá ser fatorado como:

876(10)  = 800    +   70    +    6
 
= 8*10^2 + 7*10^1 + 6*10^0.

 

No caso acima, o elemento que está sendo exponenciado, corresponde à própria base. Sendo assim, a fatoração de valores binários não é diferente, ou seja, o processo é o mesmo em relação à base decimal, porém, ao invés de trabalharmos com a base 10, trabalharemos com a base 2. Por exemplo, o valor:

1011(2)  =  1*2^3 + 0*2^2 + 1*2^1 + 1*2^0

= 8 + 0 + 2 + 1 = 11(10).

- **Conversão de binário para decimal:**

</span>
<div align-"center">
<img src="https://user-images.githubusercontent.com/113153237/220798812-f2ca971d-3882-4583-a168-5cf33a98ee91.gif" width= "500px" />
</div>

O processo apresentado acima corresponde à conversão de um valor na base binária para a base decimal.
Você pode notar que ao ser realizada a exponenciação da base pelo expoente que representa o grau de significância do termo, em função de sua localização, obtém-se: [2^3; 2^2; 2^1 ; 2^0 = 8; 4; 2; 1] (WEBER, 2012). Dessa combinação, originou-se o nome do modelo de representação binária que utilizamos: BCD 8421 (binary coded decimal). 

- **Conversão de hexadecimal para decimal:** 

</span>
<div align-"center">
<img src="https://user-images.githubusercontent.com/113153237/220799373-9fa2a4fb-a083-48a4-9b4a-ee9f4fd2400f.jpg" width= "500px" />
</div>

- **Conversão de decimal para hexadecimal:** 

</span>
<div align-"center">
<img src="https://user-images.githubusercontent.com/113153237/220799504-869dbe22-5819-4526-9192-d0577160c4ef.png" width= "500px" />
</div>


Voltando à programação em C/C++, o que acontece quando utilizamos o modificador de tipo unsigned? Esse modificador faz com que a variável represente apenas valores positivos. No caso do unsigned char, todos os 256 valores possíveis serão positivos (0 a 255). Isso ocorre porque, na verdade, na representação que permite trabalharmos com valores negativos, gasta-se 1 bit para representar o sinal. O bit mais significativo (MSB – most significant bit) representa o sinal. Caso o MSB seja zero, então o valor representado é positivo, caso contrário, um valor negativo é representado. Diante desse fato, tem-se 2^7 valores negativos (-128 a -1) e 2^7 valores positivos (0 a 127).

Essa ideia da possibilidade de se operar valores negativos e positivos remete a uma forma de representação denominada como complemento 2. Para se converter um valor de positivo para negativo ou negativo para positivo, usa-se o mesmo algoritmo constituído por duas fases:

- a) inverte-se todos os bits da palavra; 
- b) soma-se o valor um ao valor com os bits invertidos.


Sobre os valores binários representados em **BCD 8421** ou em complemento dois, poderão ser realizadas operações aritméticas de forma análoga ao processo empregado em valores com representação decimal.

**BCD:** Acrónimo da expressão inglesa Binary-Coded Decimal e pode ser traduzida por decimais codificados em binário. O BCD é um formato usado para representar números decimais internos onde cada dígito decimal é representado por quatro bits (nibble).

Além dos valores inteiros, existe também a representação dos números reais, conhecidos, computacionalmente, por **ponto flutuante** (float, em C/C++). O complemento dois é padronizado pelo IEEE sob número 754, que permite armazenar um valor de maneira semelhante à notação científica.

Na nossa notação científica, temos, por exemplo, o número 532,41 representado na forma 5.3241E2, ou seja, 5.3241 * 10^2. Nesse exemplo, temos, como mantissa o valor 5.3241 e, como expoente, o valor dois.

A responsabilidade de execução das instruções aritméticas, assim como as de operações lógicas, são de responsabilidade da Unidade Lógica e Aritmética. 

### Unidade Lógica e Aritmética (ULA):
A unidade lógica aritmética (ULA ou ALU – Arithmetic-Logic Unit) é o módulo de hardware integrante do computador, cuja função é realizar operações aritméticas e lógicas.

De forma simplista, podemos falar que a ULA realiza interfaceamento com o banco de registradores, de modo que ela possa coletar os valores a serem manipulados pelas operações aritméticas (como soma, multiplicação sobre números inteiros ou ponto flutuante) e pelas operações lógicas (como operação AND, deslocamentos etc.). 

Como resultados, a ULA fornece o valor da operação propriamente dito e, também, é responsável por gerar os bits do registrador de flags (indicando, por exemplo, resultado negativo, nulo e overflow).

### Unidade de Controle (UC):
A unidade de controle do processador tem por objetivo gerenciar todo o fluxo de execução das instruções. Esse gerenciamento é conseguido pelo envio de sinais de controle aos módulos da CPU, ativando-os quando necessário e pelo roteamento das informações de forma a encaminhá-las de forma apropriada.

A ULA poderá executar instruções da forma reg op reg (quando os dois operandos estão armazenados em registradores) ou reg op constante (a instrução representa uma operação entre o valor do registrador e uma constante). Você pode já imaginar que a UC, além de ativar a ULA, também deverá selecionar os operandos que incidirão no processamento. A figura abaixo, extraída de (PATTERSON, 1998), ilustra o interfaceamento entre a UC e a ULA.

</span>
<div align-"center">
<img src="https://user-images.githubusercontent.com/113153237/220801065-8d8bf5ab-7ef2-42bf-ad50-ed64852877d2.png" width= "500px" />
</div>

*Datapath do processador MIPS destacando-se a interface entre unidade de controle e a ALU e o chaveamento no fluxo de dados a ser encaminhado à ALU.Fonte: Adaptada de PATTERSON, 1998, p. 209.*

Na figura acima, nota-se que o módulo de controle, responsável pela decodificação das instruções, produz, para a ALU, dois sinais de controle: ALUop (operação de ALU) e ALUsrc (ALU source – ALU fonte). A seleção do dado é realizada por intermédio de um seletor denominado como MUX (também conhecido como multiplexador ou multiplex). O outro operando é coletado, sempre, do banco de registradores. O sinal “Read data 1” representa o conteúdo do registrador apontado por Read Register 1.

Por fim, tem-se, com saídas da ULA, o valor propriamente dito e, também, sinais do registrador de flags para indicar o status de seu processamento – no caso da figura, o bit zero. Ainda em relação à figura anterior, temos, para facilitar o processo de decodificação e demais ações, a quebra da palavra de instrução em vários pedaços. Por exemplo, o opcode das instruções corresponde aos bits 31 ao 26.

Você poderá notar, ainda na figura acima, que o datapath em questão é de um processador típico RISC. Mas como chegou-se à tal conclusão? Observando-se as entradas da ULA, percebe-se que operações do tipo soma (ADD) manipulam três registradores (dois fontes e um destino), as operações de ULA são da forma reg_destino, reg_fonte_1, reg_fonte2.

Para finalizar, podemos falar que o funcionamento do computador, em sua essência, é algo básico – baseado em decodificações, envio de sinais de controle, roteamento de informações. O que o torna complexo são as técnicas cada dia mais agressivas para conseguir, continuamente, aumentar o poderio de processamento e de sua performance computacional. Essas técnicas são baseadas no pipeline e na superescalaridade. Um outro complicante no quesito de complexidade é representado pelo processamento paralelo cada vez mais atuante e presente. Temos vários exemplos e níveis de paralelismo: nível de programação, nível de pipeline (pseudoparalelismo), nível de superescalaridade e, por fim, nível de múltiplos núcleos (cores – físicos e virtuais) de paralelismo. 
