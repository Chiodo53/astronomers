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

