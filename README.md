# Extracteur SHERPA-RoMEO
Tableau d'extraction des durées d'embargo de postprints, via les ISSN requêtés dans l'API SHERPA RoMEO.

## Clé d'accès à l'API SHERPA RoMEO
L'API SHERPA RoMEO limite le nombre de requêtes à 500 / jour. Enregistrez-vous pour lever cette limitation :

http://www.sherpa.ac.uk/romeo/apiregistry.php

Vous recevrez une clé d'accès à l'API Sherpa. Collez-la dans l'onglet "Clé Sherpa" dans la cellule D2.

## Extraction Sherpa
Collez une liste d'ISSN dans l'onglet "Extraction Sherpa" dans la colonne A. Quelques ISSN d'exemples sont proposés dans l'onglet "Exemples ISSN".

Sélectionnez les cellules A2:W2.

Faites glisser le cadre jusqu'au dernier ISSN de la liste.

--> Les conditions d'embargo de postprint, et la durée d'embargo des postprints en mois le cas échéant, s'affichent dans la colonne B : "Bilan postprint".

## Pour compléter la recherche des conditions d'embargo de postprint
L'API SHERPA-RoMEO renvoie un résultat au format XML (colonne H).

Le résultat contient une balise `<postarchiving>` pour le dépôt du postprint, qui peut contenir les valeurs can, cannot, restricted, unknown etc. Par exemple : `<postarchiving>can</postarchiving>`.

Le résultat contient également un ensemble de balises `<condition>` parmi lesquelles une concerne la durée d'embargo du postprint, par exemple : `<condition>Author's post-print after 12 months after publication</condition>`. Ces conditions sont extraites dans les colonnes J:W et leur texte concaténé en colonne X.

Une fonction analyse ces métadonnées au format XML pour afficher un bilan des conditions de  dépôt de postprints (colonne B) :
- On écarte les postprints interdits,
- Dans la concaténation des conditions (colonne X), on recherche toutes les chaînes de caractères que SHERPA utilise pour indiquer les conditions d'embargo de postprint. Lorsqu'il y a une correspondance, on a la durée d'embargo.

Cette fonction est mise à disposition séparémment dans les fichiers Requête Sherpa désindentée, indentée, et commentée pour faciliter sa compréhension et sa modification si besoin. À ouvrir de préférence dans un éditeur de code comme Notepad++.
