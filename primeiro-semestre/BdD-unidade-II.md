##  Introdução à modelagem de dados
A implementação de um banco de dados começa com a sua modelagem pelo analista ou projetista de dados, ou, simplesmente, analista. Nesta etapa, com base nos requisitos do sistema a serem tratados, o analista identifica o modo de estruturar entidades, atributos ou campos, e relações, e assim especificar o banco de dados que será implantado para prover as informações aos sistemas e seus usuários.

No caso da modelagem de dados, o nosso “protagonista” é um modelo relacional. Um exemplar é representado na Figura 2.2. O foco, nesta unidade, será sabermos como construir um desses diagramas, com as suas várias decisões de projeto.

</span>
<div align-"center">
<img src="https://user-images.githubusercontent.com/113153237/224853839-04833adb-4840-4dd4-a84b-2520499dd8da.png" width= "750px" />
</div>

*Modelo Relacional de um Sistema de Compras
Fontes: Elaborada pelo autor.*   
  
O ato de modelar, nas diversas áreas, permite uma visão preliminar do que será construído e apresenta algumas vantagens no processo de sua construção. Para software , em específico, Booch (2012) apresenta uma visão bem interessante e abrangente. As vantagens de uma boa modelagem com os seus diagramas, em em suas diversas áreas e contextos, englobam:

- **Melhor compreensão do que está sendo concebido:** Observe que o diagrama desenhado, no ato de modelar, é uma representação, isto é, expressa o produto final a ser construído. Portanto, durante a sua elaboração, o projetista enfrentará algumas dúvidas, precisará entender melhor situações e tomará decisões para expressar no diagrama. Essas atividades aprofundam a compreensão do projetista quanto ao mundo real que está sendo retratado.
- **Comunicação entre partes interessadas:**  É fácil percebermos que o diagrama apresentará melhor essas informações, e ainda com uma série de outros dados, como medidas da mesa, distância da janela, largura da porta etc. No nosso caso, de trato com dados, o diagrama já expressa suas tabelas, os campos e relacionamentos mais facilmente do que se tratados em texto.
- **Especificação para construção:** Complementando a comunicação, o diagrama da modelagem acaba ajudando a quem depois vai precisar de construir o artefato em questão. Um mestre de obras saberá a largura da janela e a posição na parede, sem a necessidade de o engenheiro estar todo o tempo disponível para esclarecer as dúvidas. Para o nosso caso de dados, o analista não precisa, a todo o momento, dizer quais os campos e tipos de dados da tabela. O desenvolvedor pode consultar o diagrama ou modelo para entender de que modo os dados estão estruturados.
- **Automatização do processo:** Um diagrama bem especificado pode servir para gerar, automaticamente, via ferramentas, outros produtos para a construção do sistema. Por exemplo, diante de um modelo relacional, uma ferramenta já pode gerar todos os comandos de SQL para a criação das tabelas e, ainda, outras ferramentas podem ajudar a gerar outros códigos para a programação do software.

#### Cenário de Exemplo:

Uma forma de desenvolvermos nossa habilidade de modelar é por meio de um exemplo da exploração de um cenário prático. Imagine, portanto, que nós fazemos parte de uma empresa de desenvolvimento de software, e uma loja gostaria de abrir a sua versão virtual para venda on-line na Internet. Em uma conversa com o cliente, surgiu a seguinte descrição do sistema:

“Quando um cliente deseja um produto, ele acessa o site da loja, na internet. Na primeira tela, pode consultar produtos e analisar características como Descrição e Preço. Conforme interesse, adiciona os produtos em seu ‘carrinho de compras’. Ao final do processo de escolha dos produtos, o usuário pode, então, efetivar a compra. Acessa uma seção para conferir o carrinho, depois faz o login no sistema para se autenticar, e daí efetiva o pagamento da compra”.

Diante desse cenário, quais são os produtos finais da modelagem? Uma primeira visão está na versão de Modelo de Entidade-Relacionamento, da Figura 2.3, e o Modelo Relacional do sistema é o diagrama que já foi apresentado na Figura 2.2. Algumas concepções estão abstraídas, e a ideia, neste momento, é termos uma visão dos produtos que construiremos no decorrer do aprendizado.

</span>
<div align-"center">
<img src="https://user-images.githubusercontent.com/113153237/224854706-976f3da4-0870-4b08-9fbe-64991cc3cc54.png" width= "750px" />
</div>
*Modelo de Entidade e Relacionamento do Sistema de Compras
Fonte: Elaborada pelo autor.*

### Modelo Conceitual, Modelo Lógico e Modelo Físico:

Nas fases para a implementação de um banco de dados, o nível de abstração ou detalhe varia desde uma visão mais próxima do mundo real e da sua representação conceitual até a forma como os dados serão concretizados no armazenamento em disco no SGBD. Esse caminho, com variação na profundidade, origina a distinção entre Modelos Conceitual, Lógico e Físico, um conteúdo muito comum sobre o tema banco de dados.

Conforme Amadeu (2019), o modelo conceitual de dados representa as informações que existem no contexto do negócio, com maior foco nos processos. Esse modelo utiliza termos e linguagem próprios do negócio mais adequados ao dia a dia do segmento envolvido no projeto. Perceba que, dessa forma, o modelo conceitual é o mais próximo do mundo real, não há ainda preocupações sobre como os dados serão representados por tipos de dados, como inteiro ou varchar. Para exemplificar, em um consultório poderia ser mapeada a existência de alguns médicos disponíveis, compostos de informações como nome e CRM. Esses médicos possuem uma agenda com os dias da semana e horários em que atende e os clientes podem realizar as consultas. Não é necessário, nesse nível de abstração, perceber que nome não pode ter mais do que 50 caracteres. Concentra-se em um nível mais alto de representação dos dados.

No nível lógico, começa a preocupação com a tecnologia com que o modelo conceitual vai “ganhar vida” para a solução. Por exemplo, o tipo de banco de dados deve ser identificado. É muito comum usarmos os bancos de dados relacionais comerciais. Mas existem alguns outros, como os bancos de dados hierárquicos, em rede e ainda os mais recentes, como os bancos orientados a objetos ou os bancos NOSQL ( not only SQL). Além do tipo de banco, questões como quais os nomes das entidades e dos campos, agora em uma linguagem mais próxima da programação e menos do mundo real.

Descendo ainda mais o nível de abstração, o projetista precisa definir questões do armazenamento físico dos dados, de como os dados serão implementados em uma solução computacional. De acordo com o tipo de banco de dados, as especificidades, como nomes de tabelas, campos, quais tipos de dados de cada campo e, ainda, restrições de integridade serão codificadas.

A Figura 2.4 permite compreender essa transição entre os modelos com seus respectivos níveis de detalhes. Perceba que o modelo conceitual está mais próximo dos processos de negócio. Na parte lógica e física, os modelos interagem com a aplicação e o modelo externo (parte baixa à direita). Por exemplo, nesse ponto estão os softwares clientes, que acessam os dados.

</span>
<div align-"center">
<img src="https://user-images.githubusercontent.com/113153237/224855190-18186580-93c2-430e-8a4e-ce17fa85d545.png" width= "750px" />
</div>

*Contextualização dos Modelos Conceitual, Lógico e Físico
Fonte: Amadeu (2019, p. 34).*

## Modelagem de Entidade e Relacionamento
Em cada um dos níveis de abstração explorados no tópico anterior, um determinado modelo pode ser aplicado, e dois deles são muito comuns: o Modelo de Entidade e Relacionamento, que é muito usado para os níveis de modelo conceitual, e o Modelo Relacional, popularmente empregado para o nível lógico e físico.

Conforme Puga (2013), o Modelo de Entidade-Relacionamento (MER) foi proposto por Peter Chen, nos anos 1970, e visa apresentar uma perspectiva do mundo real como constituído de um conjunto de objetos, entidades que se relacionam entre si. Ainda em Puga (2013), uma entidade representa uma categoria de elementos relevantes para um negócio, podendo ser, por exemplo, os clientes, fornecedores, vendas, contratos, pagamentos, registro de funcionários, entre outros. Sobre esses objetos são realizadas as regras do negócio, como “Cadastrar um cliente” ou “Efetivar uma venda”. Essas entidades, portanto, representam um conjunto de dados que precisam ser armazenados e que são manipulados pelas aplicações que informatizam o negócio.

Uma entidade é formada por atributos que apresentam alguma característica ou informação da entidade. Por exemplo, um cliente pode ser formado pelos atributos como nome, endereço, telefone, data de nascimento e outros. Uma transação financeira em um banco pode ter os atributos de data e hora da ocorrência, o valor e o tipo de transação, de crédito ou débito na conta. Um relacionamento indica uma relação que existe entre as entidades, por exemplo, um cliente realiza uma compra no site ou uma transação financeira é realizada em uma determinada conta corrente. Assim, no primeiro caso, existe um relacionamento entre as entidades cliente e compra e, no segundo caso, transação e conta corrente estão relacionados.

### Diagrama de Entidade e Relacionamento:
Modelagem e diagrama são dois conceitos intimamente relacionados: a **modelagem é o ato de refletir sobre como representar**, e o **diagrama é o esquema ou desenho que especifica o que está sendo modelado.** Muitas vezes, o termo modelo e diagrama são usados indistintamente. Os **conceitos de entidades, atributos e relacionamentos são o “coração” do diagrama de entidade e relacionamento (DER).**

</span>
<div align-"center">
<img src="https://user-images.githubusercontent.com/113153237/224855973-d84e45a0-83b2-4d0d-b699-7aae41546c3d.png" width= "750px" />
</div>
*Exemplo de parte de um diagrama de entidade e relacionamento
Fonte: Elaborada pelo autor.*

Note que, em texto, o que estamos dizendo é: “um cliente realiza uma compra e é formado pelos atributos CPF, Nome e Endereço, e a entidade compra é composta de Número, Data, Status e Valor”. Quando estamos modelando, o que fazemos é o oposto: em geral, temos uma compreensão do mundo real muitas vezes em texto e daí traduzimos para o formato de diagrama. Verificamos também que **entidade é desenhada como um retângulo;** o **relacionamento, como um losango** e os **atributos, como círculos,** todos eles ligados por linhas. **Essa maneira de desenhar os componentes de um diagrama é denominada notação, uma “linguagem”** para expressar o que estamos representando, e é útil, pois como todo diagrama DER, ou mesmo um diagrama de outra natureza é desenhado da mesma forma. Qualquer projetista de dados conhecerá a “linguagem” usada e, portanto, o que está sendo representado.

#### Um primeiro exemplo:
“Para o site da Loja Virtual funcionar, é necessário que os produtos sejam cadastrados com suas informações de Código de Barras, Descrição e Valor. Quando um Cliente acessa o site, ele se cadastra com seus dados de CPF, Nome, Endereço e Telefone. O Endereço, na verdade, é um conjunto de campos ou atributos, dentre eles, Rua e Número, Complemento, Bairro, Cidade, UF e CEP. Uma vez cadastrado, o cliente pode realizar as suas compras, que, enquanto transação, precisam do registro de seu Número, Data, Valor e Status. O Status indica se a compra já foi entregue, se está em andamento etc. E, para finalizar nossa compreensão, as Compras contêm os produtos que o Cliente escolheu para comprar”.

Para construir uma primeira versão do diagrama DER com base no texto, basicamente, **três ações serão necessárias: identificar as entidades, mapear os seus atributos e estabelecer os relacionamentos entre as entidades.** Nessa diagramação, ferramentas são empregadas.
A visão de como representar o cenário pode ter algumas variações de projetista para a projetista. Uma primeira versão para expressar o cenário descrito no texto está na Figura 2.6. Perceba que as entidades identificadas foram Produtos, Clientes e Compras, e dentre os atributos de Produtos, foram diagramados Código, Descrição e Valor, e existem dois relacionamentos entre Clientes-Compras e entre Compras-Produtos. Outras especificações podem ser vistas no próprio diagrama. Para efeito didático, algumas questões do mundo real foram abstraídas, por exemplo, um produto pode ter outras informações, como fotos, um Cliente pode ter muitos outros dados associados, e assim por diante.

</span>
<div align-"center">
<img src="https://user-images.githubusercontent.com/113153237/224856798-6648ba13-18cb-4953-869b-1c384eed02bf.png" width= "750px" />
</div>
*Versão inicial de um DER para o cenário de exemplo (Loja Virtual)
Fonte: Elaborada pelo autor.*

### Outras Características: Atributos e Cardinalidade
Perceba que, no diagrama, existem alguns atributos que estão marcados ou pintados. São os atributos identificadores, isto é, podem identificar, exclusivamente, a entidade. Dessa forma, o CPF é um atributo identificador de Cliente, pois não existem dois clientes que possuem o mesmo CPF, ou seja, um número de CPF é único, identifica unicamente o Cliente. O mesmo ocorre para Produtos, que são identificados pelo atributo Código de Barras, e a entidade Compras, que é identificada pelo atributo Número. Esses atributos serão, depois, tratados como chaves primárias no banco de dados.

Ainda, é possível visualizar, no modelo, alguns números (0,1), (0,n) ou (1,n) junto aos relacionamentos nas entidades, representando a cardinalidade. A cardinalidade indica quantos objetos de uma entidade podem se relacionar com objetos de outra entidade. No nosso exemplo, um Cliente pode se relacionar com (0,n) Compras, o que indica que um Cliente pode fazer nenhuma compra ou até n compras. Por outro lado, uma Compra tem uma relação (1,1) com Cliente, isto é, ela precisa estar associada a um Cliente, e somente a um Cliente. Não é possível, por exemplo, ter uma compra sem um cliente associado.

Do mesmo modo, uma compra pode conter N produtos e deve ter, pelo menos, um produto (relação (1,n) ), e um produto pode estar registrado em N compras, mas pode também não ser associado a uma compra, por exemplo, um tipo de produto novo que não foi vendido ainda. Dessa forma, com os vários tipos de cardinalidade são estabelecidas as regras sobre a quantidade de itens envolvidos nos relacionamentos.

Além das citadas, existem situações em que relações 1:1 (1 para 1) que não foram representadas em nosso exemplo. Nesse caso, um objeto se relaciona com apenas um, de outra entidade. Por exemplo, em um sistema, imagine que um Funcionário só pode ocupar um computador em uma estação de trabalho; assim, existe uma relação 1:1 entre eles. Ou ainda, imagine que, em uma empresa, um só funcionário pode chefiar um departamento, que só é chefiado por um funcionário.

#### Outras Situações Importantes 
Além das situações e elementos citados até agora, mais comuns em modelos ER, existem outras situações importantes, que podem, por vezes, ocorrer: **autorrelacionamento, generalização e o conceito de entidades fortes e fracas.**

No autorrelacionamento, há um relacionamento de uma entidade para ela mesma. Por exemplo, em um sistema, uma Pessoa pode ser cônjuge de outro elemento que é também da entidade Pessoa, ou um Funcionário pode ter como supervisor um outro elemento, que também é Funcionário.

</span>
<div align-"center">
<img src="https://user-images.githubusercontent.com/113153237/224857433-60191fe9-ae9c-4e72-8308-6564db8f8418.png" width= "750px" />
</div>
*Exemplo de autorrelacionamento*  

A **generalização ocorre quando uma entidade engloba características de outras entidades subjacentes.** A entidade mais “alta” generaliza os conceitos subjacentes. Um exemplo típico de uma entidade Pessoa, em um sistema, pode ser uma Pessoa Física ou uma Pessoa Jurídica, ou uma determinada entidade Usuário, que pode ser um Funcionário, um Professor ou um Estudante, em uma biblioteca da universidade. No caso, o conceito Pessoa é mais geral, generaliza os conceitos de Pessoa Física e Pessoa Jurídica. Da mesma forma todo Funcionário, Professor e Estudante são um Usuário da biblioteca da universidade. Portanto, Usuário generaliza os outros elementos. Um exemplo de generalização: 

</span>
<div align-"center">
<img src="https://user-images.githubusercontent.com/113153237/224857701-d7ccd8b1-dd0e-4cef-a492-1a93a8e2fe71.png" width= "750px" />
</div>
*Exemplo de relacionamento de generalização*

Uma entidade fraca é uma entidade cuja existência depende da existência de outra entidade, no caso, uma entidade forte. Para exemplificar, imagine que um sistema de Recursos Humanos precisa ter uma entidade de Dependentes. A existência de um dependente só faz sentido se estiver vinculada a um elemento da entidade Funcionário. Em geral, a identificação da entidade fraca depende de um atributo identificador da entidade forte. Em dependente, para ser identificado, ele poderia ter um número, juntamente com a identificação do funcionário, isto é, a tupla Identificação do Funcionário e número do dependente identifica o Dependente.

</span>
<div align-"center">
<img src="https://user-images.githubusercontent.com/113153237/224857965-5a86f64c-d150-46fa-a0ee-6ba5e5c63f76.png" width= "750px" />
</div>
*Exemplo de relacionamento entre entidade forte e entidade fraca
Fonte: Elaborada pelo autor.*

## Modelagem Relacional

Vamos relembrar aqui o que foi abordado: no modelo de entidade e relacionamento, o foco é “estar mais próximo” do mundo real, representando-o em uma perspectiva conceitual com independência quanto à tecnologia que seria empregada. Por exemplo, o mesmo modelo vale para implementar nos diversos tipos de bancos de dados (hierárquico, rede e outros). **Para tratar a forma como as informações serão implementadas, efetivamente, em um banco de dados, com tipos de dados, codificações, arquivos e outras questões mais tecnológicas de implementação (e menos conceituais), é necessário utilizar uma modelagem do nível Lógico e Físico, e para bancos de dados relacionais utiliza-se o Modelo Relacional.**

Em termos práticos, neste momento, é feita uma conversão da modelagem ER em uma modelagem relacional. Na verdade, será muito comum encontrar equipes de desenvolvimento, que inicia o trabalho com banco de dados com base no modelo relacional, já que existe forte equivalência entre eles. E o que vai mesmo determinar como as aplicações vão trabalhar com dados são as tabelas (ou relações) no banco de dados. Para nós, que tivemos a compreensão do MER antes, aprenderemos o Modelo Relacional justamente fazendo uma equivalência do que foi representado no MER e sua conversão para esse novo modelo. E, além disso, como nesse nível lógico e físico, novos detalhes tecnológicos são tratados.

### Relações ou Tabelas:
Os termos relação e tabela são equivalentes: em geral, relação é usado com mais frequência no campo teórico, e tabela será o jargão adotado no dia a dia.
Uma relação é um conjunto de tuplas (ou linhas de uma tabela), que, por sua vez, é um conjunto de valores com o respectivo valor referente a um atributo. Esses valores pertencem a um domínio, ou são de um tipo de dados (inteiro, conjunto de caracteres, real e outros), e podem, ainda, ter um valor NULL, que indica sem valor.

### Atributos, Tipos, Obrigatoriedade e Chaves Primárias:
Cada um dos atributos equivalentes aos atributos no MER – precisa ser associado a um tipo de dados, que, na teoria, é associado ao conceito de domínio, pois indica qual domínio de valores o atributo pode assumir, domínio dos números inteiros, dos números reais ou outros. 

#### Tipos de dados, descrição e   exemplo

- **INTEGER*:** Números inteiros, (23, 341, 899);
- **CHAR(N):** “Palavras” ou sequências de caracteres que são armazenados com um tamanho fixo de N caracteres, (“Joana”, “Marcos”);
- **VARCHAR(N):** Nesse caso, o banco de dados pode otimizar, variando o armazenamento conforme necessidade até o máximo de N caracteres, (Idem anterior, a mudança é no armazenamento interno);
- **NUMERIC(P,D):** Muito usado para números reais. A Precisão P indica quando dígitos podem ter o número e a quantidade de decimais; D indica quantas casas decimais. Por exemplo, NUMERIC(5,2) seria um número como 432.21, (347.20 ; 480.21);
- **DATE:**	Para campos do tipo data,	(22/03/2019);
- **BLOB:**	Usado para dados binários, por exemplo, caso seja necessário armazenar um arquivo de imagem ou de vídeo no banco de dados.

Algumas restrições podem ser associadas a um atributo, por exemplo, a obrigatoriedade. **Um atributo obrigatório é aquele que precisa, necessariamente, ter um valor, que não pode ser NULL.** Por exemplo, se um novo aluno está sendo cadastrado, não faz sentido ele não ter o seu nome preenchido.

Alguns atributos podem identificar uma tupla, linha da tabela ou entidade. Esses são aqueles atributos identificadores discutidos na modelagem de entidade e relacionamento. Aqui no modelo relacional, esses atributos são tratados como chaves. **O atributo que identifica a tupla é considerada chave primária,** e **outros eventuais atributos, que também identificam a tupla, podem ser considerados chaves candidatas.** Uma **chave pode ser composta, isto é, pode conter mais de um atributo.** Assim, em uma entidade ALUNO, a sua matrícula pode ser considerada a chave primária, o CPF, uma chave candidata, e os campos CI e UF (carteira de identidade e estado), também chave candidata, porém chave composta.

### Relacionamentos e Chaves Estrangeiras: 
Um conhecimento típico, nessa transição do modelo de entidade e relacionamento, é o trato com os relacionamentos, pois a forma de fisicamente representá-los em um modelo relacional é transpondo a chave primária de uma tabela para a outra tabela, que passa a ser chamada chave estrangeira, nome dado justamente para referenciar uma chave em outra tabela.

Um exemplo pode nos ajudar a compreender melhor essa conversão, e vamos relembrar de nosso cenário. Em nosso modelo, um CLIENTE realiza COMPRA com cardinalidade, em que um cliente pode estar associado a diversas compras, e uma compra só pode estar associada um CLIENTE. Nesse caso, a chave primária de CLIENTE passa a incorporar a tabela COMPRA, e na tabela de compra é denominada chave estrangeira por referenciar um elemento da tabela de CLIENTE. A Figura 2.13  ilustra essa conversão muito comum em relacionamentos 1:N:


</span>
<div align-"center">
<img src="https://user-images.githubusercontent.com/113153237/224860332-6172b9d2-37f5-4b9e-90c3-a0116918197e.png" width= "750px" />
</div>
*Transposição de chave estrangeira em relacionamento 1:N
Fonte: Elaborada pelo autor.* 

Assim como há esse tratamento no relacionamento 1:N, os outros tipos precisam também de ser tratados. Outra situação muito comum é a do relacionamento N:N, por exemplo, no nosso exemplo, a relação que existe entre COMPRA e PRODUTO, pois uma COMPRA pode conter diversos produtos, e um PRODUTO pode estar em diversas compras. Nesse caso, surge uma tabela associativa, isto é, uma nova tabela, que faz a associação com as outras duas. A Figura 2.14 representa melhor essa situação. Na esquerda, o relacionamento N:N, e na direita, a tabela associativa equivalente, PRODUTO_COMPRA.

</span>
<div align-"center">
<img src="https://user-images.githubusercontent.com/113153237/224860563-b7ef855f-bbee-4a6e-89db-df9acdbe68ba.png" width= "750px" />
</div>
*Conversão de relação N:N em tabela associativa
Fonte: Elaborada pelo autor.*

Os outros relacionamentos também apresentam uma forma de conversão para sua versão equivalente no modelo relacional. Note que a forma como as chaves primárias são transpostas para as tabelas relacionadas é que determina essa forma de conversão. O Quadro 3.X, a seguir, mostra a conversão que resta, do relacionamento 1:1 e do relacionamento de generalização:

</span>
<div align-"center">
<img src="https://user-images.githubusercontent.com/113153237/224860777-04ba6eb3-ef54-40a1-9ae5-42d88cc46f93.png" width= "750px" />
</div>
*Descrição da forma de determinar as chaves estrangeiras nos relacionamentos
Fonte: Elaborada pelo autor.*

## Normalização 
Normalização de banco de dados é um conjunto de regras que visa, principalmente, a organização de um projeto de banco de dados para reduzir a redundância de dados, aumentar a integridade de dados e o desempenho.

Ao analisar o que vimos anteriormente, sobre modelagem, usando como base o modelo relacional, inferimos que cada informação possui a sua tabela, o seu local de ser armazenado, evitando, desse modo, redundâncias e algumas inconsistências ao manipular os dados. De maneira informal, essa pode ser a explicação para o que, em banco de dados, chamamos normalização.

Elmasri trata normalização da seguinte maneira:  

*A normalização de dados pode ser considerada um processo de analisar os esquemas de relação dados com base em suas dependências funcionais e chaves primárias para conseguir as propriedades desejadas de (1) minimização de redundância e (2) minimização de anomalias de inserção, exclusão e atualização. Ele pode ser considerado um processo de filtragem ou purificação que faz com que o modelo tenha qualidade cada vez melhor. (ELMASRI, 2011, p. 348).*  

A dependência funcional referida, ao referir à normalização, diz respeito à dependência entre dois atributos. Diz-se que um atributo B depende, funcionalmente, de A quando duas tuplas com mesmo valor para A, necessariamente, devem apresentar o mesmo valor para B.

Na normalização, algumas dessas dependências serão checadas ou testadas de forma que se encontre uma melhor forma de separar as informações. Para cada tipo de teste, de acordo com uma situação, podemos dizer que o conjunto de dados foi normalizado conforme a primeira, segunda ou terceira forma normal, as mais comuns.

### Primeira Forma Normal (1FN):
Na primeira forma normal (1FN), os atributos não podem, para uma mesma entidade ter valores diferentes ou atributos possuindo mais de um valor, o que significa que não é permitido ter, na mesma relação, atributos multivalorados.
Para tratar essa situação, da primeira forma normal, deve-se identificar a chave primária e o atributo multivalorado e separá-los (o atributo multivalorado), em uma outra relação ou tabela, e utilizar a chave primária da entidade como chave estrangeira na nova relação. 

### Segunda Forma Normal (2FN):
Na segunda forma normal (2FN), os atributos que não compõem a chave devem depender unicamente da chave primária da tabela, e, além disso, os atributos que não são dependentes dessa chave devem ser realocados em uma nova tabela, utilizando esses dados.
Antes de seguir para a decomposição, vale comentar que as formas normais devem ser acumulativas. Portanto, para uma relação obedecer à segunda forma normal, (2FN), deve, previamente, ter atendido à primeira forma normal (1FN) dos atributos multivalorados.

No caso da decomposição da segunda forma normal, a tarefa é identificar a chave primária, os atributos dependentes e os atributos não dependentes. Desse modo, separam-se os atributos não dependentes em uma outra relação e faz-se o relacionamento através da chave estrangeira.

### Terceira Forma Normal (3FN):
Para estar na terceira forma normal (3FN), a relação, primeiramente, deve estar na segunda forma normal. Lembre-se de que as formas normais são acumulativas, e, para estar em uma forma normal “maior”, devem-se ter atendido as formas normais “menores”. Para a 3FN, em específico, é preciso eliminar os campos que podem ser obtidos a partir de um cálculo, ou de alguma lógica aplicada a outro campo.

Imagine que, na nossa relação de compras, tivesse um atributo chamado VLR_IMPOSTO, que diz respeito a um cálculo do imposto, calculado sobre o valor da compra. Portanto, o valor do imposto não precisa, necessariamente, ser armazenado. Nesse caso, o atributo, ou campo, pode ser retirado da relação, e os valores são calculados via regras de negócio da aplicação, isto é, o programa, quando manipulasse os dados de valor, faria os cálculos de imposto via alguma parte do programa.

### Normalização, Desnormalização e Performance: 
A normalização, como vimos, permite que os dados fiquem melhor estruturados, e isso tem uma motivação: consegue-se melhor integridade e qualidade da informação.
Por exemplo, imagine que a nossa relação desnormalizada, em que existem várias tuplas com os mesmos nomes e códigos, concentra na primeira e segunda linha, que possui o valor de COD igual a 1, e NOME igual a “João”. Suponha que gostaríamos de alterar o nome do cliente de “João” para “João Manoel”, e fizéssemos isso apenas na primeira linha. Teríamos, dessa forma, uma inconsistência ou anomalia nos dados, uma tupla de cliente com código 1 e nome “João”, e outra também com código 1, porém com nome “João Manoel”. Portanto, a normalização dos dados permite encontrar um esquema, ou estruturação, que garante melhor a qualidade das informações armazenadas, que ficam mais imunes a essas distorções.

Por outro lado, um banco muito normalizado pode causar alguns impactos de performance. Retomemos o caso da 3FN, do cálculo de imposto. A todo o momento que a compra for manipulada, um processamento deve ser feito para realizar o cálculo do imposto. Se formos ainda mais a fundo em nosso modelo, desde o início colocamos um campo de Valor da Compra, porém esse valor pode ser processado a partir da soma dos valores dos itens presentes na Compra. Mas note que, toda vez que uma compra for recuperada, a tabela de itens precisa ser processada para se calcular o total da compra para se ter o total da compra. Isso requer maior processamento para tratar dos dados.

Dessa forma, em algumas situações o projetista de dados pode tomar decisões quanto à normalização ou não dos dados, tendo a devida cautela para especificar bem, no caso de algumas desnormalizações, as regras de negócios a fim de que os dados sejam mantidos com boa consistência.

