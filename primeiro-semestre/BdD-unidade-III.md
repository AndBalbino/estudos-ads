## BANCO DE DADOS LINGUAGEM SQL, DEFINIÇÃO E MANIPULAÇÃO DE DADOS 
Com um servidor de dados disponível e com a estruturação de tabelas e outros elementos obtidos na modelagem, um banco de dados pode ser manipulado. Para esta manipulação, existe uma linguagem própria que chamamos de SQL ( Structured Query Language ), ou Linguagem de Consulta Estruturada.

## Introdução, SQL e Álgebra Relacional
Durante a implementação de um banco de dados, de início, a modelagem é feita e, a partir daí, é necessário criar o banco de dados em si em um sistema gerenciador de banco de dados (SGBD). A forma como as tabelas foram estruturadas e os diversos outros elementos identificados na modelagem, chaves primárias, chaves estrangeiras, tipos de dados e outros, tudo isso deve ser instalado para que os usuários possam enfim usar o banco de dados para abrigar seus registros.

A SQL ( Structured Query Language ) é uma linguagem própria para o trato com os dados e pode ser empregada de forma bem variada ao operar com os componentes em um banco de dados. Ela é dividida em grupos ou subconjuntos de comandos, entre os quais dois deles serão focados neste nosso estudo, a DDL e a DML. **A DDL**, que no português seria linguagem para definição de dados (no inglês, Data Definition Language ), **contém comandos para operações como criação, alteração e exclusão de tabelas, alterações em campos, manipulação em índices, chaves e outros.** Enfim **serve para indicar como os dados estão estruturados no banco de dados.** A **DML,** linguagem de manipulação de dados (do inglês, Data Manipulation Language ), contém os **comandos para operar com os registros das tabelas, por exemplo, para recuperar, inserir, alterar ou excluir dados em uma tabela de clientes no banco de uma loja virtual.**

</span>
<div align-"center">
<img src="https://user-images.githubusercontent.com/113153237/225162735-bd8657d8-4c6e-4de3-ada7-174d0e4f9d2c.png" width= "750px" />
</div>

### Operações sobre uma Tabela:
Em uma visão bem simplificada, as operações sobre os dados terão de dar conta de como tratar as colunas e as linhas de uma tabela, considerando-se que uma tabela é um dos elementos centrais de um banco de dados.

### Álgebra Relacional:
Um banco de dados relacional tem este nome, pois, conforme Elmasri (2011), r**elação é o bloco básico na qual este tipo de banco de dados funciona.** A álgebra relacional, conforme Puga (2013), é uma linguagem formal de alto nível para expressar as operações sobre tabelas, suas linhas e colunas. **Ela engloba operações de conjuntos por exemplo: união, interseção, produto cartesiano e diferença de conjuntos; e operações chamadas relacionais de projeção, seleção, junção e divisão.**
A Álgebra Relacional é a fundamentação que permite entender como a linguagem SQL foi concebida, o que nos dá maior propriedade para compreendermos os comandos de SQL. Veremos, dessa maneira, que envolverá bastante do que discutimos anteriormente, sobre o trato com linhas e colunas de tabelas.

### Operação de SELEÇÃO (σ) para filtrar linhas:
Vamos então compreender os comandos de álgebra relacional. O primeiro deles é o de Seleção, que visa filtrar linhas da tabela conforme uma condição. Lembrando nosso exemplo anterior de selecionar os clientes com idade inferior a 40, a escrita em álgebra relacional está exposta a seguir. **A letra sigma (σ) é o símbolo que representa a operação de seleção.**  

- Exemplo:  
  
  
  σ idade < 40  (CLIENTE)  
    
Quando falamos de comandos no mundo da computação, é comum estabelecermos a sintaxe, isto é, a regra com que um comando deve ser escrito. Para este comando de seleção em álgebra relacional, a sintaxe é a exposta a seguir e indica que o comando é escrito com o símbolo σ seguido da condição e depois da relação a qual a operação se aplica.  
  
- Exemplo:   

 σ <condição>  (<Relação>)  
  
Essa operação de seleção pode ter condições combinadas com operadores lógicos como os operadores E e OU. Por exemplo, a sentença abaixo fará a seleção de linhas de pessoas com idade acima de 40 anos e que moram no Morumbi. O operador E escreve-se com “^” e o operador ou se escreve com “ ̌ “ (“circunflexo invertido”).  
   
- Exemplo:  

 σ ((idade > 40) ^ (Cidade= ‘Salvador’ )) (CLIENTE)  
  
 ### Operação de Projeção (π) para escolher colunas:
 Assim como é possível escolher as linhas, a operação de projeção permite escolher as colunas de uma determinada relação ou tabela e é representada pela letra grega Pi (π) . Também com base em nosso exemplo, para escolher as colunas de Nome e Cidade na tabela de clientes, o comando está exposto a seguir.   
   
 - Exemplo: 

π NOME, CIDADE (CLIENTE)  
  
Enquanto comando, a sintaxe da projeção é:   
  
π <lista de atributos>  (<Relação>)  
 
### Combinação de operações:
A álgebra relacional permite a combinação de operações, isto é, o resultado para uma determinada consulta é obtido pela execução de operações combinadas por meio de parênteses. No exemplo a seguir, primeiro é feita a operação de seleção (σ) para filtrar as linhas de CLIENTE. Depois é realizada a de projeção (π) para escolher as colunas que devem ser apresentadas.  
    
- Exemplo:  
    
  π NOME, CIDADE ( σ idade < 40  (CLIENTES))  
                                
Ao aplicar estas operações sobre a tabela mostrada em nosso exemplo CLIENTES, o resultado será o mostrado no Quadro: 
                              
</span>
<div align-"center">
<img src="https://user-images.githubusercontent.com/113153237/225166493-5a26dae9-08fe-47c7-9d68-d2b101deddc8.png" width= "750px" />
</div>

Alguns livros, como em Puga (2013), a notação está registrada conforme o que foi escrito até aqui, mas poderá ser encontrada também a escrita de comandos em álgebra relacional nos quais as condições ou campos das diversas operações são escritas em subscrito como a seguir.

π NOME, CIDADE ( σ idade<40  (CLIENTES))
                            
### Outras operações: 
Além dessas operações básicas, a Álgebra Relacional dispõe de diversas outras com variadas finalidades no trato com as relações.  Puga (2013) e Elmasri (2011) apresentam detalhes destas operações.  A Figura a seguir é uma adaptação de Puga (2013) com algumas outras operações relevantes de álgebra relacional presentes. Perceba que há muitos aspectos em comum com conceitos matemáticos, de teoria de conjuntos e relações. Esta é a base na qual os comandos de SQL foram concebidos.

                            
</span>
<div align-"center">
<img src="https://user-images.githubusercontent.com/113153237/225167614-d85983e8-ec05-4b4f-b04d-5f06e6bee969.png" width= "750px" />
</div>
  
</span>
<div align-"center">
<img src="https://user-images.githubusercontent.com/113153237/225167660-5e8624b6-f159-405f-b979-003b198db2dc.png" width= "750px" />
</div>
  
</span>
<div align-"center">
<img src="https://user-images.githubusercontent.com/113153237/225167707-be744c93-ac71-4790-931e-1ae6107a927d.png" width= "750px" />
</div>

## Data Definition Language (DDL)
