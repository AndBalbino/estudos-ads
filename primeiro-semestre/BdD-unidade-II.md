## 1. Modelo relacional (R) 
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

## 2. Mapeamento MER -> Relacional 
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

