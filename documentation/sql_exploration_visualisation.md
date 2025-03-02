# Exploration et visualisation de données


## Visualiser les générations de mathématiciens

Regroupement par périodes de 20 ans.
Exporter en CSV et visualiser dans un tableur

    WITH RECURSIVE
    cnt(x,y) AS (
        SELECT 1441,1460
        UNION ALL
        SELECT x+20, y+20 FROM cnt
        WHERE x < 1750
    ),
    tw1 AS (
        SELECT numeric_value, COUNT(*) as effectif
        FROM "statement" s 
        WHERE import_metadata LIKE '%20221204_1%'
        GROUP BY numeric_value 
        )
    SELECT x,y, SUM(tw1.effectif) effectif_total 
    FROM cnt, tw1
    WHERE tw1.numeric_value >= cnt.x 
    AND tw1.numeric_value < cnt.y
    GROUP BY x,y;


## Fréquences des occupations par génération

### Associer la génération à l'occupation

    WITH RECURSIVE
    cnt(x,y) AS (
        SELECT 1441,1460
        UNION ALL
        SELECT x+20, y+20 FROM cnt
        WHERE x < 1750
    )
    SELECT vp.label_occupation, s.numeric_value as year, 
        cnt.x || '_' || cnt.y as generation
    FROM v_pursuits vp, "statement" s, cnt
    WHERE vp.pk_person = s.fk_subject_instance 
    AND s.property_uri = 'http://dbpedia.org/ontology/birthYear'
    AND s.numeric_value >= cnt.x 
    AND s.numeric_value < cnt.y;

## Coder les occupations

### Ajouter à la base de données cette relation

    occupation (classe 2) --is classified by--> occupation_class (classe )

### Créer la vue correspondante

    CREATE VIEW v_occupation_classes AS
    SELECT i.pk_instance, i.label, i2.pk_instance, i2.label 
    FROM "instance" i 
    LEFT JOIN "statement" s 
        ON s.fk_subject_instance = i.pk_instance AND s.fk_property = 4 
    LEFT JOIN "instance" i2 ON s.fk_object_instance = i2.pk_instance AND i2.fk_class = 5 
    WHERE i.fk_class = 2;

    SELECT *
    FROM v_occupation_classes;

Après quelques ajouts à la main, ajouté toutes les lignes statements nécessaires, puis remplies:

    INSERT INTO "statement" (fk_subject_instance, fk_property)
    SELECT pk_instance, 4
    FROM "instance" i 
    WHERE pk_instance BETWEEN 292 AND 500
    AND fk_class = 2;

### Vérifier les codes renseignés:

    SELECT pk_instance_object, label_object, COUNT(), 
	GROUP_CONCAT(label, '; ') occupations
    FROM v_occupation_classes voc 
    GROUP BY pk_instance_object
    ORDER BY label_object ;

## Compter les occupations par génération

On utilise les classes précédemment créés

    WITH RECURSIVE
    cnt(x,y) AS (
        SELECT 1441,1460
        UNION ALL
        SELECT x+20, y+20 FROM cnt
        WHERE x < 1750
    ),
    TW2 AS (
    SELECT vp.label_occupation, voc.label_object occupation_class, s.numeric_value as year, 
        cnt.x || '_' || cnt.y as generation
    FROM v_pursuits vp, "statement" s, cnt, v_occupation_classes voc 
    WHERE vp.pk_person = s.fk_subject_instance 
    AND s.property_uri = 'http://dbpedia.org/ontology/birthYear'
    AND s.numeric_value >= cnt.x 
    AND s.numeric_value < cnt.y
    AND voc.pk_instance = vp.pk_occupation
    -- la prochaie clause exclut les lignes non significatives car non définies
    AND voc.label_object NOT LIKE 'Diver%'	)
    SELECT generation, occupation_class, count(*) as effectif
    FROM tw2
    GROUP BY occupation_class, generation
    ORDER BY generation, occupation_class;

On exporte ensuite le résultat sour forme de CSV (texte séparé par virgule) et on l'ouvre dans un tableur, Calc de la suite LibreOffice pour ce qui me concerne.

### Créer une table pivot

Dans le tableur Calc créer une table pivot à partir des trois colonnes (bouton à droite de celui qui créé les diagrammes)

Glisser les colonnes et prendre la fonction SUM

J'ai ensuite calculé le tableau d'écart à l'indépendance et réalisé un graphique à barres superposées


