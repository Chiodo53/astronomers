
## Le point de départ: Wikpedia


### Population d'astronomes

<https://en.wikipedia.org/wiki/List_of_astronomers>

&nbsp;


### Une fiche d'astronome dans Wikipedia (données non-structurées et semi-structurées)

<https://en.wikipedia.org/wiki/Giovanni_Domenico_Cassini>

* Observer l'information que contient le texte
* Observer les propriétés de l'objet présentes dans l'infobox
  * [Infobox](https://en.wikipedia.org/wiki/Infobox)
  * [HelpInfobox](https://en.wikipedia.org/wiki/Help:Infobox)
* Procédure 'analogique': extraire 'manuellement' l'information du texte et de l'infobox et la mettre dans la base de données SQLite

&nbsp;

### Une fiche d'astronome dans DBPedia (données structurées)

<https://dbpedia.org/page/Giovanni_Domenico_Cassini>

Les informations qui figurent sur cette page sont extraites de Wikipedia et produites sous forme de données structurées selon le protocole RDF.

On peut donc les interroger et récupérer grâce à des requêtes formulées dans le langage SPARQL.

Observer dans la page quelle informations intéressantes sont disponibles. RDF fonctionne sur un modèle "sujet -> prédicat-> objet" qui constitue les triplets.

Le sujet de la page est le sujet de tous les triplets (dans ce cas la personne). Les prédicats sont exprimés sous forme de propriétés (<u>_properties_</u>) 

Exemples de propriétés:

* dbp:birthDate
  * URI complète de la propriété: <http://dbpedia.org/property/birthDate>
  * préfixe de l'espace de noms: 'dbp' (pour <http://dbpedia.org/property/>)
  * dbp:birthDate est un qualified name, ou QName
* dbo:influencedBy ('dbo' pour <http://dbpedia.org/ontology>)
  * essayez de naviguer d'un _influencer_ vers autre: c'est là qu'on voit des données structurées, toutes définies par des URI
  
&nbsp;

À noter (parmi d'autres entités):

* dbr:List_of_astrologers
* dbr:List_of_astronomers
* [dbr:Astronomer]()
* dbr:Astrology
* dbr:Astronomy


dbr: est le préfixe qui remplace http://dbpedia.org/resource/. En entier la première entrée donne http://dbpedia.org/resource/List_of_astrologers.

dbr:List_of_astrologers est donc un QName

&nbsp;


## DBPedia  

Présentation de DBPedia dans Wikipedia:
<https://en.wikipedia.org/wiki/DBpedia>

Documentation:

* [Linked Data Access](https://www.dbpedia.org/resources/linked-data/). Entre autres: spécification des URI, Content Negotiation
* [SPARQL over Online Databases](https://www.dbpedia.org/resources/sparql/) (documentation)
* __Interfaces__ pour requêtes __SPARQL__:
  * <https://dbpedia.org/sparql>
  * <https://dbpedia.org/snorql/>  (navigateur)  

### DBPedia Live

Modifier Wikipedia et voir les résultats en temps réel

* <https://www.dbpedia.org/resources/live/>
* <https://live.dbpedia.org/sparql>
* NB : Default Data Set Name :  <http://live.dbpedia.org>

### SPARQLIS

* [SPARQLIS sur DBPedia](http://www.irisa.fr/LIS/ferre/sparklis/?title=Core%20English%20DBpedia&endpoint=http%3A//servolis.irisa.fr/dbpedia/sparql)
* [Example queries for Sparklis](http://www.irisa.fr/LIS/ferre/sparklis/examples.html)

SPARQLIS permet de construire des requêtes SPARQL grâce à une interface graphique

&nbsp;

## Requêtes d'exploration

* Interface pour requêtes: <https://dbpedia.org/sparql>

### Occupation: astronomer

    PREFIX dbr: <http://dbpedia.org/resource/>
    PREFIX dbo: <http://dbpedia.org/ontology/>
    SELECT DISTINCT ?thing_1 ?birthDate
    WHERE { ?thing_1 dbo:occupation dbr:Astronomer .
        OPTIONAL { 
                   ?thing_1 dbo:birthYear ?birthDate .
                   }
          }


* Noter que changer les espaces de noms dbp et dbo donne des résultats différents
* Cette requête liste 160 astronomes (3 décembre 2022), le maximum des effectifs avec cette approche

      PREFIX dbr: <http://dbpedia.org/resource/>
      PREFIX dbo: <http://dbpedia.org/ontology/>
      PREFIX dbp: <http://dbpedia.org/property/>
      SELECT (COUNT(*) as ?effectif)
      WHERE { ?thing_1 dbo:occupation dbr:Astronomer .
            }

### Astronomes nés entre 1451 et 1770

    PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
    PREFIX dbr: <http://dbpedia.org/resource/>
    PREFIX dbo: <http://dbpedia.org/ontology/>
    PREFIX dbp: <http://dbpedia.org/property/>
    SELECT DISTINCT ?thing_1 ?intYear
    WHERE { ?thing_1 dbo:occupation dbr:Astronomer .
         ?thing_1 dbo:birthYear ?birthYear .
         BIND(xsd:integer(str(?birthYear)) AS ?intYear)
    FILTER ( (?intYear >= 1451
                  && ?intYear < 1771 ) ) }
    ORDER BY ?intYear

Leur effectif (3 décembre 2022): 23

La requête ci-dessous ne change rien, en espace de nboms dbr seulement 13 astronomes

    PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
    PREFIX dbr: <http://dbpedia.org/resource/>
    PREFIX dbo: <http://dbpedia.org/ontology/>
     PREFIX dbp: <http://dbpedia.org/property/>
    SELECT (COUNT(*) as ?effectif)
    WHERE {
      {SELECT DISTINCT ?thing_1
           WHERE {
        { ?thing_1 dbo:occupation dbr:Astronomer }
        UNION
        {?thing_1 dbp:occupation dbr:Astronomer}
              }
        }
     ?thing_1 dbo:birthYear ?birthYear .
     BIND(xsd:integer(str(?birthYear)) AS ?intYear)
    FILTER ( (?intYear >= 1451
              && ?intYear < 1771 ) ) }
    ORDER BY ?intYear

&nbsp;

### Liste: dbr:List_of_astronomers

    PREFIX dbr: <http://dbpedia.org/resource/>
    PREFIX dbo: <http://dbpedia.org/ontology/>
    SELECT DISTINCT ?p ?o1 
    WHERE { 
      dbr:List_of_astronomers ?p ?o1.
      ?o1 a dbo:Person.
      }
    LIMIT 10

### Effectif de la population

Effectifs au 3 décembre 2022 : 762

    PREFIX dbr: <http://dbpedia.org/resource/>
    PREFIX dbo: <http://dbpedia.org/ontology/>
    SELECT (COUNT(*) as ?eff)
    WHERE { 
    dbr:List_of_astronomers ?p ?o1.
    ?o1 a dbo:Person.
      }

###  Propriétés sortantes et effectifs

    PREFIX dbr: <http://dbpedia.org/resource/>
    PREFIX dbo: <http://dbpedia.org/ontology/>
    SELECT ?p1 (COUNT(*) as ?eff)
    WHERE { 
    dbr:List_of_astronomers ?p ?o1.
    ?o1 a dbo:Person;
        ?p1 ?o2.
      }
    GROUP BY ?p1
    ORDER BY DESC(?eff)

Noter ces propriétés:

* <http://dbpedia.org/property/birthDate>: 443
* <http://dbpedia.org/ontology/birthDate>: 396

&nbsp;

    PREFIX dbr: <http://dbpedia.org/resource/>
    PREFIX dbp: <http://dbpedia.org/ontology/>
    PREFIX dbo: <http://dbpedia.org/ontology/>
    SELECT (COUNT(*) as ?eff)
    WHERE { 
    dbr:List_of_astronomers ?p ?o1.
    ?o1 a dbo:Person;
      dbr:birthDate ?birthDate.
    BIND(xsd:integer(SUBSTR(STR(?birthDate), 1, 4)) AS ?birthYear)
    FILTER ( (?birthYear >= 1451
                && ?birthYear < 1771 ) ) 
          }

&nbsp;

Documentation: [Property path syntax](https://www.w3.org/TR/sparql11-property-paths/)

Alternative entre propriétés  ( | ):

Effectif: 56


    PREFIX dbr: <http://dbpedia.org/resource/>
    PREFIX dbp: <http://dbpedia.org/ontology/>
    PREFIX dbo: <http://dbpedia.org/ontology/>
    SELECT DISTINCT ?o1 ?birthDate ?birthYear
    WHERE { 
    dbr:List_of_astronomers ?p ?o1.
    ?o1 a dbo:Person;
      dbr:birthDate | dbo:birthDate ?birthDate.
    BIND(xsd:integer(SUBSTR(STR(?birthDate), 1, 4)) AS ?birthYear)
    FILTER ( (?birthYear >= 1451
                && ?birthYear < 1771 ) ) 
          }
    ORDER BY ?birthYear

&nbsp;

Astonomes et _astrologues_ et _mathématiciens_:

    PREFIX dbr: <http://dbpedia.org/resource/>
    PREFIX dbp: <http://dbpedia.org/ontology/>
    PREFIX dbo: <http://dbpedia.org/ontology/>
    SELECT DISTINCT ?o1 ?birthDate ?birthYear
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
      dbr:birthDate | dbo:birthDate ?birthDate.
    BIND(xsd:integer(SUBSTR(STR(?birthDate), 1, 4)) AS ?birthYear)
    FILTER ( (?birthYear >= 1451
                && ?birthYear < 1771 ) ) 
          }
    ORDER BY ?birthYear

&nbsp;

Effectif : 292 mathématiciens, astrologues, astronomes

__Définition de la population__: cette requêtes définit la population — cette requête sera la base de toutes les autres

    PREFIX dbr: <http://dbpedia.org/resource/>
    PREFIX dbp: <http://dbpedia.org/ontology/>
    PREFIX dbo: <http://dbpedia.org/ontology/>
    SELECT (COUNT(*) as ?effectif)
    WHERE {
      SELECT DISTINCT ?o1 ?birthDate ?birthYear
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
          dbr:birthDate | dbo:birthDate ?birthDate.
        BIND(xsd:integer(SUBSTR(STR(?birthDate), 1, 4)) AS ?birthYear)
        FILTER ( (?birthYear >= 1451
                    && ?birthYear < 1771 ) ) 
              }
      }

        

&nbsp;
Avec les labels des noms, même effectif:

    PREFIX dbr: <http://dbpedia.org/resource/>
    PREFIX dbp: <http://dbpedia.org/ontology/>
    PREFIX dbo: <http://dbpedia.org/ontology/>
    PREFIX rdfs:<http://www.w3.org/2000/01/rdf-schema#>
    SELECT (COUNT(*) as ?effectif)
    WHERE {
      SELECT DISTINCT ?o1 ?birthDate ?birthYear
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
          dbr:birthDate | dbo:birthDate ?birthDate;
      rdfs:label ?label.
        BIND(xsd:integer(SUBSTR(STR(?birthDate), 1, 4)) AS ?birthYear)
        FILTER ( (?birthYear >= 1451   && ?birthYear < 1771 )  && LANG(?label) = 'en') 
              }
      }



### Liste des astronomes—astrologues à exporter

Noter la propriété <http://dbpedia.org/ontology/birthYear> ajoutée en vue de l'import dans la base de données SQLite. Sauvegarder au format CSV, puis ouvrir dans DBeaver et importer dans la table 'statement' en mettant les valeurs dans les champs.

ATTENTION: ne pas créer de nouveaux champs mais mettre ainsi

* ?o1 dans le champs subject_uri
* ?bY dans property_uri
* ?birthYear dans numeric_value
* ?import_metadata dans import_metadata

Ce dernier champs est important pour tracer les import et garder souvenir de la source.

    PREFIX dbr: <http://dbpedia.org/resource/>
    PREFIX dbp: <http://dbpedia.org/ontology/>
    PREFIX dbo: <http://dbpedia.org/ontology/>
    PREFIX rdfs:<http://www.w3.org/2000/01/rdf-schema#>
    SELECT ?o1 (dbo:birthYear as ?bY) ?birthYear ('20221204_1' as ?import_metadata)
    WHERE {
      SELECT DISTINCT ?o1 ?birthYear
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
          dbr:birthDate | dbo:birthDate ?birthDate;
      rdfs:label ?label.
        BIND(xsd:integer(SUBSTR(STR(?birthDate), 1, 4)) AS ?birthYear)
        FILTER ( (?birthYear >= 1451   && ?birthYear < 1771 )  && LANG(?label) = 'en') 
              }
      ORDER BY ?birthYear
      }

292 lignes exportées le 3 décembre 2022

&nbsp;

## Les propriétés

### Liste des propriétés sortantes

    PREFIX dbr: <http://dbpedia.org/resource/>
    PREFIX dbo: <http://dbpedia.org/ontology/>
    SELECT ?p1 (COUNT(*) as ?eff)
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
    dbr:birthDate | dbo:birthDate ?birthDate;
        ?p1 ?o2.
    BIND(xsd:integer(SUBSTR(STR(?birthDate), 1, 4)) AS ?birthYear)
    FILTER ( (?birthYear >= 1451   && ?birthYear < 1771 )) 
      }
    GROUP BY ?p1
    ORDER BY DESC(?eff)

### Liste des propriétés entrantes

    PREFIX dbr: <http://dbpedia.org/resource/>
    PREFIX dbo: <http://dbpedia.org/ontology/>
    SELECT ?p1 (COUNT(*) as ?eff)
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
    dbr:birthDate | dbo:birthDate ?birthDate.
    ?o2 ?p1 ?o1.
    BIND(xsd:integer(SUBSTR(STR(?birthDate), 1, 4)) AS ?birthYear)
    FILTER ( (?birthYear >= 1451   && ?birthYear < 1771 )) 
      }
    GROUP BY ?p1
    ORDER BY DESC(?eff)

&nbsp;

### Le nom

Cette requête prépare les données pour importation. Enregistrer dans un fichier CSV puis importer dans la table statements
ATTENTION: ne pas créer de nouveaux champs mais mettre ainsi

* ?o1 dans le champs subject_uri
* ?property dans property_uri
* ?str_label dans text_value
* ?import_metadata dans import_metadata

&nbsp;

    PREFIX dbr: <http://dbpedia.org/resource/>
    PREFIX dbp: <http://dbpedia.org/ontology/>
    PREFIX dbo: <http://dbpedia.org/ontology/>
    PREFIX rdfs:<http://www.w3.org/2000/01/rdf-schema#>
    SELECT ?o1 (rdfs:label as ?property) ?str_label ('20221204_3' as ?import_metadata)
    WHERE {
      SELECT DISTINCT ?o1 (STR(?label) as ?str_label)
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
          dbr:birthDate | dbo:birthDate ?birthDate;
      rdfs:label ?label.
        BIND(xsd:integer(SUBSTR(STR(?birthDate), 1, 4)) AS ?birthYear)
        FILTER ( (?birthYear >= 1451   && ?birthYear < 1771 )  && LANG(?label) = 'en') 
              }
      ORDER BY ?birthYear
      }

### Trouver les URI correspondantes à DBPedia francophone

Cette requête prépare les données pour importation. Enregistrer dans un fichier CSV puis importer dans la table statements
ATTENTION: ne pas créer de nouveaux champs mais mettre ainsi

* ?o1 dans le champs subject_uri
* ?property dans property_uri
* ?target dans object_uri
* ?import_metadata dans import_metadata

&nbsp;

    PREFIX dbr: <http://dbpedia.org/resource/>
    PREFIX dbp: <http://dbpedia.org/ontology/>
    PREFIX dbo: <http://dbpedia.org/ontology/>
    PREFIX rdfs:<http://www.w3.org/2000/01/rdf-schema#>
    PREFIX owl:	<http://www.w3.org/2002/07/owl#>
    SELECT ?o1 (owl:sameAs as ?property) ?target ('20221204_4' as ?import_metadata)
    # (COUNT(*) AS ?effectif) 
    WHERE {
      {
      SELECT DISTINCT ?o1 ?target 
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
          dbp:birthDate | dbo:birthDate ?birthDate;
          owl:sameAs ?target.
    
        BIND(xsd:integer(SUBSTR(STR(?birthDate), 1, 4)) AS ?birthYear)
        FILTER ( (?birthYear >= 1401   && ?birthYear < 1771 )  ) 
        ### Erreur sur Maldonado
        FILTER (CONTAINS( STR(?target), 'fr.dbp') && !CONTAINS( STR(?o1), 'Pedro_Vicente_Maldonado'))
              }
    }
    
      }

Seulement 257 renseignés

### Occupation

    PREFIX dbr: <http://dbpedia.org/resource/>
    PREFIX dbp: <http://dbpedia.org/ontology/>
    PREFIX dbo: <http://dbpedia.org/ontology/>
    PREFIX rdfs:<http://www.w3.org/2000/01/rdf-schema#>
    SELECT ?o1 ?target ?name
    # (COUNT(*) AS ?effectif) 
    WHERE {
      SELECT DISTINCT ?o1 ?target (str(?label) as ?name)
      WHERE { 
        {
          {dbr:List_of_astronomers ?p ?o1.}
          UNION
          {dbr:List_of_astrologers ?p ?o1.}
        }
        ?o1 a dbo:Person;
          dbr:birthDate | dbo:birthDate ?birthDate;
          dbr:occupation | dbo:occupation ?target.
      ?target rdfs:label ?label.
        BIND(xsd:integer(SUBSTR(STR(?birthDate), 1, 4)) AS ?birthYear)
        FILTER ( (?birthYear >= 1451   && ?birthYear < 1771 )  && LANG(?label) = 'en') 
              }
      ORDER BY ?birthYear
      }

72 lignes exportées le 3 décembre 2022





### Tests

    PREFIX dbr: <http://dbpedia.org/resource/>
    PREFIX dbp: <http://dbpedia.org/ontology/>
    PREFIX dbo: <http://dbpedia.org/ontology/>
    PREFIX rdfs:<http://www.w3.org/2000/01/rdf-schema#>
    SELECT ?o1 ?target
    # (COUNT(*) AS ?effectif) 
    WHERE {
      {
      SELECT DISTINCT ?o1 ?target 
      WHERE { 
        {
          {dbr:List_of_astronomers ?p ?o1.}
          UNION
          {dbr:List_of_astrologers ?p ?o1.}
        }
        ?o1 a dbo:Person;
          dbp:birthDate | dbo:birthDate ?birthDate;
          dbp:occupation | dbo:occupation | dbo:academicDiscipline ?target.
    
        BIND(xsd:integer(SUBSTR(STR(?birthDate), 1, 4)) AS ?birthYear)
        FILTER ( (?birthYear >= 1401   && ?birthYear < 1771 )  ) 
              }
    }
    
        }




    PREFIX dbr: <http://dbpedia.org/resource/>
    PREFIX dbp: <http://dbpedia.org/ontology/>
    PREFIX dbo: <http://dbpedia.org/ontology/>
    PREFIX rdfs:<http://www.w3.org/2000/01/rdf-schema#>
    SELECT ?o1 ?target MAX((str(?label) as ?name))
    # (COUNT(*) AS ?effectif) 
    WHERE {
      {
      SELECT DISTINCT ?o1 ?target 
      WHERE { 
        {
          {dbr:List_of_astronomers ?p ?o1.}
          UNION
          {dbr:List_of_astrologers ?p ?o1.}
        }
        ?o1 a dbo:Person;
          dbr:birthDate | dbo:birthDate ?birthDate;
          dbr:occupation | dbo:occupation ?target.
    
        BIND(xsd:integer(SUBSTR(STR(?birthDate), 1, 4)) AS ?birthYear)
        FILTER ( (?birthYear >= 1451   && ?birthYear < 1771 )  ) 
              }
    }
    ?target rdfs:label ?label.
      FILTER (LANG(?label) IN ('en', 'fr'))
      }
