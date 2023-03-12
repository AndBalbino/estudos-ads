## 1. Banco de dados 
Um **banco de dados** é uma coleção de dados. Nesse contexto, um dado é um fato que deve ser armazenado (persistido) e que tem um significado implícito. 

- Diz respeito a algum aspecto do mundo real e é criado com foco em um propósito específico; 
- Tem uma estrutura lógica que confere um significado aos dados. 

Essa estrutura lógica que deve ser construida é estabelecida para que possamos armazenar as informações de determinado contexto, e ficará armazenado e gerenciado em um **SGBD.** 

Segundo Korth, um banco de dados “é uma coleção de dados inter-relacionados, representando informações sobre um domínio específico”, ou seja, sempre que for possível agrupar informações que se relacionam e tratam de um mesmo assunto, posso dizer que tenho um banco de dados.

Podemos exemplificar situações clássicas como uma lista telefônica, um catálogo de CDs ou um sistema de controle de RH de uma empresa.

Já um sistema de gerenciamento de banco de dados (SGBD) é um software que possui recursos capazes de manipular as informações do banco de dados e interagir com o usuário. Exemplos de SGBDs são: Oracle, SQL Server, DB2, PostgreSQL, MySQL, o próprio Access ou Paradox, entre outros.

Por último, temos que conceituar um sistema de banco de dados como o conjunto de quatro componentes básicos: dados, hardware, software e usuários. Date conceituou que “sistema de bancos de dados pode ser considerado como uma sala de arquivos eletrônica”. 

### Modelagem de dados:
Para que seja possível construir um banco de dados, é necessário estabelecer a forma como os dados serão armazenados nesse banco. 
Estabelecer a forma como os dados serão armazenados implica na construção de um modelo para a organização dos dados: **uma modelagem de dados.** 


#### Profissionais que atuam no banco de dados: 
- **Administradores de banco de dados (DBA - *database administrator*):** são os profissionais responsáveis principalmente pelo modelo de dados que será usado para modelar e representar uma situação do mundo real, sobre a qual sistemas computacionais serão construídos.  
- **Projetista de banco de dados (*database designers*):** atuam diretamente na proposição do modelo de dados.
- **Analista de sistemas e programadores de aplicações:** são profissionais preocopados com o desenvolvimento das aplicações e dos sistemas que precisam estar disponniveis para os usuários finais.
- **Usuários finais.**

### Sistema de gerenciamento de banco de dados (SGBD): 
**SGBD** é a sigla em inglês de *Data Base Management System,* ou Sistema Gerenciador de Banco de Dados, em tradução para o português. Trata-se de um conjunto de software que gerencia uma base de dados, sendo responsável pelo controle, acesso, organização e proteção das informações da sua empresa.
Um **sistema de gerenciamento de banco de dados (SGBD)** é definido também como uma coleção de programas que permite que um usuário crie e mantenha um banco de dados. Trata-se de um sistema de propósito geral no qual é possível: 

- **Definir um banco de dados:** criar as estruturas para armazenamento dos dados e especificar as restrições que devem ser impostas aos dados; 
- **Manipular os dados do  banco de dados:** consultar, inserir, alterar e excluir dados do banco de dados sem que as restrições sejam violadas. 

</span>
<div align-"center">
<img src="https://user-images.githubusercontent.com/113153237/223275180-b1dfc48a-7e4f-478c-ae5f-5212c098c65d.png" width= "500px" />
</div>  
  
#### Profissionais que atuam nos SGBDs: 

- **Projetistas e implementadores de módulos e interfaces dos SGBDs:** são profissionais que conhecem o funcionamento dos SGBDs internamente e são responsáveis por implementar tecnologias.
- **Desenvolvedores de ferramentas:** também conhecem as estruturas dos SGBDs e desenvolvem as funcionalidades que estão disponiveis nesses sistemas para que os administradores de banco de dados e os desenvolvedores de aplicações possam atuar.
- **Analistas de suporte para o SGBD:** são profissionais que precisam conhecer as demandas de um SGBD para preparar o ambiente em que o sistema será aplicado.

#### Vantagens do uso dos SGBDs:

- Independência entre dados e programas;
- Aplicações (ou sistemas) que fazzem uso de um SGBD e de um banco de dados não precisam lidar com o armazenamento e o controle de acesso aos dados;
- Os sgbds permitem que operações sobre os dados sejam definidas de maneira independente de aplicação. As aplicações podem chamar tais operações por meio de seus nomes e argumentos, e não se preocupam como tais operações são implementadas. 
- **Controle de redundância:** todos os dados estão armazenados em um único lugar, e diferentes aplicações acessam a mesma instância (valor) desses dados. Se diferentes instâncias de um mesmo dado são armazenadas em locais diferentes e gerenciadas por aplicações diferentes, ocorre-se o risco de criar inconsistência de dados.
- **Controle de acesso:** O SGBD oferece um subsistema de autorização e segurança que previne que usuários acessem dados sem que estejam autorizados. 
- **Persistência para programas e estruturas de dados (objetos):** códigos e estruturas de dados são armazenados e gerenciados pelos SGBDs como objetos - são nomeados e podem ser invocados, alterados e excluídos a partir de funcionalidades oferecidas pelo sistema.
- **Eficiência no processamento de consultas:** Os SGBDs possuem funcionalidades que permitem executar requisições sobre os dados de forma eficiente. Essas funcionalidades incluem gerenciamento de índices e de memória, e otimização de consultas. 
- **Oferecimento de sistemas de *backup* e recuperação:** SGBDs oferecem subsistemas que realizam a recuperação dos dados após a ocorrência de falhas de software e hardware.
- **Garantia das restrições e integridade:** Os dados armazenados em um banco de dados são associados a algumas restrições. Tais restrições são constantemente verificadas, e garantidas pelo SGBD.
- Garante padrões.
- Redduz o tempo de desenvolvimento de aplicações. 
- Fornececimento de flexibilidade e disponibilidade.
- Promove economia de escala.

### Abstração de dados:
Para que seja possível usar as funcionalidades de um SGBD e atuar sobre um banco de dados, é preciso conhecer o **modelo de dados**, o qual usualmente é apresentado aos usuários via representação conceitual. 
O **modelo de dados conceitual** é construído por analista de dados e sua **implementação física** é realizada em um SGBD.

### Modelo de dados: 
- Modelos de **alto nível** ou **modelos de dados conceituais**, fornecem conceitos que são próximos á forma como os usuários percebem os dados, permitem explicar como os dados deveram ser estruturados e essas estruturas são estabelecidas no modelo de acordo com as regras de negócios que futuramente serão implementadas no sistema de banco de dados. EX: **Modelo Entidade-Relacionamento**.
- Modelos de **baixo nível** ou **modelos de dados físicos**, fornecem conceitos que descrevem em detalhes como os dados são armazenados no meio de persistência. Ex: **Formato de registros, ordenaão e formas de acesso.**
- Modelo de **dados de representação** ou **implementação**, fornecem conceitos que são compreensíveis por parte dos usuários mas que não estão longe de maneira como os dados são armazenados no meio de persistência. Ex: **Modelo relacional.**
 
### Conceitos importantes na área de banco de dados: 
- **Esquema:** descrição de um banco de dados. É especificado durante o projeto do banco de dados e não é esperado que sofra mudanças frequentes.
- **Instância (estado):** os dados armazenados em um banco de dados em um momento particular (tempo). Muitos (diferentes) estados de um banco de dados podem ser construídos a partir de um mesmo esquema. 

### Linguagens usadas no banco de dados especificamente os de consulta (SQL): 
- **Linguagem de definição de dados (DDL):** é usada para definir o esquema do banco de dados. *Atualmente pode englobar a SDL - Linguagem de definição de armazenamento - e a VDL - Linguagem de definição de visão.*
- **Linguagem de manipulção de dados (DML):** é usada para executar instruções de recuperação, inserção, exclusão e modificação de dados.  

</span>
<div align-"center">
<img src="https://user-images.githubusercontent.com/113153237/223287629-bc06cc2b-86b2-4564-92b9-992e5e1ac900.jpeg" width= "750px" />

*As ações que estão acima da linha pontilhada dizem respeito a acões que podem ser execultadas independente da tecnologia usada no SGBD.*  

*As ações que estão abaixo da linha pontilhada dizem respeito a ações que só poderam ser execultadas após a escolha do SGBD.* 

- #### Estrutura de sistemas de banco de dados

</span>
<div align-"center">
<img src="https://user-images.githubusercontent.com/113153237/223288269-f94e6a80-a74c-4f25-b559-67bf29acdf1b.jpeg" width= "750px" />
</div>

- #### Estrutura interna do SGBD

</span>
<div align-"center">
<img src="https://user-images.githubusercontent.com/113153237/223288454-c775fb48-98b0-46be-b408-f4bb171f0d86.jpeg" width= "750px" />
</div>

## 2. Modelo Entidade-Relacionamento (MER)
É um modelo de dados conceitual, de alto nível, que permite expressar a organização que deve ser imposta aos dados de um banco de dados.
Existe uma notação baseada em diagramas para a construção de um MER: o driagrama ER. 

#### Contexto didádico
- Exemplo de uma empresa:
Cada departamento da empresa possui um nome e um número exclusivos.
Um funcionário gerencia um departamento e a data de início desse trabalho de gerência deve ser registrada. 
Um mesmo departamento pode estar localizado em diferentes prédios. 
Os departamentos possuem vários empregados e controlam uma série de projetos. 

### Elementos do diagrama ER 
- Entidades
- Atributos
- Chaves
- Relacionamentos
- Cardinalidades

### Entidade

- **Entidade (forte):** é um objeto básico do MER usado para representar uma *coisa* no mundo real, física ou conceitual, com existência independente. Se tal existência só faz sentido quando está relacionada a outra entidade, a entidade é dita **fraca.**
**Heurística:** no discurso que descreve o mundo real, as entidades são frequentemente mencionadas, e geralmente são descritas em termos de suas propriedades. 
**Exemplo (entidade):** Cada **departamento** da empresa possui um nome e um número exclusivos. Um funcionário gerencia um **departamento** e a data de início desse trabalho de gerência deve ser registrada. Um mesmo **departamento** pode estar localizado em diferentes prédios. Os **departamentos** possuem vários empregados e controlam uma série de projetos. 
**Departamento** pode ser modelado como uma entidade. 
*Nos diagramas ER, as entidades são representadas por **retângulos.**

### Atributo

- **Atributo (entidade funcionário):** é uma propriedade que descreve uma entidade. 
**Exemplo:** Um funcionário possui um **número** que o identifica (identidade), **nome, endereço, salário** e **data de nascimento.**
*Nos diagramas ER, os atributos são representados por **Elipses.**

</span>
<div align-"center">
<img src="https://user-images.githubusercontent.com/113153237/223570209-ad811506-fa9c-447f-8e51-ee11b466dc54.jpeg" width= "750px" />
</div>  

#### Tipos de atributos: 
- Simples x composto;
- Univalorado x multivalorado;
- Armazenados x derivados; 

</span>
<div align-"center">
<img src="https://user-images.githubusercontent.com/113153237/223570844-134a8a27-8967-4abf-aa3a-9b11f4862dbc.jpeg" width= "750px" />
</div>  

- O **atributo** que contém a palavra nome é um **atributo composto.**
- Os demais **atributos** são considerados **simples.** 

</span>
<div align-"center">
<img src="https://user-images.githubusercontent.com/113153237/223571551-5a1ae065-8a24-4951-ade6-74955b0b0ed7.jpeg" width= "750px" />
</div> 

- O **elipse** com borda suplicada significa que ele é um **atributo multivalorado** ou seja ele pode assumir vários valores.
- O **elipse** com a borda pontilhada significa que esse **atributo é derivado** ou seja o valor que ele pode assumir será calculado a partir de outros valores ou dados que estão armazenados nesse banco de dados. Esse atributo não precisa necessariamente ser persistido quando for emplementado o banco de dados ao SGBD, poderemos associar ele a uma função que processa várias informações e calcula o número de empregados disponibilizando esse número de empregados para as aplicações que precisam dessa informação.

### Conceitos importantes: 
- Um tipo entidade define uma coleção, ou conjunto, de entidades que têm os mesmos atributos. É o **esquema.**  
- A coleção de todas as entidades de um tipo entidade é chamada de conjunto entidade. É a **instância.** 

</span>
<div align-"center">
<img src="https://user-images.githubusercontent.com/113153237/223574994-2750b150-7a59-435b-bf1e-4532ef93ae03.jpeg" width= "750px" />
</div> 


### Atributo chave 

- **Atributo chave:** um tipo entidade, usualmente, tem um ou mais atributos que assumem valores distintos para cada entidade individual dentro do conjunto entidade. Esse atributo, ou conjunto de atributos (chave composta), identifica unicamente uma entidade. 

- **Restrição de unicidade:** proíbe que duas entidades, em um mesmo conjunto entidade, tenham os mesmos valores no seu atributo chave.

</span>
<div align-"center">
<img src="https://user-images.githubusercontent.com/113153237/223576844-af15dda8-0ad6-46ce-a0b6-217f61181869.jpeg" width= "750px" />
</div>  

--  

</span>
<div align-"center">
<img src="https://user-images.githubusercontent.com/113153237/223577419-3cf6fde1-a210-4283-9cfc-48528eb4a699.jpeg" width= "750px" />
</div> 


### Relacionamento 

- **Relacionamentos:** representam as associações existentes entre as entidades. 
- **Heurística:** no discurso que descreve o mundo real, os relacionamentos são geralmente expressos por ações que envolvem entidades. 

#### Contexto didádico
- Exemplo de uma emrpesa:
Um funcionário **gerencia** um departamento (...) Os departamentos **possuem** vários empregados e **controlam** uma série de projetos ...  

A gerência, a existência de empregados associados aos departamentos e o controle de projetos podem ser modelados como relacionamentos associados à entidade DEPARTAMENTO. 

</span>
<div align-"center">
<img src="https://user-images.githubusercontent.com/113153237/223580851-db5e1b23-f7d9-4079-abec-9bdc79e900b6.jpeg" width= "750px" />
</div> 

### Conceitos importantes: 
- Um tipo relacionamento R entre *n* entidades, E1, E2, ... En, define um conjunto de associações - ou um conjunto relacionamento - entre entidades desses tipos entidade. 

</span>
<div align-"center">
<img src="https://user-images.githubusercontent.com/113153237/223582540-70a2b5c2-ef36-481c-8d8d-effa9953d6a3.jpeg" width= "750px" />
</div>   


O **grau** de um tipo relacionamento é o número de tipos entidade participantes do relacionamento: 
- Binário (ou de grau dois);
- Ternário (ou de grau três);
- *n*-ário (ou de grau *n*);

**Exemplo:** um fornecedor fornece peças para um projeto.  
O relacionamento **fornece** envolve as entidades **fornecedor, peça** e **projeto.**

</span>
<div align-"center">
<img src="https://user-images.githubusercontent.com/113153237/223586108-2a324764-6907-43ad-8aed-c924a8dd5c37.jpeg" width= "750px" />
</div>   

### Cardinalidade
- **Cardinalidade:** especifica o número máximo de instâncias de relacionamentos nas quais uma instância de entidade pode participar. 
- 1;1 (um para um)
- 1;N (um para muitos, N;1 (muitos para um) 
- M;N (muitos para muitos) 

A **cardinalidade** está associada a um relacionamento e no diagrama ER é representada por **1, M** e **N (...)** junto aos losangos. 

### Conceito de restrição de participação: 
**Restrição de participação:** especifíca se uma entidade individuak precisa, necessariamente, estar associada a outra entidade individual via um tipo relacionamento. Se a participação em um tipo relacionamento é obrigatórua, ela é dita **TOTAL**, senão ela é dita **PARCIAL.**
No diagrama ER a participação total é representada por uma **linha dupla** que conecta o tipo entidade ao tipo relacionamento. A participação parcial é representada pela **linha simples.**


#### Modelo entidade relacionamento 

</span>
<div align-"center">
<img src="https://user-images.githubusercontent.com/113153237/223589095-9cd9a9db-c7ee-40d3-ad49-a08f311be05c.jpeg" width= "750px" />
</div>   

## 3. Modelo Entidade-Relacionamento estendido (Especialização-generalização e agregação)
Modelo de dados conceitual mais acurado, capaz de expressar propriedades e restrições dos dados com maior precisão.

#### Características
- Especialização-generalização;
- Agregação;

**Especialização:** Processo de definir um conjunto de subtipos(ou subclasses) de um tipo entidade (supertipo ou superclasse), a partir das características que distiguem subconjuntos de entidades individuais.
**Generalização:** Processo inverso da abstração, no qual as diferenças entre vários tipos entidades são suprimidas na criação de um supertipo. Quanto já temos subtipos estabelecidos e entendemos que precisamos criar um supertipo para descrever melhor a situação que está sendo modelada.  
**Agregação:** É uuma abstração que pérmite a construção de objetos a partir de seus componentes. 
- **Obs:** No MER estendido podemos agregar (combinar) objetos que estão relacionados. A partir dessa agregação, criamos um novo objeto que pode ser tomado como uma entidade de alto nível e pode, portanto, participar de um relacionamento.
 
### Especialização: 

- **Restrição de disjunção:** Significa que determinada entidade só pode se especificar em uma única subcategoria de forma exclusiva. 
-  
 </span>
<div align-"center">
<img src="https://user-images.githubusercontent.com/113153237/223862883-b9146438-841b-4a44-828f-d88fa45b7a79.jpeg" width= "750px" />
</div>   
     
 </span>
<div align-"center">
<img src="https://user-images.githubusercontent.com/113153237/223864417-9eb3e4de-3377-4b57-8dae-fd3d86a9d0b1.jpeg" width= "750px" />
</div>   

### Generalização: 

- **Restrição de sobreposição (overlap):** As subclasses não tem restrição de disjunção, ou seja, podem ser sobrepostas. Uma entidade pode ser membro de mais de uma subclasse da especialização.

 </span>
<div align-"center">
<img src="https://user-images.githubusercontent.com/113153237/223865315-e4ff5137-b8f2-4d2f-880b-ca4a816d4786.jpeg" width= "750px" />
</div>   
  
 </span>
<div align-"center">
<img src="https://user-images.githubusercontent.com/113153237/223865453-b0107214-2cec-4390-9604-ea24ff5d7505.jpeg" width= "750px" />
</div>  


### Agregação: 

 </span>
<div align-"center">
<img src="https://user-images.githubusercontent.com/113153237/223867869-d79e298a-f437-44d1-991e-06e891b66cfc.jpeg" width= "750px" />
</div> 

## 4. Modelo relacional (R) 
**Modelo relacional** é um modelo de dados que representa um banco de dados como uma coleção de relações. Uma relação remete a uma tabela de valores, na qual cada linha representa uma coleção de valores (colunas) relacionadas.
Uma linha representa um fato que tipicamente corresponde a uma entidade ou relacionamento do mundo real. 

#### Glossário para o modelo relacional

- Relação -> Tabela
- Tupla -> Linha
- Atributo -> Coluna
- Domínio -> Tipo de dado 

#### Conceitos: 
- Um esquema de relação *R*(A1, A2, ..., An) é composta de uma relação de nome *R* e da lista de atributos A1, A2, ..., An.
- Cada atributo Ai é o nome do papel desempenhado por um domínio D no esquema de relação *R*. 
- O grau de uma relação é o número *n* de atributos do esquema de relação que a define.


</span>
<div align-"center">
<img src="https://user-images.githubusercontent.com/113153237/223870658-90ebc172-4b48-4754-af1d-1006ec07fe1e.jpeg" width= "750px" />
</div>

#### Conceitos: 
- Uma relação (ou estado de uma relaçao) *r*, definida sob o esquema *R*(A1, A2, ..., An), é um conjunto de *m*-tuplas *r*={t1, t2, ..., tm}.
- Cada *m*-tupla é uma lista ordenada de *n* valores t = < V1, V2, ..., Vn >.
- O I*ésimo* valor da tupla *t*, o qual corresponde ao atributo Ai, é referenciado como t[Ai] ou t.Ai.

</span>
<div align-"center">
<img src="https://user-images.githubusercontent.com/113153237/223874136-3bc6f7ee-1e76-40c0-b875-59e6894e562c.jpeg" width= "750px" />
</div>

#### Ordenação de tuplas em uma relação
Uma relação é definida como um conjunto de tuplas. Elementos de um conjunto não são ordenados. Assim, as tuplas em uma relação não possuem nenhuma ordenação. 



*Obs: Se tivermos o mesmo conjunto de tuplas nas duas relações mas em ordens diferentes teremos relações iguais, pois a ordem das tuplas em uma relação não importa*

#### Ordenação dos valores dentro de uma tupla 
Uma tupla é uma **lista ordenada de valores**, então a ordem dos valores na tupla é importante.
Para efeitos práticos, e em determinadas situações, essa restrição pode ser flexibilizada. 

</span>
<div align-"center">
<img src="https://user-images.githubusercontent.com/113153237/223876220-fa97ce90-9d69-45ab-b9a1-6d694db7d435.jpeg" width= "750px" />
</div>

#### Valores e NULL nas tuplas 
Cada valor em uma tupla é um valor **atômico**. Assim, atributos compostos e atributos multivalorados **não são permitidos.** 
Valores NULL são usados para representar os valores **desconhecidos** ou que **não se aplicam** aquele atributo naquela tupla. 


### Restrição de domínio: 
O modelo relacional possue uma série de restrições, todas essas retrições elas implicam em regras que precisam ser seguidas na manipulação dos dados no SGBD. Essas restrições do modelo relacional elas são garantidas pelo SGBD, eles implementam uma série de funções que nos auxiliam a manter a consistência dos dados.

Restrições de domínio especificam que o valor de cada atributo **A** deve ser um valor atômico dentro de um domínio **dom(A)**, em todas as tuplas da relação. 

### Restrição chave: 
Por definição todos os elementos de um conjutno são distintos; logo, todas as tuplas em uma relação devem ser distintas, ou seja, duas tuplas quaisquer **não podem ter a mesma combinação de valores para os seus atributos.**

*T1[SK] <> T2[SK]*  
  
#### Conceito de superchave 
- **Superchave:** Qualqier conjunto de atributos SK, pode ser considerado uma superchave. Toda relação tem pelo menos uma superchave - todos os seus atributos. Uma superchave pode ter atributos redundantes. 


</span>
<div align-"center">
<img src="https://user-images.githubusercontent.com/113153237/223881186-68980ceb-07ef-4dc5-a015-d709241cf3f6.jpeg" width= "750px" />
</div>

#### Conceito de chave
- **Chave:** É uma superchave de *R* sem atributos redundantes; *i*.*e*. é um conjunto de atributos mínimo capaz de garantis a restrição de unicidade.
- Em geral, um esquema *R* pode ter mais de uma chave. Cada uma delas é uma **chave candidata.**
- É comum escolher uma das chaves candidatas para ser a **chave primária** da relação.
- Cada uma das demais chaves candidatas é chamada de **chave única.** 

</span>
<div align-"center">
<img src="https://user-images.githubusercontent.com/113153237/223881486-387484db-8590-4367-9cb8-d65e6a1cc05f.jpeg" width= "750px" />
</div>

#### Conceito de chave estrangeira 
Considere dois esquemas de relação *R1* e *R2*. Um conjunnto de atributos **FK** no esquema *R1* é uma chave estrangeira de *R1* que referencia *R2* se: 
- Os atributos em **FK** tem o mesmo domínio dos atributos da chave primária **PK** em *R2*;
- O valor de **FK** na tupla *t1* de um estado de *r1* *(R2)* ou ocorre como um valor de **PK** para alguma tupla *t2* de um estado de *r2(R2)* ou é **NULL.** 

*t1[FK} = t2[PK]*

</span>
<div align-"center">
<img src="https://user-images.githubusercontent.com/113153237/223884200-95d011eb-027e-4c67-8a5a-c7af574dbb50.jpeg" width= "750px" />
</div>

### Restrição de integridade de entidade:
O valor de uma chave primária não pode ser NULL.

### Restrição de integridade referencial: 
É especificada entre duas relações e usada para manter a consistência entre as suas tuplas.
- Uma tupla de uma relação **A** que referencia uma relação **B** deve fazer a referência a uma **tupla existente** na relação **B.**

## 5. Mapeamento MER -> Relacional 
**Mapeamento:** Uma forma de projetar um esquema de um banco de dados relacional (um projeto lógico) tendo como base o esquema de um projeto conceitual.
- A maneira clássica de desenvolvimento de um banco de dados é por meio da construção de um modelo conceitual - independente de SGBD - o qual é posteriormente convertido, ou mapeado, para um projeto lógico que seja implementável no SGBD escolhido para desenvolvimento do sistema de banco de dados.


</span>
<div align-"center">
<img src="https://user-images.githubusercontent.com/113153237/223287629-bc06cc2b-86b2-4564-92b9-992e5e1ac900.jpeg" width= "750px" />
</div>

Ao implementar o projeto lógico no SGBD teremos **garantidas** algumas **restrições** que devem ser impostas aos dados.   
 
**Exemplo:**
- Restrições de **domínio**
- Restrições de **chave**
- Restrições de **integridade referencial** (chave estrangeira)   
  
Para que essas restrições sejam mantidas na nossa aplicação da maneira que atende aos requisitos de dados que levantamos na coleta de dados, precisamos ter certeza de que o projeto lógico está bem estabelecido, então fazer o projeto conceitual com cuidado e mapea-lo para o projeto lógico é uma boa alternativa para tentar garantir a qualidade do nosso projeto e a qualidade dos dados.

### Mapeamento tipos entidade forte (ou regulares) 
- Para cada tipo de entidade forte em um MER é criada uma relação ou modelo Relacional;
- Essa relação inclui todos os atributos simples, e os componentes simples dos atributos compostos, do tipo entidade forte; 
- Um atributo chave da entidade é escolhido como chave primária para a relação recém criada. 


</span>
<div align-"center">
<img src="https://user-images.githubusercontent.com/113153237/224177936-642bba87-a9a9-4d3a-abfb-33169bc661f7.jpeg" width= "750px" />
</div>

</span>
<div align-"center">
<img src="https://user-images.githubusercontent.com/113153237/224178347-33ee3f26-d653-4e6a-a32e-70bef2d0de68.jpeg" width= "750px" />
</div>

</span>
<div align-"center">
<img src="https://user-images.githubusercontent.com/113153237/224178478-2d827a44-bd6f-4675-9b22-a2bd84550f33.jpeg" width= "750px" />
</div>

</span>
<div align-"center">
<img src="https://user-images.githubusercontent.com/113153237/224178556-da6be3d9-b44c-4a0d-9f85-a767a2f54ca8.jpeg" width= "750px" />
</div>

### Mapeando os atributos multivalorados: 
Para cada um desses atributos é preciso criar uma nova relação.
- Essa relação incluirá um atributo **A** correspondente ao atributo multivalorado, mais o atributo chave primária **K** da relação que representa o tipo entidade no qual o atributo multivalorado foi especificado; 
- O atributo **K** será uma chave estrangeira na nova relação;
- A chave primária dessa nova relação será a combinação dos atributos **A** e **K**.

</span>
<div align-"center">
<img src="https://user-images.githubusercontent.com/113153237/224448108-71da0d43-1a38-43b1-9095-14f5ddaddda6.jpeg" width= "750px" />
</div>

</span>
<div align-"center">
<img src="https://user-images.githubusercontent.com/113153237/224448236-e3756682-ce81-45bb-ba03-c62bb8db87a8.jpeg" width= "750px" />
</div>

### Mapeamento tipos entidade fraca: 
- Para cada tipo entidade fraca em um MER é criada uma relação no modelo Relacional.
- Essa relação inclui todos os atributos simples, e os componentes simples dos atributos compostos, do tipo entidade fraca; e inclui como atributo chave estrangeira, a chave da entidade forte associada à entidade fraca; 
- A chave primária da relação criada é a combinação do atributo chave da entidade forte com o atributo chave parcial da entidade fraca. 

</span>
<div align-"center">
<img src="https://user-images.githubusercontent.com/113153237/224449121-6207a31a-b056-4f29-bd35-4fac63c33399.jpeg" width= "750px" />
</div>

</span>
<div align-"center">
<img src="https://user-images.githubusercontent.com/113153237/224449144-6fc3be9b-94d1-4674-a45e-e1ad58d7901b.jpeg" width= "750px" />
</div>

</span>
<div align-"center">
<img src="https://user-images.githubusercontent.com/113153237/224449181-c581afa4-ef07-488c-8808-ab90ba221e99.jpeg" width= "750px" />
</div>


##

#### Resumo de mapeamento do MER para o Modelo Relacional
**Conceitos importantes:**  

*Consideramos aqui apenas os mapeamentos entidades, atributos e algumas discussões sobre os conceitos chave.*  

*Quando temos atributos simples ou elementos simples de atributos compostos, eles aparecem no nosso modelo relacional como atributos das relações, mas os atributos multivalorados precisam ser trabalhados como no exemplo abaixo em DEPTO_LOCALIZAÇÔES.*  

*Temos também a questão da entidade fraca, que deverá compor a sua chave com a chave primária da entidade forte.*  

*Para dois pares de relações temos o conceito de chave estrangeira que está representando um tipo de relacionamento entre funcionário e depentende e entre departamento e depto-localizações.*  


</span>
<div align-"center">
<img src="https://user-images.githubusercontent.com/113153237/224451214-e71075b6-2f56-4185-a0c9-6e30841b8469.jpeg" width= "750px" />
</div>

##

### Mapeamento tipos relacionamento binário 1:1: 
- Para cada tipo relacionamento binário 1:1 no MER, identifique as relações S e T que corresponde aos tipos entidade participantes no relacionamento.

#### Escolher um tipo de abordagem:
- 1. Abordagem da chave estrangeira (mais comum); 
- 2. Abordagem de relação unificada;
- 3. Abordagem referência cruzada ou relação de relacionamento; 

#### 1. Abordagem de chave estrangeira 
- Escolha uma das relações, por exemplo a relação S - e inclua como chave estrangeira em S a chave primária de T;
- Se houver tipo entidade com participação total envolvido no relacionamento, escolhê-lo para o papel S será a melhor opção;
- Inclua todos os atributos compostos, do tipo relacionamento como atributos de S. 

</span>
<div align-"center">
<img src="https://user-images.githubusercontent.com/113153237/224452807-a01d1ece-5972-4c69-9a81-1de29affccc9.jpeg" width= "750px" />
</div>

#### 2. Abordagem da relação unificada
- Unifique os dois tipos entidade e o tipo relacionamento é uma única relação; 
- Isto é possível quando ambos tipos entidade possuem participação total, indicando que as duas relações referentes aos tipos entidade participantes do relacionamento possuem sempre o mesmo número de tuplas.

#### 3. Abordagem cruzada 
- Crie uma terceira relação para atuar como uma referência cruzada das chaves primárias de cada uma das duas relações S e T; 
- A terceira relação incluirá as chaves primárias de S e T como chaves estrangeiras; 
- A chave primária da terceira relação será uma das duas chaves estrangeiras, e a outra chave estrangeira será uma chave única.

### Mapeando tipos relacionamento binário 1:N (N:1): 
- Para cada tipo relacionamento regular binário 1:N, identifique a relação S que representa o tipo entidade que participa do tipo relacionamento uma vez; 
- Inclua a chave primária da relação T (a outra entidade que participa do relacionamento) como chave estrangeira na relação S;
- Inclua como atributo de S todos os atributos simples, e os componentes simples dos atributos compostos, do tipo relacionamento.

</span>
<div align-"center">
<img src="https://user-images.githubusercontent.com/113153237/224454079-ceb5aa28-419e-41c7-9769-e7c235340481.jpeg" width= "750px" />
</div>

##

</span>
<div align-"center">
<img src="https://user-images.githubusercontent.com/113153237/224454104-22751f16-09f9-4ab2-9906-4ccc2c7549bf.jpeg" width= "750px" />
</div>

##

</span>
<div align-"center">
<img src="https://user-images.githubusercontent.com/113153237/224454403-861d028a-32df-4720-891a-99284fadcd1d.jpeg" width= "750px" />
</div>

### Mapeamento tipos relacionamento binário M:N: 
- Para cada tipo relacionamento binário M:N, crie uma nova relação para representar o relacionamento;
- Inclua como chaves estrangeiras na nova relação asa chaves primárias das relações que representam as entidades participantes do relacionamento;
- A chave primária da nova relação é a combinação dessas chaves estrangeiras; 
- Também inclua todos os atributos simples, ou componentes simples de atributos compostos, como atributos na nova relação.

</span>
<div align-"center">
<img src="https://user-images.githubusercontent.com/113153237/224455262-8d3b48f6-2035-4e9b-9c00-367df1392703.jpeg" width= "750px" />
</div>

##

#### Modelo relacional completo 

</span>
<div align-"center">
<img src="https://user-images.githubusercontent.com/113153237/224455286-d79adc40-6995-4ad7-a740-f2c89a12cd1b.jpeg" width= "750px" />
</div>

## 

### Mapeamento tipos relacionamento n-ários:
- Para cada tipo relacionamento n-ário, em que n >2, crie uma nova relação S para representá-lo;
- Inclua como chaves estrangeiras em S, as chaves primárias das relações que representam os tipos entidades participantes do relacionamento;
- Inclua qualquer atributo simples, ou componentes simples de atributos compostos, como atributos de S; 
- A chave primária de S é, usualmente, a combinação de todas as chaves estrangeiras em S; 
- Se a cardinalidade em qualuer participação de um tipo entidade é 1, então a chave primária de S não deveria incluir a chave estrangeira que referencia a relação que representa esse tipo entidade.


</span>
<div align-"center">
<img src="https://user-images.githubusercontent.com/113153237/224456127-6e6ff195-a08b-415b-9a03-02c2e75396f5.jpeg" width= "750px" />
</div>

</span>
<div align-"center">
<img src="https://user-images.githubusercontent.com/113153237/224456199-e82b2908-5cde-4869-bc1d-1c518ffb82e3.jpeg" width= "750px" />
</div>

##

</span>
<div align-"center">
<img src="https://user-images.githubusercontent.com/113153237/224456225-3fc9f8a8-f7e8-43a2-8dbb-e2e5fbe6e9f5.jpeg" width= "750px" />
</div>

##

### Mapeando especialização ou generalizações:
Converte cada especialização com *m* subclasses {S1, S2, ..., Sn} e a superclasse C, cujos atributos são {k, a1, ..., an} e a chave primária é k, em relações usando uma das seguintes opções: 

1. Múltiplas relações: superclasses e subclasses;
2. Múltiplas relações: apenas subclasses;
3. Relação única com um único atributo *tipo*;
4. Relação única com vários atributos *tipo*. 


#### 1. Múltiplas relações: superclasses e subclasses:
- Crie uma relação L para representar a superclasse C, e inclua em L os atributos Atrb (L) = {k, a1, ..., an} e a chave primária PK (L) = k;
- Crie uma relação Li para cada subclasse Si, 1 <= i <=m, com os atributos Atrb(L1) = {k} U(nido) {atrb(Si)} e faça PK(Li) = k;
- Esta opção funciona para qualquer tipo de especialização (**total** ou **parcial**, com restrição de **disjunção** ou de **sobreposição**).

</span>
<div align-"center">
<img src="https://user-images.githubusercontent.com/113153237/224457495-418313ed-322a-430f-933a-89ed8d6e7dc8.jpeg" width= "750px" />
</div>

</span>
<div align-"center">
<img src="https://user-images.githubusercontent.com/113153237/224457503-1e93a7d3-286e-432e-bbdd-9697e1ab6c70.jpeg" width= "750px" />
</div>

#### 2. Múltiplas relações: apenas subclasses;
- Crie uma relação Li para cada subclasse Si, 1 <= i <= m, com os atributos Atrb(Li) = {atributos de Si} U(nido) {k, a1, ..., an} e PK(Li) = k;
- Esta opção funciona **apenas** para especializações de **participação total.**
- E é **recomendada** para especializações com **restrição de disjunção**. Se a individual pode suplicada em várias relações.


</span>
<div align-"center">
<img src="https://user-images.githubusercontent.com/113153237/224571508-3dac150b-ad17-4f65-a89e-d67d582238eb.jpeg" width= "750px" />
</div>

</span>
<div align-"center">
<img src="https://user-images.githubusercontent.com/113153237/224571527-1914f8a7-0ccd-48a7-b79a-eb58af839820.jpeg" width= "750px" />
</div>

##

#### 3. Relação única com um único atributo *tipo*; 
- Crie uma única relação L com os atributos Atrb(L) = {k, a1, ..., an} U(nidos) {atributos de S1} U ... U {atributos de Sm} U {t} e PK {L} = k. 
- O atributo t é chamado atributo *tipo* (ou discriminador) e seu valor indica a subclasse à qual cada tupla pertence, se ela pertencer a alguma subclasse. 
- Esta opção funciona somente para especializações cujas subclasses são **disjuntas**.
- Esta opção pode gerar muitos valores **NULL** se as subclasses tiverem muitos atributos especifícos.

</span>
<div align-"center">
<img src="https://user-images.githubusercontent.com/113153237/224571919-2e3a502d-e511-4f97-9b40-9175b31927f9.jpeg" width= "750px" />
</div>

#### 4. Relação única com vários atributos *tipo*; 
- Crie uma única relação L com os atributos Atrb(L) = {k, a1, ..., an} U(nidos) {atributos de S1} U ... U {atributos de Sm} U {t1, t2, ..., tm} e PK(L) = k.
- Cada ti, 1 <= i <= m, é um atributo do tipo booleano que indica se uma tupla pertence a uma subclasse Si.
- Esta opção é usada para uma especialização com restrição de **sobreposição**.
- Ela também funciona para a restrição de **disjunção**.

</span>
<div align-"center">
<img src="https://user-images.githubusercontent.com/113153237/224572432-59ba1590-bef7-47d8-a320-601bde9a35e2.jpeg" width= "750px" />
</div>

</span>
<div align-"center">
<img src="https://user-images.githubusercontent.com/113153237/224572468-a204da91-6c69-4fc7-857b-c5d8ffda9d73.jpeg" width= "750px" />
</div>

## 

#### Mapeando agregações:
- Valem as mesmas regras.
- Porém, ao mapear o tipo relacionamento do qual a abstração de agregação participa, usualmente, cria-se uma nova relação que recebe uma chave primária adequada proveniente do mapeamento obtido para o conteúdo da agregação e a chave primária do outro tipo entidade participante do relacionamento.

_______________________________________________________________________________________________________________________________________________________
    
      
Link útil: 
[Banco de dados, o que é, os tipos e a importância para o site da sua empresa](https://rockcontent.com/br/blog/banco-de-dados/) 


