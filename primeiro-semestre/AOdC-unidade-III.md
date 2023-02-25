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



