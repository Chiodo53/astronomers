

## Récupérer les nationalités et les importer dans une table de la base de données

    PREFIX dbr: <http://dbpedia.org/resource/>
    PREFIX dbp: <http://dbpedia.org/property/>
    PREFIX dbo: <http://dbpedia.org/ontology/>
    PREFIX rdfs:<http://www.w3.org/2000/01/rdf-schema#>
    SELECT DISTINCT (?o1 AS ?subject_uri) ?birthYear ?country ?nationality
    WHERE {
    SELECT DISTINCT ?o1 ?birthYear ?country ?nationality
    WHERE { 
        {
            {dbr:List_of_astronomers ?p ?o1.}
        UNION
            {dbr:List_of_astrologers ?p ?o1.}
        UNION
            {?o1 ?p dbr:Astrologer.}
        UNION
            {?o1 ?p dbr:Astronomer.}
        UNION
            {?o1 ?p dbr:Mathematician.}
        }
        ?o1 a dbo:Person;
        dbp:birthDate | dbo:birthDate ?birthDate.
    OPTIONAL {
    ?o1 dbo:birthPlace ?birthPlace.
    ?birthPlace a dbo:Country.
    }
    BIND(STRAFTER(STR(?birthPlace), 'http://dbpedia.org/resource/') as ?country)
    OPTIONAL {
    ?o1 dbo:nationality|dbp:nationality ?mixedNationality.
    }
    BIND(IF(
        STRSTARTS(STR(?mixedNationality), 'http://dbpedia.org/resource/'), 
        STRAFTER(STR(?mixedNationality), 'http://dbpedia.org/resource/'), 
        STR(?mixedNationality)
    ) as ?nationality)
    BIND(xsd:integer(SUBSTR(STR(?birthDate), 1, 4)) AS ?birthYear)
        FILTER ( (?birthYear >= 1351   )) 
            }
    ORDER BY ?birthYear
    }




## Explorations des générations d'astronomes

![Distribution par périodes de 25 ans](https://raw.github.com/Sciences-historiques-numeriques/astronomers/master/notebooks_jupyter/dbpedia_exploration/pictures/birth_years_20241208.html)


![Distribution par périodes de 25 ans](https://raw.github.com/Sciences-historiques-numeriques/astronomers/master/notebooks_jupyter/dbpedia_exploration/pictures/birth_years_20241208.png)