Ce modèle est issu de la transcription sour forme relationnelle du modèle conceptuel

Cf. [cette page](http://phn-wiki.ish-lyon.cnrs.fr/doku.php?id=intro_histoire_numerique:modele_logique&#le_modele_logique_ou_relationnel) et celle-ci: [[How to Convert ER Diagram to Relational Database|https://www.learndb.com/databases/how-to-convert-er-diagram-to-relational-database]]

<br/>

person(pk_person, name, definition, gender, death_date, fk_birth, notes)

appellation(pk_appellation, pk_person, name, sources, notes)

tag(pk_tag, fk_parent_tag, name, definition, notes)

tags(pk_tags, fk_person, fk_tag, notes)

pursuit(pk_pursuit, fk_person, fk_occupation, fk_organisation, begin_date, end_date, sources, notes)

organisation(pk_organisation, fk_geographical_place, name, definition, notes)

occupation(pk_occupation, name, definition, notes)

specializes_occupation(pk_specializes_occupation, fk_parent_occupation, fk_child_occupation, notes)

birth(pk_birth, date, fk_geographical_place, fk_union, sources, notes)

union(pk_union, fk_union_type, begin_date, end_date, fk_person_1, fk_person_2, sources, notes)

union_type(pk_union_type, name, definition, notes)

geographical_place(pk_geographical_place, name, definition, longitude,latitude, fk_geographical_place_type, notes)

geographical_place_type(pk_geographical_place_type, name, definition, fk_parent_geographical_place_type, notes) 