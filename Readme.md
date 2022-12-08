# Trabalho de banco de dados SQL

## Criação das tabelas

```bash 
# Tabela aluno
```
<div align="center">
  <img src="/imgs/tb_aluno.png">
</div>

```bash 
# Code tb_aluno
create table tb_aluno (
	cod_aluno int primary key,
	nome_aluno varchar(60) not null,
	ano_nasc int,
	email varchar(60),
	sexo varchar(1) not null
)
```

```bash 
# Tabela curso
```

<div align="center">
  <img src="/imgs/tb_curso.png">
</div>

```bash 
# Code tb_curso
create table tb_curso(
	cod_curso int primary key,
	nome_curso varchar(60) not null
)
```

```bash 
# Tabela matricula
```

<div align="center">
  <img src="/imgs/tb_matricula.png">
</div>

```bash 
# Code tb_matricula
create table tb_matricula(
	cod_curso int references tb_curso(cod_curso),
	cod_aluno int references tb_aluno(cod_aluno)
)
```

## Inserção dos dados

```bash 
# Insert aluno
```

<div align="center">
  <img src="/imgs/insert_tb_aluno.png">
</div>


```bash 
# Code insert dos dados aluno
insert into tb_aluno(cod_aluno,nome_aluno,ano_nasc,email,sexo)
values(1, 'Josiel Jardim', '1974','josiel@provaSQL.com.br','M');
values(2, 'Ana Maria', '1980','ana@provaSQL.com.br','F');
values(3, 'João Pedro', '1979','joao@provaSQL.com.br','M');
```

```bash 
# Insert curso
```

<div align="center">
  <img src="/imgs/insert_tb_curso.png">
</div>

```bash 
# Code insert dos dados curso
insert into tb_curso(cod_curso, nome_curso)
values(1, 'Medicina')
values(2, 'Arquitetura')
values(3, 'Filosofia')
values(4, 'Informática')
values(5, 'Jornalismo')
```

```bash 
# Insert matricula
```

<div align="center">
  <img src="/imgs/insert_tb_matricula.png">
</div>

```bash 
# Code insert dos dados matricula
insert into tb_matricula(cod_curso, cod_aluno)
values(1, 1)
values(1, 2)
values(2, 3)
values(5, 3)
```

## Resposta das questões práticas:

>### 01. Matricula do aluno Pedro César.

<div align="center">
  <img src="/imgs/Q1_sql.png">
</div>

```bash 
# Code
insert into tb_aluno(cod_aluno,nome_aluno,ano_nasc,email,sexo)
values(4, 'Pedro César', NULL, null,'M');

## obs: Não sei linkar a chave estrangeira

insert into tb_matricula(cod_curso, cod_aluno)
values(4, 4)
```

>### 02. Retornar os nomes dos alunos e seus cursos ordenados por nome.

<div align="center">
  <img src="/imgs/Q2_sql.png">
</div>

```bash 
# Code
select tb_aluno.nome_aluno, tb_curso.nome_curso
FROM tb_aluno
INNER JOIN tb_matricula
ON tb_aluno.cod_aluno = tb_matricula.cod_aluno
INNER JOIN tb_curso
ON tb_curso.cod_curso = tb_matricula.cod_curso
```

>### 03. Retornar o email de todos maiores de idade.

<div align="center">
  <img src="/imgs/Q3_sql.png">
</div>

```bash 
# Code
select email
from tb_aluno where 2022 - ano_nasc >= 18
```

>### 04. Retorne quantos alunos tem cadastrados.

<div align="center">
  <img src="/imgs/Q4_sql.png">
</div>

```bash 
# Code
select count(cod_aluno)
from tb_aluno 
```

>### 05. Retorne quantos alunos estão cadastrados em cada curso.

<div align="center">
  <img src="/imgs/Q5_sql.png">
</div>

```bash 
# Attention
'Obs: Essa questão esta respondido de forma errada, principalmente na linha 4.
obrigado pela sua atenção'
```

```bash 
# Code
select tb_curso.nome_curso,
cod_curso + cod_aluno as numero_alunos 
from tb_curso
inner join tb_aluno
on tb_aluno.cod_aluno = tb_curso.cod_curso
```

>### 06. Retorne o nome de todos maiores que 18 anos.

<div align="center">
  <img src="/imgs/Q6_sql.png">
</div>

```bash 
# Code
select nome_aluno
from tb_aluno where 2022 - ano_nasc >= 18 
```

>### 07. Retorne os nomes de todas as mulheres.

<div align="center">
  <img src="/imgs/Q7_sql.png">
</div>

```bash 
# Code
select nome_aluno, sexo
from tb_aluno where sexo = 'F'
```

>### 08. Retorne os nomes de todas as mulheres no curso de medicina.

<div align="center">
  <img src="/imgs/Q8_sql.png">
</div>

```bash 
# Code
select tb_aluno.nome_aluno, tb_curso.nome_curso
from tb_aluno
inner join tb_curso
on tb_aluno.cod_aluno = tb_curso.cod_curso
where nome_curso = 'Medicina' and sexo = 'F'
```

>### 09. Retorne os nomes dos cusos em ordem alfabetica.

<div align="center">
  <img src="/imgs/Q9_sql.png">
</div>

```bash 
# Code
select nome_curso
from tb_curso order by nome_curso asc
```

>### 10. Criar um enunciado que utilize "junção" (como resposta).

```bash 
# Retorne os nomes, os anos de nascimento e o nome de seus respectivo curso em ordem alfabetica
```

<div align="center">
  <img src="/imgs/Q10_sql.png">
</div>

```bash 
# Code
select tb_aluno.nome_aluno, ano_nasc, tb_curso.nome_curso
from tb_aluno
inner join tb_curso
on tb_aluno.cod_aluno = tb_curso.cod_curso
order by nome_curso asc
```

## Resposta das questões teóricas:

>### 01. Defina: SQL.

```bash 
# Answer
'SQL é o acrónimo para Structured Query Languagem é uma lnguagem para acesso e manipulação de dados, principalmente para banco de 
dados RELACIONAIS'
```

>### 02.Faça um relacionamento cronológico sobre SQL.

```bash 
# Answer
O SQL foi desenvolvido originalmente no início dos anos 70 nos laboratórios da IBM. O nome originalmente da linguagem era SEQUEL, 
que significa "Structured English Query Language".
```

>### 03. Liste as principais caracteríticas de SQL.

```bash 
# Answer
'Sintaxe dos comandos o mais próximo possível da lingua natural inglesa;
Não procedimental: indica-se a informação que se pretende obter sem qualquer preocupação em "como se vai obter". O utilizador não 
se preocupa com o método de acesso aos dados que fica a cargo do SGBD;
Trabalha com conjuntos de registos e não com um registo de cada vez. Não existem comandos como "Next record" ou "Previus record";
É utilizada tanto pelos utilizadores normais como pelo DBA (Database Administrator);'
```

>### 04. Descreva a sintaxe do comando SQL: SELECT. Quais cláusulas são obrigatórias e quais são opcionais?

```bash 
# Answer
'O comando Select deve conter o nome do campo que deve ser retornado, de qual tabela e quando contêm a claúsula WHERE, as 
condições que o registro deve obedecer para retornar os valores. Uma expressão básica em SQL consiste em três cláusulas 
obrigatórias: SELECT, FROM e WHERE. A cláusula SELECT corresponde à operação de projeção da álgebra relacional. É usada para 
relacionar os atributos desejados no resultado de uma consulta. As cláusulas apcionais são: INNER JOIN, ORDER BY, GROUP BY, ASC, 
DESC.'
```

>### 05. Qual a importância da linguagem SQL no desenvolvimento de softwares atualmente? Justifique.

```bash 
# Answer
'Quem quer trabalhar com desenvolvimento de softwares precisa aprender a SQL, pois a maioria dos sistemas de informação interage 
com banco de dados, e essa é a linguagem universal para fazer qualquer coisa nos bancos de dados relacionais (o tipo de banco de 
dados mais utilizado na industria).'
```
