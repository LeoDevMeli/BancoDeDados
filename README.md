# BandoDeDados

#RESOLUCAO DAS QUESTOES ESCRITAS

#O que é chamado de JOIN em um banco de dados? 
#-> JOIN é um meio de combinar colunas de uma (auto-junção) ou mais tabelas, usando valores comuns a cada uma delas.

#Nomeie e explique 2 tipos de JOIN. 
#-> INNER JOIN compara cada linha da tabela A com as linhas da tabela B para encontrar todos os pares de 
#linhas que satisfazem a condição de junção. Se a condição de junção for avaliado como TRUE, os valores da 
#coluna das linhas correspondentes das tabelas A e B serão combinados em uma nova linha e incluídos no conjunto de resultados.
#-> LEFT JOIN Retorna todos os registros da tabela esquerda e os registros correspondentes da tabela direita.

#Para que é usado o GROUP BY?
#-> reúne todas as linhas que contiverem dados em colunas especificadas e permite que funções agregadas 
#sejam executadas nestas colunas com base nos valores da coluna.

#Para que é usado o HAVING?
#-> HAVING é usada para especificar condições de filtragem em grupos de registros ou agregações.
#É frequentemente usada em conjunto com a cláusula GROUP BY para filtrar as colunas agrupadas.

#Dados os diagramas a seguir, indique a qual tipo de JOIN cada um corresponde:
#figura1 = INNER JOIN figura2 = LEFT JOIN

#Escreva uma consulta genérica para cada um dos diagramas abaixo:
#figura 1 = SELECT <select_list> FROM Tabela A RIGHT JOIN Tabela B ON A.Key = B.Key
#figura 2 = SELECT <select_list> FROM Tabela A FULL JOIN Tabela B ON A.Key = B.Key


#RESOLUCAO EXERCICIOS PRATICOS
#Mostre o título e o nome do gênero de todas as séries.
SELECT series.title, genres.name FROM series INNER JOIN genres ON series.genre_id = genres.id; 

#Mostre o título dos episódios, os nomes e sobrenomes dos atores que atuam em cada um deles.
SELECT episodes.title, actors.first_name, actors.last_name FROM episodes INNER JOIN actors ON episodes.id = actors.id;

#Mostre o título de todas as séries e o número total de temporadas que cada uma delas possui.
SELECT s.title , max(s2.`number` ) as num_tot_temp FROM series s , seasons s2  WHERE s.id = s2.serie_id  GROUP BY s.title 

#Mostre o nome de todos os gêneros e o número total de filmes de cadaum, desde que seja maior ou igual a 3.
SELECT g.name , max(m.genre_id) as num_tot_films FROM genres g , movies m   WHERE g.id = m.genre_id GROUP BY g.name HAVING COUNT(*) >= 3

#Mostre apenas o nome e o sobrenome dos atores que atuam em todos os filmes Guerra nas Estrelas e que estes não se repitam.
SELECT DISTINCT CONCAT(a.first_name,'', a.last_name) as nome_Sobrenome_actors FROM actors a, actor_movie am , movies m WHERE m.id = am.movie_id and a.id = am.actor_id and m.title like 'La Guerra de las galaxias: %'
r o modelo lógico do banco de dados de filmes criado acima.
