# Guia de consultas para o Comando SELECT. :D

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
SELECT * FROM Cliente WHERE País = 'Brasil
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
    
    
