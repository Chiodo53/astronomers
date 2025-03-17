## Import to Allegrograph

In this notebook we describe the steps of data import to our Allegrograph repository.


The SPARQL queries are to be executed on the Allegrograph SPARQL Endpoint

First we check the basic properties of the population: name, sex, year of birth.

```sparql
PREFIX wd: <http://www.wikidata.org/entity/>
PREFIX wdt: <http://www.wikidata.org/prop/direct/>
PREFIX wikibase: <http://wikiba.se/ontology#>
PREFIX bd: <http://www.bigdata.com/rdf#>

SELECT DISTINCT ?item  ?itemLabel  ?gender ?year
        WHERE {

        ## note the service address            
        SERVICE <https://query.wikidata.org/sparql>
            {
            {?item wdt:P106 wd:Q11063}  # astronomer
            UNION
            {?item wdt:P101 wd:Q333}     # astronomy
            UNION
            {?item wdt:P106 wd:Q169470}  # physicist
            UNION
            {?item wdt:P101 wd:Q413}     # physics   
          
            ?item wdt:P31 wd:Q5;  # Any instance of a human.
                wdt:P569 ?birthDate;
                wdt:P21 ?gender.
        BIND(REPLACE(str(?birthDate), "(.*)([0-9]{4})(.*)", "$2") AS ?year)
         FILTER(xsd:integer(?year) > 1750  && xsd:integer(?year) < 1951) 

        ## Add this clause in order to fill the variable      
        BIND ( ?itemLabel as ?itemLabel)
        SERVICE wikibase:label { bd:serviceParam wikibase:language "en" }   
        }
        }
        LIMIT 10
    

```
### Preparing to import data

* Here we use the CONSTRUCT query to prepare the triples for import into a graph database.
* We limit the test to a few rows to avoid displaying thousands of them.
* Inspect and check the triplets that are generated.
* Reuse if possible the Wikidata properties 

```sparql
PREFIX wd: <http://www.wikidata.org/entity/>
PREFIX wdt: <http://www.wikidata.org/prop/direct/>
PREFIX wikibase: <http://wikiba.se/ontology#>
PREFIX bd: <http://www.bigdata.com/rdf#>

CONSTRUCT 
        {?item  rdfs:label ?itemLabel.
           ?item wdt:P21 ?gender.
           ?item wdt:P569 ?year. 
           ?item  wdt:P31 wd:Q5. }
        
        WHERE {

        ## note the service address            
        SERVICE <https://query.wikidata.org/sparql>
            {
            {?item wdt:P106 wd:Q11063}  # astronomer
            UNION
            {?item wdt:P101 wd:Q333}     # astronomy
            UNION
            {?item wdt:P106 wd:Q169470}  # physicist
            UNION
            {?item wdt:P101 wd:Q413}     # physics   
          
            ?item wdt:P31 wd:Q5;  # Any instance of a human.
                wdt:P569 ?birthDate;
                wdt:P21 ?gender.
        BIND(xsd:integer(REPLACE(str(?birthDate), "(.*)([0-9]{4})(.*)", "$2")) AS ?year)
        FILTER(?year > 1750  && ?year < 1951) 

        ## Add this clause in order to fill the variable      
        BIND ( ?itemLabel as ?itemLabel)
        SERVICE wikibase:label { bd:serviceParam wikibase:language "en" }   
        }
        }
        LIMIT 10
    

```
### Import the triples into a dedicated graph

Two import strategies are possible: 
* directly through a federated query
  * the query can be executed on a sparql-book 
  * or directly on the Allegrograph server, if it takes to much time to work through the notebook 
* execute a CONTRUCT with the complete data (without LIMIT clause) and export it to the Turtle format (suffix: .ttl)
  * then import the data into Allegrograph with the appropriate functionality


In all cases, activate in Allegrograph the 'Duplication suppression' of type SPOG, cf. menu: Repository control -> Manage duplicates -> Duplicate suppression type


The graph URI is in fact a URL pointing to a page with the description of the [imported data](../Wikidata/graph/imported-data.md)

```sparql
PREFIX wd: <http://www.wikidata.org/entity/>
PREFIX wdt: <http://www.wikidata.org/prop/direct/>
PREFIX wikibase: <http://wikiba.se/ontology#>
PREFIX bd: <http://www.bigdata.com/rdf#>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>

INSERT {

        ### Note that the data is imported into a named graph and not the DEFAULT one
        GRAPH <https://github.com/Sciences-historiques-numeriques/astronomers/blob/main/Wikidata/graph/imported-data.md>
        {?item  rdfs:label ?itemLabel.
           ?item wdt:P21 ?gender.
           ?item wdt:P569 ?year. 
           # ?item  wdt:P31 wd:Q5.
           ?item  rdf:type wd:Q5.
           }
}
        
        WHERE {

        ## note the service address            
        SERVICE <https://query.wikidata.org/sparql>
            {
            {?item wdt:P106 wd:Q11063}  # astronomer
            UNION
            {?item wdt:P101 wd:Q333}     # astronomy
            UNION
            {?item wdt:P106 wd:Q169470}  # physicist
            UNION
            {?item wdt:P101 wd:Q413}     # physics   
          
            ?item wdt:P31 wd:Q5;  # Any instance of a human.
                wdt:P569 ?birthDate;
                wdt:P21 ?gender.
        BIND(xsd:integer(REPLACE(str(?birthDate), "(.*)([0-9]{4})(.*)", "$2")) AS ?year)
        FILTER(?year > 1750  && ?year < 1951) 

        ## Add this clause in order to fill the variable      
        BIND ( ?itemLabel as ?itemLabel)
        SERVICE wikibase:label { bd:serviceParam wikibase:language "en" }   
        }
        }
        
    

```
### Correctif si la requête précédente a été réalisée avec wdt:P31 à la place de rdf:type

* rdf:tpye permet d'indiquer explicitement que wd:Q5 est un type RDF et donc vituellement une classe
* noter qu'il faut exécuter cette requête DIRECTEMENT sur le serveur Allegrograph  

```sparql
PREFIX wd: <http://www.wikidata.org/entity/>
PREFIX wdt: <http://www.wikidata.org/prop/direct/>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>

WITH <https://github.com/Sciences-historiques-numeriques/astronomers/blob/main/Wikidata/graph/imported-data.md>
DELETE {?item  wdt:P31 wd:Q5}
INSERT {?item rdf:type wd:Q5}
WHERE {
            ?item  wdt:P31 wd:Q5.
        }

```
### Verify imported triples and add labels to genders

```sparql
### Number of triples in the graph
SELECT (COUNT(*) as ?n)
WHERE {
    GRAPH <https://github.com/Sciences-historiques-numeriques/astronomers/blob/main/Wikidata/graph/imported-data.md>
        {?s ?p ?o}
}
```

```sparql
### Number of persons with more than one label : no person
SELECT (COUNT(*) as ?n)
WHERE {
    GRAPH <https://github.com/Sciences-historiques-numeriques/astronomers/blob/main/Wikidata/graph/imported-data.md>
        {?s rdf:label ?o}
}
GROUP BY ?s
HAVING (?n > 1)
```

```sparql
### Number of persons having more than one gender
PREFIX wd: <http://www.wikidata.org/entity/>
PREFIX wdt: <http://www.wikidata.org/prop/direct/>

SELECT ?s (COUNT(*) as ?n)
WHERE {
    GRAPH <https://github.com/Sciences-historiques-numeriques/astronomers/blob/main/Wikidata/graph/imported-data.md>
        {?s wdt:P21 ?gen}
}
GROUP BY ?s
HAVING (?n > 1)
```

```sparql
### Number of persons per gender
PREFIX wd: <http://www.wikidata.org/entity/>
PREFIX wdt: <http://www.wikidata.org/prop/direct/>

SELECT ?gen (COUNT(*) as ?n)
WHERE {
    GRAPH <https://github.com/Sciences-historiques-numeriques/astronomers/blob/main/Wikidata/graph/imported-data.md>
        {?s wdt:P21 ?gen}
}
GROUP BY ?gen
#HAVING (?n > 1)
```

```sparql
### Number of persons per gender
PREFIX wd: <http://www.wikidata.org/entity/>
PREFIX wdt: <http://www.wikidata.org/prop/direct/>

SELECT ?gen (COUNT(*) as ?n)
WHERE {
    GRAPH <https://github.com/Sciences-historiques-numeriques/astronomers/blob/main/Wikidata/graph/imported-data.md>
        {?s wdt:P21 ?gen}
}
GROUP BY ?gen
HAVING (?n > 1)
```

```sparql
### Number of persons per gender
PREFIX wd: <http://www.wikidata.org/entity/>
PREFIX wdt: <http://www.wikidata.org/prop/direct/>

SELECT ?gen (COUNT(*) as ?n)
WHERE {
    GRAPH <https://github.com/Sciences-historiques-numeriques/astronomers/blob/main/Wikidata/graph/imported-data.md>
        {?s wdt:P21 ?gen;
            wdt:P569 ?birthDate.
        FILTER (?birthDate < '1900')     
          }
}
GROUP BY ?gen
#HAVING (?n > 1)
```

```sparql
### Add the label to the gender

PREFIX wd: <http://www.wikidata.org/entity/>
PREFIX wdt: <http://www.wikidata.org/prop/direct/>
PREFIX wikibase: <http://wikiba.se/ontology#>
PREFIX bd: <http://www.bigdata.com/rdf#>

SELECT ?gen ?genLabel
WHERE {

    

    {SELECT DISTINCT ?gen
    WHERE {
        GRAPH <https://github.com/Sciences-historiques-numeriques/astronomers/blob/main/Wikidata/graph/imported-data.md>    
            {?s wdt:P21 ?gen}
    }
    }   

    SERVICE  <https://query.wikidata.org/sparql> {
        ## Add this clause in order to fill the variable      
        BIND(?gen as ?gen)
        BIND ( ?genLabel as ?genLabel)
        SERVICE wikibase:label { bd:serviceParam wikibase:language "en" }  
    }
}
```

```sparql
### Add the label to the gender

PREFIX wd: <http://www.wikidata.org/entity/>
PREFIX wdt: <http://www.wikidata.org/prop/direct/>
PREFIX wikibase: <http://wikiba.se/ontology#>
PREFIX bd: <http://www.bigdata.com/rdf#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>

CONSTRUCT {
     ?gen rdfs:label ?genLabel
    
} 
WHERE {

    

    {SELECT DISTINCT ?gen
    WHERE {
        GRAPH <https://github.com/Sciences-historiques-numeriques/astronomers/blob/main/Wikidata/graph/imported-data.md>    
            {?s wdt:P21 ?gen}
    }
    }   

    SERVICE  <https://query.wikidata.org/sparql> {
        ## Add this clause in order to fill the variable      
        BIND(?gen as ?gen)
        BIND ( ?genLabel as ?genLabel)
        SERVICE wikibase:label { bd:serviceParam wikibase:language "en" }  
    }
}
```

```sparql
### Add the label to the gender: INSERT

PREFIX wd: <http://www.wikidata.org/entity/>
PREFIX wdt: <http://www.wikidata.org/prop/direct/>
PREFIX wikibase: <http://wikiba.se/ontology#>
PREFIX bd: <http://www.bigdata.com/rdf#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>

WITH <https://github.com/Sciences-historiques-numeriques/astronomers/blob/main/Wikidata/graph/imported-data.md> 
INSERT {
     ?gen rdfs:label ?genLabel
    
} 
WHERE {    

    {SELECT DISTINCT ?gen
    WHERE {
        GRAPH <https://github.com/Sciences-historiques-numeriques/astronomers/blob/main/Wikidata/graph/imported-data.md>    
            {?s wdt:P21 ?gen}
    }
    }   

    SERVICE  <https://query.wikidata.org/sparql> {
        ## Add this clause in order to fill the variable      
        BIND(?gen as ?gen)
        BIND ( ?genLabel as ?genLabel)
        SERVICE wikibase:label { bd:serviceParam wikibase:language "en" }  
    }
}
```

```sparql
### Verify data insertion - using only Allegrograph data

PREFIX wd: <http://www.wikidata.org/entity/>
PREFIX wdt: <http://www.wikidata.org/prop/direct/>
PREFIX wikibase: <http://wikiba.se/ontology#>
PREFIX bd: <http://www.bigdata.com/rdf#>

SELECT ?gen ?genLabel
WHERE
{
    {
    SELECT DISTINCT ?gen
        WHERE {
            GRAPH <https://github.com/Sciences-historiques-numeriques/astronomers/blob/main/Wikidata/graph/imported-data.md>  
                    {
            ?s wdt:P21 ?gen.
            }
     }
    }    
    ?gen rdfs:label ?genLabel
    }   

```
### Prepare data to analyse

```sparql
PREFIX wd: <http://www.wikidata.org/entity/>
PREFIX wdt: <http://www.wikidata.org/prop/direct/>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>


SELECT ?s ?label ?birthDate ?gen
WHERE {
    GRAPH <https://github.com/Sciences-historiques-numeriques/astronomers/blob/main/Wikidata/graph/imported-data.md>
        {?s wdt:P21 ?gen;
            rdfs:label ?label;
            wdt:P569 ?birthDate.
          }
}
ORDER BY ?birthDate
LIMIT 10
```

```sparql
### Nombre de personnes

PREFIX wd: <http://www.wikidata.org/entity/>
PREFIX wdt: <http://www.wikidata.org/prop/direct/>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>

SELECT (COUNT(*) as ?n)
WHERE {
    GRAPH <https://github.com/Sciences-historiques-numeriques/astronomers/blob/main/Wikidata/graph/imported-data.md>
        {
          # ?s wdt:P31 wd:Q5 
          ?s a wd:Q5
          }
}
```

```sparql
### Personnes avec choix aléatoire de modalités pour variables doubles

PREFIX wd: <http://www.wikidata.org/entity/>
PREFIX wdt: <http://www.wikidata.org/prop/direct/>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>


SELECT  ?s (MAX(?label) as ?label) (xsd:integer(MAX(?birthDate)) as ?birthDate) (MAX(?gen) as ?gen)
WHERE {
    GRAPH <https://github.com/Sciences-historiques-numeriques/astronomers/blob/main/Wikidata/graph/imported-data.md>
        {?s wdt:P21 ?gen;
            rdfs:label ?label;
            wdt:P569 ?birthDate.
          }
}
GROUP BY ?s
LIMIT 10

```

```sparql
### Nombre de personnes avec propriétés de base sans doublons (choix aléatoire)

PREFIX wd: <http://www.wikidata.org/entity/>
PREFIX wdt: <http://www.wikidata.org/prop/direct/>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>

SELECT (COUNT(*) as ?n)
WHERE {
SELECT  ?s (MAX(?label) as ?label) (xsd:integer(MAX(?birthDate)) as ?birthDate) (MAX(?gen) as ?gen)
WHERE {
    GRAPH <https://github.com/Sciences-historiques-numeriques/astronomers/blob/main/Wikidata/graph/imported-data.md>
        {?s wdt:P21 ?gen;
            rdfs:label ?label;
            wdt:P569 ?birthDate.
          }
}
GROUP BY ?s
}
```
