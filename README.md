# Sql_estudos
Repositório para estudo de SQL 
Create database cadastro  default character set utf8 default collate utf8_general_ci ;
cria um banco com caracteres especificos no cado utf8 

Create Table pessoas ( 
id int not null  AUTO_Increment,
nome varchar(30) NOT null , 
nascimento date,
sexo enum('M','F'),
peso decimal(5,2) ,
altura decimal (3,2) ,
nacionalidade varchar(20) DEFAULT 'Brasil' ,
Primary key (id)
) default Charset = utf8;


Insert into pessoas values 
(default , 'GodoFredo' , '1984-01-02', 'M' , '78.5' , '1.83' , 'Brasil');

## column não é obrigatorio 
Alter table pessoas add column profissao varchar(10);
Alter table pessoas drop column profissao;
Alter table pessoas add column profissao varchar(10) after nome;
Alter table pessoas add codigo int first ;
Alter table pessoas Modify profissao varchar(20) not null default "";
Alter table pessoas change profissao prof varchar(20);
Alter table pessoas rename to gafanhotos;
Alter table cursos Modify nome varchar(30) not null unique;
Alter table cursos Modify carga int unsigned;

update cursos set nome = 'php', descricao ='curso php'  where idcurso = '2' limit = '1';
delete from cursos where idcurso='3';
truncate cursos ;


select * from cursos order by nome ;
select * from cursos order by nome desc; 
select nome , ano  from cursos order by nome ;
select * from cursos  where ano = '2023' order by nome ;
select * from cursos where ano <= '2015' order by nome ; 
select * from cursos where ano <> '2015' order by ano , nome ; 
select * from cursos where ano between 2014 and 2016 order by ano desc, nome;
select * from cursos where ano in (2014 , 2016 ) order by ano ; 
select * from cursos where carga > 35 and totaulas < 30;
select * from cursos where carga > 35 or totaulas < 30;
select * from cursos where nome like 'a%';
select * from cursos where nome like '%a';
select * from cursos where nome like '%a%';
select * from cursos where nome not like '%a%';
select * from cursos where nome like 'a_%';

## pega todas as opções 
select distinct ano from cursos;
## conta registros  
select count(*) from cursos where carga > 30;
##pega o maior 
select max(totaula) from cursos ;
select max(totaula) from cursos where ano = '2013';
## pega o menor
select nome ,min(totaul) from cursos ; 
## resultado é soma 
select sum(totaulas) from cursos;
## resultado  é media 
select Avg(totaulas) from cursos; 
## Exercios curso em video
select * from gafanhotos where nome = 'gafanhota';
select * from gafanhotos where ano between 2000  and 2015;
select * from gafanhotos where nascimento between 1999 and 2016;
select * from gafanhotos where sexo = 'M' and profisao = 'Programadores';
select * from gafanhotos where sexo = 'F' and nacionalidade = 'Brasil' and  nome like "j%" ;
select * from gafanhotos where sexo = 'M' and nome like "%silva%" and nacionalidade not like "Brasil" and peso < 100;
select max(altura) from gafanhotos where sexo = 'M' and nacionalidade = 'Brasil'; 
select Avg(peso) from gafanhotos;
select min(peso) from gafanhotos where betwen 1990/01/01  and 2000/12/31 and sexo= 'F';
select count(altura)  from gafanhotos where sexo = 'M' and  altura < 1.90; 
 
 
 ## Agrupando 
 select carga from cursos group by carga ; 
 select carga, count(nome) from cursos group by carga;  
 select carga, count(nome) from cursos group by carga having count(nome) > 3;  