---
type:
  - Tech
tags:
  - ML
  - Neo4j
  - Graph
  - Database
  - Recommendation
published: true
created: 2023-10-26 11:05
modified: 2023-10-26T21:51:00
folder: Tech
---
# Some recommendation strategy
## Popularity recommendations (Top 10)
- The naive approach
- One size fits most
## Content based recommendations
- Step 1: collect item characteristics
- Step 2: find similar items
- Step 3: recommend similar items

- Example: similar movie genres

![Imgur](https://i.imgur.com/Bwso0UN.png)

## Collaborative filtering recommendations
- Step 1: collect user behavior
- Step 2: find similar users
- Step 3: recommend behavior taken by similar users

- Example: people with similar musical tastes

![Imgur](https://i.imgur.com/hnnP6UC.png)

# Challenges for real-time recommendations
**Make effective real-time recommendations**:
- Timing is everything in point-of-touch applications
- Base recommendations on current data, not last night's batch load
**Process large amounts of data and relationships for context**:
- Relevance is king: make the right connections
- Drive traffic: get users to do more with your application
**Accommodate new data and relationships continuously**:
- Systems get richer with new data and relationships
- Recommendations become more relevant

# Example:
## Data model
![Imgur](https://i.imgur.com/9bn0kKJ.png)

1. What are the top 25 Movies
- that i haven't seen
- with the same genres as Toy Story
- given high ratings
- by people who liked Toy Story

```Cypher
MATCH (watched:Movie {title:"Toy Story"}<-[r1:RATED]-()-[r2:RATED]->(unseen:Movie))
WHERE r1.rating > 7 AND r2.rating > 7
AND watched:genres = unseen.genres
AND NOT ((:Person {username:"max"})-[:RATED|WATCHED]->(unseen))
RETURN unseen.title, COUNT(*)
ORDER BY COUNT(*) DESC
LIMIT 25
```

2. What are the movies these 2 users have both rated?
```Cypher
MATCH (p1:Person {name:'Sherman'})-[r1:RATED]->(m:Movie),
MATCH (p2:Person {name:'Hunger'})-[r2:RATED]->(m:Movie)
RETURN m.name AS Movie,
		r1.rating AS `M.Sherman's rating`,
		r2.rating AS `M.Hunger's rating`
```

![Imgur](https://i.imgur.com/D4JzlyH.png)

3. Calculate for all Person nodes with at least one Movie between them
```Cypher
MATCH (p1:Person)-[x:RATED]->(m:Movie)<-[y:RATED](p2:Person)
WITH SUM(X.rating * y.rating) AS xyDotProduct,
	SQRT(REDUCE(xDot = 0.0, a IN COLLECT(x.rating) | xDot + a^2)) AS xLength,
	SQRT(REDUCE(yDot = 0.0, b IN COLLECT(y.rating) | yDot + b^2)) AS yLength,
	p1, p2
MERGE (p1)-[s:SIMILARITY]->(p2)
SET s.similarity = xyDotProduct/(xLength * yLength)
```


![Imgur](https://i.imgur.com/XzwdKXN.png)

4. Your nearest neighbors. Who are the
- top 5 Person and their similarity score
- ordered by similarity in descending order
- for Grace Andrews

```Cypher
MATCH (p1:Person {name: "Grace Andrews"}) ->[s:SIMILARITY]->(p2:Person)
WITH p2, s.score AS sim
ORDER BY sim DESC
LIMIT 5
RETURN p2.name AS Neighbor, sim AS Similarity
```
![Imgur](https://i.imgur.com/ry79iWF.png)

5. kNN. What are the top 25 Movie
- that Zoltan has not seen
- using the average rating
- by my top 3 neighbors

```Cypher
MATCH (m:Movie)<-[r:RATED]-(b:Person)-[s:SIMILARITY]-(p:Person {name:'Zoltan'})
WHERE NOT((p)-[:RATED]->(m))
WITH m, s.similarity AS similarity, r.rating AS ratings
WITH movie, REDUCE(s=0, i IN ratings | s + i) * 1.0/LENGTH(ratings) AS recommendation
ORDER BY recommendation DESC
RETURN moviem recommendation
LIMIT 25
```

# Dataset
<iframe
	height=420
	width=650
	src="https://github.com/caserec/Datasets-for-Recommender-Systems">
	
</iframe>