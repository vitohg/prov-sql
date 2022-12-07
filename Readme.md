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

### 01. Matricula do aluno Pedro César.

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

### 02. Retornar os nomes dos alunos e seus cursos ordenados por nome.

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
