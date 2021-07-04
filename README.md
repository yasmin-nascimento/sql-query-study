# Guia Básico de consultas para o Comando SELECT :D

Este guia foi criado para auxiliar iniciantes que desejem aprender a realizar consultas básicas em banco de dados SQL.

## O que significa a sigla SQL?

A sigla SQL significa, Linguagem de Consulta Estruturada ou em inglês, Structured Query Language. É uma linguagem de consulta para Banco de Dados Relacional, você pode checar mais informações [aqui](https://pt.wikipedia.org/wiki/Banco_de_dados_relacional). Para saber mais sobre o que é o SQL, você pode dar uma olhada nas [referências](#referências) no final ou clicando neste [link](https://www.alura.com.br/artigos/o-que-e-sql).

## Conteúdo

* [SQL SELECT](#sql-select)
* [SQL SELECT Distinct](#sql-distinct)
* [SQL WHERE](#sql-where)
  * [Operadores em Where](#operadores-em-where)
* [SQL AND, OR e NOT](#sql-and-or-e-not)
* [SQL ORDER BY](#sql-order-by)
* [SQL SELECT TOP](#sql-select-top)
* [SQL MIN() e MAX()](#sql-min-e-max)
* [SQL Count, Avg, Sum](#sql-count-avg-sum)
* [SQL LIKE](#sql-like)
* [SQL BETWEEN](#sql-between)
* [SQL ALIASES](#sql-aliases)
* [SQL JOINS](#sql-joins)
  * [Diferentes tipos de JOINS](#diferentes-tipos-de-joins)
* [Para praticar](#para-praticar)
* [Referências](#referências)

 ## SQL SELECT

O SELECT é utilizado para selecionar dados a partir de um banco de dados. Você pode especificar as colunas que serão selecionadas ou utilizar o arterisco para selecionar todas as colunas da tabela em que você deseja realizar uma consulta.

~~~~sql
SELECT coluna1, coluna2 FROM nome_tabela
~~~~
~~~~sql
SELECT * FROM nome_tabela
~~~~

  ## SQL DISTINCT
  
O SELECT DISTINCT é utilizado para retornar somente valores distintos/diferentes de uma tabela, a coluna pode ter dados duplicados; e algumas vezes você só quer que seja listados os dados distintos.

~~~~sql
SELECT DISTINCT coluna1, coluna2 FROM nome_tabela
~~~~

  ## SQL WHERE

O WHERE é utilizado para  realizar filtros específicos a partir de uma condição.

Nos dois últimos exemplos está sendo feita uma seleção de todas as colunas da tabela **Clientes**, com alguns filtros aplicados, onde primeiramente é filtrado todos os clientes que possuem o valor do País igual a Brasil e no ultimo exemplo, um filtro onde o cliente possui o código identificador igual a 1.

Sintaxe WHERE

~~~~sql
SELECT coluna1, coluna2 FROM nome_tabela WHERE condicao
~~~~
~~~~sql
SELECT * FROM Clientes WHERE País = 'Brasil'
~~~~
~~~~sql
SELECT * FROM Clientes WHERE ClienteID = 1
~~~~

Com o WHERE você pode utilizar operadores lógicos para buscar por informações distintas ou definir uma range de pesquisa.
Segue abaixo um tabela com os operadores:

### Operadores em WHERE
    
| Operador | Descrição |
| --- | --- |
| = | Igual |
| > | Maior que |
| < | Menor que |
| >= | Maior igual |
| <= | Menor igual |
| <> | Não igual. Em algumas versões do SQL, o operador pode ser escrito como != |
| BETWEEN | Especifica um range |
| LIKE | Específica um pattern |
| IN | Específica multiplos possíveis valores para uma coluna |
 
Sintaxe com o uso dos operadores

~~~~sql
SELECT ClienteID, NomeCliente FROM Clientes
WHERE ClienteID >= 15 AND ClienteID <= 50
~~~~ 
 
## SQL AND, OR e NOT 
  
O WHERE ainda pode ser combinado com os operados AND, OR e NOT.
Os operadores AND e OR são utilizados para filtrar resultados baseados em mais de uma condição. Esse dois operadores retornarão os resultados, quando eles forem verdadeiros. O NOT, irá retornar o resultado quando a condição não for verdadeira.


Sintaxe AND, OR e NOT
~~~~sql
SELECT coluna1, coluna2 FROM nome_tabela 
WHERE condicao1 AND condicao2
~~~~
~~~~sql
SELECT * FROM Clientes
WHERE Cidade = 'Sao Paulo' AND Cep = 01000-123
~~~~
~~~~sql
SELECT ClienteID, NomeCliente FROM Clientes
WHERE UF = 'MG' OR (UF = 'SP' AND ClienteAtivo = 'N')
~~~~
~~~~sql
SELECT * FROM Clientes
WHERE Cidade = 'Sao Paulo' OR Cidade = 'Campinas'
~~~~
~~~~sql
SELECT * FROM Clientes
WHERE NOT Cidade = 'Sao Paulo'
~~~~
    
 ## SQL ORDER BY 
 
 A palavra-chave ORDER BY é usada para ordernar um resultado de maneira ascendente ou descendente. Por padrão, os resultados retornam de maneira ascendente. Sendo assim, para ordernar de maneira descendente é necessário usar a palavra-chave DESC após o nome da coluna que será ordenada.
 
 Sintaxe
 
 ~~~~sql
 SELECT coluna1, coluna2 FROM nome_tabela
 ORDER BY coluna1, coluna2 
 ~~~~

Sintaxe Descendente DESC

 ~~~~sql
 SELECT * FROM Clientes
 ORDER BY NomeCliente DESC
 ~~~~

Sintaxe Ascendente e Descendente

 ~~~~sql
 SELECT * FROM Clientes
 ORDER BY Pais ASC, NomeCliente DESC
 ~~~~
 
 ## SQL SELECT TOP

O SELECT TOP é utilizado quando você deseja limitar a quantidade de registros que serão retornados em uma consulta. Seu uso é útil quando você possui uma base de dados com milhares de registros. Nem todos os bancos de dados possuem suporte para esse comando.

Sintaxe
 ~~~~sql
 SELECT TOP 3 * FROM Clientes
 ~~~~
 
 Sintaxe TOP n PERCENT
 
 A seguinte sintaxe permite selecionar 50% dos resgistros da tabela "Clientes"
 ~~~~sql
 SELECT TOP 50 PERCENT * FROM Clientes
 ~~~~
 
 ## SQL MIN e MAX
 
 A função MIN() retorna o menor valor da coluna selecionada. Enquanto a função MAX(), retorna o maior valor da coluna selecionada.
 
 Sintax MIN()
 ~~~~sql
 SELECT MIN(coluna_nome)
 FROM tabela_nome
 WHERE condição
 ~~~~
 ~~~~sql
 SELECT MIN(Precos)
 FROM Produtos
 ~~~~
 
 Sintax MAX()
 ~~~~sql
 SELECT MAX(coluna_nome)
 FROM tabela_nome
 WHERE condição
 ~~~~
 ~~~~sql
 SELECT MAX(Precos)
 FROM Produtos
 ~~~~
 
 ## SQL Count, Avg, Sum
 
 A função COUNT() é utilizada para retornar o número de linhas a partir de uma determinada condição. Já a função AVG() retorna a média aritmédica de uma coluna numérica. 
 E por último, a função SUM() retorna o total de uma coluna numérica.
  
 Vale lembrar que para a função COUNT(), valores nulos não são considerados. Já para as outras duas funções, os valores nulos são ignorados.
 
 Sintaxe COUNT()
 ~~~~sql
 SELECT COUNT(nome_coluna)
 FROM nome_tabela
 WHERE condicao
 ~~~~
 ~~~~sql
 SELECT COUNT(ProdutoID)
 FROM Produtos
 ~~~~
  
 Sintaxe AVG()
 ~~~~sql
 SELECT AVG(nome_coluna)
 FROM nome_tabela
 WHERE condicao
 ~~~~
 ~~~~sql
 SELECT AVG(Preco)
 FROM Produtos
 ~~~~
 
 Sintaxe SUM()
 ~~~~sql
 SELECT SUM(nome_coluna)
 FROM nome_tabela
 WHERE condicao
 ~~~~
 ~~~~sql
 SELECT SUM(Quantidade)
 FROM DetalhePedidos
 ~~~~
 
 ## SQL LIKE
 
 O operador LIKE é usado com o WHERE para pesquisar por especificos resultados em uma coluna com informações do tipo **texto**. Por exemplo, se você deseja obter um resultado de 
 todos os clientes que começem ou terminem com uma letra específica, você deve usar o LIKE.

| Operador | Descrição |
| --- | --- |
| WHERE NomeCliente LIKE 'a%' | Encontra qualquer valor que comece com a letra "a" |
| WHERE NomeCliente LIKE '%a' | Encontra qualquer valor que termine com a letra "a |
| WHERE NomeCliente LIKE '%ou%' | Encontra qualquer valor que possua "ou" em qualquer posição |
| WHERE NomeCliente LIKE '_m%' | Encontra qualquer valor que "m" na secunda posição |
| WHERE NomeCliente LIKE 'a_%' | Encontra qualquer valor que comece com a letra "a" e possui pelo menos o tamanho de dois caracteres |
| WHERE NomeCliente LIKE 'a__%' | Encontra qualquer valor que comece com a letra "a" e possui pelo menos o tamanho de três caracteres |
| WHERE NomeCliente LIKE  'a%r' | Encontra qualquer valor que comece com a letra "a" e termine com a letra "r"|

Sintaxe 

 ~~~~sql
 SELECT * FROM Clientes
 WHERE NomeCliente LIKE 'a%'
 ~~~~
 
 O exemplo abaixo, seleciona todos os clientes da tabela NomeCliente que não começem com a letra "a". E o último por sua vez, seleciona todos os Clientes que possuem a Cidade  em que as iniciais sejam as letras, A, C e S.
 
 ~~~~sql
 SELECT * FROM Clientes
 WHERE NomeCliente NOT LIKE 'a%'
 ~~~~
 ~~~~sql
 SELECT * FROM Clientes
 WHERE Cidade LIKE '[acs]%'
 ~~~~

###### *Observação: para alguns bancos de dados, a máscara do filtro não é representada pelo símbolo %*

 ## SQL BETWEEN
 
 O operador BETWEEN seleciona valores dentro de um range especificado. O valores podem ser numéricos, texto ou datas.
 
 Sintaxe
 ~~~~sql
 SELECT NomeCliente
 FROM TabelaNome
 WHERE NomeCliente BETWEEN valor1 AND valor2
 ~~~~
 ~~~~sql
 SELECT * FROM Produtos
 WHERE Preco BETWEEN 10 AND 20
 ~~~~
 ~~~~sql
 SELECT * FROM Produtos
 WHERE NomeProduto BETWEEN 'Abacaxi' AND 'Manteiga'
 ORDER BY NomeProduto
 ~~~~
 ~~~~sql
 SELECT * FROM Pedidos
 WHERE DataPedido BETWEEN #4/01/2021# AND #4/31/2021#
 ~~~~
 
 NOT BETWEEN retorna como resultado os preços que estão foram da range 10 e 20
 
 ~~~~sql
 SELECT * FROM Produtos
 WHERE Preco NOT BETWEEN 10 AND 20
 ~~~~
 
 ## SQL ALIASES
 
 O Aliases é utilizado para dar a uma tabela/coluna em uma tabela, um nome temporário. Normalmente utilizado para tornar o nome das colunas mais legiveis.
 Esse nome temporário, só existe durante a execução da query. A palavra-chave que representa o ALIASES é **AS**.
 
 Sintaxe
  ~~~~sql
 SELECT ClienteID AS ID, NomeCliente AS Cliente
 FROM Clientes
 ~~~~
 ~~~~sql
 SELECT NomeCliente AS Cliente, NomeContato AS [Contato Pessoal]
 FROM Clientes
 ~~~~
 
  ## SQL JOINS

O JOIN é utilizado para combinar colunas de duas ou mais tabelas, baseada na relação que existem entre elas.

Por exemplo, uma tabela chamada **"Pedidos"**:

| PedidoID | ClienteID | DataPedido |
| --- | --- | --- |
| 2021001 | 50 | 01-06-2021 |
| 2021002 | 14 | 16-06-2021 |
| 2021003 | 1 | 17-06-2021 |

E uma outra tabela chamada **"Clientes"**:

| ClienteID | NomeCliente | NomeContato | Pais |
| --- | --- | --- | --- |
| 1 | Restaurante X | Maria Silva | Brasil |
| 5 | Lanchonete Brasil | Jose Souza | Colombia |
| 6 | Bar do Beto | Carla Moreno | Brasil |

Repare que "ClienteID" é uma coluna comum entre as tabelas "Pedidos" e "Cliente". Sendo assim, a relação entre essas duas tabelas se dá através dessa coluna "ClienteID".
Podemos criar a seguinte query para selecionar registros que combinem os valores das duas tabelas:

 ~~~~sql
 SELECT Pedidos.PedidoID, Clientes.NomeCliente, Pedidos.DataPedido
 FROM Pedidos
 INNER JOIN Clientes ON Pedidos.ClienteID = Clientes.ClienteID
 ~~~~

Essa query irá resultar em:

| PedidoID | NomeCliente | DataPedido |
| --- | --- | --- |
| 2021001 | Restaurante Baixo | 02-02-2021 |
| 2021052 | Ana Sorveteria | 16-06-2021 |
| 2021003 | Restaurante X | 17-06-2021 |
| 2021010 | HotDog Maia | 01-05-2021 |
| 2021035 | Acai Belem | 27-04-2021 |

  ### Diferentes tipos de JOINS
  
  Existem diferentes tipos de Joins no SQL:

   * (INNER) JOIN - retorna resultados em que combinam valores em ambas tabelas
   * LEFT (OUTER) JOIN - retorna todos os resultados da tabela da esquerda e combina os resultados a partir da tabela da direita
   * RIGHT (OUTER) JOIN - retorna todos os resultados da tabela da direita e combina os resultados a partir da tabela da esquerda
   * FULL (OUTER) JOIN - retorna todos os resultados quando existir uma combinação do lado direito ou esquerdo da tabela.


![image](https://user-images.githubusercontent.com/33867110/124308083-1c59c580-db3f-11eb-9baf-ed29e5347d53.png)


Sintaxe INNER JOIN

 ~~~~sql
 SELECT nome_coluna(s)
 FROM tabela1
 INNER JOIN tabela2 ON tabela1.nome_coluna = tabela2.nome_coluna
 ~~~~
 ~~~~sql
 SELECT Pedidos.PedidoID, Clientes.NomeCliente, Pedidos.DataPedido
 FROM Pedidos
 INNER JOIN Clientes ON Pedidos.ClienteID = Clientes.ClienteID
 ~~~~
 
 Sintaxe LEFT JOIN
 
  ~~~~sql
 SELECT nome_coluna(s)
 FROM tabela1
 LEFT JOIN tabela2 ON tabela1.nome_coluna = tabela2.nome_coluna
 ~~~~

 Sintaxe RIGHT JOIN

  ~~~~sql
 SELECT nome_coluna(s)
 FROM tabela1
 RIGHT JOIN tabela2 ON tabela1.nome_coluna = tabela2.nome_coluna
 ~~~~

Sintaxe FULL OUTER JOIN

  ~~~~sql
 SELECT nome_coluna(s)
 FROM tabela1
 FULL OUTER JOIN tabela2 ON tabela1.nome_coluna = tabela2.nome_coluna
 WHERE condicao
 ~~~~

  ~~~~sql
 SELECT Clientes.NomeCliente, Pedidos.PedidoID
 FROM Clientes
 FULL OUTER JOIN Pedidos ON Clientes.ClienteID = Pedidos.ClienteID
 ORDER BY Clientes.ClienteNome
 ~~~~
 
 ## Para praticar
 
 * [Exercícios para praticar todos os comandos acima](https://www.w3schools.com/sql/default.asp)
 
 ## Referências
   
   * [O que é o SQL? - Alura](https://www.alura.com.br/artigos/o-que-e-sql)
   * [Introdução ao SQL - W3Schools](https://www.w3schools.com/sql/sql_intro.asp)
   * [SQL Tutorial - TutorialPoint](https://www.tutorialspoint.com/sql/index.htm)
   * [SQL - Wikipédia](https://pt.wikipedia.org/wiki/SQL)
   * [SQL Count - Alura](https://www.alura.com.br/artigos/select-count-count1-e-countnome-a-batalha-dos-counts-de-sql?gclid=CjwKCAjwuIWHBhBDEiwACXQYsUlRjVAu0JFsXU8CRXxGwMftxYT6hTJn3-3FgAME9tI7zPXcZtRO1hoCRWkQAvD_BwE)
