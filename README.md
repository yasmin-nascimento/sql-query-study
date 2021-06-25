# Guia Básico de consultas para o Comando SELECT :D

Este guia está sendo desenvolvido para auxiliar iniciantes que desejam aprender como realizar consultas básicas em banco de dados.

## O que é o SQL?

SQL - Structured Query Language

## Tabela de Conteúdo

* SQL SELECT
* SQL SLECT Distinct
* SQL WHERE
  * Operadores em Where
* SQL AND, OR e NOT
  * Combinação dos operadores AND, OR e NOT
* SQL ORDER BY
* SQL SELECT TOP
* SQL MIN() e MAX()
* SQL LIKE
* SQL BETWEEN


 ## SQL SELECT

O SELECT é utilizado para selecionar dados a partir de um banco de dados. Você pode espeficar as colunas que serão selecionadas ou utilizar o arterisco para selecionar todas as colunas da tabela em que você deseja realizar uma consulta.

~~~~sql
SELECT coluna1, coluna2 FROM nome_tabela
~~~~
~~~~sql
SELECT * FROM nome_tabela
~~~~

  ## SQL DISTINCT
  
O SELECT DISTICT é utilizado para retornar somente valores distintos/diferentes de uma tabela, a coluna pode ter dados duplicados; e algumas vezes você só quer que seja listados os dados distintos.

~~~~sql
SELECT DISTINCT coluna1, coluna2 FROM nome_tabela
~~~~

  ## SQL WHERE

O WHERE é utilizado para filtrar especificos resultados a partir de uma condição.

~~~~sql
SELECT coluna1, coluna2 FROM nome_tabela WHERE condicao
~~~~
~~~~sql
SELECT * FROM Cliente WHERE País = 'Brasil'
~~~~
~~~~sql
SELECT * FROM Cliente WHERE ClienteID = 1
~~~~

Nos dois últimos exemplos está sendo feita uma seleção de todas as colunas da tabela Cliente, com alguns filtros aplicados, onde primeiramente é para um filtro todos os clientes que possuem o valor do País igual a Brasil e na depois um filtro onde o cliente possui o código identificador 1.

   ## Operadores em WHERE
    
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
| IN | Especifica multiplos possíveis valores para uma coluna |
    
## SQL AND, OR e NOT 
  
O WHERE pode ser combinado com os operados AND, OR e NOT.
Os operadores AND e OR são utilizados para filtrar resultados baseados em mais de uma condição. Esse dois operadores returnam os resultados quando eles são verdadeiros. O NOT, ira retornar o resultado quando a condição não for verdadeira

~~~~sql
SELECT coluna1, coluna2 FROM nome_tabela 
WHERE condicao1 AND condicao2
~~~~
~~~~sql
SELECT * FROM Cliente
WHERE Cidade = 'Sao Paulo'
AND Cep = 01000-123
~~~~

Sintaxe OR

~~~~sql
SELECT * FROM Cliente
WHERE Cidade = 'Sao Paulo'
OR Cidade = 'Campinas'
~~~~

Sintaxe NOT

~~~~sql
SELECT * FROM Cliente
WHERE NOT Cidade = 'Sao Paulo'
~~~~
    
 ## SQL ORDER BY 
 
 A palavra-chave ORDER BY é usada para ordernar um resultado de maneira ascendente ou descendente. Por padrão, os resultados retornam de maneira ascendente. Sendo assim, para ordernar de maneira descendente é necessário usar a palavra-chave DESC.
 
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

O SELECT TOP é utilizado quando você deseja limitar a quantidade de registros que serão retornados em uma consulta. Seu uso é útil quando você possui uma base de dados com milhares de registros. Nem todas os bancos de dados tem suporte para esse comando.

Sintaxe

 ~~~~sql
 SELECT TOP 3 * FROM Clientes
 ~~~~
 
 Sintaxe TOP n PERCENT
 
 A seguinte sintaxe permite selecionar 50% dos resgistros da tabela "Clientes"
 ~~~~sql
 SELECT TOP 50 PERCENT * FROM Clientes
 ~~~~
 
 ## SQL MIN() e MAX()
 
 A função MIN() retorna o menor valor da coluna selecionada. Enquanto a função MAX(), retorna o mair valor da coluna selecionada.
 
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
 
 ## SQL LIKE
 
 O operador LIKE é usando com o WHERE para pesquisar por especificos resultados em uma coluna.

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
 
 O exemplo abaixo, seleciona todos os clientes da tabela NomeCliente que não começem com a letra "a".
 
  ~~~~sql
 SELECT * FROM Clientes
 WHERE NomeCliente NOT LIKE 'a%'
 ~~~~

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
 
 O Aliases é utilizado para dar a uma tabela, coluna em uma tabela, um nome temporário. Normalmente utilizado para tornar o nome das colunas mais legiveis.
 Esse nome temporário, só existi durante a execução da query. A palavra-chave que representa o ALIASES é AS.
 
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

Repare que "ClienteID" é uma coluna comum entre as tabelas "Pedidos" e "Cliente". Sendo assim, a relação entre essas duas tabela se dá através dessa coluna "ClienteID".
Podemos criar a seguinte query para selecionar registros que combinem os valores das duas tabelas:

 ~~~~sql
 SELECT Pedidos.PedidoID, Clientes.NomeCliente, Pedidos.DataPedido
 FROM Pedidos
 INNER JOIN Clientes ON Pedidos.ClienteID=Clientes.ClienteID
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

   * (INNER) JOIN
   * LEFT (OUTER) JOIN
   * RIGHT (OUTER) JOIN
   * FULL (OUTER) JOIN




[Em desenvolvimento...]
