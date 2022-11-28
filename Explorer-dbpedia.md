
## Le point de départ: Wikpedia
<br/>

### Population d'astronomes

https://en.wikipedia.org/wiki/List_of_astronomers

### Une fiche d'astronome

https://en.wikipedia.org/wiki/Giovanni_Domenico_Cassini

* Extraire l'information du texte
* Utiliser l'infobox
  * [Infobox](https://en.wikipedia.org/wiki/Infobox)
  * [HelpInfobox](https://en.wikipedia.org/wiki/Help:Infobox)

### Une fiche d'astronome (données structurées)

https://dbpedia.org/page/Giovanni_Domenico_Cassini

À noter (parmi d'autres):
* dbr:List_of_astrologers
* dbr:List_of_astronomers


<br/>

## DBPedia  

Présentation de DBPedia dans Wikipedia:
https://en.wikipedia.org/wiki/DBpedia

Documentation:
* [Linked Data Access](https://www.dbpedia.org/resources/linked-data/). Entre autres: spécification des URI, Content Negotiation
* [SPARQL over Online Databases](https://www.dbpedia.org/resources/sparql/)
* Interfaces pour requêtes SPARQL:
  * https://dbpedia.org/sparql
  * https://dbpedia.org/snorql/  (navigateur)  


### DBPedia Live


Modifier Wikipedia et voir les résultats en temps réel

* https://www.dbpedia.org/resources/live/
* https://live.dbpedia.org/sparql 
* NB : Default Data Set Name :  http://live.dbpedia.org


### SPARQLIS

* [SPARQLIS sur DBPedia](http://www.irisa.fr/LIS/ferre/sparklis/?title=Core%20English%20DBpedia&endpoint=http%3A//servolis.irisa.fr/dbpedia/sparql)
* [Example queries for Sparklis](http://www.irisa.fr/LIS/ferre/sparklis/examples.html)

<br/>




## Requêtes d'exploration


### Occupation: astronomy

    PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
    PREFIX dbr: <http://dbpedia.org/resource/>
    PREFIX dbo: <http://dbpedia.org/ontology/>
    PREFIX db: <http://dbpedia.org/>
    SELECT DISTINCT ?thing_1 ?birthDate
    WHERE { ?thing_1 dbo:occupation dbr:Astronomy .
        ?thing_1 dbo:birthYear ?birthDate .
    FILTER ( (  xsd:double(str(?birthDate)) >= 1450
                  && xsd:double(str(?birthDate)) <= 1770 ) ) }

### Liste: dbr:List_of_astronomers
    PREFIX dbr: <http://dbpedia.org/resource/>
    PREFIX dbo: <http://dbpedia.org/ontology/>
    SELECT DISTINCT ?p ?ob_1 
    WHERE { 
      dbr:List_of_astronomers ?p ?o1.
      ?o1 a dbo:Person.
      }
    LIMIT 10

### Effectif de la population
28 novembre 2022 : 762

    PREFIX dbr: <http://dbpedia.org/resource/>
    PREFIX dbo: <http://dbpedia.org/ontology/>
    SELECT (COUNT(*) as ?eff)
    WHERE { 
    dbr:List_of_astronomers ?p ?o1.
    ?o1 a dbo:Person.
      }

### Properiétés sortantes et effectifs

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


### Liste des astronomes à exporter

Noter le n° de classe déjà ajouté. Sauvegarder au format CSV, puis ouvrir dans DBeaver et importer dans la table instance

PREFIX dbr: <http://dbpedia.org/resource/>
PREFIX dbo: <http://dbpedia.org/ontology/>
SELECT  (str(?label) as ?label) ?o1 (1 as ?class) # (count(*) as ?eff)     
WHERE { 
 dbr:List_of_astronomers ?p ?o1.
?o1 a dbo:Person;
  <http://www.w3.org/2000/01/rdf-schema#label> ?label.
   
FILTER(LANG(?label) = 'en')
}


### Avec filtre sur les dates


    PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
    PREFIX dbr: <http://dbpedia.org/resource/>
    PREFIX dbo: <http://dbpedia.org/ontology/>
    SELECT DISTINCT ?o1 ?birthDate
    WHERE {  dbr:List_of_astronomers ?p ?o1.
    ?o1 a dbo:Person;
          dbo:birthDate ?birthDate .
    FILTER ( (  str(?birthDate) >= '1450-01-01')
    && (str(?birthDate) <= '1770-01-01' )) 

    }

    LIMIT 200


Le décompte:
 seulement 52

    PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
    PREFIX dbr: <http://dbpedia.org/resource/>
    PREFIX dbo: <http://dbpedia.org/ontology/>
    SELECT (count(*) as ?eff)
    WHERE {  dbr:List_of_astronomers ?p ?o1.
    ?o1 a dbo:Person;
          dbo:birthDate ?birthDate .
    FILTER ( (  str(?birthDate) >= '1450-01-01')
    && (str(?birthDate) <= '1770-01-01' )) 

    