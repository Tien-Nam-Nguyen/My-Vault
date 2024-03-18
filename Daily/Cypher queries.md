---
type: 
tags: 
published: false
created: 2023-11-03 16:31
modified: 2023-11-05T22:46:00
folder: Daily
---
# Bước 1:  
Tạo folder neo4j tại home gồm ba folder con gồm import, conf, data

# Bước 2:
Download và đặt các file csv vào folder import

# Bước 3: 
Đặt file neo4j.conf vào folder conf với nội dung sau:

```Conf
dbms.memory.transaction.total.max=0
dbms.memory.heap.initial_size=12G
dbms.memory.heap.max_size=12G
```

# Bước 4

Chạy theo thứ tự các command sau:

```Cypher
docker run -d --name testneo4j --publish=7474:7474 --publish=7687:7687 --volume=$HOME/neo4j/data:/data --volume=$HOME/neo4j/import:/import --volume=$HOME/neo4j/conf:/conf -e NEO4J_apoc_export_file_enabled=true -e NEO4J_apoc_import_file_enabled=true -e NEO4J_apoc_import_file_use__neo4j__config=true -e NEO4J_PLUGINS=\[\"apoc\"\] neo4j
``` 

```Cypher
docker exec --interactive --tty testneo4j neo4j-admin database import full --nodes=Movie=/import/movies.csv --nodes=User=/import/users.csv --nodes=GenomeTag=/import/genome-tags.csv --relationships=RATED=/import/ratings.csv --relationships=SCORED=/import/genome-scores.csv --overwrite-destination neo4j
```

Create index
```Cypher
CREATE INDEX user_range_index_id FOR (n:User) ON (n.userId);
CREATE  INDEX movie_range_index_id FOR (n:Movie) ON (n.movieId);
CREATE INDEX rated_range_index_rating FOR ()-[r:RATED]-() ON (r.rating);
```

Set similarities
```Cypher
MATCH (u1: User {userId: "1"})-[r1:RATED]->(m: Movie)<-[r2:RATED]-(u2: User)
WITH COUNT(m) AS countMovie, u1, u2, SUM(r1.rating * r2.rating) AS DotProduct, COLLECT(r1.rating) AS rats1, COLLECT(r2.rating) AS rats2
WHERE countMovie >= 20
WITH SQRT(REDUCE(r1Dot = 0.0, a IN rats1 | r1Dot + a^2)) AS R1LENGTH,
SQRT(REDUCE(r2Dot = 0.0, b IN rats2| r2Dot + b^2)) AS R2LENGTH,
u1, u2, DotProduct, countMovie
MERGE (u1)-[s:SIMILARITY]-(u2)
ON CREATE SET s.score = DotProduct / (R1LENGTH * R2LENGTH)
ON CREATE SET s.len = countMovie
RETURN u1, u2, countMovie, s.score;
```

```Cypher
MATCH (u1: User {userId: "1"})-[s:SIMILARITY]-(u2: User)-[r:RATED]->(m: Movie)
WHERE NOT ((u1)-[:RATED]->(m))
WITH u2, s.score AS sim, s.len AS LEN, u1, collect(m)[0..3] AS recoms
RETURN sim, recoms, LEN
ORDER BY LEN DESC, sim DESC
LIMIT 5;
```

