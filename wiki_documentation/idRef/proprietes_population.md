
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


### Références bibliographiques

    PREFIX wdt: <http://www.wikidata.org/prop/direct/>
    PREFIX owl: <http://www.w3.org/2002/07/owl#>
    PREFIX wd: <http://www.wikidata.org/entity/>
    SELECT ?s ?p ?o
      # SELECT ?p (count(*) as ?eff)
      WHERE {  
      { SELECT DISTINCT ?uri
        WHERE {
          GRAPH <http://localhost.org/personal_db/wikidata> {
          ?si owl:sameAs ?uri.
          FILTER( CONTAINS(STR(?uri), 'idref.fr'))
            }
          }
      LIMIT 300
      }
        SERVICE <https://data.idref.fr/sparql> {
          ?s <http://id.loc.gov/vocabulary/relators/aut> ?uri;
              a 	<http://purl.org/ontology/bibo/Book>;
              <http://purl.org/dc/terms/bibliographicCitation> ?o.      }
      }
      #GROUP BY ?p
    ORDER BY ?s



### Auteurs

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
    LIMIT 100
    }
      SERVICE <https://data.idref.fr/sparql> {
        ?s <http://id.loc.gov/vocabulary/relators/aut> ?uri;
           ?p ?o.      }
    }
    GROUP BY ?p
    ORDER BY DESC(?eff)