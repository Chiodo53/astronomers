
```sparql
### Number of persons 
PREFIX wd: <http://www.wikidata.org/entity/>
PREFIX wdt: <http://www.wikidata.org/prop/direct/>

SELECT (COUNT(*) as ?n)
WHERE {
    GRAPH <https://github.com/Sciences-historiques-numeriques/astronomers/blob/main/graphs/wikidata-imported-data.md>
        {?s a wd:Q5.}
}

```

```sparql
### Number of persons 
PREFIX wd: <http://www.wikidata.org/entity/>
PREFIX wdt: <http://www.wikidata.org/prop/direct/>

SELECT ?s
WHERE {
    GRAPH <https://github.com/Sciences-historiques-numeriques/astronomers/blob/main/graphs/wikidata-imported-data.md>
        {?s a wd:Q5.}
}
LIMIT 3

```

```sparql


## Explorer les idref

PREFIX franzOption_defaultDatasetBehavior: <franz:rdf>
PREFIX wd: <http://www.wikidata.org/entity/>
PREFIX wdt: <http://www.wikidata.org/prop/direct/>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX wikibase: <http://wikiba.se/ontology#>
PREFIX bd: <http://www.bigdata.com/rdf#>

SELECT ?item ?idRef
WHERE
    {

         GRAPH <https://github.com/Sciences-historiques-numeriques/astronomers/blob/main/graphs/wikidata-imported-data.md>
   
        ## Find the persons in the imported graph
        {SELECT ?item ?birthYear
        WHERE 
                {?item a wd:Q5}
        ORDER BY ?item      
        OFFSET 0
        #OFFSET 10000
        #OFFSET 20000
       LIMIT 1000

        }
        ## 
        SERVICE <https://query.wikidata.org/sparql>
            {
                ?item wdt:P269 ?idRefId.
                BIND(URI(CONCAT('http://www.idref.fr/', ?idRefId, '/id')) as ?idRef)

            }
                
        }
ORDER BY ?birthYear 
LIMIT 5

```

```sparql
### Prepare the data to be imported
# With LIMIT clause 
## Apparently labels are not repeated if already available
# We therefore car integrate them directly in the INSERT below

PREFIX wd: <http://www.wikidata.org/entity/>
PREFIX wdt: <http://www.wikidata.org/prop/direct/>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX wikibase: <http://wikiba.se/ontology#>
PREFIX bd: <http://www.bigdata.com/rdf#>
PREFIX owl: <http://www.w3.org/2002/07/owl#>

CONSTRUCT {?item wdt:P269 ?idRef.}
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
        LIMIT 10

        }
        ## 
        SERVICE <https://query.wikidata.org/sparql>
            {
                # IdRef
                ?item wdt:P269 ?idRefId.
                BIND(URI(CONCAT('http://www.idref.fr/', ?idRefId, '/id')) as ?idRef)

            }
                
        }
```

```sparql
### Prepare the data to be imported
# With LIMIT clause 
## Apparently labels are not repeated if already available
# We therefore car integrate them directly in the INSERT below

PREFIX wd: <http://www.wikidata.org/entity/>
PREFIX wdt: <http://www.wikidata.org/prop/direct/>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX wikibase: <http://wikiba.se/ontology#>
PREFIX bd: <http://www.bigdata.com/rdf#>
PREFIX owl: <http://www.w3.org/2002/07/owl#>

WITH <https://github.com/Sciences-historiques-numeriques/astronomers/blob/main/graphs/wikidata-imported-data.md>
INSERT {?item wdt:P269 ?idRef.}
WHERE
    {
        ## Find the persons in the imported graph
        {SELECT ?item
        WHERE 
                {?item a wd:Q5.}
        ORDER BY ?item      
        #OFFSET 10000
        #OFFSET 20000
        OFFSET 30000
        LIMIT 10000

        }
        ## 
        SERVICE <https://query.wikidata.org/sparql>
            {
                # IdRef
                ?item wdt:P269 ?idRefId.
                BIND(URI(CONCAT('http://www.idref.fr/', ?idRefId, '/id')) as ?idRef)

            }
                
        }
```
### Inspect imported information

```sparql
### Basic query about number of persons per employers

PREFIX franzOption_defaultDatasetBehavior: <franz:rdf>
PREFIX wd: <http://www.wikidata.org/entity/>
PREFIX wdt: <http://www.wikidata.org/prop/direct/>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>

SELECT (COUNT(*) as ?n)
WHERE {
    GRAPH <https://github.com/Sciences-historiques-numeriques/astronomers/blob/main/graphs/wikidata-imported-data.md>
        { ?item wdt:P269 ?idRefId
         }         
}


```

```sparql
### Insert the label of the property
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX wd: <http://www.wikidata.org/entity/>
PREFIX wdt: <http://www.wikidata.org/prop/direct/>


INSERT DATA {
  GRAPH <https://github.com/Sciences-historiques-numeriques/astronomers/blob/main/graphs/wikidata-imported-data.md>
  {wdt:P269 rdfs:label 'same as IdRef'.}
}
```
## Explore IdRef available information

```sparql

  PREFIX wdt: <http://www.wikidata.org/prop/direct/>
  PREFIX owl: <http://www.w3.org/2002/07/owl#>
  PREFIX wd: <http://www.wikidata.org/entity/>

  SELECT ?idRef
  WHERE {  
    { SELECT DISTINCT ?idRef
      WHERE {
          GRAPH <https://github.com/Sciences-historiques-numeriques/astronomers/blob/main/graphs/wikidata-imported-data.md>
        { ?item wdt:P269 ?idRef
        }                   
      }
      LIMIT 5
    }
  }

      
```

```sparql

PREFIX wdt: <http://www.wikidata.org/prop/direct/>
PREFIX owl: <http://www.w3.org/2002/07/owl#>
PREFIX wd: <http://www.wikidata.org/entity/>

SELECT ?p ?o
WHERE {  
  { SELECT DISTINCT ?idRef
    WHERE {
        GRAPH <https://github.com/Sciences-historiques-numeriques/astronomers/blob/main/graphs/wikidata-imported-data.md>
      { ?item wdt:P269 ?idRef
      }                   
    }
    LIMIT 3
  }
  SERVICE <https://data.idref.fr/sparql> {
    ?idRef ?p ?o.
  }
}

```
## Inspect available information in IdRef / SUDOC
### Outgoing properties


We can observe that there is a number of instances maximum set for queries, so we observe the first 4000 persons.


The outgoing properties provide basic identification information, like names, _same as_ references to other data stores, citizenships, gender, births (as events)


[April 2025] For the time being, we do not use this information.


```sparql
### Outgoing properties
PREFIX wdt: <http://www.wikidata.org/prop/direct/>
PREFIX owl: <http://www.w3.org/2002/07/owl#>
PREFIX wd: <http://www.wikidata.org/entity/>

SELECT ?p (COUNT(*) as ?n)
WHERE {  
  { SELECT DISTINCT ?idRef
    WHERE {
        GRAPH <https://github.com/Sciences-historiques-numeriques/astronomers/blob/main/graphs/wikidata-imported-data.md>
      { ?item wdt:P269 ?idRef
      }                   
    }
    LIMIT 4000
  }
  SERVICE <https://data.idref.fr/sparql> {
    ?idRef ?p ?o.
  }
}
GROUP BY ?p
ORDER BY DESC(?n)
```
### Incoming properties


The information provided by the incoming properties (namely from the SUDOC collective catalogue of university libraries) is richer.

It is about authorship of books, being an editor, etc.

We can also see that many properties are expressed using the Library of Congress catalogue vocabulary. 

Examples of properties can be found [in this file](../Wikidata/idref_properties_20250425.csv).

In order to collect this information, and put it into a specific graph, we will use a dedicated Jupyter notebook


```sparql
### Incoming properties
# The result is stored 
# in the 'Wikidata/idref_properties_20250425.csv' file

PREFIX wdt: <http://www.wikidata.org/prop/direct/>
PREFIX owl: <http://www.w3.org/2002/07/owl#>
PREFIX wd: <http://www.wikidata.org/entity/>

SELECT ?p (COUNT(*) as ?n)
WHERE {  
  { SELECT DISTINCT ?idRef
    WHERE {
        GRAPH <https://github.com/Sciences-historiques-numeriques/astronomers/blob/main/graphs/wikidata-imported-data.md>
      { ?item wdt:P269 ?idRef
      }                   
    }
    LIMIT 4000
  }
  SERVICE <https://data.idref.fr/sparql> {
    ?s ?p ?idRef.
  }
}
GROUP BY ?p
ORDER BY DESC(?n)
```
## Inspect ABES data sources and available information

```sparql
### Resources base-URI in the ABES data repository
# substr	ns
# www.sudoc.fr	1062
# /hal.archive	608
# hub.abes.fr/	300
# www.idref.fr	163
# /zbmath.org/	50
# www.calames.	29
# www.numdam.o	22
# /orbi.uliege	13
# /archive-ouv	9





PREFIX wdt: <http://www.wikidata.org/prop/direct/>
PREFIX owl: <http://www.w3.org/2002/07/owl#>
PREFIX wd: <http://www.wikidata.org/entity/>

SELECT ?substr (STR(COUNT(*)) as ?ns) (COUNT(*) as ?n)
WHERE {  
  { SELECT DISTINCT ?idRef
    WHERE {
        GRAPH <https://github.com/Sciences-historiques-numeriques/astronomers/blob/main/graphs/wikidata-imported-data.md>
      { ?item wdt:P269 ?idRef
      }                   
    }
    LIMIT 300
  }
  SERVICE <https://data.idref.fr/sparql> {
    ?s <http://id.loc.gov/vocabulary/relators/aut> ?idRef.
    BIND (substr(str(?s), 8, 12) as ?substr)
  }
}
GROUP BY ?substr
ORDER BY DESC(?n)
```

```sparql
### Properties of SUDOC items of which the population persons
# are authors


PREFIX wdt: <http://www.wikidata.org/prop/direct/>
PREFIX owl: <http://www.w3.org/2002/07/owl#>
PREFIX wd: <http://www.wikidata.org/entity/>

SELECT ?p (COUNT(*) as ?n)
WHERE {  
  { SELECT DISTINCT ?idRef
    WHERE {
        GRAPH <https://github.com/Sciences-historiques-numeriques/astronomers/blob/main/graphs/wikidata-imported-data.md>
      { ?item wdt:P269 ?idRef
      }                   
    }
    LIMIT 1000
  }
  SERVICE <https://data.idref.fr/sparql> {
    ?s <http://id.loc.gov/vocabulary/relators/aut> ?idRef;
         ?p ?o.
    FILTER (CONTAINS(STR(?s), 'sudoc'))
  }
}
GROUP BY ?p
HAVING (?n > 20)
ORDER BY DESC(?n)
```

```sparql
### Examples of books


PREFIX wdt: <http://www.wikidata.org/prop/direct/>
PREFIX rdf:	<http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX owl: <http://www.w3.org/2002/07/owl#>
PREFIX wd: <http://www.wikidata.org/entity/>
PREFIX dcterms:	<http://purl.org/dc/terms/>
PREFIX marcrel:	<http://id.loc.gov/vocabulary/relators/>
PREFIX dc11:	<http://purl.org/dc/elements/1.1/>

SELECT DISTINCT ?s ?idRef ?author ?date ?bibliographicCitation ?dcterms_subject
WHERE {  
  { SELECT DISTINCT ?idRef
    WHERE {
        GRAPH <https://github.com/Sciences-historiques-numeriques/astronomers/blob/main/graphs/wikidata-imported-data.md>
      { ?item wdt:P269 ?idRef
      }                   
    }
    LIMIT 7
  }
  SERVICE <https://data.idref.fr/sparql> {
        ?s marcrel:aut ?idRef;
            marcrel:aut ?author;
            dc11:date	?date;
            dcterms:bibliographicCitation	?bibliographicCitation.
        FILTER (STR(?idRef) != STR(?author))
        FILTER (CONTAINS(STR(?s), 'sudoc'))
        OPTIONAL {?s dcterms:subject	?dcterms_subject}
        #OPTIONAL {?s rdf:type	?rdf_type}
        #OPTIONAL {?s dc11:subject	?dc11_subject}
    
  }
}

ORDER BY ?s ?idRef ?author ?date
```

```sparql
### Properties of journal articles of which the population persons
# are authors
## Cf. https://scienceplus.abes.fr/ 


PREFIX wdt: <http://www.wikidata.org/prop/direct/>
PREFIX owl: <http://www.w3.org/2002/07/owl#>
PREFIX wd: <http://www.wikidata.org/entity/>

SELECT ?p (COUNT(*) as ?n)
WHERE {  
  { SELECT DISTINCT ?idRef
    WHERE {
        GRAPH <https://github.com/Sciences-historiques-numeriques/astronomers/blob/main/graphs/wikidata-imported-data.md>
      { ?item wdt:P269 ?idRef
      }                   
    }
    LIMIT 1000
  }
  SERVICE <https://data.idref.fr/sparql> {
    ?s <http://id.loc.gov/vocabulary/relators/aut> ?idRef;
         ?p ?o.
    FILTER (CONTAINS(STR(?s), 'hub.abes'))
  }
}
GROUP BY ?p
ORDER BY DESC(?n)
```

```sparql
### Examples of periodical articles


PREFIX wdt: <http://www.wikidata.org/prop/direct/>
PREFIX rdf:	<http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX owl: <http://www.w3.org/2002/07/owl#>
PREFIX wd: <http://www.wikidata.org/entity/>
PREFIX dcterms:	<http://purl.org/dc/terms/>
PREFIX marcrel:	<http://id.loc.gov/vocabulary/relators/>
PREFIX dc11:	<http://purl.org/dc/elements/1.1/>

SELECT DISTINCT ?s ?idRef ?author ?date ?title ?dcterms_subject
WHERE {  
  { SELECT DISTINCT ?idRef
    WHERE {
        GRAPH <https://github.com/Sciences-historiques-numeriques/astronomers/blob/main/graphs/wikidata-imported-data.md>
      { ?item wdt:P269 ?idRef
      }                   
    }
    LIMIT 7
  }
  SERVICE <https://data.idref.fr/sparql> {
        ?s marcrel:aut ?idRef;
            marcrel:aut ?author;
            dc11:date	?date;
            dcterms:title	?title.
        FILTER (STR(?idRef) != STR(?author))
        FILTER (CONTAINS(STR(?s), 'hub.abes'))
        OPTIONAL {?s dcterms:subject	?dcterms_subject}
        #OPTIONAL {?s rdf:type	?rdf_type}
        #OPTIONAL {?s dc11:subject	?dc11_subject}
    
  }
}

ORDER BY ?s ?idRef ?author ?date
```
## Import SUDOC publications

```sparql
### Examples of books


PREFIX wdt: <http://www.wikidata.org/prop/direct/>
PREFIX rdf:	<http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX owl: <http://www.w3.org/2002/07/owl#>
PREFIX wd: <http://www.wikidata.org/entity/>
PREFIX dcterms:	<http://purl.org/dc/terms/>
PREFIX marcrel:	<http://id.loc.gov/vocabulary/relators/>
PREFIX dc11:	<http://purl.org/dc/elements/1.1/>

SELECT DISTINCT ?s ?idRef
WHERE {  
  { SELECT DISTINCT ?idRef
    WHERE {
        GRAPH <https://github.com/Sciences-historiques-numeriques/astronomers/blob/main/graphs/wikidata-imported-data.md>
      { ?item wdt:P269 ?idRef
      }                   
    }
    LIMIT 7
  }
  SERVICE <https://data.idref.fr/sparql> {
        ?s marcrel:aut ?idRef.
    FILTER (CONTAINS(STR(?s), 'sudoc'))
  }
}
ORDER BY ?s ?idRef 
```
