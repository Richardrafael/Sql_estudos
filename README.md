# Sql_estudos
Repositório para estudo de SQL 
Create database cadastro  default character set utf8 default collate utf8_general_ci ;
cria um banco com caracteres especificos no cado utf8 <br>

Create Table pessoas ( 
id int not null  AUTO_Increment, <br>
nome varchar(30) NOT null , <br>
nascimento date,<br>
sexo enum('M','F'),<br>
peso decimal(5,2) ,<br>
altura decimal (3,2) ,<br>
nacionalidade varchar(20) DEFAULT 'Brasil' ,<br>
Primary key (id)<br>
) default Charset = utf8;<br>


Insert into pessoas values <br>
(default , 'GodoFredo' , '1984-01-02', 'M' , '78.5' , '1.83' , 'Brasil');<br>

## column não é obrigatorio 
Alter table pessoas add column profissao varchar(10);<br>
Alter table pessoas drop column profissao;<br>
Alter table pessoas add column profissao varchar(10) after nome;<br>
Alter table pessoas add codigo int first ;<br>
Alter table pessoas Modify profissao varchar(20) not null default "";<br>
Alter table pessoas change profissao prof varchar(20);<br>
Alter table pessoas rename to gafanhotos;<br>
Alter table cursos Modify nome varchar(30) not null unique;<br>
Alter table cursos Modify carga int unsigned;<br>

update cursos set nome = 'php', descricao ='curso php'  where idcurso = '2' limit = '1';<br>
delete from cursos where idcurso='3';<br>
truncate cursos ;<br>


select * from cursos order by nome ;<br>
select * from cursos order by nome desc; <br>
select nome , ano  from cursos order by nome ;<br>
select * from cursos  where ano = '2023' order by nome ;<br>
select * from cursos where ano <= '2015' order by nome ; <br>
select * from cursos where ano <> '2015' order by ano , nome ; <br>
select * from cursos where ano between 2014 and 2016 order by ano desc, nome;<br>
select * from cursos where ano in (2014 , 2016 ) order by ano ; <br>
select * from cursos where carga > 35 and totaulas < 30;<br>
select * from cursos where carga > 35 or totaulas < 30;<br>
select * from cursos where nome like 'a%';<br>
select * from cursos where nome like '%a';<br>
select * from cursos where nome like '%a%';<br>
select * from cursos where nome not like '%a%';<br>
select * from cursos where nome like 'a_%';<br>

## pega todas as opções 
select distinct ano from cursos;<br>
## conta registros  
select count(*) from cursos where carga > 30;<br>
## pega o maior 
select max(totaula) from cursos ;<br>
select max(totaula) from cursos where ano = '2013';<br>
## pega o menor
select nome ,min(totaul) from cursos ; <br>
## resultado é soma 
select sum(totaulas) from cursos; <br>
## resultado  é media 
select Avg(totaulas) from cursos; <br>
## Exercios curso em video
select * from gafanhotos where nome = 'gafanhota';<br>
select * from gafanhotos where ano between 2000  and 2015;<br>
select * from gafanhotos where nascimento between 1999 and 2016;<br>
select * from gafanhotos where sexo = 'M' and profisao = 'Programadores';<br>
select * from gafanhotos where sexo = 'F' and nacionalidade = 'Brasil' and  nome like "j%" ;<br>
select * from gafanhotos where sexo = 'M' and nome like "%silva%" and nacionalidade not like <br>"Brasil" and peso < 100;<br>
select max(altura) from gafanhotos where sexo = 'M' and nacionalidade = 'Brasil'; <br>
select Avg(peso) from gafanhotos;<br>
select min(peso) from gafanhotos where betwen 1990/01/01  and 2000/12/31 and sexo= 'F';<br>
select count(altura)  from gafanhotos where sexo = 'M' and  altura < 1.90; <br>
 
 
 ## Agrupando 
 select carga from cursos group by carga ; <br>
 select carga, count(nome) from cursos group by carga;  <br>
 select carga, count(nome) from cursos group by carga having count(nome) > 3; <br> 
 select ano , count(*) from cursos group by ano having count(ano) >= 5 order by count(*) desc;<br>
 select carga , count(*) from cursos where ano > 2015 group by carga <br>
 having carga > (select avg (carga) from cursos );<br>
## Exercicio 2
select profissoes , count(*) from gafanhotos group by profissoes;<br>
select  sexo , count(sexo) from gafanhotos where nacimento > 2005/01/01 group by sexo;<br>
select nacionalidade , nome from where not like "Brasil" group by nacionalidade  having count<br>(nacionalidade) > 3 ;<br>
select altura , count(*) from gafanhotos where peso > 100 having altura > (select avg(altura) from <br> gafanhotos ) group by altura 
