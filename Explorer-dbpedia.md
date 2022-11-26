# Explorer DBPedia

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

<br/>

## DBPedia  

Présentation de DBPedia dans Wikipedia:
https://en.wikipedia.org/wiki/DBpedia

Documentation:
* [Linked Data Access](https://www.dbpedia.org/resources/linked-data/). Entre autres: spécification des URI, Content Negotiation
* [SPARQL over Online Databases](https://www.dbpedia.org/resources/sparql/)
* Interfaces pour requêtes SPARQL:
  * https://dbpedia.org/sparql 
  * https://dbpedia.org/snorql/  (navigateur)  


### DBPedia Live


Modifier Wikipedia et voir les résultats en temps réel

* https://www.dbpedia.org/resources/live/
* https://live.dbpedia.org/sparql 
* NB : Default Data Set Name :  http://live.dbpedia.org


### SPARQLIS

* [SPARQLIS sur DBPedia](http://www.irisa.fr/LIS/ferre/sparklis/?title=Core%20English%20DBpedia&endpoint=http%3A//servolis.irisa.fr/dbpedia/sparql)
* [Example queries for Sparklis](http://www.irisa.fr/LIS/ferre/sparklis/examples.html)

<br/>




## Requêtes


### Occupation: astronomy

    PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>

    PREFIX dbr: <http://dbpedia.org/resource/>

    PREFIX dbo: <http://dbpedia.org/ontology/>

    PREFIX db: <http://dbpedia.org/>

    SELECT DISTINCT ?thing_1 ?birthYear_9

    WHERE { ?thing_1 dbo:occupation dbr:Astronomy .
        ?thing_1 dbo:birthYear ?birthYear_9 .

    FILTER ( (  xsd:double(str(?birthYear_9)) >= 1450
                 && xsd:double(str(?birthYear_9)) <= 1770 ) ) }
                 
                 LIMIT 200







