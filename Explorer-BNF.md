


    PREFIX owl: <http://www.w3.org/2002/07/owl#>
    PREFIX bio: <http://vocab.org/bio/0.1/>
    PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
    PREFIX foaf: <http://xmlns.com/foaf/0.1/>
    PREFIX  egr:  <http://rdvocab.info/ElementsGr2/>
    
    SELECT DISTINCT  ?s ?sameAs ?name ?annee ?bio
    WHERE
    { { { SELECT DISTINCT  ?s ?bio
            WHERE
            {   { ?s egr:biographicalInformation ?bio
                    FILTER ( CONTAINS(?bio, "mathém") || CONTAINS(?bio, "Mathém") )
                }
                UNION
                { ?s egr:biographicalInformation ?bio
                    FILTER ( CONTAINS(?bio, "astrono") || CONTAINS(?bio, "Astrono") )
                }
            UNION
                { ?s egr:biographicalInformation ?bio
                    FILTER ( CONTAINS(?bio, "astrolog") || CONTAINS(?bio, "Astrolog") )
                }

        
            }
        }
        ?s egr:dateOfBirth ?bd
        OPTIONAL {?s foaf:name ?name}
        OPTIONAL { ?s owl:sameAs ?sameAs
        FILTER (CONTAINS(STR(?sameAs), 'dbped'))
        }
        
        
        }
        BIND(STRBEFORE(STRAFTER(STR(?bd), "http://data.bnf.fr/date/"), "/") AS ?annee)
        FILTER ( ( ?annee > "1400" ) && ( ?annee < "1771" ) )
    }
    ORDER BY ?annee