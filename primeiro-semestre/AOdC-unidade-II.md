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
</div

### Hierarquia das memórias 

</span>
<div align-"center">
<img src="https://user-images.githubusercontent.com/113153237/220212854-5b851030-b9eb-4822-ba92-fd76e1fc24ef.png" width= "500px" />
</div

Além dos módulos em si, precisamos ter em mente que, para que eles atuem, é necessária toda uma sincronização de trabalho. **Essa sincronização é atingida pela geração de sinais de controle, os quais estão presentes dentro do processador para que este possa executar as instruções, e, também, estão presentes nos demais módulos que integram o computador.**

### Interconexão do computador, estrutura e função do processador:
Os caminhos que conectam os componentes de um sistema computacional é chamado de estrutura de interconexão. A estrutura de interconexão deve suportar os seguintes tipos de transferência: – Da memória para o processador. – Do processador para a memória.
A figura a seguir ilustra os módulos e a sua interconexão.
 
</span>
<div align-"center">
<img src="https://user-images.githubusercontent.com/113153237/220213916-647a26b7-f69d-41ed-ae82-916acdfa3eb4.png" width= "500px" />
</div

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
- **MAR (memory address memory):** o registrador de endereço de memória contém o valor do endereço para o próximo acesso à memória. **Com o uso desse registrador, o processador informa, ao sistema de memória, o endereço sobre o qual será realizado o acesso (para a leitura ou para a escrita)**;
- **MBR (memory buffer register):** após o MAR configurado, ao efetivar o acesso à memória, o item manipulado (gravado ou lido da memória) é armazenado no MBR. Sendo assim, o MAR e o MBR fazem parte do interfaceamento entre o processador e a memória;
- **I/O AR (input-output address register):** de forma análoga ao interfaceamento entre processador e memória, existe o registrador I/O AR, que contém o endereço do dispositivo de E/S a ser acessado;
- **I/O BR (input-output buffer register):** o item manipulado entre o processador e o dispositivo de I/O é armazenado no registrador I/O BR.

Não poderíamos deixar de citar o registrador de flags. Flags são registradores onde cada bit significa um estado do processador. Esse flag é setado sempre quando houver "vai um" depois de uma adição ou quando há BORROW depois de uma subtração. Pode ser usado também em uma operação de deslocamento de bits, quando o bit mais ao extremo for deslocado para fora do dado.
O registrador de flags é instanciado ao término, por exemplo, das operações aritméticas a fim de armazenar o estado final da operação, bem como informar se a operação resultou em algum valor negativo, nulo ou, ainda, se houve estouro de representação numérica (overflow). Mas por que armazenar esse estado final da operação? Vamos lhe dar um exemplo. Na maioria dos processadores, para se fazer uma operação de desvio, é necessário testar exatamente esse registrador de flags.

A figura a seguir ilustra a tradução de um desvio condicional a partir de uma linguagem de alto nível para um assembly (linguagem de máquina) hipotético.

</span>
<div align-"center">
<img src="https://user-images.githubusercontent.com/113153237/220216558-d29c3cbd-3fb8-4e02-a1c4-745d948dc226.png" width= "500px" />
</div

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
