# Récupérer les liens entre Wikidata et DBpedia



## Récupérer les liens de la version anglophone

[4 avril 2024] Effectué

    PREFIX owl: <http://www.w3.org/2002/07/owl#>
    PREFIX wd: <http://www.wikidata.org/entity/>
    PREFIX wdt: <http://www.wikidata.org/prop/direct/>
    PREFIX schema: <http://schema.org/>

    PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>

    ### indique vers quel graphe effectuer l'insertion
    ## l'URI du graphe est au choix dans un projet privé
    ## désactivé ici, on importe dans le graphe par défaut
    # WITH <http://import_uri_wikidata>

    INSERT {?item owl:sameAs  ?uri_dbpedia}
        WHERE {
        SERVICE <https://query.wikidata.org/sparql>
        {
                
                {
                {?item wdt:P106 wd:Q169470}
                UNION
                {?item wdt:P101 wd:Q413}  
            UNION 
            {?item wdt:P106 wd:Q11063}
                UNION
                {?item wdt:P101 wd:Q333} 
                UNION
                {?item wdt:P106 wd:Q155647}
                UNION
                {?item wdt:P101 wd:Q34362} 
                }
            
            
            ?item wdt:P31 wd:Q5;  # Any instance of a human.
                wdt:P569 ?birthDate.
            BIND(REPLACE(str(?birthDate), "(.*)([0-9]{4})(.*)", "$2") AS ?year)
            FILTER(xsd:integer(?year) > 1350 )

        ?article schema:about ?item .
        ?article schema:inLanguage "en" .
        FILTER (SUBSTR(str(?article), 1, 25) = "https://en.wikipedia.org/")
        BIND (URI(replace(str(?article), "https://en.wikipedia.org/wiki/", "http://dbpedia.org/resource/")) AS ?uri_dbpedia)       
                }
                }


## Vérifier les liens récupérés

    PREFIX owl: <http://www.w3.org/2002/07/owl#>
    
    SELECT ?item  ?uri_dbpedia
        WHERE {
        {?item owl:sameAs  ?uri_dbpedia}
                }




## Récupérer les liens de la version germanophone


[4 avril 2024] Effectué


    PREFIX owl: <http://www.w3.org/2002/07/owl#>
    PREFIX wd: <http://www.wikidata.org/entity/>
    PREFIX wdt: <http://www.wikidata.org/prop/direct/>
    PREFIX schema: <http://schema.org/>

    PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>

    ### indique vers quel graphe effectuer l'insertion
    ## l'URI du graphe est au choix dans un projet privé
    ## désactivé ici, on importe dans le graphe par défaut
    # WITH <http://import_uri_wikidata>

    INSERT {?item owl:sameAs  ?uri_dbpedia}
        WHERE {
        SERVICE <https://query.wikidata.org/sparql>
        {
                
                {
                {?item wdt:P106 wd:Q169470}
                UNION
                {?item wdt:P101 wd:Q413}  
            UNION 
            {?item wdt:P106 wd:Q11063}
                UNION
                {?item wdt:P101 wd:Q333} 
                UNION
                {?item wdt:P106 wd:Q155647}
                UNION
                {?item wdt:P101 wd:Q34362} 
                }
            
            
            ?item wdt:P31 wd:Q5;  # Any instance of a human.
                wdt:P569 ?birthDate.
            BIND(REPLACE(str(?birthDate), "(.*)([0-9]{4})(.*)", "$2") AS ?year)
            FILTER(xsd:integer(?year) > 1350 )

        ?article schema:about ?item .
        ?article schema:inLanguage "de" .
        FILTER (SUBSTR(str(?article), 1, 25) = "https://de.wikipedia.org/")
        BIND (URI(replace(str(?article), "https://de.wikipedia.org/wiki/", "http://de.dbpedia.org/resource/")) AS ?uri_dbpedia)       
                }
                }


## Vérifier les liens récupérés

    PREFIX owl: <http://www.w3.org/2002/07/owl#>
    
    SELECT ?item  ?uri_dbpedia
        WHERE {
        {?item owl:sameAs  ?uri_dbpedia}
                }



PREFIX wdt: <http://www.wikidata.org/prop/direct/>
PREFIX wd: <http://www.wikidata.org/entity/>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
PREFIX schema: <http://schema.org/>



SELECT DISTINCT ?item ?uri_dbpedia
WHERE {
SERVICE <https://query.wikidata.org/sparql>
     {
          SELECT ?item ?uri_dbpedia
          WHERE {
          
          {?item  wdt:P106 wd:Q28692502} 
          ?item wdt:P31 wd:Q5; # Any instance of a human.
               wdt:P569 ?birthDate.
          BIND(REPLACE(str(?birthDate), "(.*)([0-9]{4})(.*)", "$2") AS ?year)
          FILTER(xsd:integer(?year) > 1815 && xsd:integer(?year) < 2000)
          
          ?article schema:about ?item .
               ?article schema:inLanguage "en" .
               FILTER (SUBSTR(str(?article), 1, 25) = "https://en.wikipedia.org/")
               BIND (URI(replace(str(?article), "https://en.wikipedia.org/wiki/", "http://dbpedia.org/resource/")) AS ?uri_dbpedia)       
          
          }
     }
       
}  
