# Import citizenships

In this notebook we add to the imported Wikidata population properties regarding citizenship in countries

```sparql
### Number of persons in our population
PREFIX wd: <http://www.wikidata.org/entity/>
PREFIX wdt: <http://www.wikidata.org/prop/direct/>

SELECT (COUNT(*) as ?n)
WHERE {
    GRAPH <https://github.com/Sciences-historiques-numeriques/astronomers/blob/main/graphs/wikidata-imported-data.md>
        {?s a wd:Q5.}
}

```

```sparql
### Some examples
PREFIX wd: <http://www.wikidata.org/entity/>
PREFIX wdt: <http://www.wikidata.org/prop/direct/>

SELECT ?s ?label ?birthYear
WHERE {
    GRAPH <https://github.com/Sciences-historiques-numeriques/astronomers/blob/main/graphs/wikidata-imported-data.md>
        {?s a wd:Q5;
            rdfs:label ?label;
            wdt:P569 ?birthYear}
}
ORDER BY ?s
LIMIT 3

```

```sparql
### 


PREFIX wd: <http://www.wikidata.org/entity/>
PREFIX wdt: <http://www.wikidata.org/prop/direct/>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX wikibase: <http://wikiba.se/ontology#>
PREFIX bd: <http://www.bigdata.com/rdf#>

CONSTRUCT {?item wdt:P27 ?citizenship.
            ?citizenship rdfs:label ?citizenshipLabel}
WHERE
    {
        GRAPH <https://github.com/Sciences-historiques-numeriques/astronomers/blob/main/graphs/wikidata-imported-data.md>

        ## Find the persons in the imported graph
        {SELECT ?item
        WHERE 
                {?item a wd:Q5.}
        ORDER BY ?item      
        OFFSET 0
        #OFFSET 10000
        #OFFSET 20000
        LIMIT 10

        }
        ## 
        SERVICE <https://query.wikidata.org/sparql>
            {
                ?item wdt:P27 ?citizenship.
                BIND (?citizenshipLabel as ?citizenshipLabel)
                SERVICE wikibase:label { bd:serviceParam wikibase:language "en". } 
            }
                
        }
```

```sparql
### This insert query has to be carried out directly on the Allegrograph server
## Also, you have to carry it out in three steps. The accepted limit by Wikidata 
## of instances in a variable ('item' in our case) appears to be 10000.
## You therefore have to have three steps for a population of around 23000 persons  

PREFIX wd: <http://www.wikidata.org/entity/>
PREFIX wdt: <http://www.wikidata.org/prop/direct/>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>


WITH <https://github.com/Sciences-historiques-numeriques/astronomers/blob/main/graphs/wikidata-imported-data.md>
INSERT {?item wdt:P27 ?citizenship.}
WHERE
    {
        ## Find the persons in the imported graph
        {SELECT ?item
        WHERE 
                {?item a wd:Q5.}
        ORDER BY ?item      
        OFFSET 0
        #OFFSET 10000
        #OFFSET 20000
        LIMIT 10000

        }
        ## 
        SERVICE <https://query.wikidata.org/sparql>
            {
                ?item wdt:P27 ?citizenship.
            }
                
        }
```
### ??? ajouter le llabel de la propriété citizenship

```sparql
### 
PREFIX wikibase: <http://wikiba.se/ontology#>
PREFIX bd: <http://www.bigdata.com/rdf#>
PREFIX wd: <http://www.wikidata.org/entity/>
PREFIX wdt: <http://www.wikidata.org/prop/direct/>


    SELECT (COUNT(*) as ?n) 
    WHERE {
        GRAPH <https://github.com/Sciences-historiques-numeriques/astronomers/blob/main/graphs/wikidata-imported-data.md>
            {
                ?s wdt:P27 ?o.
            }
            }
    
```

```sparql
### 
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX wd: <http://www.wikidata.org/entity/>
PREFIX wdt: <http://www.wikidata.org/prop/direct/>


INSERT DATA {
  GRAPH <https://github.com/Sciences-historiques-numeriques/astronomers/blob/main/graphs/wikidata-imported-data.md>
  {wdt:P27 rdfs:label 'country of citizenship'.}
}
```

```sparql
### Get the labels of the countries or citizenships
PREFIX wikibase: <http://wikiba.se/ontology#>
PREFIX bd: <http://www.bigdata.com/rdf#>
PREFIX wd: <http://www.wikidata.org/entity/>
PREFIX wdt: <http://www.wikidata.org/prop/direct/>

CONSTRUCT  {
    ?citizenship rdfs:label ?citizenshipLabel.
}
#SELECT DISTINCT ?citizenship ?citizenshipLabel
WHERE {

    {
    SELECT DISTINCT ?citizenship
    WHERE {
        GRAPH <https://github.com/Sciences-historiques-numeriques/astronomers/blob/main/graphs/wikidata-imported-data.md>
            {
                ?s wdt:P27 ?citizenship.
            }
            }
    LIMIT 5
    }

    SERVICE <https://query.wikidata.org/sparql>
                {
                BIND (?citizenship as ?citizenship)
                BIND (?citizenshipLabel as ?citizenshipLabel)
                SERVICE wikibase:label { bd:serviceParam wikibase:language "en". } 
                }



}
```

```sparql
### 
PREFIX wikibase: <http://wikiba.se/ontology#>
PREFIX bd: <http://www.bigdata.com/rdf#>
PREFIX wd: <http://www.wikidata.org/entity/>
PREFIX wdt: <http://www.wikidata.org/prop/direct/>

WITH <https://github.com/Sciences-historiques-numeriques/astronomers/blob/main/graphs/wikidata-imported-data.md> 
INSERT  {
    ?citizenship rdfs:label ?citizenshipLabel.
}
WHERE {

    {
    SELECT DISTINCT ?citizenship
    WHERE {
            {
                ?s wdt:P27 ?citizenship.
            }
          }
    }

    SERVICE <https://query.wikidata.org/sparql>
                {
                BIND (?citizenship as ?citizenship)
                BIND (?citizenshipLabel as ?citizenshipLabel)
                SERVICE wikibase:label { bd:serviceParam wikibase:language "en". } 
                }



}
```

```sparql
### 
PREFIX wikibase: <http://wikiba.se/ontology#>
PREFIX bd: <http://www.bigdata.com/rdf#>
PREFIX wd: <http://www.wikidata.org/entity/>
PREFIX wdt: <http://www.wikidata.org/prop/direct/>


SELECT ?citizenship ?citizenshipLabel (COUNT(*) as ?n)
WHERE {
GRAPH <https://github.com/Sciences-historiques-numeriques/astronomers/blob/main/graphs/wikidata-imported-data.md>
{
   ?s wdt:P27 ?citizenship.
   ?citizenship rdfs:label ?citizenshipLabel.
}

}
GROUP BY ?citizenship ?citizenshipLabel
ORDER BY DESC(?n)
limit 20
```

```sparql
### 
PREFIX wikibase: <http://wikiba.se/ontology#>
PREFIX bd: <http://www.bigdata.com/rdf#>
PREFIX wd: <http://www.wikidata.org/entity/>
PREFIX wdt: <http://www.wikidata.org/prop/direct/>


SELECT ?item (COUNT(*) as ?n)
WHERE {
GRAPH <https://github.com/Sciences-historiques-numeriques/astronomers/blob/main/graphs/wikidata-imported-data.md>
{
   ?item wdt:P27 ?citizenship
}

}
GROUP BY ?item
HAVING (?n > 1)
ORDER BY DESC(?n)
LIMIT 5
```

```sparql
### Get the labels of the countries or citizenships
PREFIX wikibase: <http://wikiba.se/ontology#>
PREFIX bd: <http://www.bigdata.com/rdf#>
PREFIX wd: <http://www.wikidata.org/entity/>
PREFIX wdt: <http://www.wikidata.org/prop/direct/>

CONSTRUCT  {
    ?citizenship wdt:P30 ?continent.
    ?continent rdfs:label ?continentLabel.
}
#SELECT DISTINCT ?citizenship ?citizenshipLabel
WHERE {

    {
    SELECT DISTINCT ?citizenship
    WHERE {
        GRAPH <https://github.com/Sciences-historiques-numeriques/astronomers/blob/main/graphs/wikidata-imported-data.md>
            {
                ?s wdt:P27 ?citizenship.
            }
            }
    LIMIT 5
    }

    SERVICE <https://query.wikidata.org/sparql>
                {

                ?citizenship wdt:P30 ?continent.
                # BIND (?continent as ?citizenship)
                BIND (?continentLabel as ?continentLabel)
                SERVICE wikibase:label { bd:serviceParam wikibase:language "en". } 
                }



}

```

```sparql
### Get the labels of the countries or citizenships
PREFIX wikibase: <http://wikiba.se/ontology#>
PREFIX bd: <http://www.bigdata.com/rdf#>
PREFIX wd: <http://www.wikidata.org/entity/>
PREFIX wdt: <http://www.wikidata.org/prop/direct/>

WITH  <https://github.com/Sciences-historiques-numeriques/astronomers/blob/main/graphs/wikidata-imported-data.md>   
INSERT  {
    ?citizenship wdt:P30 ?continent.
    ?continent rdfs:label ?continentLabel.
}
#SELECT DISTINCT ?citizenship ?citizenshipLabel
WHERE {

    {
    SELECT DISTINCT ?citizenship
    WHERE {
            {
                ?s wdt:P27 ?citizenship.
            }
            }
    }

    SERVICE <https://query.wikidata.org/sparql>
                {

                ?citizenship wdt:P30 ?continent.
                # BIND (?continent as ?citizenship)
                BIND (?continentLabel as ?continentLabel)
                SERVICE wikibase:label { bd:serviceParam wikibase:language "en". } 
                }



}

```

```sparql
### 
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX wd: <http://www.wikidata.org/entity/>
PREFIX wdt: <http://www.wikidata.org/prop/direct/>


INSERT DATA {
  GRAPH <https://github.com/Sciences-historiques-numeriques/astronomers/blob/main/graphs/wikidata-imported-data.md>
  {wdt:P30 rdfs:label 'continent'.}
}
```
