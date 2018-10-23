# bancoAv2
create schema bancoDeDados2
use bdTr2

create table fornecedores ( fnr int primary key auto_increment,
                            Nome varchar(30) not null,
                            situacao char not null,
                            cidade varchar(30) not null);
create table projetos (jnr int primary key auto_incremente,
                       nome varchar(30) not null,
                       cidade varchar(30) not null);
-- drop table projetos;

create table pecas(pnr int primary key auto_increment,
				   nome varchar(30) not null,
                   cor varchar(30) not null,
                   peso int not null,
                   cidade varchar(50) not null);		

-- drop table pecas;
                   
create table malote(fnr int, jnr int, pnr int, qtd int not null, 
					foreign key(pnr) references pecas(pnr), 
                    foreign key(jnr) references projetos(jnr),
                    foreign key(fnr) references fornecedores(fnr),
                    primary key(jnr,pnr,fnr));             -- Nota pra mim, pode fazer referencia na ultima linha des instrução

-- drop table malote;
-- Criação do banco e tabelas termina aqui

insert into fornecedores(Nome, situacao, cidade) values ('Arthur', 'a', 'Fortaleza'),
														                            ('Bruno', 'b', 'Fortaleza'),
                                                        ('Carlos', 'c', 'Fortaleza'),
                                                        ('Dario', 'd', 'Caracas'),
                                                        ('Eduardo', 'e', 'Clinton'),
                                                        ('Felipe', 'f', 'Bariloche'),
                                                        ('Guilherme', 'g', 'Whashington'),
                                                        ('Groot', 'g', 'Whashington'),
                                                        ('Tom Hanks', 'g', 'Benton Harbor'),
                                                        ('Obama', 'd', 'Novi'),
                                                        ('Clint Eastwood', 'e', 'Saginaw'),
                                                        ('Bee Vang', 'a', 'Flint'),
                                                        ('Ahney Her', 'a', 'Detroit'),
                                                        ('Selton Mello', 'a', 'Passos'),
                                                        ('Scott Eastwood', 'a', 'California'),
                                                        ('Matheus Nachtergaele', 'a', 'São Paulo,'),
                                                        ('Fernanda Montenegro', 'a', 'Rio de Janeiro'),
                                                        ('Marco Nanini', 'a', 'Recife'),
                                                        ('Denise Fraga', 'a', 'Rio de Janeiro'),
                                                        ('Lima Duarte', 'a', 'Sacramento'),
                                                        ('Luís Melo', 'a', 'Curitiba'); -- 21 itens
insert into fornecedores(Nome, situacao, cidade) values ('Larissa Maria', 'a', 'Fortaleza'); -- 22 itens
insert into fornecedores(Nome, situacao, cidade) values ('Lorena Cavalcanti', 'c', 'California'); -- 23 itens
insert into fornecedores(nome, situacao, cidade) values ('Larissa Melo', 'f', 'Lorena'); -- 24 itens
insert into fornecedores(nome, situacao, cidade) values ('F1', 'f', 'Fortaleza'); -- 25 itens
update fornecedores set cidade = 'Curitiba' where fnr = 2;
update fornecedores set cidade = 'Recife' where fnr = 3;


select * from fornecedores;

insert into pecas(nome, cor, peso, cidade) values ('Cambio de marcha', 'preto', 3.7, 'California'),
													('Volante', 'branco', 2.1, 'Fortaleza'),
                                                    ('Poltrona', 'cinza', 11.3, 'Curitiba'),
                                                    ('Motor', 'preto', 3.7, 'California'),
                                                    ('Caixa de marcha', 'preto', 3.7, 'Passos'),
                                                    ('Radio', 'preto', 2, 'Rio de Janeiro'),
                                                    ('Pneu', 'amarelo', 8.15, 'Sacramento'),
                                                    ('Maçaneta', 'prata', 1.2, 'Detroit'),
                                                    ('Disco de freio', 'prata', 5, 'Clinton'),
                                                    ('Sensor de ré', 'roxo', 0.7, 'Clinton'),
                                                    ('Calota', 'azul', 1, 'Clinton'),
                                                    ('Bateria', 'preto', 4.1, 'Caracas'),
                                                    ('Velocimetro', 'branco', 0.4, 'Bariloche'),
                                                    ('Alavanca de freio', 'preto', 2, 'Saginaw'),
                                                    ('Acelerador', 'rosa', 3, 'Caracas'),
                                                    ('Freio', 'verde', 3.7, 'Flint'),
                                                    ('Embreagem', 'branco', 3.7, 'Benton Harbor'),
                                                    ('Vidro', 'SEM COR', 3.7, 'Benton Harbor'),
                                                    ('Porta-luvas', 'preto', 3.7, 'Fortaleza'),
                                                    ('Parabrisa', '', 1, 'Fortaleza'); -- 20 itens
insert into pecas(nome, cor, peso, cidade) value ('Cambio de marcha', 'preto', 8.0, 'California');
insert into pecas(nome, cor, peso, cidade) value ('Cambio de marcha', 'roxo', 8.0, 'Fortaleza');
insert into pecas(nome, cor, peso, cidade) values ('Copo descartavel', 'azul-marinho', 0.09, 'Lorena');
insert into pecas(nome, cor, peso, cidade) values ('P1', 'azul-marinho', 10, 'Lorena'); -- 25 itens (Não pergunte pq 25)

-- delete from pecas where pecas.pnr = 8;
-- delete from pecas where pecas.pnr = 21;
-- insert into pecas(pnr, nome, cor, peso, cidade) values (8,'Maçaneta', 'prata', 1.2, 'Detroit');

update pecas set cor = 'branco' where pnr = 18;
update pecas set cor = 'prata' where pnr = 20;
           
select * from pecas;           
           
insert into projetos(nome, cidade) values ('Carro', 'California' ),
										('Aviao', 'California' ),
                                        ('X1', 'Fortaleza' ),
										('X2', 'Benton Harbor' ),
                                        ('X3', 'Detroit' ),
                                        ('X4', 'Rio de Janeiro' ),
                                        ('X5', 'California' ),
										('X6', 'Caracas' ),
										('Y1', 'Benton Harbor' ); 

insert into projetos( nome, cidade) values( 'J1', 'Rio de Janeiro');
insert into projetos( nome, cidade) values( 'J2', 'Lorena');
insert into projetos( nome, cidade) values( 'J3', 'Fortaleza');
insert into projetos( nome, cidade) values( 'J4', 'Lorena');
select * from projetos;

insert into malote(fnr, jnr, pnr,qtd) values(1, 1,1,30),  -- fornecedor(fnr) / projeto(jnr) / peça(pnr)
											                      (1, 1,2,10),
                                            (2, 1,3,23),
                                            (2, 1,4,90),
                                            (3, 1,5,954),
                                            (3, 1,6,51),
                                            (4, 1,7,61),
                                            (4, 2,1,83),
                                            (4, 2,2,9),
                                            (4, 2,3,7),
                                            (5, 1,1,340),
											                      (5, 1,2,3500),
                                            (5, 1,3,500),
                                            (5, 1,4,432),
                                            (5, 1,5,699),
                                            (5, 1,6,100),
                                            (5, 1,7,340),
                                            (5, 2,4,19),
                                            (6, 1,1,10),
                                            (6, 1,2,1000),
                                            (6, 1,3,632),
                                            (6, 1,4,340),
                                            (6, 1,5,555),
                                            (6, 2,5,99),
                                            (7, 2,6,66),
                                            (8, 2,7,30);  
                                            
insert into malote(fnr, jnr, pnr,qtd) values(1, 2,1,30);    

insert into malote(fnr, jnr, pnr,qtd) values(1, 3,1,30);
insert into malote(fnr, jnr, pnr,qtd) values(1, 4,1,120);
insert into malote(fnr, jnr, pnr,qtd) values(1, 5,1,900);
insert into malote(fnr, jnr, pnr,qtd) values(1, 6,1,351);

insert into malote(fnr, jnr, pnr,qtd) values(2, 2,1,43);
insert into malote(fnr, jnr, pnr,qtd) values(2, 3,1,45);
insert into malote(fnr, jnr, pnr,qtd) values(2, 4,1,444);
insert into malote(fnr, jnr, pnr,qtd) values(2, 5,1,100);
insert into malote(fnr, jnr, pnr,qtd) values(2, 6,1,3);

insert into malote(fnr, jnr, pnr,qtd) values(22, 12,22,340);
insert into malote(fnr, jnr, pnr,qtd) values(22, 10,5,300);
insert into malote(fnr, jnr, pnr,qtd) values(23, 11,15,421);
insert into malote(fnr, jnr, pnr,qtd) values(24, 1,11, 500);
insert into malote(fnr, jnr, pnr,qtd) values(24, 10,11, 500);
insert into malote(fnr, jnr, pnr, qtd) values(24, 11, 24, 730);
insert into malote(fnr, jnr, pnr,qtd) values(24, 12,11, 500);
insert into malote(fnr, jnr, pnr,qtd) values(25, 6,5, 500);

insert into malote(fnr, jnr, pnr,qtd) values(25, 6,25, 920);
insert into malote(fnr, jnr, pnr,qtd) values(25, 7,25, 250);  



select * from malote;    
                               
 use bdTr2;
 -- Questão 01. Obter detalhes completos de todos os projetos.
  select * from projetos;
 
 -- Questão 02. Obter detalhes completos de todos os projetos em Lorena(Lorena é uma cidade).
 - SELECT * FROM Projetos WHERE cidade = 'Lorena' ;
 
 select count(qtd) from malote;
 -- questão 3. Obter números de fornecedores para aqueles que fornecem peças para o projeto J1.
 
 select count(fornecedores.Nome) from fornecedores  
 inner join malote on malote.fnr = fornecedores.fnr
 inner join pecas on malote.pnr = pecas.pnr
 inner join projetos on projetos.jnr = malote.jnr
 where projetos.nome = 'J1';
 
 -- questão 4. Obter todos os malotes onde a quantidade estiver na faixa de 300 a 750 inclusive.

select * from malote where qtd between 300 and 750;
 
 -- questão 5. Obter uma lista de todas as combinações cor-cidade de peças, com os pares em duplicata sendo eliminados.

select distinct cor,cidade from pecas order by cor;
 
 -- questão 06. Obter todos os malotes onde a quantidade não for nula.
select * from malote where qtd is not null;

-- questão 07. Obter os números de projeto e cidade onde a cidade tenha um “o” como segunda letra de seu nome.

select * from projetos where cidade like '_o%'; 

-- questão 08. Obter todas as combinações de triplas fornecedor/peça/projeto quando o fornecedor, peça e projeto 
-- estiverem localizados em uma mesma cidade.

select fornecedores.Nome, fornecedores.cidade,pecas.nome, pecas.cidade, projetos.nome,projetos.cidade from fornecedores 
inner join malote on malote.fnr = fornecedores.fnr
inner join pecas on malote.pnr = pecas.pnr
inner join projetos on malote.jnr = projetos.jnr
where fornecedores.cidade = pecas.cidade and fornecedores.cidade = projetos.cidade;

-- questão 09. Obter todas as combinações de triplas fornecedor/peça/projeto quando o fornecedor, peça e projeto 
-- não estiverem localizados em um mesma cidade.


select fornecedores.Nome, fornecedores.cidade,pecas.nome, pecas.cidade, projetos.nome,projetos.cidade from fornecedores 
inner join malote on malote.fnr = fornecedores.fnr
inner join pecas on malote.pnr = pecas.pnr
inner join projetos on malote.jnr = projetos.jnr
where fornecedores.cidade != pecas.cidade and fornecedores.cidade != projetos.cidade and pecas.cidade != projetos.cidade
order by fornecedores.cidade;

-- questão 11. Obter os números de peças para as peças fornecidas por fornecedores em Lorena.(usar count inner join entre tabela peças e tabela fornecedores)


select count(malote.qtd) as quantidade_total from malote
inner join pecas on malote.pnr = pecas.pnr
inner join fornecedores on fornecedores.fnr = malote.fnr
inner join projetos on malote.jnr = projetos.jnr
where projetos.cidade = 'Lorena';

-- questao 12. Obter os números de peças para as peças fornecidas por fornecedores em Lorena para projetos em Lorena.

select sum(malote.qtd) from malote 
inner join fornecedores on fornecedores.fnr = malote.fnr
inner join projetos on malote.jnr = projetos.jnr
where fornecedores.cidade = 'Lorena' and projetos.cidade = 'Lorena';

select * from fornecedores
inner join malote on malote.fnr = fornecedores.fnr
inner join projetos on malote.jnr = projetos.jnr
where fornecedores.cidade = 'Lorena' and projetos.cidade = 'Lorena'; -- esse aqui é tira prova

-- S13. Obter todos os pares de cidades de modo que o fornecedor da primeira cidade forneça peças para um projeto da segunda cidade.

SELECT fornecedores.cidade as Primeira_cidade, 
projetos.cidade as Segunda_cidade  
FROM fornecedores 
INNER JOIN malote on malote.fnr = fornecedores.fnr
INNER JOIN pecas on malote.pnr = pecas.pnr
INNER JOIN projetos on malote.jnr = projetos.jnr
WHERE fornecedores.cidade <> projetos.cidade  -- ' <> ' é a mesma coisa que ' != '
AND pecas.cidade = fornecedores.cidade
GROUP BY Primeira_cidade;

select fornecedores.fnr as ID_FORNECEDOR, 
fornecedores.cidade as CIDADE_FORNECEDOR,
projetos.jnr as ID_PROJETO,
projetos.cidade as CIDADE_PROJETO
from fornecedores
INNER JOIN malote on malote.fnr = fornecedores.fnr
INNER JOIN pecas on malote.pnr = pecas.pnr
INNER JOIN projetos on malote.jnr = projetos.jnr
WHERE fornecedores.cidade <> projetos.cidade  
AND pecas.cidade = fornecedores.cidade; 


-- S14. Obter os números de peças para aquelas que forem fornecidas a qualquer projeto por fornecedor na mesma cidade desse projeto.

select pecas.pnr as ID_PECAS 
from pecas
inner join malote on malote.pnr = pecas.pnr
inner join fornecedores on malote.fnr = fornecedores.fnr
inner join projetos on malote.jnr = projetos.jnr
where fornecedores.cidade = projetos.cidade
group by pecas.pnr;

- S15. Obter os números de projetos fornecidos por pelo menos um fornecedor que não esteja na mesma cidade do projeto.

/*select * from projetos
inner join malote on malote.pnr = projetos.jnr
inner join fornecedores on malote.fnr = fornecedores.fnr
inner join pecas on malote.pnr = pecas.pnr
where fornecedores.cidade != projetos.cidade; */

select fornecedores.fnr as ID_FORNECEDOR, count(*) as TOTAL
from fornecedores 
inner join malote on fornecedores.fnr = malote.fnr
inner join projetos on projetos.jnr = malote.jnr
where fornecedores.cidade <> projetos.cidade
group by fornecedores.fnr asc;  -- ordena do menor para o maior


- S16. Obter os números de peças de modo que algum fornecedor forneça ambas as peças indicadas.


select pecas.pnr as ID_PECAS 
from pecas
inner join malote on malote.pnr = pecas.pnr
inner join fornecedores on malote.fnr = malote.fnr
where fornecedores.fnr = pecas.pnr
;

-- S17. Obter o número total de projetos fornecidos por F1.

select count(p.jnr) 
from projetos as p
inner join malote 
on malote.jnr = p.jnr
inner join fornecedores 
on malote.fnr = fornecedores.fnr
where fornecedores.nome = 'F1';

-- S18. Obter a quantidade total da peça P1 fornecida por F1.

select count(pecas.pnr)
from pecas
INNER JOIN malote 
ON pecas.pnr = malote.pnr
INNER JOIN fornecedores
ON malote.fnr = fornecedores.fnr
Where fornecedores.fnr = 'F1'
And Pecas.pnr = 'P1';

select sum(malote.qtd) from malote
inner join pecas on malote.pnr = pecas.pnr
inner join fornecedores on fornecedores.fnr = malote.jnr
where fornecedores.fnr = malote.fnr and pecas.pnr = malote.pnr;

-- S19. Para cada peça sendo fornecida a um projeto, obter o número da peça, o número do projeto e a quantidade total correspondente.

select pecas.pnr as peça, projetos.jnr as ID, 
sum(malote.qtd) as total
from pecas
INNER JOIN malote 
ON pecas.pnr = malote.pnr 
INNER JOIN projetos
ON malote.jnr = projetos.jnr; 

-- S20. Obter os números de projetos para todos os projetos cuja cidade seja a primeira em ordem alfabética.

select count(projetos.jnr) as Quantidade, projetos.cidade
from projetos
order by projetos.Cidade asc
limit 1;

-- S21. Obter os números de projetos fornecidos com a peça P1 em uma quantidade média maior que a maior quantidade em que qualquer peça é ornecida ao projeto J1

   SELECT COUNT(Projetos.jrn) AS qtd, avg(Malotes.qtd) AS Media FROM Malotes
   INNER JOIN Projetos ON Projetos.jrn = Malotes.jnr INNER JOIN Pecas ON Pecas.pnr =
   Malotes.pnr WHERE Pecas.pnr = 1 and Projetos.jrn = 1 HEVING avg(Malotes.qtd) >
   (SELECT MAX(qtd) FROM Malotes);

-- S22. Obter os números de fornecedores que forneçam para algum projeto a peça P1 em uma quantidade maior que a quantidade média em que a peça P1 é fornecida para esse projeto.(não tem resposta)

