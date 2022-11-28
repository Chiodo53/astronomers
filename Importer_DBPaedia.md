
-- compter les instances
SELECT COUNT(*)
FROM "instance" i ;

-- regrouper les instances par classe  
SELECT c.label, COUNT(*) eff
FROM "instance" i, class c 
WHERE i.fk_class = c.pk_class 
GROUP BY c.label 
ORDER BY eff DESC ;



-- inspecter les instances avec les propriétés
SELECT i.pk_instance, i.external_uri, s.pk_statement, s.subject_uri 
FROM "instance" i , "statement" s 
WHERE s.subject_uri = i.external_uri ;


-- ajouter les valeurs de clé étrangère entre les assertions et les instances
UPDATE "statement"  set fk_subject_instance = i.pk_instance 
FROM "instance" i 
WHERE "statement".subject_uri = i.external_uri ;

-- lister les dates de naissance
SELECT i.label, SUBSTRING(s.text_value, 1, 4)
FROM "instance" i , "statement" s 
WHERE s.fk_subject_instance  = i.pk_instance
AND s.property_uri LIKE '%birthDat%';

-- effectif des dates de naissance inférieures à 1771
SELECT COUNT(*) 
FROM "instance" i , "statement" s 
WHERE s.fk_subject_instance  = i.pk_instance
AND s.property_uri LIKE '%birthDat%'
AND SUBSTRING(s.text_value, 1, 4) < '1771';

-- même requêtes que la précédente avec transformation de type de valeur
SELECT COUNT(*) 
FROM "instance" i , "statement" s 
WHERE s.fk_subject_instance  = i.pk_instance
AND s.property_uri LIKE '%birthDat%'
AND CAST(SUBSTRING(s.text_value, 1, 4) AS INT) < 1770;




