# Fiche d'analyse du jeu de données

## Identification

- **Groupe** : Groupe-09
- **Date** : 2026
- **Nom du jeu de données** : Higher Education Sample
- **Source / producteur** : Dataset pédagogique (ENSIAS / TP Linked Data)
- **URL de la source** : (local)
- **Domaine métier** : Enseignement supérieur

## Description générale

- **Objectif du jeu de données** : Décrire des établissements d’enseignement supérieur avec leurs caractéristiques (localisation, classement, etc.)
- **Format(s) disponible(s)** : CSV
- **Langue(s)** : francais
- **Licence** : Non précisée
- **Fréquence de mise à jour** : Inconnue
- **Unité d'observation** : Un établissement universitaire
- **Granularité des enregistrements** : 1 ligne = 1 université

Explication : dataset simple → bon pour analyse mais limité pour LOD réel

---

## Structure du jeu de données

| Champ / colonne | Signification | Exemple de valeur | Observation |
| --- | --- | --- | --- |
| University | Nom de l’université | ENSIAS | Texte non normalisé |
| City | Ville | Rabat | Peut être ambigu |
| Country | Pays | Morocco | Réutilisable |
| Ranking | Classement | 1 | Numérique |
| Students | Nombre d’étudiants | 1200 | Peut varier |
| Website | Site web | ensias.ma | Bon candidat identifiant |

---

## Évaluation "Open Data"

| Critère | Observation | Score / 5 |
| --- | --- | --- |
| Accessibilité | Fichier simple accessible | 5 |
| Réutilisabilité | Format exploitable | 4 |
| Documentation | Très limitée | 2 |
| Format exploitable | CSV structuré | 5 |
| Présence d'une licence | Absente | 1 |

Explication : bon techniquement mais faible documentation

---

## Évaluation "Linked Data readiness"

| Point observé | Oui / Non / Partiel | Commentaire |
| --- | --- | --- |
| Identifiants stables pour les enregistrements | Non | Pas d’ID unique |
| Entités clairement distinguables | Oui | Université, Ville, Pays |
| Valeurs normalisées | Partiel | Noms non contrôlés |
| Informations géographiques exploitables | Oui | Ville / Pays |
| Possibilité de lien vers des référentiels externes | Oui | Wikidata possible |
| Présence de clés candidates plausibles | Oui | Nom + site |
| Présence de codes ou nomenclatures réutilisables | Non | Aucun code |

---

## Maturité "5 étoiles"

| Niveau | Atteint ? | Justification |
| --- | --- | --- |
| 1 étoile | Oui | Données disponibles |
| 2 étoiles | Oui | Structuré |
| 3 étoiles | Oui | CSV (non propriétaire) |
| 4 étoiles | Non | Pas d’URI |
| 5 étoiles | Non | Pas de liens |

Niveau global : ⭐⭐⭐ (3/5)

---

## Clés candidates et identifiants

| Objet ou entité cible | Champ(s) candidat(s) | Fiabilité | Limites | Recommandation |
| --- | --- | --- | --- | --- |
| Université | Nom + Website | Moyenne | Nom ambigu | Créer ID |
| Ville | Nom ville | Faible | Homonymes | GeoNames |
| Pays | Nom pays | Élevée | Peu de risques | ISO code |

---

## Normalisation préalable nécessaire

| Champ | Problème observé | Impact pour le LOD | Action recommandée |
| --- | --- | --- | --- |
| University | Variations de noms | Mauvais matching | Standardiser |
| City | Ambiguïtés | Mauvais lien externe | Normaliser |
| Country | Variations possibles | Liens incorrects | ISO codes |

---

## Qualité des données

- **Forces observées** :
  - Structure simple
  - Données compréhensibles
  - Champs utiles pour linking

- **Faiblesses observées** :
  - Pas d’identifiant unique
  - Pas de normalisation
  - Peu de métadonnées

- **Ambiguïtés ou doublons potentiels** :
  - Universités avec noms similaires
  - Villes homonymes

- **Champs manquants** :
  - ID unique
  - coordonnées GPS
  - type d’établissement

- **Risque principal** :
  Mauvais appariement avec sources externes

---

## Conclusion courte

Ce jeu de données constitue une base correcte pour une transformation vers les données ouvertes liées, notamment grâce à sa structure simple et la présence d’entités identifiables comme les universités, les villes et les pays. Toutefois, l’absence d’identifiants stables et de normalisation des valeurs constitue un frein important. Pour une intégration efficace dans un écosystème LOD, il sera nécessaire de définir des identifiants uniques, de normaliser les noms (notamment géographiques) et d’établir des correspondances fiables avec des référentiels externes comme Wikidata ou GeoNames. Avec ces améliorations, ce dataset pourrait évoluer vers un graphe de données interopérable et enrichi.