# Importer et structurer les données issues de DBPedia

Ces instructions concernent la base de données générique

## Instructions générales

Pour vider complètement les tables, utiliser l'instruction suivante. Mais attention: cette instruction est irréversible !

    /*
    La ligne est commentée afin d'éviter toute erreur de manipulation 
    */
    --DELETE FROM "statement" ;
    /* 
    après avoir vidé la table exécuter une instruction vacuum afin de vider la mémoire
    */
    VACUUM;

Normalement cette instruction remet à zéro les valeurs des clés primaires auto
&nbsp;

## Importation des données depuis les CSV

Importer les donnnées depuis le CSV dans la table 'statement', cf. les instructions dans la page Explorer DBPedia.


### Vérification après import des données

    -- compter les instances
    SELECT COUNT(*)
    FROM "statement" ;

### Créer les personnes

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




### Vérifier l'import des liens vers DBPedia francophone

    SELECT property_uri, COUNT(*) as effectif 
    FROM "statement" s   
    GROUP BY s.property_uri 
    ORDER BY effectif DESC ;

### Lien des deux population à travers l'URI dbpedia francophone

127 personnes de DBPedia et BNF data sont liées, après importation des données de BNF data. Reste la question de comment traiter celles qui manquent pour éviter de créer des doublons dans la table instance.


    SELECT s1.subject_uri, s2.subject_uri  
    FROM "statement" s1, "statement" s2
    WHERE s1.object_uri = s2.object_uri 
    AND s1.import_metadata = '20221204_4'
    AND s2.import_metadata = '20221204_6';    

### Visualiser les générations de mathématiciens

Regroupement par périodes de 20 ans.
Exporter en CSV et visualiser dans un tableur

    WITH RECURSIVE
    cnt(x,y) AS (
        SELECT 1441,1460
        UNION ALL
        SELECT x+20, y+20 FROM cnt
        WHERE x < 1750
    ),
    tw1 AS (SELECT numeric_value, COUNT(*) as effectif
    FROM "statement" s 
    WHERE import_metadata LIKE '%20221204_1%'
    GROUP BY numeric_value )
    SELECT x,y, SUM(tw1.effectif) effectif_total 
    FROM cnt, tw1
    WHERE tw1.numeric_value >= cnt.x 
    AND tw1.numeric_value < cnt.y
    GROUP BY x,y;

