
## Exploration des données de la Bibliothèque nationale de France

Point d'accès SPARQL: https://data.bnf.fr/sparql/

### Définition de la population

    PREFIX owl: <http://www.w3.org/2002/07/owl#>
    PREFIX bio: <http://vocab.org/bio/0.1/>
    PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
    PREFIX foaf: <http://xmlns.com/foaf/0.1/>
    PREFIX  egr:  <http://rdvocab.info/ElementsGr2/>
    
    SELECT DISTINCT  ?s ?sameAs ((IF (?name, ?name, ?fName)) AS ?label) ?annee ?bio
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
        ?s foaf:familyName ?fName.
        OPTIONAL{?s foaf:name ?name}
        OPTIONAL { ?s owl:sameAs ?sameAs
        FILTER (CONTAINS(STR(?sameAs), 'dbped'))
        }
        
        
        }
        BIND(STRBEFORE(STRAFTER(STR(?bd), "http://data.bnf.fr/date/"), "/") AS ?annee)
        FILTER ( ( ?annee > "1401" ) && ( ?annee < "1771" ) )
    }
    ORDER BY ?annee

### Propriétés _outgoing_ de la population

    PREFIX owl: <http://www.w3.org/2002/07/owl#>
    PREFIX bio: <http://vocab.org/bio/0.1/>
    PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
    PREFIX foaf: <http://xmlns.com/foaf/0.1/>
    PREFIX  egr:  <http://rdvocab.info/ElementsGr2/>

    SELECT ?p (COUNT(*) AS ?effectif)
    WHERE
    {  
        { SELECT DISTINCT  ?s ?bio
            WHERE
            {   
            {
                { ?s egr:biographicalInformation ?bio
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
        ?s egr:dateOfBirth ?bd.
        BIND(STRBEFORE(STRAFTER(STR(?bd), "http://data.bnf.fr/date/"), "/") AS ?annee)
        FILTER ( ( ?annee > "1401" ) && ( ?annee < "1771" ) )
        }
        }
        
        ?s ?p ?o.
        }
        
    GROUP BY ?p
    ORDER BY DESC(?effectif)


### Propriétés _incoming_ de la population

    PREFIX owl: <http://www.w3.org/2002/07/owl#>
    PREFIX bio: <http://vocab.org/bio/0.1/>
    PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
    PREFIX foaf: <http://xmlns.com/foaf/0.1/>
    PREFIX  egr:  <http://rdvocab.info/ElementsGr2/>

    SELECT ?p (COUNT(*) AS ?effectif)
    WHERE
    {  
        { SELECT DISTINCT  ?s ?bio
            WHERE
            {   
            {
                { ?s egr:biographicalInformation ?bio
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
        ?s egr:dateOfBirth ?bd.
        BIND(STRBEFORE(STRAFTER(STR(?bd), "http://data.bnf.fr/date/"), "/") AS ?annee)
        FILTER ( ( ?annee > "1401" ) && ( ?annee < "1771" ) )
        }
        }
        
        ?s1 ?p ?s.
        }
        
    GROUP BY ?p
    ORDER BY DESC(?effectif)


###  Les noms

Sauvegarder l'export CSV et importer dans la table _statement_ selon la méthode habituelle

    PREFIX owl: <http://www.w3.org/2002/07/owl#>
    PREFIX bio: <http://vocab.org/bio/0.1/>
    PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
    PREFIX foaf: <http://xmlns.com/foaf/0.1/>
    PREFIX  egr:  <http://rdvocab.info/ElementsGr2/>

    SELECT (?s as ?subject_uri) (rdfs:label as ?property_uri) ((IF (?name, ?name, ?fName)) AS ?label) ('20221204_5' as ?import_metadata)
    WHERE
    {  
        { SELECT DISTINCT  ?s ?bio
            WHERE
            {   
            {
                { ?s egr:biographicalInformation ?bio
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
        ?s egr:dateOfBirth ?bd.
        BIND(STRBEFORE(STRAFTER(STR(?bd), "http://data.bnf.fr/date/"), "/") AS ?annee)
        FILTER ( ( ?annee > "1401" ) && ( ?annee < "1771" ) )
        }
        }
        
        ?s foaf:familyName ?fName.
    OPTIONAL{?s foaf:name ?name}
        }
        
    ORDER BY (?annee)


### Lien vers dbpedia francophone

Sauvegardé sous forme de CSV et importé dans la table _statement_ selon la méthode habituelle

    PREFIX owl: <http://www.w3.org/2002/07/owl#>
    PREFIX bio: <http://vocab.org/bio/0.1/>
    PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
    PREFIX foaf: <http://xmlns.com/foaf/0.1/>
    PREFIX  egr:  <http://rdvocab.info/ElementsGr2/>

    SELECT DISTINCT (?s AS ?subject_uri) (owl:sameAs AS ?property) (?sameAs AS ?object_uri) ('20221204_6' AS ?import_metadata)
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
        { ?s owl:sameAs ?sameAs
        FILTER (CONTAINS(STR(?sameAs), 'dbped'))
        }
        
        
        }
        BIND(STRBEFORE(STRAFTER(STR(?bd), "http://data.bnf.fr/date/"), "/") AS ?annee)
        FILTER ( ( ?annee > "1401" ) && ( ?annee < "1771" ) )
    }
    ORDER BY ?annee

En résultent 692 lignes pour lesquelles il y a la référence vers dbpedia: francophone