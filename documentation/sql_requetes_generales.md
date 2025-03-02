# Table _Instance_

## Ensemble des classes avec liste individus

    SELECT i.fk_class, c.label, COUNT(*) as effectif 
    FROM "instance" i, class c 
    WHERE c.pk_class = i.fk_class 
    GROUP BY i.fk_class 
    ORDER BY effectif DESC ;

&nbsp;

# Table _Statement_

## Exploration de la partie RDF

### Regrouper par _property_uri_ et compter

    SELECT property_uri, count(*) AS effectif  
    FROM "statement" s 
    GROUP BY property_uri 
    ORDER BY effectif DESC;


### Regrouper par métadonnées d'importation

    SELECT import_metadata, count(*) AS effectif  
    FROM "statement" s 
    GROUP BY import_metadata 
    ORDER BY effectif DESC;

# Création de vues génériques

## Vue qui liste l'ensemble des propriétés avec classe domain et range

    --DROP VIEW v_classes_properties;
    CREATE VIEW v_classes_properties AS
    SELECT 'outgoing' as direction, c.pk_class, c.label, c.class_type, 
        p.pk_property, p.label, p.inverse_label, p.definition,
        c1.pk_class as pk_target_class, c1.label target_class_label, c1.class_type target_class_type 
    FROM class c, property p, class c1
    WHERE p.has_domain = c.pk_class
    AND c1.pk_class = p.has_range
    UNION 
    SELECT 'incoming' as direction, c.pk_class, c.label, c.class_type, 
        p.pk_property, p.inverse_label AS label, p.label AS inverse_label,  p.definition,
        c1.pk_class, c1.label , c1.class_type 
    FROM class c, property p, class c1
    WHERE p.has_range = c.pk_class
    AND c1.pk_class = p.has_domain;

## Interroger la vue

    SELECT  *
    FROM v_classes_properties;

