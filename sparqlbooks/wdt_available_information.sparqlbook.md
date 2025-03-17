

```sparql
### Nombre de personnes

PREFIX wd: <http://www.wikidata.org/entity/>
PREFIX wdt: <http://www.wikidata.org/prop/direct/>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>

SELECT (COUNT(*) as ?n)
WHERE {
    GRAPH <https://github.com/Sciences-historiques-numeriques/astronomers/blob/main/Wikidata/graph/imported-data.md>
        {?s a wd:Q5
          }
}
```

```sparql
### Propriétés des personnes

PREFIX wd: <http://www.wikidata.org/entity/>
PREFIX wdt: <http://www.wikidata.org/prop/direct/>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>

SELECT ?p (COUNT(*) as ?n)
WHERE {
    GRAPH <https://github.com/Sciences-historiques-numeriques/astronomers/blob/main/Wikidata/graph/imported-data.md>
        {?s a wd:Q5;
            ?p ?o.
          }
}
GROUP BY ?p
ORDER BY DESC(?n)
```
