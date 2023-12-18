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

## Importer les personnes

    -- chercher les doublons de la table des personnes importée

    SELECT o1
    FROM liste_personnes_20231208 lp 
    GROUP BY o1 
    HAVING COUNT(*) > 1 ;

    -- compter les personnes existantes
    SELECT count(*)
    FROM person;

    -- vider la table: ATTENTION Irréversible !
    DELETE FROM person  ;

    -- remettre à 0 la pk
    update SQLITE_SEQUENCE 
    set seq = 0
    where name ='person';

    -- nettoyer automatiquement
    vacuum;


    -- insérer les personnes
    insert into person (label, original_uri)
    select name, o1
    from liste_personnes_20231208 lp ;




## Liste des occupations

    PREFIX dbr: <http://dbpedia.org/resource/>
    PREFIX dbp: <http://dbpedia.org/property/>
    PREFIX dbo: <http://dbpedia.org/ontology/>
    PREFIX rdfs:<http://www.w3.org/2000/01/rdf-schema#>
    SELECT DISTINCT (?o1 AS ?subject_uri) (dbo:occupation as ?property_uri) (?target AS ?object_uri)  (?name as ?label)
    #(COUNT(*) AS ?effectif) 
    WHERE {
    SELECT DISTINCT ?o1 ?target (str(?label) as ?name)
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
        dbp:occupation | dbo:occupation ?target.
    ?target rdfs:label ?label.
    BIND(xsd:integer(SUBSTR(STR(?birthDate), 1, 4)) AS ?birthYear)
        FILTER ( (?birthYear >= 1451   && ?birthYear < 1771 )  && LANG(?label) = 'en') 
            }
    ORDER BY ?birthYear
    }




## Liste des disciplines académiques


 PREFIX dbr: <http://dbpedia.org/resource/>
    PREFIX dbp: <http://dbpedia.org/property/>
    PREFIX dbo: <http://dbpedia.org/ontology/>
    PREFIX rdfs:<http://www.w3.org/2000/01/rdf-schema#>
    SELECT DISTINCT (?o1 AS ?subject_uri) (dbo:occupation as ?property_uri) (?target AS ?object_uri)  (?name as ?label)
    #(COUNT(*) AS ?effectif) 
    WHERE {
    SELECT DISTINCT ?o1 ?target (str(?label) as ?name)
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
        dbp:academicDiscipline ?target.
    ?target rdfs:label ?label.
    BIND(xsd:integer(SUBSTR(STR(?birthDate), 1, 4)) AS ?birthYear)
        FILTER ( (?birthYear >= 1451   && ?birthYear < 1771 )  && LANG(?label) = 'en') 
            }
    ORDER BY ?birthYear
    }



## Nationalité

    PREFIX dbr: <http://dbpedia.org/resource/>
    PREFIX dbp: <http://dbpedia.org/property/>
    PREFIX dbo: <http://dbpedia.org/ontology/>
    PREFIX rdfs:<http://www.w3.org/2000/01/rdf-schema#>
    SELECT DISTINCT (?o1 AS ?subject_uri) (STR(?target) AS ?text_value) 
    # (COUNT(*) AS ?effectif) 
    WHERE {
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
        dbp:nationality | dbo:nationality ?target.
        BIND(xsd:integer(SUBSTR(STR(?birthDate), 1, 4)) AS ?birthYear)
        FILTER ( (?birthYear >= 1451   && ?birthYear < 1771 )  && !isIRI(?target) && strlen(STR(?target)) > 0)
            }
    ORDER BY ?birthYear
    }


## Créer un table par requête

* Exporter en CSV ou TSV le résultat de la requête SPARQL
* En utilisant DBeaver, créer une table par fichier TSV dans la base de données
* Pour les tables des disciplines et nationalités ajouter une colonne pour les valeurs corrigées ou codées, en utilisant SQLite Studio

### Remplir ensuite les colonnes avec les valeurs existantes

Les données seront nettoyées plus tard:

    UPDATE liste_academicDisciplines SET valeur_codee = label ;
    UPDATE nationalite_20231218  SET valeur_nettoyee  = text_value  ;



## Créer une vue SQL qui regroupe les personnes, nationalités et disciplines

Cette vue utilisé les colonnes codées et ajoute un colonne avec les périodes de 50 ans

    DROP VIEW v_nationalite_discipline_annee_code ;
    CREATE VIEW v_nationalite_discipline_annee_code AS
    WITH RECURSIVE
    cnt(x) AS (
    SELECT 1451
    UNION ALL
    SELECT x+50 FROM cnt
    WHERE x < 1801
    ), tw1 AS (
    SELECT x as begin_a, x+49 as end_a FROM cnt
    )
    SELECT lp.o1, n.valeur_nettoyee as nationalite, lad.valeur_codee as discipline, 
            lp.birthYear as annee_naissance,
            begin_a as periode
    from liste_personnes_20231208 lp
        left join liste_academicDisciplines lad 
            on lp.o1 = lad.subject_uri
        left join nationalite_20231218 n 
            on n.subject_uri = lp.o1 
        left join tw1 on lp.birthYear between begin_a and end_a ;


    

    SELECT *
    from v_nationalite_discipline_annee_code;



## Distribution par période: graphique

Exécuter la requête suivante, exporter sous format CSV le résultat et réaliser un graphique sous Calc (ou Excel)

    WITH tw1 AS (
    SELECT DISTINCT o1, periode
    from v_nationalite_discipline_annee_code
    )
    SELECT periode, count(*) effectif
    FROM tw1
    GROUP BY periode;
        


## Nettoyer les nationalités

    SELECT nationalite, count(*) as eff
    FROM v_nationalite_discipline_annee_code
    WHERE nationalite NOTNULL 
    GROUP BY  nationalite
    ORDER BY eff DESC  ; 


    -- chercher les occurrences d'un terme
    -- chercher les occurrences d'un terme
    SELECT *
    FROM nationalite_20231218 n 
    WHERE valeur_nettoyee  LIKE '%Italian, French%';

    -- remplacer toute la cellule par un autre terme
    /*
    * replaced: '%Mulhous%', '%Genev%', '%German, Russian%',
    * '%Tusc%' Italian, French
    */
    UPDATE nationalite_20231218 set valeur_nettoyee = 'Italian'
    WHERE valeur_nettoyee LIKE '%Italian, French%';


## Graphique des nationalités

Exécuter la requête, expoerter le résultat sous forme de CSV et ouvrir avec Calc afin de réaliser un graphique

    SELECT DISTINCT o1, nationalite, periode
    FROM v_nationalite_discipline_annee_code
    WHERE nationalite in (
    SELECT nationalite
    FROM v_nationalite_discipline_annee_code
    WHERE nationalite NOTNULL 
    GROUP BY  nationalite
    HAVING count(*) > 2);