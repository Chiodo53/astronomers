



   PREFIX owl: <http://www.w3.org/2002/07/owl#>
    PREFIX dbo: <http://dbpedia.org/ontology/>

    #SELECT *

    INSERT { GRAPH <http://dbpedia-data> {?uri dbo:doctoralStudent ?o} }
    WHERE {    
    {
        
        SELECT ?uri
        WHERE {       
        {?item owl:sameAs	?t}
        FILTER (CONTAINS (STR(?t), '://db'))
        BIND( URI(?t) as ?uri )
        }
    LIMIT 500
    }
    SERVICE <https://dbpedia.org/sparql>
    { ?uri dbo:doctoralStudent ?o }
    }     





    PREFIX owl: <http://www.w3.org/2002/07/owl#>
    PREFIX dbo: <http://dbpedia.org/ontology/>


    SELECT *
    WHERE  {
    GRAPH <http://dbpedia-data>
        {?uri dbo:doctoralStudent ?o}
    }