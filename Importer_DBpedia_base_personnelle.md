# Importer et structurer les données issues de DBPedia dans la base personnelle

Ces instructions concernent l'importation de données issues de DBpedia dans une base de données qui a la structure de celle du projet personnel.

Dans le contexte de ce projet elle s'appelle _astronomers_import.db_ et se trouve dans le dossier [_astronomers/data/astronomers_import.db_](https://github.com/Sciences-historiques-numeriques/astronomers/tree/main/data)


## Préparation de la base de données

Créer une copie (par simple copier-coller dans le dossier de travail) de la base de données de son propre projet, en renommant ensuite la copie, par exemple, en ajoutant à la fin du nom '_import' ou semblable.


Vider complètement les tables en utilisant l'instruction suivante. Mais attention: cette instruction est irréversible !

Ne pas oublier de temps en temps de sauvegarder sur un ou plusieurs disques externes la base de données et plus en général toutes les donnes de l'ordinateur.

    /*
    La ligne est commentée afin d'éviter toute erreur de manipulation — décommenter la ligne afin de l'exécuter, puis recommenter
    */
    --DELETE FROM "statement" ;
    /* 
    après avoir vidé la table exécuter une instruction vacuum afin de vider la mémoire
    */
    VACUUM;

Normalement cette instruction remet à zéro les valeurs des clés primaires autoincrémentées

&nbsp;

## Production des données à importer


### Liste des astronomes—astrologues à exporter

Exécuter la requête suivante, d'abord au format de réponse HTML, puis texte séparé par tabulateur (\t) ou virgule et enregistrer le fichier exporté dans un espace (dossier) dédié du dossier de travail.


    PREFIX dbr: <http://dbpedia.org/resource/>
    PREFIX dbp: <http://dbpedia.org/property/>
    PREFIX dbo: <http://dbpedia.org/ontology/>
    SELECT DISTINCT ?o1  (str(?label) as ?name) ?birthYear
    WHERE {
    SELECT DISTINCT ?o1 ?birthDate ?birthYear ?label
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
        rdfs:label ?label.
        BIND(xsd:integer(SUBSTR(STR(?birthDate), 1, 4)) AS ?birthYear)
        FILTER ( (?birthYear >= 1451
                    && ?birthYear < 1771 )
                    && LANG(?label) = 'en') 
            }
    }


### Creation de la table dans la base SQLIte

En utilisant DBeaver, sélectionner la base de données 'import' et active l'import des données, puis:

* selectionner le fichier TSV (CSV) à importer


&nbsp;






