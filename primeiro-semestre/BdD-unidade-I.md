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




