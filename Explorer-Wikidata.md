
## Documentation concernant les requêtes SPARQL dans Wikidata

* SPARQL Endpoint: https://query.wikidata.org
* Query builder: https://query.wikidata.org/querybuilder/?uselang=en
* [SPARQL query service/queries](https://www.wikidata.org/wiki/Wikidata:SPARQL_query_service/queries)
* [Structure of statements in Wikidata(https://www.wikidata.org/wiki/Help:Statements)]




## Chercher les astronomes dans Wikidata

    PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>

    select distinct ?item ?itemLabel ?itemDescription ?birthDate ?year ?birthPlace ?birthPlaceLabel
    where {
        ?item wdt:P31 wd:Q5;  # Any instance of a human.
            wdt:P106 wd:Q11063;
            wdt:P569 ?birthDate;
            wdt:P19 ?birthPlace.
    #    ?birthPlace wdt:P31 ?birthPlaceType.
    #   filter not exists {?birthPlace a wdno:P6}.

    BIND(REPLACE(str(?birthDate), "(.*)([0-9]{4})(.*)", "$2") AS ?year)
    FILTER(?year > '1400' && ?year < '1760')
    ### Filtrage sur les années comme entiers si souhaité
    # FILTER(xsd:integer(?year) < "890"^^xsd:integer)
    SERVICE wikibase:label { bd:serviceParam wikibase:language "en,nl" }
    }

    ORDER BY ?year

    LIMIT 500 





### Les 'assertions' (statements)

    PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>

    select distinct ?item ?itemLabel ?itemDescription ?p ?o
    where {
        ?item wdt:P31 wd:Q5;  # Any instance of a human.
            p:P106 ?statement.
            ?statement ps:P106 wd:Q11063;
                    ?p ?o.
    SERVICE wikibase:label { bd:serviceParam wikibase:language "en,nl" }
    }
    LIMIT 100 