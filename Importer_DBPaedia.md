# Importer et structurer les données issues de DBPedia

Ces instructions concernent l'importation des données issues de DBPedia base de données générique.

La base de données de ce projet se trouve dans le dossier [_astronomers/data/generic_database.sqlite_](https://github.com/Sciences-historiques-numeriques/astronomers/tree/main/data)


## Instructions générales

Pour vider complètement les tables, utiliser l'instruction suivante. Mais attention: cette instruction est irréversible !

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

## Importation des données depuis les CSV

Importer les donnnées depuis le CSV dans la table 'statement', cf. les instructions dans la page Explorer DBPedia.


### Vérification après import des données

    -- compter les instances
    SELECT COUNT(*)
    FROM "statement" ;

### Créer les personnes

On a préalablement créé la classe _Person_ dans la table _Class_.

On effectue une requête sur la table _statement_, on sélection les entités qu'on vient d'importer et on ajoute dans la clause SELECT la valeur de la classe _Person_ et les métadonnées d'importation, pour garder trace explicite

    INSERT INTO "instance" (external_uri, fk_class, import_metadata)
    SELECT subject_uri, 1, '20221204_2' FROM "statement" s
    WHERE import_metadata LIKE '%20221204_1%' ;

#### Vérification

Regrouper les instances par classe. Noter la jointure avec la table _class_  


    SELECT c.label, COUNT(*) eff
    FROM "instance" i, class c 
    WHERE i.fk_class = c.pk_class 
    GROUP BY c.label 
    ORDER BY eff DESC ;

### Ajouter un lien en clé étrangère entre les instances et les assertions

    -- inspecter les instances avec les propriétés

    SELECT i.pk_instance, i.external_uri, s.pk_statement, s.subject_uri 
    FROM "instance" i , "statement" s 
    WHERE s.subject_uri = i.external_uri ;

    -- ajouter les valeurs de clé étrangère entre les assertions et les instances

    UPDATE "statement" set fk_subject_instance = i.pk_instance 
    FROM "instance" i 
    WHERE "statement".subject_uri = i.external_uri ;


### Ajouter les noms des personnes

Importer le CSV qui contient les labels selon les instructions de la page dédiée à DBPedia.

Pour vérifier l'import exécuter la requête suivante:

    SELECT property_uri, COUNT(*) as effectif 
    FROM "statement" s   
    GROUP BY s.property_uri 
    ORDER BY effectif DESC ;

#### Ajouter les noms des personnes dans les instances

    UPDATE "instance" set label = s.text_value  
    FROM "statement" s 
    WHERE s.subject_uri = "instance".external_uri ;	

# Traitement des _occupations_

Exporter les deux CSV contenant les _occupations_ sous forme de ressources et de _literals_

## Exploration

### Regroupement par URI de 'occupation'

On constate des inconsistances. Je corrice à la main les labels sur la base de cette liste et j'utiliserai les labels pour créer les 'occupations' dans la table Instances

    SELECT object_uri, count(*) as effectif  
    FROM "statement" s 
    WHERE import_metadata  = '20221211_1' 
    GROUP BY object_uri ;


J'efface deux lignes visiblement erronées:
* <http://dbpedia.org/resource/Riobamba>
* <http://dbpedia.org/resource/Mughal_Empire>

&nbsp;


### Liste des occupations qui seront créées

    SELECT label, count(*) as effectif  
    FROM "statement" s 
    WHERE import_metadata  = '20221211_1' 
    GROUP BY label
    ORDER BY effectif DESC ;


### Créer les occupations

    INSERT INTO "instance" (label, fk_class, import_metadata)
    SELECT label, 2, '20221211_3' 
    FROM "statement" s 
    WHERE import_metadata  = '20221211_1' 
    GROUP BY label;

#### Vérification
    SELECT c.label, COUNT(*) eff
    FROM "instance" i, class c 
    WHERE i.fk_class = c.pk_class 
    GROUP BY c.label 
    ORDER BY eff DESC ;

### Reporter la clé des occupations vers les statements

    UPDATE "statement" set fk_object_instance  = i.pk_instance 
    FROM "instance" i 
    WHERE i.fk_class = 2
    AND "statement".label = i.label 
    AND metadata_import = '20221211_1' ;

### Reporter la clé des personnes vers les statements
    UPDATE "statement" set fk_subject_instance = i.pk_instance 
    FROM "instance" i 
    WHERE "statement".subject_uri = i.external_uri
    AND "statement".import_metadata = '20221211_1'  ;

### Chercher puis supprimer les doublons

NB : il y a aussi des personnes non renseignées. Vérifier

    SELECT fk_subject_instance, fk_object_instance, COUNT(*) as eff 
    FROM "statement" s  
    WHERE s.import_metadata  = '20221211_1'  
    AND fk_subject_instance IS NOT NULL 
    GROUP BY fk_subject_instance, fk_object_instance
    HAVING COUNT(*) > 1 ;

#### Requête pour le nettoyage dans DBeaver

    SELECT * 
    FROM "statement" s2 
    WHERE fk_subject_instance IN (
        SELECT fk_subject_instance 
        FROM "statement" s  
        WHERE s.import_metadata  = '20221211_1'  
        AND fk_subject_instance IS NOT NULL 
        GROUP BY fk_subject_instance, fk_object_instance
        HAVING COUNT(*) > 1 )
    AND property_uri LIKE '%occupation%';


## Créer les pursuits

    INSERT INTO "instance" (import_metadata, notes, fk_class)
    SELECT pk_statement || '_20221211_4' , pk_statement, 3
    FROM "statement" s 
    WHERE import_metadata = '20221211_1'
    AND fk_subject_instance IS NOT NULL;


### Créer l'association à la personne

    INSERT INTO "statement" (fk_subject_instance, fk_property, fk_object_instance, import_metadata)
    SELECT  i.pk_instance, 1, s.fk_subject_instance, '20221211_6_'|| i.pk_instance 
    FROM "instance" i, "statement" s 
    WHERE i.notes = s.pk_statement ;

### Créer l'association à la profession
    INSERT INTO "statement" (fk_subject_instance, fk_property, fk_object_instance, import_metadata)
    SELECT  i.pk_instance, 2, s.fk_object_instance, '20221211_5_'|| i.pk_instance 
    FROM "instance" i, "statement" s 
    WHERE i.notes = s.pk_statement ;

## Créer la vue qui liste les professions

    --DROP VIEW v_pursuits;
    CREATE VIEW v_pursuits AS
    SELECT i.pk_instance, s1.pk_statement, i1.pk_instance, i1.label, i2.label label_occupation, s2.pk_statement pk_statement_occupation
    FROM "instance" i
    LEFT JOIN "statement" s1 ON s1.fk_subject_instance = i.pk_instance AND s1.fk_property = 1 
    LEFT JOIN "instance" i1 ON s1.fk_object_instance = i1.pk_instance
    LEFT JOIN "statement" s2 ON s2.fk_subject_instance = i.pk_instance AND s2.fk_property = 2  
    LEFT JOIN "instance" i2 ON s2.fk_object_instance = i2.pk_instance
    WHERE i.fk_class = 3;


### Interroger la vue

SELECT *
FROM v_pursuits;



# Association à des données issues d'une autre source

### Vérifier l'import des liens vers DBPedia francophone

    SELECT property_uri, COUNT(*) as effectif 
    FROM "statement" s   
    GROUP BY s.property_uri 
    ORDER BY effectif DESC ;

&nbsp;

## Lien des deux population à travers l'URI dbpedia francophone

127 personnes de DBPedia et BNF data sont liées, après importation des données de BNF data. Reste la question de comment traiter celles qui manquent pour éviter de créer des doublons dans la table instance.


    SELECT s1.subject_uri, s2.subject_uri  
    FROM "statement" s1, "statement" s2
    WHERE s1.object_uri = s2.object_uri 
    AND s1.import_metadata = '20221204_4'
    AND s2.import_metadata = '20221204_6';  



