# Information de base

## Personnes avec année de naissance

    SELECT i.pk_instance, i.label, s.numeric_value 
    FROM "instance" i,"statement" s
    WHERE i.pk_instance = s.fk_subject_instance 
    AND i.fk_class = 1
    AND s.property_uri LIKE '%birthY%'
    LIMIT 10;