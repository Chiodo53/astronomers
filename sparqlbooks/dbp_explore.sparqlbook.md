# Exploration de DBpedia
## Liste de ma population

Créer la liste de la population à traiter dans DBpedia

```sparql
PREFIX dbr: <http://dbpedia.org/resource/>
PREFIX dbo: <http://dbpedia.org/ontology/>

SELECT DISTINCT ?person ?birthDate
WHERE { ?person dbo:occupation dbr:Astronomer .
    OPTIONAL { 
               ?person dbo:birthYear ?birthDate .
               }
      }
LIMIT 5

```

```sparql

```
