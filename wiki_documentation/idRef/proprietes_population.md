
## Propriétés entrantes

Noter que le résultat (10 juillet 2024) se trouve [dans ce fichier](./proprietes_population_entrantes.html)

    PREFIX wdt: <http://www.wikidata.org/prop/direct/>
    PREFIX owl: <http://www.w3.org/2002/07/owl#>
    PREFIX wd: <http://www.wikidata.org/entity/>

    SELECT ?p (count(*) as ?eff)
    WHERE {  
    { SELECT DISTINCT ?uri
      WHERE {
       GRAPH <http://localhost.org/personal_db/wikidata> {
        ?si owl:sameAs ?uri.

        FILTER( CONTAINS(STR(?uri), 'idref.fr'))
          }
       }
    }
      SERVICE <https://data.idref.fr/sparql> {
        ?s ?p ?uri.
      }
    }
    GROUP BY ?p
    ORDER BY DESC(?eff)


