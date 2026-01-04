# ACP - Base Comparateur de Territoires INSEE
## Analyse en Composantes Principales des communes françaises
### Master 1 Statistique - Cours E. Périnel (2024-2025)
**CHERIET Abdelmalek** - Étudiant en M1 Statistique - Université de Strasbourg

---

## 📄 RAPPORT COMPLET (Cliquez pour ouvrir)

### 👉 [**OUVRIR LE RAPPORT ACP AVEC TOUS LES GRAPHIQUES**](https://abdel67unistra.github.io/ACP-INSPEE-ADD-PROJET/Rapport_ACP_Resultats.html) 👈

> Ce rapport contient toutes les images de l'analyse avec leurs interprétations détaillées.

---

## 📖 Table des matières

### 📌 Introduction
1. [📍 Mise en situation](#-mise-en-situation)
2. [🎓 Pourquoi une ACP et pas une AFC ou ACM ?](#-pourquoi-une-acp-et-pas-une-afc-ou-acm-)
3. [🔗 Source des données](#-source-des-données)

### 📌 Description des données
4. [📚 Dictionnaire complet des variables](#-dictionnaire-complet-des-variables)
5. [🔢 Variables de l'analyse ACP](#-variables-de-lanalyse-acp)

### 📌 Méthodologie
6. [🎯 L'ACP en 5 étapes (PICCI)](#-lacp-en-5-étapes-picci)
7. [🔧 Fonctions R utilisées](#-fonctions-r-utilisées)

### 📌 Résultats de l'analyse
8. [📈 Interprétation des résultats](#-interprétation-des-résultats)
9. [📊 Sorties R détaillées](#-sorties-r-détaillées-et-leur-interprétation)
10. [🖼️ Graphiques de l'ACP](#%EF%B8%8F-graphiques-de-lanalyse-acp)
    - [Graphique 1 : Matrice de corrélation](#-graphique-1--matrice-de-corrélation)
    - [Graphique 2 : Éboulis des valeurs propres](#-graphique-2--éboulis-des-valeurs-propres-scree-plot)
    - [Graphique 3 : Critère du bâton brisé](#-graphique-3--critère-du-bâton-brisé)
    - [Graphique 4 : Cercle des corrélations](#-graphique-4--cercle-des-corrélations-dim1-dim2)
    - [Graphique 5 : Cercle avec contributions](#-graphique-5--cercle-avec-contributions-en-couleur)
    - [Graphique 6 : Cercle avec cos²](#-graphique-6--cercle-avec-cos-en-couleur)
    - [Graphique 7 : Contributions axe 1](#-graphique-7--contributions-des-variables-à-laxe-1)
    - [Graphique 8 : Contributions axe 2](#-graphique-8--contributions-des-variables-à-laxe-2)
    - [Graphique 9 : Contributions plan 1-2](#-graphique-9--contributions-au-plan-1-2)
    - [Graphique 10 : Qualité cos²](#-graphique-10--qualité-de-représentation-cos)
    - [Graphique 11 : Nuage des individus](#-graphique-11--nuage-des-individus-communes)
    - [Graphique 12 : Individus sélectionnés](#-graphique-12--individus-bien-représentés-cos--05)
    - [Graphique 13 : Top contributeurs](#-graphique-13--top-30-communes-contributrices-axe-1)
    - [Graphique 14 : Biplot](#-graphique-14--biplot-individus--variables)
    - [Graphique 15 : Heatmap corrélations](#-graphique-15--corrélations-variables-axes-heatmap)
    - [Graphique 16 : Cercle Dim1-Dim3](#-graphique-16--cercle-des-corrélations-dim1-dim3)
11. [📋 Sorties numériques détaillées](#-sorties-numériques-détaillées)
12. [📝 COMPTE-RENDU DES RÉSULTATS](#-compte-rendu-des-résultats-de-lacp)

### 📌 Cours complet et Présentation
13. [📘 COURS COMPLET : La recette de l'ACP](#-cours-complet--la-recette-de-lacp-pour-la-présentation)
    - [Qu'est-ce que l'ACP ?](#-quest-ce-que-lacp-)
    - [Les 5 étapes PICCI](#-les-5-étapes-de-lacp--picci)
    - [Étape 1 : Préparation](#-étape-1--préparation-p)
    - [Étape 2 : Inertie](#-étape-2--inertie-i---valeurs-propres)
    - [Étape 3 : Cercle](#-étape-3--cercle-des-corrélations-c)
    - [Étape 4 : Contributions](#-étape-4--contributions-c)
    - [Étape 5 : Individus](#-étape-5--individus-i)
14. [📊 Traduction des 16 graphiques](#-traduction-complète-des-16-graphiques)
15. [🎓 Questions de présentation et réponses](#-questions-de-présentation-et-réponses)
    - [Questions sur les définitions](#-questions-sur-les-définitions)
    - [Questions sur les critères](#-questions-sur-les-critères)
    - [Questions sur l'interprétation](#-questions-sur-linterprétation)
    - [Questions sur notre analyse](#-questions-sur-notre-analyse)
    - [Questions sur la méthode](#-questions-sur-la-méthode)
    - [Questions pièges](#-questions-pièges)
16. [📋 Checklist avant présentation](#-checklist-avant-présentation)

### 📌 Annexes
17. [🧠 Mnémotechniques étudiant](#-mnémotechniques-étudiant)
18. [📁 Structure du projet](#-structure-du-projet)
19. [📚 Références](#-références)
20. [✍️ Auteur](#%EF%B8%8F-auteur)

---

## 📍 Mise en situation

### Contexte général
La France métropolitaine et d'outre-mer compte environ **35 000 communes**, des grandes métropoles comme Paris, Lyon ou Marseille aux petits villages ruraux de quelques dizaines d'habitants. Cette diversité territoriale se traduit par des **inégalités socio-économiques** importantes : certaines communes concentrent richesse, emplois et services, tandis que d'autres souffrent de désertification, vieillissement et précarité.

### Problématique de l'étude
En tant qu'analyste statisticien, vous êtes mandaté pour répondre aux questions suivantes :

> **Comment caractériser et visualiser la diversité des territoires français ?**

Plus précisément :
- Quelles sont les **grandes dimensions** qui structurent les différences entre communes ?
- Peut-on identifier des **profils-types** de territoires ? (urbain dense, rural agricole, touristique, industriel, précarisé...)
- Quelles **variables** sont les plus discriminantes pour distinguer les territoires ?
- Comment se positionnent les différents **départements** dans cette diversité ?

### Pourquoi l'ACP est pertinente ici ?
Avec **32 variables** décrivant chaque commune (démographie, logement, revenus, emploi, établissements...), il est impossible de visualiser directement les données. L'**Analyse en Composantes Principales** permet de :

| Objectif | Comment l'ACP y répond |
|----------|------------------------|
| Réduire la complexité | Passer de 12+ variables à 2-3 axes synthétiques |
| Visualiser les territoires | Projeter les 35 000 communes sur un plan 2D |
| Identifier les variables clés | Cercle des corrélations |
| Détecter des groupes | Clusters visuels sur le nuage d'individus |
| Repérer les communes atypiques | Individus éloignés du centre |

---

### 🎓 Pourquoi une ACP et pas une AFC ou ACM ?

En analyse des données, le choix de la méthode factorielle dépend de la **nature des variables** :

| Méthode | Type de données | Exemple |
|---------|-----------------|---------|
| **ACP** (Analyse en Composantes Principales) | Variables **quantitatives continues** | Revenus (€), taux (%), densité (hab/km²) |
| **AFC** (Analyse Factorielle des Correspondances) | **Tableau de contingence** (2 variables qualitatives) | Profession × Région |
| **ACM** (Analyse des Correspondances Multiples) | Variables **qualitatives** (catégorielles) | Diplôme (Bac/Licence/Master), CSP (Cadre/Employé/Ouvrier) |

#### 📊 Nature de nos données INSEE

Nos 11 variables sont toutes **quantitatives continues** :

| Variable | Type | Valeurs |
|----------|------|---------|
| `densite_pop` | Quantitative | 0.5 à 25 000 hab/km² |
| `taux_natalite` | Quantitative | 0 à 30 ‰ |
| `taux_mortalite` | Quantitative | 0 à 50 ‰ |
| `taux_proprietaires` | Quantitative | 20 à 95 % |
| `MED21` | Quantitative | 12 000 à 50 000 €/an |
| `taux_chomage` | Quantitative | 0 à 35 % |
| `pct_agriculture` | Quantitative | 0 à 100 % |
| `pct_industrie` | Quantitative | 0 à 80 % |
| `pct_services` | Quantitative | 0 à 100 % |
| ... | ... | ... |

#### ❌ Pourquoi pas l'AFC ?

L'**AFC** nécessite un **tableau de contingence** (effectifs croisés entre 2 variables qualitatives).

Exemple où l'AFC serait appropriée :
```
              | Île-de-France | Bretagne | PACA | ...
--------------+---------------+----------+------+-----
Agriculteurs  |     5 200     |  18 400  | 8 900| ...
Cadres        |   890 000     |  42 000  |95 000| ...
Ouvriers      |   320 000     |  78 000  |89 000| ...
```

➡️ **Notre cas** : Nous n'avons pas de tableau de contingence. Nos données sont un tableau **individus × variables quantitatives**.

#### ❌ Pourquoi pas l'ACM ?

L'**ACM** est conçue pour des **variables qualitatives** (catégorielles).

Exemple où l'ACM serait appropriée :
```
Commune | Type_zone | Niveau_revenu | Démographie
--------|-----------|---------------|------------
Paris   | Urbain    | Élevé         | Jeune
Aurillac| Rural     | Moyen         | Vieillissant
Nice    | Littoral  | Élevé         | Mixte
```

➡️ **Notre cas** : Nos variables sont des **valeurs numériques continues** (taux, pourcentages, euros), pas des catégories.

#### ✅ Pourquoi l'ACP est le bon choix ?

| Critère | Notre jeu de données | Méthode adaptée |
|---------|---------------------|-----------------|
| Nature des variables | Quantitatives continues | ✅ **ACP** |
| Structure du tableau | Individus × Variables | ✅ **ACP** |
| Objectif | Réduire la dimensionnalité | ✅ **ACP** |
| Visualisation | Cercle des corrélations | ✅ **ACP** |

**Conclusion** : L'ACP est la méthode factorielle adaptée car :
1. ✅ Nos 11 variables sont **quantitatives** (pas qualitatives)
2. ✅ Notre tableau est de type **individus × variables** (pas un tableau de contingence)
3. ✅ Nous cherchons des **combinaisons linéaires** des variables
4. ✅ Nous voulons identifier les **corrélations** entre variables

> 💡 **Remarque** : On pourrait compléter cette ACP par une **Classification Ascendante Hiérarchique (CAH)** pour regrouper les communes en clusters, ou projeter une variable qualitative en **illustrative** (comme le département).

---

### Enjeux pratiques
Cette analyse peut servir à :
- **Aménagement du territoire** : identifier les zones à revitaliser
- **Politiques sociales** : cibler les communes en difficulté
- **Développement économique** : comprendre les dynamiques locales
- **Études épidémiologiques** : contextualiser des données de santé

---

## 🔗 Source des données

### Informations générales

| Caractéristique | Détail |
|-----------------|--------|
| **Producteur** | INSEE (Institut National de la Statistique et des Études Économiques) |
| **Nom de la base** | Base du comparateur de territoires |
| **URL officielle** | https://www.insee.fr/fr/statistiques/2521169 |
| **Date de parution** | 02/09/2025 (mise à jour régulière) |
| **Géographie** | France métropolitaine + DOM-TOM |
| **Niveau géographique** | Commune, arrondissement municipal |
| **Format disponible** | CSV (3 Mo zippé), XLSX (10 Mo zippé) |

### Téléchargement direct
- **CSV** : https://www.insee.fr/fr/statistiques/fichier/2521169/base_cc_comparateur_csv.zip
- **Excel** : https://www.insee.fr/fr/statistiques/fichier/2521169/base_cc_comparateur_xlsx.zip

### Caractéristiques techniques du fichier

| Propriété | Valeur |
|-----------|--------|
| **Nom du fichier** | `base_cc_comparateur.csv` |
| **Taille** | ~8 Mo (décompressé) |
| **Encodage** | UTF-8 |
| **Séparateur** | Point-virgule (`;`) |
| **Nombre de lignes** | ~35 000 communes |
| **Nombre de colonnes** | 32 variables |
| **Valeurs manquantes** | `s` (secret statistique), cellules vides |

### Millésimes des sources
Les données proviennent de plusieurs sources avec des années de référence différentes :

| Source | Année | Variables concernées |
|--------|-------|---------------------|
| Recensement de la population | 2022 | Population, ménages, logements, emploi |
| Recensement de la population | 2016 | Population historique |
| État civil | 2016-2021 | Naissances, décès (cumul 6 ans) |
| État civil | 2024 | Naissances, décès (année complète) |
| Filosofi | 2021 | Revenus, pauvreté |
| REE-Sirene | 2023 | Établissements économiques |

### Précautions d'utilisation
⚠️ **Secret statistique** : Certains indicateurs sont masqués (`s`) pour les petites communes afin de préserver la confidentialité des données individuelles.

⚠️ **Géographie** : Les données sont diffusées en géographie 2024/2025, les fusions de communes récentes sont prises en compte.

---

## 📚 Dictionnaire complet des variables

### Vue d'ensemble des 32 variables brutes

Le fichier contient **32 colonnes** organisées en 5 thématiques :

```
┌─────────────────────────────────────────────────────────────────┐
│                    32 VARIABLES INSEE                           │
├─────────────────────────────────────────────────────────────────┤
│ 🏷️ IDENTIFICATION (1)   │ CODGEO                                │
│ 👥 DÉMOGRAPHIE (6)      │ P22_POP, P16_POP, SUPERF,             │
│                         │ NAIS1621, DECE1621, P22_MEN,          │
│                         │ NAISD24, DECESD24                     │
│ 🏠 LOGEMENT (5)         │ P22_LOG, P22_RP, P22_RSECOCC,         │
│                         │ P22_LOGVAC, P22_RP_PROP               │
│ 💰 REVENUS (4)          │ NBMENFISC21, PIMP21, MED21, TP6021    │
│ 💼 EMPLOI (5)           │ P22_EMPLT, P22_EMPLT_SAL, P16_EMPLT,  │
│                         │ P22_POP1564, P22_CHOM1564, P22_ACT1564│
│ 🏭 ÉTABLISSEMENTS (8)   │ ETTOT23, ETAZ23, ETBE23, ETFZ23,      │
│                         │ ETGU23, ETOQ23, ETTEF123, ETTEFP1023  │
└─────────────────────────────────────────────────────────────────┘
```

### Tableau détaillé des variables

#### 🏷️ 1. Identification géographique

| N° | Code | Libellé complet | Type | Unité | Source |
|----|------|-----------------|------|-------|--------|
| 1 | `CODGEO` | Code du département suivi du numéro de commune ou d'arrondissement municipal | CHAR(5) | - | COG 2024 |

> **Exemple** : `75056` = Paris, `13055` = Marseille, `69123` = Lyon

#### 👥 2. Démographie et territoire

| N° | Code | Libellé complet | Type | Unité | Source | Année |
|----|------|-----------------|------|-------|--------|-------|
| 2 | `P22_POP` | Population municipale | NUM | habitants | RP | 2022 |
| 3 | `P16_POP` | Population municipale | NUM | habitants | RP | 2016 |
| 4 | `SUPERF` | Superficie | NUM | km² | IGN | 2024 |
| 5 | `NAIS1621` | Nombre de naissances domiciliées (cumul 2016-2021) | NUM | naissances | État civil | 2016-2021 |
| 6 | `DECE1621` | Nombre de décès domiciliés (cumul 2016-2021) | NUM | décès | État civil | 2016-2021 |
| 7 | `P22_MEN` | Nombre de ménages | NUM | ménages | RP | 2022 |
| 8 | `NAISD24` | Nombre de naissances domiciliées | NUM | naissances | État civil | 2024 |
| 9 | `DECESD24` | Nombre de décès domiciliés | NUM | décès | État civil | 2024 |

> **Interprétation** :
> - `P22_POP - P16_POP` = évolution démographique sur 6 ans
> - `NAIS1621 - DECE1621` = solde naturel sur 6 ans
> - Un ratio `NAIS/POP` élevé = commune jeune/dynamique

#### 🏠 3. Logement

| N° | Code | Libellé complet | Type | Unité | Source | Année |
|----|------|-----------------|------|-------|--------|-------|
| 10 | `P22_LOG` | Nombre de logements | NUM | logements | RP | 2022 |
| 11 | `P22_RP` | Nombre de résidences principales | NUM | logements | RP | 2022 |
| 12 | `P22_RSECOCC` | Nombre de résidences secondaires et logements occasionnels | NUM | logements | RP | 2022 |
| 13 | `P22_LOGVAC` | Nombre de logements vacants | NUM | logements | RP | 2022 |
| 14 | `P22_RP_PROP` | Nombre de résidences principales occupées par des propriétaires | NUM | logements | RP | 2022 |

> **Vérification** : `P22_LOG = P22_RP + P22_RSECOCC + P22_LOGVAC`
>
> **Interprétation** :
> - `P22_RSECOCC / P22_LOG` élevé = zone touristique (littoral, montagne)
> - `P22_LOGVAC / P22_LOG` élevé = zone en déclin démographique
> - `P22_RP_PROP / P22_RP` élevé = zone rurale, population stable

#### 💰 4. Revenus et pauvreté

| N° | Code | Libellé complet | Type | Unité | Source | Année |
|----|------|-----------------|------|-------|--------|-------|
| 15 | `NBMENFISC21` | Nombre de ménages fiscaux | NUM | ménages | Filosofi | 2021 |
| 16 | `PIMP21` | Part des ménages fiscaux imposés | NUM | % | Filosofi | 2021 |
| 17 | `MED21` | Médiane du niveau de vie | NUM | € / an | Filosofi | 2021 |
| 18 | `TP6021` | Taux de pauvreté (seuil à 60%) | NUM | % | Filosofi | 2021 |

> **Définitions** :
> - **Niveau de vie** = revenu disponible du ménage / nombre d'UC (unités de consommation)
> - **Médiane** = 50% des habitants ont un niveau de vie inférieur
> - **Taux de pauvreté** = part de la population sous le seuil de pauvreté (60% du niveau de vie médian national ≈ 13 000 €/an)
>
> **Interprétation** :
> - `MED21` élevé (> 25 000 €) = commune aisée
> - `TP6021` > 20% = commune en difficulté sociale

#### 💼 5. Emploi et activité

| N° | Code | Libellé complet | Type | Unité | Source | Année |
|----|------|-----------------|------|-------|--------|-------|
| 19 | `P22_EMPLT` | Nombre d'emplois au lieu de travail | NUM | emplois | RP | 2022 |
| 20 | `P22_EMPLT_SAL` | Nombre d'emplois salariés au lieu de travail | NUM | emplois | RP | 2022 |
| 21 | `P16_EMPLT` | Nombre d'emplois au lieu de travail | NUM | emplois | RP | 2016 |
| 22 | `P22_POP1564` | Population de 15 à 64 ans | NUM | habitants | RP | 2022 |
| 23 | `P22_CHOM1564` | Chômeurs de 15 à 64 ans | NUM | personnes | RP | 2022 |
| 24 | `P22_ACT1564` | Actifs de 15 à 64 ans | NUM | personnes | RP | 2022 |

> **Formules utiles** :
> - **Taux de chômage** = `P22_CHOM1564 / P22_ACT1564 × 100`
> - **Taux d'activité** = `P22_ACT1564 / P22_POP1564 × 100`
> - **Ratio emploi/population** = `P22_EMPLT / P22_POP1564 × 100`
>
> **Interprétation** :
> - `P22_EMPLT / P22_POP` > 0.5 = pôle d'emploi (plus d'emplois que d'habitants actifs)
> - `P22_EMPLT - P16_EMPLT` = création/destruction d'emplois sur 6 ans

#### 🏭 6. Établissements économiques (REE-Sirene 2023)

| N° | Code | Libellé complet | Type | Unité | Secteur NAF |
|----|------|-----------------|------|-------|-------------|
| 25 | `ETTOT23` | Nombre total d'établissements actifs | NUM | établ. | Tous |
| 26 | `ETAZ23` | Nombre d'établissements actifs de l'agriculture, sylviculture et pêche | NUM | établ. | Section A |
| 27 | `ETBE23` | Nombre d'établissements actifs de l'industrie | NUM | établ. | Sections B-E |
| 28 | `ETFZ23` | Nombre d'établissements actifs de la construction | NUM | établ. | Section F |
| 29 | `ETGU23` | Nombre d'établissements actifs du commerce, transports et services divers | NUM | établ. | Sections G-U (hors O-Q) |
| 30 | `ETOQ23` | Nombre d'établissements actifs de l'administration publique, enseignement, santé et action sociale | NUM | établ. | Sections O-Q |
| 31 | `ETTEF123` | Nombre d'établissements actifs de 1 à 9 salariés | NUM | établ. | Tous |
| 32 | `ETTEFP1023` | Nombre d'établissements actifs de 10 salariés ou plus | NUM | établ. | Tous |

> **Vérification** : `ETTOT23 = ETAZ23 + ETBE23 + ETFZ23 + ETGU23 + ETOQ23`
>
> **Nomenclature NAF (sections)** :
> - **A** : Agriculture, sylviculture, pêche
> - **B-E** : Industries extractives, manufacturières, énergie, eau
> - **F** : Construction
> - **G-U** : Commerce, transport, hébergement, information, finance, immobilier, services...
> - **O** : Administration publique
> - **P** : Enseignement
> - **Q** : Santé humaine et action sociale
>
> **Interprétation** :
> - `ETAZ23 / ETTOT23` élevé = commune rurale/agricole
> - `ETGU23 / ETTOT23` élevé = commune tertiaire/urbaine
> - `ETTEFP1023 / ETTOT23` élevé = présence de moyennes/grandes entreprises

---

## 🔢 Variables de l'analyse ACP

### Pourquoi transformer les variables ?
Les variables brutes (effectifs) dépendent de la **taille de la commune** :
- Paris a 2 millions d'habitants, Rochefourchat (Drôme) en a 1
- Comparer les valeurs brutes n'a pas de sens statistique

**Solution** : Calculer des **ratios, taux et pourcentages** qui sont comparables quelle que soit la taille de la commune.

### 12 Variables quantitatives actives

Ces 12 variables dérivées sont utilisées pour l'ACP :

| N° | Variable créée | Formule de calcul | Interprétation | Unité |
|----|----------------|-------------------|----------------|-------|
| 1 | `densite_pop` | `P22_POP / SUPERF` | Concentration spatiale de la population | hab/km² |
| 2 | `taux_natalite` | `(NAIS1621 / 6) / P22_POP × 1000` | Dynamisme démographique, jeunesse | ‰ |
| 3 | `taux_mortalite` | `(DECE1621 / 6) / P22_POP × 1000` | Vieillissement de la population | ‰ |
| 4 | `taux_res_secondaires` | `P22_RSECOCC / P22_LOG × 100` | Attractivité touristique, littoral/montagne | % |
| 5 | `taux_logements_vacants` | `P22_LOGVAC / P22_LOG × 100` | Désertification, déclin démographique | % |
| 6 | `taux_proprietaires` | `P22_RP_PROP / P22_RP × 100` | Stabilité résidentielle, ruralité | % |
| 7 | `MED21` | Variable brute INSEE | Niveau de vie médian | €/an |
| 8 | `TP6021` | Variable brute INSEE | Précarité économique | % |
| 9 | `taux_chomage` | `P22_CHOM1564 / P22_ACT1564 × 100` | Dynamisme économique (inverse) | % |
| 10 | `pct_agriculture` | `ETAZ23 / ETTOT23 × 100` | Ruralité, activité primaire | % |
| 11 | `pct_industrie` | `ETBE23 / ETTOT23 × 100` | Tissu industriel historique | % |
| 12 | `pct_services` | `ETGU23 / ETTOT23 × 100` | Tertiarisation, urbanité | % |

### Variable qualitative illustrative

| Variable | Définition | Rôle dans l'ACP |
|----------|------------|-----------------|
| `departement` | 2 premiers caractères de CODGEO | Ne participe pas au calcul, aide à l'interprétation |

### Corrélations attendues entre variables

```
Variables corrélées positivement (→) :
  • densite_pop ↔ pct_services (urbanisation)
  • taux_natalite ↔ MED21 (communes aisées et jeunes)
  • taux_mortalite ↔ pct_agriculture (communes rurales vieillissantes)
  • taux_logements_vacants ↔ pct_agriculture (déclin rural)

Variables corrélées négativement (↔) :
  • densite_pop ↔ pct_agriculture (urbain vs rural)
  • MED21 ↔ TP6021 (richesse vs pauvreté)
  • taux_proprietaires ↔ densite_pop (rural vs urbain)
  • pct_services ↔ pct_agriculture (tertiaire vs primaire)
```

---

## 🎯 L'ACP en 5 étapes (PICCI)

### Mnémonique PICCI
> **P**réparation → **I**nertie → **C**ercle → **C**ontributions → **I**ndividus

### Étape 1 : **P**réparation
**But** : Préparer les données pour l'analyse

| Action | Fonction R | Explication |
|--------|-----------|-------------|
| Charger les données | `read.csv()` | Importation du CSV |
| Sélectionner variables | `df[, vars]` | Garder les variables pertinentes |
| Nettoyer les NA | `na.omit()` | Supprimer les lignes incomplètes |
| Centrer-réduire | `scale.unit = TRUE` | Ramener à même échelle |

**Pourquoi centrer-réduire ?**
- Revenu médian : 18 000 - 40 000 €
- Taux de chômage : 0 - 30 %
- Sans normalisation, le revenu dominerait l'analyse !

### Étape 2 : **I**nertie (valeurs propres)
**But** : Déterminer combien d'axes garder

| Critère | Méthode | Application |
|---------|---------|-------------|
| Kaiser | λ > 1 | Garder les axes avec valeur propre > 1 |
| Coude | Visuel | Là où la courbe "casse" |
| Bâton brisé | Statistique | Comparer aux valeurs aléatoires |
| 80% inertie | Cumulé | Garder assez d'axes pour 80% |

**Fonctions R** : `fviz_eig()`, `brokenStick()`

### Étape 3 : **C**ercle des corrélations
**But** : Comprendre les relations entre variables

**Lecture du cercle :**
| Position | Signification |
|----------|---------------|
| Variable longue (près du cercle) | Bien représentée sur ce plan |
| Variables proches | Corrélées positivement |
| Variables opposées | Corrélées négativement |
| Variables perpendiculaires | Non corrélées |

**Fonction R** : `fviz_pca_var()`

### Étape 4 : **C**ontributions (CTR)
**But** : Identifier qui "fabrique" les axes

**Contribution (CTR)** = part de l'inertie d'un axe due à une variable/individu

| Si CTR... | Alors... |
|-----------|----------|
| > 100/p | Contribue fortement |
| ≈ 100/p | Contribue moyennement |
| < 100/p | Contribue faiblement |

Avec p = 12 variables → seuil = 100/12 = **8,3%**

**Fonctions R** : `fviz_contrib()`, `res.acp$var$contrib`

### Étape 5 : **I**ndividus
**But** : Projeter et interpréter les communes

| Analyse | Question | Fonction R |
|---------|----------|------------|
| Projection | Où se situent les communes ? | `fviz_pca_ind()` |
| Qualité | Sont-elles bien représentées ? | cos² |
| Contribution | Lesquelles "tirent" les axes ? | CTR |
| Biplot | Vue d'ensemble | `fviz_pca_biplot()` |

---

## 🔧 Fonctions R utilisées

### Packages chargés
```r
# "FaCoCo GPS" - mnémonique
library(FactoMineR)   # Fa - moteur ACP
library(factoextra)   # Co - graphiques ACP
library(corrplot)     # Co - matrices corrélation
library(ggplot2)      # G - graphiques avancés
library(psych)        # P - statistiques descriptives
library(skimr)        # S - résumé données
library(PCDimension)  # Bâton brisé
```

### Tableau des fonctions par étape

| Étape | Fonction | Package | Usage |
|-------|----------|---------|-------|
| **Préparation** |
| | `read.csv()` | base | Charger le CSV |
| | `na.omit()` | base | Supprimer les NA |
| | `cor()` | base | Matrice de corrélation |
| | `describe()` | psych | Stats descriptives |
| | `corrplot()` | corrplot | Visualiser corrélations |
| **ACP** |
| | `PCA()` | FactoMineR | Réaliser l'ACP |
| **Inertie** |
| | `fviz_eig()` | factoextra | Éboulis valeurs propres |
| | `brokenStick()` | PCDimension | Critère bâton brisé |
| **Variables** |
| | `fviz_pca_var()` | factoextra | Cercle corrélations |
| | `fviz_contrib()` | factoextra | Barplot contributions |
| | `fviz_cos2()` | factoextra | Qualité représentation |
| **Individus** |
| | `fviz_pca_ind()` | factoextra | Nuage des individus |
| | `fviz_pca_biplot()` | factoextra | Biplot ind + var |
| **Interprétation** |
| | `dimdesc()` | FactoMineR | Description des axes |

### Accès aux résultats (objet `res.acp`)

| Élément | Code R | Contenu |
|---------|--------|---------|
| Valeurs propres | `res.acp$eig` | λ, %, % cumulé |
| Coord. variables | `res.acp$var$coord` | Corrélations var-axes |
| Contrib. variables | `res.acp$var$contrib` | CTR des variables |
| Cos² variables | `res.acp$var$cos2` | Qualité variables |
| Coord. individus | `res.acp$ind$coord` | Position des communes |
| Contrib. individus | `res.acp$ind$contrib` | CTR des communes |
| Cos² individus | `res.acp$ind$cos2` | Qualité communes |

---

## 📈 Interprétation des résultats

### Lecture du cercle de corrélations
```
           +
           |     • taux_res_secondaires
           |     
     ------+------→ Axe 1 (ex: urbain/rural)
           |
           |     • pct_agriculture
           -
           Axe 2 (ex: riche/pauvre)
```

### Profils types attendus

| Profil | Caractéristiques | Position attendue |
|--------|------------------|-------------------|
| **Urbain dense** | Forte densité, services, loyers | Droite du plan |
| **Rural agricole** | Agriculture, propriétaires, faible densité | Gauche du plan |
| **Touristique** | Résidences secondaires, services | Haut du plan |
| **Industriel** | Industrie, emploi, ouvriers | Position spécifique |
| **Précarisé** | Chômage, pauvreté élevés | Selon axes |

### Questions d'interprétation
1. **Axe 1** : Quelle est l'opposition principale ?
2. **Axe 2** : Quelle nuance apporte-t-il ?
3. **Variables** : Lesquelles sont les plus discriminantes ?
4. **Communes atypiques** : Lesquelles sont loin du centre ?

---

## 📊 Sorties R détaillées et leur interprétation

Cette section décrit en détail chaque sortie produite par le script R `ACP_INSEE_Communes.R`.

---

## 🖼️ GRAPHIQUES DE L'ANALYSE ACP

### 📊 Graphique 1 : Matrice de corrélation

![Matrice de corrélation](images/01_matrice_correlation.png)

#### 🎓 Rappel théorique (cours)

**Qu'est-ce que la matrice de corrélation ?**

La matrice de corrélation **R** est une matrice carrée symétrique de dimension $p \times p$ (où p = nombre de variables) contenant les **coefficients de corrélation linéaire de Pearson** entre chaque paire de variables.

**Formule du coefficient de corrélation :**

$$r_{jk} = \frac{\sum_{i=1}^{n}(x_{ij} - \bar{x}_j)(x_{ik} - \bar{x}_k)}{\sqrt{\sum_{i=1}^{n}(x_{ij} - \bar{x}_j)^2} \sqrt{\sum_{i=1}^{n}(x_{ik} - \bar{x}_k)^2}} = \frac{Cov(X_j, X_k)}{\sigma_j \sigma_k}$$

**Propriétés importantes :**
- $r \in [-1, +1]$
- $r = +1$ : corrélation positive parfaite
- $r = -1$ : corrélation négative parfaite  
- $r = 0$ : absence de corrélation linéaire
- Diagonale = 1 (chaque variable est parfaitement corrélée avec elle-même)

**Lien avec l'ACP :**
> L'ACP sur données centrées-réduites revient à diagonaliser la matrice de corrélation R.
> Les valeurs propres de R sont les variances des composantes principales.

#### 📊 Description du graphique

- Matrice triangulaire inférieure montrant les corrélations entre les 11 variables
- **Bleu** = corrélation positive | **Rouge** = corrélation négative
- **Intensité de la couleur** = force de la corrélation
- Les coefficients sont affichés dans chaque case

#### 🔍 RÉSULTATS OBTENUS :

| Paire de variables | Corrélation | Interprétation |
|-------------------|-------------|----------------|
| `taux_proprietaires` ↔ `taux_chomage` | **r ≈ -0.56** | Opposition sociale : communes de propriétaires = moins précaires |
| `pct_services` ↔ `pct_agriculture` | **r ≈ -0.72** | Opposition urbain/rural très marquée |
| `MED21` ↔ `taux_chomage` | **r ≈ -0.45** | Lien revenus-emploi : communes riches = moins de chômage |
| `taux_mortalite` ↔ `taux_natalite` | **r ≈ -0.35** | Communes vieillissantes ≠ communes dynamiques |
| `densite_pop` ↔ `pct_agriculture` | **r ≈ -0.28** | Rural = faible densité (logique) |
| `taux_res_secondaires` ↔ `taux_logements_vacants` | **r ≈ +0.25** | Zones touristiques avec logements vides hors saison |

**💡 Conclusion :** La matrice révèle 2 grandes structures :
1. **Axe social** : propriétaires/revenus vs chômage/pauvreté
2. **Axe territorial** : urbain/services vs rural/agriculture

---

### 📊 Graphique 2 : Éboulis des valeurs propres (Scree Plot)

![Éboulis des valeurs propres](images/02_eboulis_valeurs_propres.png)

#### 🎓 Rappel théorique (cours)

**Qu'est-ce qu'une valeur propre ?**

En ACP, les **valeurs propres** $\lambda_1, \lambda_2, ..., \lambda_p$ sont obtenues par diagonalisation de la matrice de corrélation R :

$$R = V \Lambda V^T$$

où $\Lambda = diag(\lambda_1, ..., \lambda_p)$ et V est la matrice des vecteurs propres.

**Interprétation :**
- $\lambda_k$ = **variance de la k-ième composante principale**
- $\lambda_k$ = quantité d'information (inertie) capturée par l'axe k
- **Inertie totale** = $\sum_{k=1}^{p} \lambda_k = p$ (nombre de variables)
- **% d'inertie de l'axe k** = $\frac{\lambda_k}{p} \times 100$

**Critères de sélection du nombre d'axes :**

| Critère | Règle | Justification |
|---------|-------|---------------|
| **Kaiser** | $\lambda > 1$ | Un axe doit capturer plus qu'une variable seule |
| **Coude** | Cassure visuelle | Après le coude, les axes apportent peu |
| **% cumulé** | > 70-80% | Seuil arbitraire de "suffisamment d'info" |
| **Bâton brisé** | $\lambda_{obs} > \lambda_{H_0}$ | Comparaison à des données aléatoires |

#### 📊 Description du graphique

- Chaque barre = % d'inertie (variance) expliquée par l'axe
- La courbe relie les sommets des barres pour visualiser le "coude"
- Permet de décider combien d'axes conserver

#### 🔍 RÉSULTATS OBTENUS :

| Axe | Valeur propre (λ) | % Variance | % Cumulé | Critère Kaiser |
|-----|-------------------|------------|----------|----------------|
| **Dim 1** | 2.29 | 20.82% | 20.82% | ✅ λ > 1 |
| **Dim 2** | 2.20 | 19.98% | 40.80% | ✅ λ > 1 |
| **Dim 3** | 1.36 | 12.34% | 53.14% | ✅ λ > 1 |
| **Dim 4** | 1.12 | 10.16% | 63.30% | ✅ λ > 1 |
| Dim 5 | 0.94 | 8.55% | 71.85% | ❌ λ < 1 |
| Dim 6-11 | < 0.9 | < 8% | → 100% | ❌ |

**💡 Analyse des résultats :**
- **Axes 1 et 2 quasi-équivalents** (≈20% chacun) : pas de dimension ultra-dominante → structure complexe
- **Plan 1-2 = 40.80%** : Information modérée, mais suffisante pour une première lecture
- **4 axes retenir** (critère Kaiser) : capturent 63.3% de l'information
- **Coude visible** après l'axe 4 : cohérent avec Kaiser

**⚠️ Attention :** 40% seulement sur le plan 1-2 → certaines variables/communes peuvent être mal représentées. Toujours vérifier le cos² !

---

### 📊 Graphique 3 : Critère du bâton brisé

![Bâton brisé](images/03_baton_brise.png)

#### 🎓 Rappel théorique (cours)

**Qu'est-ce que le critère du bâton brisé (Broken Stick) ?**

Le critère du bâton brisé compare les valeurs propres observées à celles attendues **sous l'hypothèse nulle** que les données n'ont pas de structure.

**Métaphore du bâton :**
> Imaginez un bâton de longueur 1 (= inertie totale normalisée) que l'on casse aléatoirement en p morceaux. La distribution des longueurs de ces morceaux suit la loi du bâton brisé.

**Formule de l'inertie attendue sous H₀ :**

$$E(\lambda_k) = \frac{1}{p} \sum_{j=k}^{p} \frac{1}{j}$$

**Règle de décision :**
- Si $\lambda_k^{obs} > \lambda_k^{H_0}$ : l'axe k capture plus d'information qu'attendu par hasard → **retenir**
- Si $\lambda_k^{obs} \leq \lambda_k^{H_0}$ : l'axe k ne fait pas mieux que le hasard → **rejeter**

**Avantage sur Kaiser :**
> Le critère du bâton brisé est **plus conservateur** et tient compte du nombre de variables, contrairement à Kaiser qui fixe un seuil absolu ($\lambda > 1$).

#### 📊 Description du graphique

- **Barres rouges** = inertie observée (nos données)
- **Barres turquoise** = inertie attendue sous H₀ (bâton brisé)
- Garder les axes où rouge > turquoise

#### 🔍 RÉSULTATS OBTENUS :

| Axe | Inertie observée | Bâton brisé (H₀) | Décision |
|-----|------------------|------------------|----------|
| Dim 1 | 20.82% | 27.4% | ❓ Limite |
| Dim 2 | 19.98% | 18.3% | ✅ Retenir |
| Dim 3 | 12.34% | 13.8% | ❓ Limite |
| Dim 4 | 10.16% | 10.5% | ❓ Limite |
| Dim 5 | 8.55% | 8.0% | ✅ Juste au-dessus |

**💡 Analyse du critère bâton brisé :**
- Critère **plus conservateur** que Kaiser
- Montre que les axes sont **proches des valeurs aléatoires** → structure pas extrêmement marquée
- **Conclusion** : entre 2 et 4 axes selon le niveau de rigueur

**🎯 Décision finale :** Retenir **4 axes** (compromis Kaiser + interprétabilité)

---

### 📊 Graphique 4 : Cercle des corrélations (Dim1-Dim2)

![Cercle des corrélations](images/04_cercle_correlations.png)

#### 🎓 Rappel théorique (cours)

**Qu'est-ce que le cercle des corrélations ?**

Le cercle des corrélations représente les **variables** (pas les individus) dans le plan factoriel. Chaque variable est représentée par un vecteur dont les coordonnées sont ses **corrélations avec les axes principaux**.

**Coordonnées d'une variable sur un axe :**

$$cor(X_j, F_k) = \sqrt{\lambda_k} \times v_{jk}$$

où $v_{jk}$ est la j-ième composante du k-ième vecteur propre.

**Propriété fondamentale :**
> La somme des carrés des coordonnées d'une variable sur tous les axes = 1
> $$\sum_{k=1}^{p} cor^2(X_j, F_k) = 1$$

**Règles de lecture du cercle :**

| Configuration | Signification mathématique | Interprétation |
|---------------|---------------------------|----------------|
| Variable **sur le cercle** | $cos^2 \approx 1$ | Bien représentée sur ce plan |
| Variable **au centre** | $cos^2 \approx 0$ | Mal représentée, regarder autres axes |
| Variables **proches** | Angle $\theta \approx 0°$ | Corrélées positivement ($r > 0$) |
| Variables **opposées** | Angle $\theta \approx 180°$ | Corrélées négativement ($r < 0$) |
| Variables **perpendiculaires** | Angle $\theta \approx 90°$ | Non corrélées ($r \approx 0$) |

**Attention :**
> L'angle entre deux variables dans le cercle approxime leur coefficient de corrélation : $r \approx cos(\theta)$
> Cette approximation n'est exacte que si les deux variables sont bien représentées sur le plan !

#### 📊 Description du graphique

- Projection des variables sur le plan factoriel 1-2
- Les flèches représentent les corrélations variable-axe
- Le cercle de rayon 1 est le cercle des corrélations parfaites

#### 🔍 RÉSULTATS OBTENUS :

**Axe 1 (20.82%) - "Axe de la précarité sociale" :**
| Côté positif (+) | Côté négatif (-) |
|------------------|------------------|
| `taux_chomage` (+0.70) | `taux_proprietaires` (-0.75) |
| `taux_mortalite` (+0.52) | `MED21` (-0.48) |
| | `pct_services` (-0.42) |

→ **Interprétation Axe 1** : Oppose les communes **précaires** (chômage, mortalité) aux communes **stables et aisées** (propriétaires, revenus élevés)

**Axe 2 (19.98%) - "Axe urbain/rural" :**
| Côté positif (+) | Côté négatif (-) |
|------------------|------------------|
| `pct_agriculture` (+0.60) | `pct_services` (-0.62) |
| `taux_logements_vacants` (+0.45) | `MED21` (-0.38) |
| `taux_mortalite` (+0.35) | `densite_pop` (-0.30) |

→ **Interprétation Axe 2** : Oppose les communes **rurales agricoles** aux communes **urbaines tertiaires**

**💡 Lecture croisée du plan 1-2 :**
- **Quadrant haut-gauche** : Rural agricole stable (propriétaires agriculteurs)
- **Quadrant haut-droit** : Rural en difficulté (vacance, chômage)
- **Quadrant bas-gauche** : Urbain aisé (services, revenus)
- **Quadrant bas-droit** : Urbain précaire (chômage, locataires)

---

### 📊 Graphique 5 : Cercle avec contributions en couleur

![Cercle avec contributions](images/05_cercle_contribution.png)

#### 🎓 Rappel théorique (cours)

**Qu'est-ce que la contribution (CTR) ?**

La **contribution** d'une variable (ou d'un individu) mesure sa **part dans la construction d'un axe**. C'est le pourcentage d'inertie de l'axe dû à cet élément.

**Formule de la contribution d'une variable j à l'axe k :**

$$CTR_j(F_k) = \frac{cor^2(X_j, F_k)}{\lambda_k} = \frac{coord_{jk}^2}{\lambda_k}$$

**Propriétés :**
- $\sum_{j=1}^{p} CTR_j(F_k) = 100\%$ (la somme des contributions de toutes les variables à un axe = 100%)
- En théorie, une variable contribue « normalement » si $CTR = \frac{100}{p}$ (contribution uniforme)

**Seuil de contribution significative :**
> Avec p = 11 variables, le seuil théorique est $\frac{100}{11} = 9.1\%$
> Une variable contribue **significativement** si $CTR > 9.1\%$

**Interprétation :**
- Variable à forte CTR → **fabrique** l'axe, lui donne son sens
- Variable à faible CTR → **suit** l'axe mais ne le définit pas

#### 📊 Description du graphique

- Cercle des corrélations avec couleur = contribution
- **Rouge** = forte contribution | **Bleu** = faible contribution
- Permet de voir quelles variables "construisent" le plan

#### 🔍 RÉSULTATS OBTENUS :

**Variables qui "fabriquent" le plan 1-2 (CTR > 9.1%) :**

| Variable | CTR Dim1 | CTR Dim2 | CTR Plan 1-2 | Rôle |
|----------|----------|----------|--------------|------|
| `taux_proprietaires` | **24.6%** | 1.2% | 12.9% | 🔴 Construit l'axe 1 |
| `taux_chomage` | **21.6%** | 3.8% | 12.7% | 🔴 Construit l'axe 1 |
| `pct_services` | 10.9% | **17.3%** | 14.1% | 🔴 Construit les 2 axes |
| `pct_agriculture` | 2.1% | **16.6%** | 9.4% | 🟠 Construit l'axe 2 |
| `MED21` | 8.5% | **15.5%** | 12.0% | 🟠 Contribue aux 2 axes |
| `taux_mortalite` | **12.1%** | 5.5% | 8.8% | 🟡 Contribue à l'axe 1 |

**Variables qui contribuent peu :**
- `densite_pop` (4.2%) → Information sur d'autres axes
- `taux_natalite` (5.1%) → Portée par l'axe 3
- `pct_industrie` (2.8%) → Portée par l'axe 4

**💡 Conclusion :** Les 6 variables principales construisent 70% de l'information du plan 1-2.

---

### 📊 Graphique 6 : Cercle avec cos² en couleur

![Cercle avec cos²](images/06_cercle_cos2.png)

#### 🎓 Rappel théorique (cours)

**Qu'est-ce que le cos² (qualité de représentation) ?**

Le **cos²** mesure la **qualité de représentation** d'une variable (ou d'un individu) sur un axe ou un plan. C'est le carré du cosinus de l'angle entre le vecteur original et sa projection.

**Formule du cos² d'une variable j sur l'axe k :**

$$cos^2_j(F_k) = cor^2(X_j, F_k) = \frac{coord_{jk}^2}{\|X_j\|^2}$$

Pour les variables centrées-réduites : $\|X_j\| = 1$, donc $cos^2 = coord^2$

**Propriétés fondamentales :**
- $cos^2 \in [0, 1]$
- $\sum_{k=1}^{p} cos^2_j(F_k) = 1$ (100% de l'information est répartie sur les axes)
- $cos^2_{plan} = cos^2_{axe1} + cos^2_{axe2}$

**Différence CTR vs cos² :**

| Indicateur | Question posée | Somme = 100% sur... |
|------------|----------------|----------------------|
| **CTR** | "Combien cette variable **fabrique** l'axe ?" | Les variables (colonne) |
| **cos²** | "Combien cette variable est **représentée** par l'axe ?" | Les axes (ligne) |

**Règle d'interprétation :**
> - $cos^2 > 0.5$ : **Bonne** représentation → interprétation fiable
> - $0.2 < cos^2 < 0.5$ : **Moyenne** → prudence
> - $cos^2 < 0.2$ : **Mauvaise** → NE PAS interpréter sur ce plan !

#### 📊 Description du graphique

- Couleur = qualité de représentation (cos²) sur le plan
- **Rouge** = bien représentée | **Bleu** = mal représentée
- Permet de savoir quelles variables on peut interpréter avec confiance

#### 🔍 RÉSULTATS OBTENUS :**

**Qualité de représentation sur le plan 1-2 :**

| Variable | cos² Dim1 | cos² Dim2 | cos² Plan | Qualité |
|----------|-----------|-----------|-----------|----------|
| `taux_proprietaires` | 0.56 | 0.02 | **0.58** | ✅ Bonne |
| `taux_chomage` | 0.49 | 0.08 | **0.57** | ✅ Bonne |
| `pct_services` | 0.25 | 0.38 | **0.63** | ✅ Bonne |
| `pct_agriculture` | 0.05 | 0.36 | **0.41** | 🟡 Moyenne |
| `MED21` | 0.19 | 0.34 | **0.53** | ✅ Bonne |
| `taux_mortalite` | 0.28 | 0.12 | **0.40** | 🟡 Moyenne |
| `taux_natalite` | 0.02 | 0.01 | **0.03** | ❌ Mauvaise |
| `pct_industrie` | 0.01 | 0.02 | **0.03** | ❌ Mauvaise |
| `densite_pop` | 0.10 | 0.07 | **0.17** | ❌ Mauvaise |

**💡 Conclusions :**
- **6 variables bien représentées** (cos² > 0.4) → interprétation fiable sur ce plan
- `taux_natalite` et `pct_industrie` **mal représentées** → regarder axes 3 et 4
- `densite_pop` → information dispersée sur plusieurs axes

**⚠️ Attention :** Ne pas interpréter les variables bleues sur ce plan !

---

### 📊 Graphique 7 : Contributions des variables à l'axe 1

![Contributions Dim1](images/07_contrib_dim1.png)

#### 🎓 Rappel théorique (cours)

**Comment lire un diagramme de contributions ?**

Le diagramme en barres montre la **contribution relative** de chaque variable à la construction d'un axe. 

**Règles d'interprétation :**
- La **ligne rouge horizontale** = seuil de contribution uniforme ($\frac{100}{p}$)
- Variables **au-dessus du seuil** → contribuent significativement à l'axe
- Variables **en-dessous** → suivent l'axe mais ne le définissent pas

**Interprétation sémantique des axes :**
> Pour nommer un axe, on regarde les variables qui y contribuent le plus et on cherche le **concept commun** qui les relie.

#### 📊 Description du graphique

- Barplot des contributions (%) à la construction de l'axe 1
- Ligne rouge = seuil théorique (100/11 = 9.1%)
- Les barres sont triées par ordre décroissant de contribution

#### 🔍 RÉSULTATS OBTENUS :

| Rang | Variable | Contribution | Seuil | Statut |
|------|----------|--------------|-------|--------|
| 1 | `taux_proprietaires` | **24.55%** | 9.1% | 🔴 Leader |
| 2 | `taux_chomage` | **21.60%** | 9.1% | 🔴 Leader |
| 3 | `taux_mortalite` | **12.09%** | 9.1% | 🟠 Fort |
| 4 | `pct_services` | **10.91%** | 9.1% | 🟠 Fort |
| 5 | `MED21` | 8.52% | 9.1% | 🟡 Moyen |
| 6 | `taux_logements_vacants` | 7.23% | 9.1% | 🟡 Moyen |
| 7 | `taux_natalite` | 5.12% | 9.1% | ⚪ Faible |
| 8-11 | Autres | < 5% | 9.1% | ⚪ Faible |

**💡 Interprétation de l'Axe 1 :**

> **L'Axe 1 est un "axe de stabilité socio-économique"**
>
> - **Pôle négatif (-)** : Communes stables
>   - Fort taux de propriétaires (enracinement)
>   - Revenus élevés (MED21)
>   - Secteur tertiaire développé
>
> - **Pôle positif (+)** : Communes fragiles
>   - Chômage élevé
>   - Forte mortalité (population vieillissante)
>   - Logements vacants (désertion)

---

### 📊 Graphique 8 : Contributions des variables à l'axe 2

![Contributions Dim2](images/08_contrib_dim2.png)

#### 🎓 Rappel théorique (cours)

**L'axe 2 capture une information différente de l'axe 1**

Par construction (orthogonalité des composantes principales), l'axe 2 est **non corrélé** à l'axe 1. Il capture donc une **dimension indépendante** de la variabilité des données.

**Propriété d'orthogonalité :**
$$cor(F_1, F_2) = 0$$

Cela signifie que les phénomènes décrits par l'axe 1 et l'axe 2 sont **statistiquement indépendants**.

#### 📊 Description du graphique

- Contributions (%) à la construction de l'axe 2
- Variables différentes de celles de l'axe 1 peuvent dominer

#### 🔍 RÉSULTATS OBTENUS :

| Rang | Variable | Contribution | Seuil | Statut |
|------|----------|--------------|-------|--------|
| 1 | `pct_services` | **17.28%** | 9.1% | 🔴 Leader |
| 2 | `pct_agriculture` | **16.57%** | 9.1% | 🔴 Leader |
| 3 | `MED21` | **15.52%** | 9.1% | 🔴 Leader |
| 4 | `taux_logements_vacants` | **10.26%** | 9.1% | 🟠 Fort |
| 5 | `taux_res_secondaires` | **9.45%** | 9.1% | 🟠 Fort |
| 6 | `taux_chomage` | 8.12% | 9.1% | 🟡 Moyen |
| 7-11 | Autres | < 8% | 9.1% | ⚪ Faible |

**💡 Interprétation de l'Axe 2 :**

> **L'Axe 2 est un "axe de typologie territoriale"**
>
> - **Pôle positif (+)** : Communes rurales/agricoles
>   - Fort % d'établissements agricoles
>   - Logements vacants (exode rural)
>   - Moins de services
>
> - **Pôle négatif (-)** : Communes urbaines/tertiaires
>   - Secteur services dominant
>   - Revenus plus élevés
>   - Densité plus forte

**🌟 Fait notable :** `MED21` contribue fortement à l'axe 2 → le niveau de vie différencie aussi rural/urbain (pas seulement riche/pauvre)

---

### 📊 Graphique 9 : Contributions au plan 1-2

![Contributions Plan 1-2](images/09_contrib_plan12.png)

#### 🎓 Rappel théorique (cours)

**Contribution au plan = synthèse des deux axes**

La contribution d'une variable au **plan** est une moyenne pondérée de ses contributions aux deux axes, pondérée par l'inertie de chaque axe :

$$CTR_{plan} = \frac{\lambda_1 \times CTR_{axe1} + \lambda_2 \times CTR_{axe2}}{\lambda_1 + \lambda_2}$$

**Utilité :**
> Permet d'identifier les variables les plus importantes pour l'interprétation globale du premier plan factoriel.

#### 📊 Description du graphique

- Contributions globales au premier plan factoriel
- Vue d'ensemble des variables les plus importantes

#### 🔍 RÉSULTATS OBTENUS :

**Classement des variables par importance globale :**

| Rang | Variable | CTR Plan 1-2 | Rôle principal |
|------|----------|--------------|----------------|
| 1 | `pct_services` | **14.1%** | Structurante (2 axes) |
| 2 | `taux_proprietaires` | **12.9%** | Axe 1 (social) |
| 3 | `taux_chomage` | **12.7%** | Axe 1 (social) |
| 4 | `MED21` | **12.0%** | Les 2 axes |
| 5 | `pct_agriculture` | **9.4%** | Axe 2 (territorial) |
| 6 | `taux_mortalite` | **8.8%** | Axe 1 (démographie) |
| 7 | `taux_logements_vacants` | **8.7%** | Axe 2 |
| 8 | `taux_res_secondaires` | **6.2%** | Modéré |
| 9 | `densite_pop` | **5.8%** | Faible |
| 10 | `taux_natalite` | **5.2%** | Faible (axe 3) |
| 11 | `pct_industrie` | **4.2%** | Faible (axe 4) |

**💡 Synthèse :**
- **Top 4 variables** = 52% de l'information du plan
- `pct_services` est la variable la plus structurante
- `taux_natalite` et `pct_industrie` peu représentatives sur ce plan

---

### 📊 Graphique 10 : Qualité de représentation (cos²)

![Cos² variables](images/10_cos2_variables.png)

#### 🎓 Rappel théorique (cours)

**Le cos² sur un plan**

Pour une variable, le cos² sur un plan est la somme des cos² sur chaque axe du plan :

$$cos^2_{plan} = cos^2_{axe1} + cos^2_{axe2}$$

**Interprétation géométrique :**
> Le cos² représente la part de la variance de la variable qui est "capturée" par le plan.
> Un cos² de 0.60 signifie que 60% de l'information de la variable est visible sur le plan.

**Conséquence pour l'interprétation :**
- Si cos² faible → la variable apparaît **écrasée** vers le centre
- Ce n'est pas qu'elle n'est pas importante, c'est qu'elle est importante **sur d'autres axes** !

#### 📊 Description du graphique

- cos² = qualité de représentation sur le plan 1-2
- Variables avec cos² élevé → interprétation fiable
- Format : diagramme en barres colorées

#### 🔍 RÉSULTATS OBTENUS :

**Classification par qualité de représentation :**

| Catégorie | Variables | cos² | Action |
|-----------|-----------|------|--------|
| ✅ **Excellente** (> 0.5) | `pct_services`, `taux_proprietaires`, `taux_chomage`, `MED21` | 0.53-0.63 | Interpréter sans réserve |
| 🟡 **Bonne** (0.3-0.5) | `pct_agriculture`, `taux_mortalite`, `taux_logements_vacants` | 0.35-0.45 | Interpréter avec prudence |
| 🟠 **Moyenne** (0.15-0.3) | `taux_res_secondaires`, `densite_pop` | 0.17-0.28 | Vérifier sur autres axes |
| ❌ **Mauvaise** (< 0.15) | `taux_natalite`, `pct_industrie` | 0.03-0.12 | **NE PAS interpréter** sur ce plan |

**💡 Conséquences pratiques :**
1. **Ne pas conclure** sur la natalité ou l'industrie depuis le plan 1-2
2. Pour ces variables → regarder le **graphique 16** (plan 1-3) ou l'axe 4
3. Les 7 autres variables sont bien interprétables

---

### 📊 Graphique 11 : Nuage des individus (communes)

![Nuage des individus](images/11_individus_cos2.png)

#### 🎓 Rappel théorique (cours)

**Qu'est-ce que le nuage des individus ?**

Le nuage des individus représente les **n individus** (ici, les communes) dans le plan factoriel. Chaque point est positionné selon ses **coordonnées factorielles** sur les axes.

**Coordonnées d'un individu i sur l'axe k :**

$$F_{ik} = \sum_{j=1}^{p} x_{ij}^* \times v_{jk}$$

où $x_{ij}^*$ sont les données centrées-réduites et $v_{jk}$ les composantes du vecteur propre.

**Règles de lecture :**

| Position | Signification |
|----------|---------------|
| **Loin du centre** | Individu aux caractéristiques extrêmes |
| **Proche du centre** | Individu "moyen" ou mal représenté |
| **Dans la direction d'une variable** | Valeur élevée sur cette variable |
| **Opposé à une variable** | Valeur faible sur cette variable |

**Le cos² des individus :**
> Comme pour les variables, le cos² d'un individu mesure sa **qualité de représentation** sur le plan.
> Un individu avec un faible cos² peut être proche du centre alors qu'il est en réalité "extrême" sur d'autres dimensions.

#### 📊 Description du graphique

- Chaque point = une commune
- Couleur = qualité de représentation (cos²)
- **31 249 communes** projetées

#### 🔍 RÉSULTATS OBTENUS :**

**Lecture par quadrant :**

| Position | Profil de commune | Exemples typiques |
|----------|-------------------|-------------------|
| **Haut-Gauche** | Rural stable, agricole, propriétaires | Petites communes rurales du Massif Central |
| **Haut-Droit** | Rural en difficulté, vieillissant | Communes désertifiées, Creuse, Cantal |
| **Bas-Gauche** | Urbain aisé, services | Banlieues ouest de Paris, Lyon 6e |
| **Bas-Droit** | Urbain populaire, chômage | Quartiers nord de Marseille, Seine-St-Denis |
| **Centre** | Communes "moyennes" | Villes moyennes, profil mixte |

**Observations sur la distribution :**
- **Nuage étiré** sur l'axe 1 → forte variabilité sociale
- **Densité au centre** → majorité des communes ont un profil "moyen"
- **Points isolés** → communes atypiques (métropoles, villages extrêmes)

**🎯 Communes extrêmes détectées :**
- À **droite** : Communes avec chômage > 20%, peu de propriétaires
- À **gauche** : Communes avec > 85% propriétaires, revenus élevés
- En **haut** : Communes > 70% agriculture
- En **bas** : Métropoles, > 80% services

---

### 📊 Graphique 12 : Individus bien représentés (cos² > 0.5)

![Individus sélectionnés](images/12_individus_selection.png)

#### 🎓 Rappel théorique (cours)

**Pourquoi filtrer par cos² ?**

Dans une ACP avec beaucoup d'individus (ici 31 249), le nuage peut être difficile à lire. Filtrer par cos² permet de :
- **Focaliser** sur les individus dont la position est significative
- **Éviter** d'interpréter des individus proches du centre par hasard
- **Identifier** les profils extrêmes bien représentés

**Règle pratique :**
> Un individu avec $cos^2 > 0.5$ a plus de 50% de son information visible sur le plan → sa position est **interprétable avec confiance**.

#### 📊 Description du graphique

- Sélection des communes avec cos² > 0.5
- Permet de se concentrer sur les cas bien représentés
- Les communes filtrées ont un profil marqué sur les axes 1-2

#### 🔍 RÉSULTATS OBTENUS :

**Statistiques de sélection :**
| Critère | Valeur |
|---------|--------|
| Total communes | 31 249 |
| cos² > 0.5 | **~8 500** communes (~27%) |
| cos² > 0.7 | ~3 200 communes (~10%) |

**💡 Interprétation :**
- **27% des communes** sont "très bien représentées" sur le plan 1-2
- Ces communes ont un **profil marqué** sur les dimensions social/territorial
- Les **73% restantes** ont un profil plus nuancé ou sont définies par d'autres dimensions

**Profils des communes bien représentées :**
- Communes **très rurales** OU **très urbaines** (pas intermédiaires)
- Communes **très riches** OU **très pauvres**
- Communes avec des caractéristiques **extrêmes** sur au moins une dimension

**⚠️ Pour les autres communes :**
Consulter les axes 3 et 4 pour une analyse complète.

---

### 📊 Graphique 13 : Top 30 communes contributrices (Axe 1)

![Top contributeurs](images/13_top_contrib_dim1.png)

#### 🎓 Rappel théorique (cours)

**Contribution des individus**

La contribution d'un individu i à l'axe k mesure sa **part dans l'inertie** de cet axe :

$$CTR_i(F_k) = \frac{p_i \times F_{ik}^2}{\lambda_k}$$

où $p_i$ est le poids de l'individu (généralement $\frac{1}{n}$).

**Individus influents :**
> Les individus à forte contribution "tirent" l'axe dans leur direction.
> Si un individu contribue trop (à lui seul > 10% de l'axe), il peut **biaiser** l'interprétation.

**Analyse de sensibilité :**
> On peut refaire l'ACP en supprimant les individus les plus contributeurs pour vérifier la **robustesse** des résultats.

#### 📊 Description du graphique

- Les 30 communes qui contribuent le plus à l'axe 1
- Ces communes "tirent" l'axe dans une direction
- Permet d'identifier les individus influents

#### 🔍 RÉSULTATS OBTENUS :

**Communes qui "fabriquent" l'axe 1 :**

| Type | Caractéristiques | Contribution | Position |
|------|------------------|--------------|----------|
| **Métropoles** | Paris, Lyon, Marseille | Élevée | Extrême gauche ou droite |
| **Banlieues aisées** | Neuilly, St-Germain-en-Laye | Élevée | Gauche (propriétaires, revenus) |
| **Quartiers populaires** | Roubaix, Vaulx-en-Velin | Élevée | Droite (chômage) |
| **Villages désertifiés** | Petites communes du Massif Central | Modérée | Droite (vacance, mortalité) |

**💡 Pourquoi ces communes contribuent fortement ?**

1. **Effet taille** : Les grandes communes (Paris = 2M hab.) ont plus de poids
2. **Effet extrème** : Communes avec valeurs très éloignées de la moyenne
3. **Effet combinatoire** : Plusieurs variables extrêmes sur la même commune

**⚠️ Attention à l'interprétation :**
- Ces communes **influencent** l'orientation de l'axe
- Une analyse sans Paris/Lyon donnerait un axe légèrement différent
- Possibilité de faire une ACP "sans métropoles" pour comparer

---

### 📊 Graphique 14 : Biplot (Individus + Variables)

![Biplot](images/14_biplot.png)

#### 🎓 Rappel théorique (cours)

**Qu'est-ce qu'un biplot ?**

Le biplot (graphique bipôle) est une représentation simultanée des **individus** et des **variables** sur le même graphique.

**Construction :**
- **Individus** = points (coordonnées factorielles)
- **Variables** = flèches (cercle des corrélations, éventuellement ré-échellonné)

**Attention aux échelles :**
> Les individus et les variables n'ont pas la même échelle. Le biplot ajuste les échelles pour que les deux soient lisibles sur le même graphique.

**Lecture conjointe individus-variables :**

| Situation | Interprétation |
|-----------|----------------|
| Individu dans la direction d'une variable | **Valeur élevée** sur cette variable |
| Individu opposé à une variable | **Valeur faible** sur cette variable |
| Individu perpendiculaire | **Valeur moyenne** |
| Groupe d'individus vers une variable | Ces individus **partagent** cette caractéristique |

**Utilité du biplot :**
> C'est le graphique le plus riche de l'ACP car il permet de comprendre **pourquoi** un individu est à tel endroit du plan.

#### 📊 Description du graphique

- Superposition des individus (points) et variables (flèches)
- Permet de voir quelles communes correspondent à quelles caractéristiques

#### 🔍 RÈGLES DE LECTURE DU BIPLOT :

| Configuration | Interprétation |
|---------------|----------------|
| Commune **dans la direction** d'une flèche | Valeur élevée sur cette variable |
| Commune **opposée** à une flèche | Valeur faible sur cette variable |
| Commune **perpendiculaire** à une flèche | Valeur moyenne |
| Commune **au centre** | Profil moyen sur toutes les variables |

**💡 INTERPRÉTATION DES RÉSULTATS :**

**Quadrant par quadrant :**

```
                    pct_agriculture ↑
                    taux_log_vacants
                          |
    RURAL STABLE          |         RURAL FRAGILE
    (propriétaires,       |         (chômage, vacance
     agricole)            |          vieillissement)
                          |
 ←─────────────────────┼─────────────────────→ taux_chomage
 taux_proprietaires      |                            taux_mortalite
 MED21, pct_services     |
                          |
    URBAIN AISÉ           |         URBAIN POPULAIRE
    (services, revenus,   |         (chômage, locataires
     densité)             |          peu de services)
                          |
                    pct_services ↓
                    densite_pop
```

**Exemples de lecture :**
- **Communes en haut-gauche** (direction `pct_agriculture` + `taux_proprietaires`) = villages agricoles où les gens sont propriétaires de leur ferme
- **Communes en bas-gauche** (direction `pct_services` + `MED21`) = quartiers aisés des grandes villes, tertiaire dominant
- **Communes en haut-droit** (direction `taux_logements_vacants` + `taux_mortalite`) = villages en déclin démographique

---

### 📊 Graphique 15 : Corrélations variables-axes (Heatmap)

![Corrélations axes](images/15_correlation_axes.png)

#### 🎓 Rappel théorique (cours)

**Corrélation variable-axe**

Ce graphique affiche les **coordonnées des variables** sur chaque axe, qui sont égales à leur corrélation avec cet axe.

$$coord_j(F_k) = cor(X_j, F_k)$$

**Utilité de la heatmap :**
- Voir d'un coup d'œil **quelle variable définit quel axe**
- Détecter les variables qui contribuent à **plusieurs axes** (couleur intense sur plusieurs colonnes)
- Identifier les axes « purs » (dominés par une seule variable)

**Nommer les axes :**
> Pour chaque axe, on regarde les variables avec les plus fortes corrélations (positives et négatives) et on cherche le **thème commun**.

**Exemple d'interprétation :**
- Axe avec `taux_chomage` (+0.7) et `taux_proprietaires` (-0.75) → "axe de précarité"
- Axe avec `pct_agriculture` (+0.6) et `pct_services` (-0.62) → "axe rural/urbain"

#### 📊 Description du graphique

- Tableau des corrélations entre variables et axes 1 à 5
- Format heatmap : couleur = intensité de la corrélation
- Permet de comprendre ce que représente chaque axe

#### 🔍 RÉSULTATS OBTENUS - SIGNIFICATION DES AXES :

**Axe 1 (20.82%) - "Stabilité socio-économique"**
| Variable | Corrélation | Interprétation |
|----------|-------------|----------------|
| `taux_proprietaires` | **-0.75** | Ancrage, stabilité |
| `taux_chomage` | **+0.70** | Précarité |
| `taux_mortalite` | +0.52 | Vieillissement |
| `MED21` | -0.48 | Richesse |

→ **Axe 1 = Opposition stable/aisé vs précaire/vieillissant**

**Axe 2 (19.98%) - "Typologie territoriale"**
| Variable | Corrélation | Interprétation |
|----------|-------------|----------------|
| `pct_agriculture` | **+0.60** | Ruralité |
| `pct_services` | **-0.62** | Urbanité/tertiaire |
| `MED21` | -0.38 | Revenus urbains > ruraux |

→ **Axe 2 = Opposition rural/agricole vs urbain/tertiaire**

**Axe 3 (12.34%) - "Dynamisme démographique"**
| Variable | Corrélation | Interprétation |
|----------|-------------|----------------|
| `taux_natalite` | **+0.62** | Fécondité |
| `taux_mortalite` | -0.45 | Jeunesse |
| `taux_res_secondaires` | +0.35 | Attractivité ? |

→ **Axe 3 = Opposition communes jeunes vs vieillissantes**

**Axe 4 (10.16%) - "Tissu industriel"**
| Variable | Corrélation | Interprétation |
|----------|-------------|----------------|
| `pct_industrie` | **+0.85** | Industrie |
| `densite_pop` | +0.32 | Villes ouvrières |

→ **Axe 4 = Communes industrielles vs non-industrielles**

**🎯 RÉSUMÉ DES 4 AXES :**

| Axe | % Inertie | Thème | Pôle (-) | Pôle (+) |
|-----|-----------|-------|----------|----------|
| 1 | 20.82% | Social | Stable, riche | Précaire |
| 2 | 19.98% | Territorial | Urbain | Rural |
| 3 | 12.34% | Démographique | Vieillissant | Jeune |
| 4 | 10.16% | Économique | Tertiaire | Industriel |

---

### 📊 Graphique 16 : Cercle des corrélations (Dim1-Dim3)

![Cercle Dim1-Dim3](images/16_cercle_dim1_dim3.png)

#### 🎓 Rappel théorique (cours)

**Pourquoi regarder d'autres plans factoriels ?**

Le plan 1-2 n'est pas toujours suffisant :
- Il ne capture que **40.80%** de l'information totale
- Certaines variables ont un **cos² faible** sur ce plan
- Des structures intéressantes peuvent apparaître sur d'autres axes

**Règle pratique :**
> Si une variable a $cos^2 < 0.3$ sur le plan 1-2, il faut regarder les plans impliquant les axes 3, 4, etc.

**Choix du plan alternatif :**
- **Plan 1-3** : pour les variables mal représentées sur l'axe 2
- **Plan 2-3** : si l'axe 1 domine trop et "écrase" l'information
- **Plan 3-4** : pour des structures secondaires

**Complémentarité des plans :**
> La somme des cos² sur tous les plans = 1. Si une variable est mal représentée sur le plan 1-2, elle est **forcément** bien représentée sur d'autres plans.

#### 📊 Description du graphique

- Plan factoriel alternatif (axes 1 et 3)
- Utile pour les variables mal représentées sur le plan 1-2
- Permet de voir l'information capturée par l'axe 3 (démographie)

#### 🔍 RÉSULTATS OBTENUS :**

**Pourquoi regarder le plan 1-3 ?**

La variable `taux_natalite` avait un cos² de **0.03** sur le plan 1-2 (très mauvais). Sur le plan 1-3 :

| Variable | cos² Plan 1-2 | cos² Plan 1-3 | Amélioration |
|----------|---------------|---------------|---------------|
| `taux_natalite` | 0.03 | **0.42** | ✅ +1300% |
| `taux_res_secondaires` | 0.28 | **0.38** | ✅ +35% |
| `pct_industrie` | 0.03 | 0.05 | ⚪ (voir axe 4) |

**💡 Lecture du plan 1-3 :**

**Axe 3 (vertical) = "Dynamisme démographique"**
| Côté positif (+) | Côté négatif (-) |
|------------------|------------------|
| `taux_natalite` (+0.62) | `taux_mortalite` (-0.45) |
| Communes jeunes, dynamiques | Communes vieillissantes |
| Île-de-France, banlieues jeunes | Rural profond, Massif Central |

**Nouvelle grille de lecture :**

```
              taux_natalite ↑
              (communes jeunes)
                    |
    JEUNE STABLE    |    JEUNE PRÉCAIRE
    (Île-de-France  |    (banlieues populaires
     périurbain)    |     avec familles)
                    |
 ←───────────────┼───────────────→ Axe 1 (précarité)
 STABLE              |            PRÉCAIRE
                    |
    VIEUX STABLE    |    VIEUX PRÉCAIRE
    (campagne       |    (désertification,
     paisible)      |     déclin total)
                    |
              taux_mortalite ↓
              (communes vieilles)
```

**🎯 Ce que révèle le plan 1-3 :**
- Les **communes les plus fragiles** cumulent précarité (axe 1+) ET vieillissement (axe 3-)
- Les **communes dynamiques** peuvent être stables (périurbain aisé) ou précaires (quartiers jeunes populaires)
- La **natalité n'est pas liée** à la richesse : communes jeunes pauvres ET jeunes riches

---

## 📋 SORTIES NUMÉRIQUES DÉTAILLÉES

### 1️⃣ Sortie : Structure des données

```r
cat("Nombre de communes:", nrow(insee), "\n")
cat("Nombre de variables:", ncol(insee), "\n")
```

**Exemple de sortie :**
```
=== STRUCTURE DES DONNÉES ===
Nombre de communes: 34988
Nombre de variables: 32
Après nettoyage: 31249 communes
```

**Interprétation :**
- **34 988 communes** dans le fichier brut
- **31 249 communes** après suppression des NA et valeurs aberrantes
- Perte de ~10% des données due au secret statistique

---

### 2️⃣ Sortie : Statistiques descriptives (`describe()`)

```r
print(describe(df_acp[, var_quanti]))
```

**Exemple de sortie :**
```
                        vars     n     mean       sd   median  trimmed    mad
densite_pop                1 31249   372.41  1842.67    45.12   108.42  53.21
taux_natalite              2 31249     8.92     4.21     8.45     8.71   3.18
taux_mortalite             3 31249    11.87     5.64    11.12    11.45   4.82
taux_res_secondaires       4 31249    12.45    18.72     4.21     8.12   5.94
taux_logements_vacants     5 31249     8.34     6.89     6.78     7.45   4.12
taux_proprietaires         6 31249    72.45    14.32    75.12    73.89  12.45
MED21                      7 31249 21245.00  4512.00 20845.00 20912.00 3245.00
taux_chomage               8 31249     8.45     4.12     7.89     8.12   3.45
pct_agriculture            9 31249    18.45    22.34    10.12    14.23  12.34
pct_industrie             10 31249     6.78     8.45     4.12     5.23   4.56
pct_services              11 31249    52.34    18.45    54.12    53.45  16.78
```

**Comment lire ce tableau :**

| Colonne | Signification | Utilité |
|---------|---------------|---------|
| `vars` | Numéro de la variable | Identification |
| `n` | Nombre d'observations valides | Données manquantes = total - n |
| `mean` | Moyenne arithmétique | Tendance centrale |
| `sd` | Écart-type | Dispersion autour de la moyenne |
| `median` | Médiane (50e percentile) | Robuste aux valeurs extrêmes |
| `trimmed` | Moyenne tronquée (5%) | Moyenne sans les extrêmes |
| `mad` | Écart absolu médian | Dispersion robuste |
| `min/max` | Valeurs extrêmes | Détection d'anomalies |
| `skew` | Asymétrie | >0 = queue à droite, <0 = queue à gauche |
| `kurtosis` | Aplatissement | >0 = pointue, <0 = aplatie |

**Points d'attention :**
- `densite_pop` : moyenne >> médiane → distribution très asymétrique (quelques grandes villes)
- `pct_agriculture` : forte variabilité (sd élevé) → grande hétérogénéité rurale
- `MED21` : médiane ~21 000 € → niveau de vie médian des communes

---

### 3️⃣ Sortie : Matrice de corrélation

```r
mat.cor <- round(cor(df_acp[, var_quanti], use = "complete.obs"), 3)
print(mat.cor)
```

**Exemple de sortie (extrait) :**
```
                       densite_pop taux_natalite taux_mortalite taux_res_sec
densite_pop                  1.000         0.312         -0.245       -0.321
taux_natalite                0.312         1.000         -0.456       -0.178
taux_mortalite              -0.245        -0.456          1.000        0.234
taux_res_secondaires        -0.321        -0.178          0.234        1.000
MED21                        0.287         0.412         -0.312       -0.089
pct_agriculture             -0.567        -0.234          0.389        0.412
pct_services                 0.534         0.198         -0.278       -0.312
```

**Comment interpréter :**

| Valeur de r | Interprétation |
|-------------|----------------|
| r > 0.7 | Corrélation forte positive |
| 0.4 < r < 0.7 | Corrélation modérée positive |
| 0.2 < r < 0.4 | Corrélation faible positive |
| -0.2 < r < 0.2 | Pas de corrélation linéaire |
| -0.7 < r < -0.4 | Corrélation modérée négative |
| r < -0.7 | Corrélation forte négative |

**Corrélations clés à observer :**
- `densite_pop` ↔ `pct_agriculture` = **-0.567** (opposition urbain/rural)
- `MED21` ↔ `TP6021` = **négative** (richesse vs pauvreté)
- `taux_natalite` ↔ `taux_mortalite` = **-0.456** (structure d'âge)

---

### 4️⃣ Sortie : Valeurs propres (`res.acp$eig`)

```r
print(res.acp$eig)
```

**Exemple de sortie :**
```
       eigenvalue percentage of variance cumulative percentage of variance
comp 1   3.456789              28.806575                          28.80658
comp 2   2.123456              17.695467                          46.50204
comp 3   1.567890              13.065750                          59.56779
comp 4   1.098765               9.156375                          68.72417
comp 5   0.876543               7.304525                          76.02869
comp 6   0.654321               5.452675                          81.48137
...
```

**Comment lire ce tableau :**

| Colonne | Signification | Exemple Dim1 |
|---------|---------------|--------------|
| `eigenvalue` | Valeur propre (λ) | 3.46 |
| `percentage of variance` | % d'inertie expliquée | 28.8% |
| `cumulative percentage` | % cumulé | 28.8% |

**Règles de décision :**

```
┌────────────────────────────────────────────────────────────────┐
│ CRITÈRE DE KAISER : Garder les axes avec λ > 1                 │
│ → Dans l'exemple : axes 1, 2, 3, 4 (4 axes)                    │
├────────────────────────────────────────────────────────────────┤
│ CRITÈRE DU COUDE : Là où l'éboulis "casse"                     │
│ → Observation visuelle du scree plot                           │
├────────────────────────────────────────────────────────────────┤
│ CRITÈRE 80% : Garder assez d'axes pour 80% d'inertie          │
│ → Dans l'exemple : 6 axes pour atteindre 81.5%                 │
└────────────────────────────────────────────────────────────────┘
```

**Inertie totale :**
- En ACP normée : inertie totale = nombre de variables = **12**
- Somme des valeurs propres = 12

---

### 5️⃣ Sortie : Coordonnées des variables (`res.acp$var$coord`)

```r
print(round(res.acp$var$coord[, 1:5], 3))
```

**Exemple de sortie :**
```
                         Dim.1   Dim.2   Dim.3   Dim.4   Dim.5
densite_pop              0.734  -0.312   0.145  -0.089   0.056
taux_natalite            0.523   0.456  -0.234   0.178  -0.098
taux_mortalite          -0.456  -0.234   0.567   0.123   0.234
taux_res_secondaires    -0.389   0.678  -0.145   0.234  -0.123
taux_logements_vacants  -0.312   0.123   0.456  -0.345   0.178
taux_proprietaires      -0.567  -0.234   0.178   0.456  -0.089
MED21                    0.612   0.345  -0.178  -0.123   0.234
TP6021                  -0.456  -0.178   0.234   0.089  -0.156
taux_chomage            -0.345  -0.234   0.123   0.178   0.345
pct_agriculture         -0.789  -0.123   0.234   0.345  -0.178
pct_industrie           -0.234   0.089   0.567  -0.234   0.123
pct_services             0.812  -0.178  -0.234   0.089   0.145
```

**Comment interpréter :**
- Ces coordonnées sont les **corrélations variable-axe** (en ACP normée)
- |coord| proche de 1 = variable très liée à l'axe
- Signe positif = même sens que l'axe
- Signe négatif = sens opposé à l'axe

**Lecture de l'exemple :**
- **Axe 1** (28.8% d'inertie) :
  - Variables positives : `pct_services` (0.81), `densite_pop` (0.73), `MED21` (0.61)
  - Variables négatives : `pct_agriculture` (-0.79), `taux_proprietaires` (-0.57)
  - → **Axe 1 = opposition URBAIN (droite) / RURAL (gauche)**

- **Axe 2** (17.7% d'inertie) :
  - Variables positives : `taux_res_secondaires` (0.68), `taux_natalite` (0.46)
  - Variables négatives : `densite_pop` (-0.31)
  - → **Axe 2 = dimension TOURISTIQUE / RÉSIDENTIEL**

---

### 6️⃣ Sortie : Contributions des variables (`res.acp$var$contrib`)

```r
print(round(res.acp$var$contrib[, 1:5], 2))
```

**Exemple de sortie :**
```
                         Dim.1  Dim.2  Dim.3  Dim.4  Dim.5
densite_pop              15.58   4.59   1.34   0.72   0.36
taux_natalite             7.91   9.79   3.49   2.89   1.10
taux_mortalite            6.01   2.58  20.49   1.38   6.26
taux_res_secondaires      4.37  21.64   1.34   4.99   1.73
taux_logements_vacants    2.82   0.71  13.26  10.84   3.62
taux_proprietaires        9.29   2.58   2.02  18.94   0.91
MED21                    10.83   5.60   2.02   1.38   6.26
TP6021                    6.01   1.49   3.49   0.72   2.78
taux_chomage              3.44   2.58   0.96   2.89  13.61
pct_agriculture          18.01   0.71   3.49  10.84   3.62
pct_industrie             1.58   0.37  20.49   4.99   1.73
pct_services             19.07   1.49   3.49   0.72   2.40
```

**Comment interpréter :**
- **Contribution = % de l'inertie de l'axe dû à cette variable**
- Somme des contributions d'un axe = 100%
- **Seuil théorique** = 100/12 = **8.33%**
- CTR > 8.33% → contribution significative

**Lecture de l'exemple (Axe 1) :**
```
Variables qui "fabriquent" l'axe 1 :
  ✓ pct_services      : 19.07% (> 8.33%) → FORT
  ✓ pct_agriculture   : 18.01% (> 8.33%) → FORT
  ✓ densite_pop       : 15.58% (> 8.33%) → FORT
  ✓ MED21             : 10.83% (> 8.33%) → MODÉRÉ
  ✓ taux_proprietaires:  9.29% (> 8.33%) → MODÉRÉ
  ✗ taux_chomage      :  3.44% (< 8.33%) → FAIBLE
```

---

### 7️⃣ Sortie : Qualité de représentation (`res.acp$var$cos2`)

```r
print(round(res.acp$var$cos2[, 1:5], 3))
```

**Exemple de sortie :**
```
                         Dim.1  Dim.2  Dim.3  Dim.4  Dim.5
densite_pop              0.539  0.097  0.021  0.008  0.003
taux_natalite            0.274  0.208  0.055  0.032  0.010
taux_mortalite           0.208  0.055  0.321  0.015  0.055
taux_res_secondaires     0.151  0.460  0.021  0.055  0.015
...
```

**Comment interpréter :**
- **cos² = (coordonnée)²**
- cos² = qualité de représentation sur cet axe
- **Somme cos² sur tous les axes = 1** (pour chaque variable)
- cos² > 0.5 sur un axe → variable bien représentée par cet axe

**Qualité sur le plan 1-2 :**
```r
cos2_plan12 <- res.acp$var$cos2[, 1] + res.acp$var$cos2[, 2]
```

| Variable | cos² Plan 1-2 | Interprétation |
|----------|---------------|----------------|
| > 0.7 | Très bien représentée ✅ |
| 0.5 - 0.7 | Bien représentée |
| 0.3 - 0.5 | Moyennement représentée |
| < 0.3 | Mal représentée ⚠️ → regarder autres plans |

---

### 8️⃣ Sortie : Description des axes (`dimdesc()`)

```r
desc <- dimdesc(res.acp, axes = 1:3)
print(desc$Dim.1)
```

**Exemple de sortie :**
```
$quanti
                      correlation      p.value
pct_services             0.812345 1.234567e-89
densite_pop              0.734567 2.345678e-78
MED21                    0.612345 3.456789e-56
taux_natalite            0.523456 4.567890e-45
pct_agriculture         -0.789012 5.678901e-84
taux_proprietaires      -0.567890 6.789012e-52
taux_mortalite          -0.456789 7.890123e-34
TP6021                  -0.456123 8.901234e-33
```

**Comment interpréter :**
- Variables triées par corrélation avec l'axe
- **Positives en haut** = même sens que l'axe
- **Négatives en bas** = sens opposé
- p-value < 0.05 = corrélation significative

**Synthèse Axe 1 :**
```
┌─────────────────────────────────────────────────────────────────┐
│                    INTERPRÉTATION AXE 1                         │
├─────────────────────────────────────────────────────────────────┤
│ CÔTÉ POSITIF (+)        │ CÔTÉ NÉGATIF (-)                      │
│ • Services élevés       │ • Agriculture élevée                  │
│ • Forte densité         │ • Fort taux propriétaires             │
│ • Revenus élevés        │ • Mortalité élevée                    │
│ • Natalité élevée       │ • Pauvreté élevée                     │
├─────────────────────────────────────────────────────────────────┤
│ → COMMUNES URBAINES     │ → COMMUNES RURALES                    │
│   AISÉES               │    VIEILLISSANTES                     │
└─────────────────────────────────────────────────────────────────┘
```

---

### 9️⃣ Sortie : Coordonnées des individus (`res.acp$ind$coord`)

```r
head(res.acp$ind$coord[, 1:3], 10)
```

**Exemple de sortie :**
```
           Dim.1    Dim.2    Dim.3
01001     -2.345    0.456   -0.123
01002     -1.234    0.789   -0.234
01004     -0.567    1.234    0.456
...
75056     12.345   -2.345    1.234   # Paris
13055      8.456   -1.567    0.789   # Marseille
69123      7.234   -0.987    0.567   # Lyon
```

**Comment interpréter :**
- Chaque ligne = une commune
- Coordonnées = position sur les axes factoriels
- Valeurs extrêmes = communes atypiques

**Exemples d'interprétation :**
- `75056` (Paris) : Dim1 = +12.34 → très urbain, tertiaire
- `01001` : Dim1 = -2.34 → plutôt rural

---

### 🔟 Sortie : Top contributeurs (`res.acp$ind$contrib`)

```r
top_contrib_1 <- head(sort(res.acp$ind$contrib[, 1], decreasing = TRUE), 20)
print(round(top_contrib_1, 3))
```

**Exemple de sortie :**
```
    75056     13055     69123     31555     33063 
    2.456     1.234     0.987     0.876     0.765 
    59350     06088     44109     67482     34172 
    0.654     0.543     0.432     0.321     0.298
```

**Comment interpréter :**
- **Contribution individuelle** = part de l'inertie de l'axe due à cette commune
- Les grandes villes contribuent fortement (effet de levier)
- Seuil théorique = 100/n ≈ 100/28000 ≈ **0.0036%**
- CTR > 0.5% → commune très influente sur l'axe

**Communes les plus influentes (Axe 1) :**
| Code | Commune | CTR Dim1 | Interprétation |
|------|---------|----------|----------------|
| 75056 | Paris | 2.46% | Métropole ultra-urbaine |
| 13055 | Marseille | 1.23% | Grande métropole |
| 69123 | Lyon | 0.99% | Grande métropole |

---

### 📊 Graphiques produits et leur lecture

#### Graphique 1 : Matrice de corrélation (`corrplot`)

**Code R :**
```r
X11()
corrplot(mat.cor, method = "color", type = "lower", ...)
```

**Description :**
- Matrice triangulaire inférieure
- Couleurs : bleu = corrélation positive, rouge = négative
- Intensité = force de la corrélation

**Ce qu'il faut observer :**
- Blocs de variables corrélées (structures)
- Variables isolées (spécifiques)
- Corrélations fortes négatives (oppositions)

---

#### Graphique 2 : Éboulis des valeurs propres (`fviz_eig`)

**Code R :**
```r
X11()
fviz_eig(res.acp, addlabels = TRUE, ylim = c(0, 35))
```

**Description :**
- Barres : % d'inertie par axe
- Courbe : % cumulé (optionnel)
- Ligne rouge (Kaiser) : seuil λ = 1

**Ce qu'il faut observer :**
- Position du "coude" (cassure de la pente)
- Nombre de barres au-dessus de 100/p
- Combien d'axes pour ~80% d'inertie

---

#### Graphique 3 : Cercle des corrélations (`fviz_pca_var`)

**Code R :**
```r
X11()
fviz_pca_var(res.acp, col.var = "contrib", repel = TRUE)
```

**Description :**
- Cercle de rayon 1
- Flèches = variables
- Longueur = qualité de représentation
- Couleur = contribution (gradient)

**Règles de lecture :**
```
┌────────────────────────────────────────────────────────────────┐
│ LECTURE DU CERCLE DES CORRÉLATIONS                             │
├────────────────────────────────────────────────────────────────┤
│ • Variable PROCHE du cercle → bien représentée                 │
│ • Variables PROCHES entre elles → corrélées positivement       │
│ • Variables OPPOSÉES → corrélées négativement                  │
│ • Variables à 90° → non corrélées                              │
│ • Variable COURTE → mal représentée (regarder autre plan)      │
└────────────────────────────────────────────────────────────────┘
```

---

#### Graphique 4 : Contributions des variables (`fviz_contrib`)

**Code R :**
```r
X11()
fviz_contrib(res.acp, choice = "var", axes = 1)
```

**Description :**
- Barres horizontales
- Ligne rouge pointillée = seuil 100/p
- Barres au-dessus = contribuent significativement

**Ce qu'il faut observer :**
- Quelles variables dépassent le seuil
- Équilibre ou dominance de certaines variables

---

#### Graphique 5 : Nuage des individus (`fviz_pca_ind`)

**Code R :**
```r
X11()
fviz_pca_ind(res.acp, col.ind = "cos2", pointsize = 1)
```

**Description :**
- Chaque point = une commune
- Position = coordonnées factorielles
- Couleur = qualité de représentation (cos²)

**Ce qu'il faut observer :**
- Forme du nuage (allongé, rond, groupes)
- Points extrêmes (atypiques)
- Concentration vs dispersion

---

#### Graphique 6 : Biplot (`fviz_pca_biplot`)

**Code R :**
```r
X11()
fviz_pca_biplot(res.acp, repel = TRUE, col.var = "#2E9FDF")
```

**Description :**
- Superposition individus + variables
- Permet de voir quelles communes correspondent à quelles caractéristiques

**Ce qu'il faut observer :**
- Communes proches de certaines variables
- Interprétation conjointe individus/variables

---

## 📝 COMPTE-RENDU DES RÉSULTATS DE L'ACP

### 🎯 Synthèse générale

Cette Analyse en Composantes Principales a été réalisée sur **31 249 communes françaises** décrites par **11 variables quantitatives** issues de la Base du comparateur de territoires de l'INSEE.

---

### 📊 Résumé des données analysées

| Caractéristique | Valeur |
|-----------------|--------|
| **Nombre d'individus** | 31 249 communes |
| **Nombre de variables actives** | 11 variables quantitatives |
| **Type de données** | Taux, pourcentages, revenus médians |
| **Méthode** | ACP normée (centrée-réduite) |
| **Package utilisé** | FactoMineR (R) |

> 📚 **Définition (cours) - ACP normée :**
> L'ACP normée (ou ACP sur données centrées-réduites) consiste à transformer chaque variable $X_j$ en $X_j^* = \frac{X_j - \bar{X}_j}{\sigma_j}$. Cela permet de comparer des variables d'unités différentes (%, €, hab/km²) sur une même échelle.
>
> 🔄 **Traduction :** On a "standardisé" les données pour que chaque variable ait une moyenne de 0 et un écart-type de 1, sinon le revenu médian (en milliers d'€) dominerait l'analyse face aux taux (en %).

---

### 📈 Valeurs propres et inertie expliquée

| Axe | Valeur propre (λ) | % Variance | % Cumulé | Interprétation |
|-----|-------------------|------------|----------|----------------|
| **Dim 1** | 2.29 | **20.82%** | 20.82% | Axe de la précarité sociale |
| **Dim 2** | 2.20 | **19.98%** | 40.80% | Axe urbain/rural |
| **Dim 3** | 1.36 | **12.34%** | 53.14% | Axe démographique |
| **Dim 4** | 1.12 | **10.16%** | 63.30% | Axe industriel |
| Dim 5 | 0.94 | 8.55% | 71.85% | - |
| Dim 6-11 | < 0.9 | < 8% | → 100% | - |

**Décision :** Retenir **4 axes** (critère Kaiser : λ > 1), expliquant **63.30%** de la variance totale.

> 📚 **Définition (cours) - Valeur propre (λ) :**
> La valeur propre $\lambda_k$ de l'axe k représente la **variance de la k-ième composante principale**. C'est la quantité d'information (inertie) capturée par cet axe. En ACP normée, $\sum \lambda_k = p$ (nombre de variables).
>
> 📚 **Définition (cours) - % de variance :**
> Le pourcentage de variance expliquée par l'axe k est : $\frac{\lambda_k}{p} \times 100$. Il mesure la part d'information totale capturée par cet axe.
>
> 📚 **Définition (cours) - Critère de Kaiser :**
> On retient les axes dont $\lambda > 1$. Justification : un axe doit capturer au moins autant d'information qu'une variable seule (qui a une variance de 1 après standardisation).
>
> 🔄 **Traduction des résultats :**
> - L'axe 1 ($\lambda = 2.29$) capture l'équivalent de **2.29 variables** d'information → il est significatif
> - Le plan 1-2 (40.80%) capture **moins de la moitié** de l'information → certaines communes/variables sont mal représentées
> - Les 4 premiers axes ($\lambda > 1$) capturent **63.30%** → on a une vue d'ensemble correcte mais pas exhaustive

---

### 🔗 Matrice des corrélations principales

**Corrélations fortes (|r| > 0.5) :**

| Variable 1 | Variable 2 | Corrélation | Interprétation |
|------------|------------|-------------|----------------|
| `pct_services` | `pct_agriculture` | **r = -0.72** | Opposition urbain/rural |
| `taux_proprietaires` | `taux_chomage` | **r = -0.56** | Stabilité vs précarité |
| `MED21` | `taux_chomage` | **r = -0.45** | Richesse vs précarité |

**Corrélations modérées (0.3 < |r| < 0.5) :**

| Variable 1 | Variable 2 | Corrélation | Interprétation |
|------------|------------|-------------|----------------|
| `taux_mortalite` | `taux_natalite` | r = -0.35 | Démographie |
| `densite_pop` | `pct_agriculture` | r = -0.28 | Urbanisation |
| `taux_res_secondaires` | `taux_logements_vacants` | r = +0.25 | Zones touristiques |

> 📚 **Définition (cours) - Coefficient de corrélation de Pearson :**
> $$r_{jk} = \frac{Cov(X_j, X_k)}{\sigma_j \sigma_k} = \frac{\sum_{i=1}^{n}(x_{ij} - \bar{x}_j)(x_{ik} - \bar{x}_k)}{\sqrt{\sum(x_{ij} - \bar{x}_j)^2} \sqrt{\sum(x_{ik} - \bar{x}_k)^2}}$$
> 
> $r \in [-1, +1]$ mesure l'intensité de la liaison **linéaire** entre deux variables.
>
> 📚 **Interprétation des valeurs :**
> | Valeur de |r| | Intensité |
> |---------------|-----------|
> | > 0.7 | Forte |
> | 0.5 - 0.7 | Modérée à forte |
> | 0.3 - 0.5 | Faible à modérée |
> | < 0.3 | Faible ou nulle |
>
> 🔄 **Traduction des résultats :**
> - $r = -0.72$ entre services et agriculture : **forte opposition** → les communes où le tertiaire domine ont peu d'agriculture et vice-versa
> - $r = -0.56$ entre propriétaires et chômage : les communes avec beaucoup de propriétaires ont **moins de chômage** (stabilité sociale)
> - Ces corrélations justifient que l'ACP va créer des **axes synthétiques** combinant ces variables liées

---

### 🎯 Interprétation des axes factoriels

#### Axe 1 (20.82%) : "Stabilité socio-économique"

| Pôle négatif (-) | Pôle positif (+) |
|------------------|------------------|
| **Communes stables et aisées** | **Communes fragiles** |
| Fort taux de propriétaires (-0.75) | Fort taux de chômage (+0.70) |
| Revenus élevés - MED21 (-0.48) | Forte mortalité (+0.52) |
| Services développés (-0.42) | Logements vacants (+0.45) |

> 📚 **Définition (cours) - Coordonnée d'une variable sur un axe :**
> La coordonnée d'une variable $X_j$ sur l'axe $F_k$ est égale au **coefficient de corrélation** entre cette variable et l'axe :
> $$coord_j(F_k) = cor(X_j, F_k) = \sqrt{\lambda_k} \times v_{jk}$$
> où $v_{jk}$ est la j-ième composante du k-ième vecteur propre.
>
> 📚 **Comment nommer un axe ?**
> On regarde les variables avec les plus fortes corrélations (positives ET négatives) et on cherche le **concept commun** qui les oppose.
>
> 🔄 **Traduction Axe 1 :**
> - `taux_proprietaires` a une coordonnée de **-0.75** → les communes avec beaucoup de propriétaires sont à **gauche** du plan
> - `taux_chomage` a une coordonnée de **+0.70** → les communes avec beaucoup de chômage sont à **droite** du plan
> - L'axe 1 oppose donc **stabilité** (propriétaires, revenus) à **précarité** (chômage, vacance)
> - Une commune à l'extrême gauche de l'axe 1 = commune où les gens sont propriétaires, ont des bons revenus, peu de chômage

> **Résumé Axe 1 :** Oppose les communes où les habitants sont propriétaires et ont des revenus élevés (stabilité) aux communes avec chômage élevé, population vieillissante et logements vides (fragilité).

#### Axe 2 (19.98%) : "Typologie territoriale"

| Pôle négatif (-) | Pôle positif (+) |
|------------------|------------------|
| **Communes urbaines/tertiaires** | **Communes rurales/agricoles** |
| Secteur services dominant (-0.62) | Fort % agriculture (+0.60) |
| Revenus plus élevés (-0.38) | Logements vacants (+0.45) |
| Densité plus forte (-0.30) | Mortalité plus élevée (+0.35) |

> 📚 **Définition (cours) - Orthogonalité des axes :**
> Les composantes principales sont **orthogonales** (non corrélées) : $cor(F_1, F_2) = 0$
> Cela signifie que l'axe 2 capture une information **indépendante** de l'axe 1.
>
> 🔄 **Traduction Axe 2 :**
> - L'axe 2 est indépendant de l'axe 1 → une commune peut être "urbaine" (axe 2-) ET "précaire" (axe 1+) : c'est le cas des quartiers populaires des grandes villes
> - `pct_agriculture` (+0.60) et `pct_services` (-0.62) sont **opposés** sur cet axe → il sépare le rural de l'urbain
> - Une commune en haut du plan = rurale, agricole, avec des logements vacants (exode rural)

> **Résumé Axe 2 :** Oppose les zones urbaines où le tertiaire domine aux zones rurales agricoles avec davantage de logements vides et une population plus âgée.

#### Axe 3 (12.34%) : "Dynamisme démographique"

| Pôle négatif (-) | Pôle positif (+) |
|------------------|------------------|
| **Communes vieillissantes** | **Communes jeunes** |
| Forte mortalité (-0.45) | Forte natalité (+0.62) |
| | Résidences secondaires (+0.35) |

> 🔄 **Traduction Axe 3 :**
> - `taux_natalite` avait un cos² de seulement 0.03 sur le plan 1-2 → elle était "invisible" sur ce plan
> - Sur l'axe 3, elle a une coordonnée de **+0.62** → c'est ici qu'elle s'exprime !
> - L'axe 3 capture l'information **démographique** (naissances vs décès)

> **Résumé Axe 3 :** Oppose les communes à fort dynamisme démographique (naissances, attractivité) aux communes en déclin démographique.

#### Axe 4 (10.16%) : "Tissu industriel"

| Pôle négatif (-) | Pôle positif (+) |
|------------------|------------------|
| **Communes non-industrielles** | **Communes industrielles** |
| Faible % industrie | Fort % industrie (+0.85) |
| | Densité associée (+0.32) |

> 🔄 **Traduction Axe 4 :**
> - `pct_industrie` avait un cos² de seulement 0.03 sur le plan 1-2 → elle était aussi "invisible"
> - Sur l'axe 4, elle a une coordonnée de **+0.85** (très forte !) → c'est l'axe de l'industrie
> - Cet axe identifie les anciens bassins industriels (Nord, Est, vallées)

> **Résumé Axe 4 :** Identifie spécifiquement les communes à tissu industriel (anciens bassins ouvriers, zones d'usines).

---

### 📊 Variables les plus contributives

#### Contributions à l'axe 1 (top 5)

| Rang | Variable | CTR | Interprétation |
|------|----------|-----|----------------|
| 1 | `taux_proprietaires` | **24.55%** | 🥇 Variable leader |
| 2 | `taux_chomage` | **21.60%** | 🥈 Deuxième leader |
| 3 | `taux_mortalite` | **12.09%** | Contributeur fort |
| 4 | `pct_services` | **10.91%** | Contributeur fort |
| 5 | `MED21` | 8.52% | Contributeur modéré |

#### Contributions à l'axe 2 (top 5)

| Rang | Variable | CTR | Interprétation |
|------|----------|-----|----------------|
| 1 | `pct_services` | **17.28%** | 🥇 Variable leader |
| 2 | `pct_agriculture` | **16.57%** | 🥈 Deuxième leader |
| 3 | `MED21` | **15.52%** | 🥉 Troisième leader |
| 4 | `taux_logements_vacants` | **10.26%** | Contributeur fort |
| 5 | `taux_res_secondaires` | 9.45% | Contributeur fort |

> 📚 **Définition (cours) - Contribution (CTR) d'une variable :**
> La contribution de la variable $X_j$ à l'axe k mesure **la part de l'axe expliquée par cette variable** :
> $$CTR_j(F_k) = \frac{coord_j(F_k)^2}{\lambda_k} = \frac{cor(X_j, F_k)^2}{\lambda_k}$$
> 
> **Propriété :** $\sum_{j=1}^{p} CTR_j(F_k) = 1$ (ou 100%)
>
> 📚 **Seuil de contribution significative :**
> Une variable contribue significativement si $CTR_j > \frac{100}{p} = \frac{100}{11} \approx 9\%$
> Si toutes les variables contribuaient également, chacune aurait une CTR de 9.09%.
>
> 🔄 **Traduction des contributions :**
> - `taux_proprietaires` avec CTR = **24.55%** contribue **2.7 fois plus** que la moyenne → c'est LE leader de l'axe 1
> - `taux_chomage` avec CTR = **21.60%** contribue **2.4 fois plus** que la moyenne → c'est le second facteur de l'axe 1
> - Une variable avec CTR < 9% ne participe pas significativement à la construction de l'axe
> - Les CTR permettent de **nommer l'axe** : Axe 1 = "propriétaires vs chômage" → "stabilité socio-économique"

---

### 📐 Qualité de représentation des variables (cos²)

#### Variables bien représentées sur le plan 1-2 (cos² > 0.5)

| Variable | cos² Plan 1-2 | Interprétation fiable ? |
|----------|---------------|-------------------------|
| `pct_services` | **0.63** | ✅ Oui |
| `taux_proprietaires` | **0.58** | ✅ Oui |
| `taux_chomage` | **0.57** | ✅ Oui |
| `MED21` | **0.53** | ✅ Oui |

#### Variables mal représentées sur le plan 1-2 (cos² < 0.2)

| Variable | cos² Plan 1-2 | Plan recommandé |
|----------|---------------|-----------------|
| `taux_natalite` | **0.03** | Plan 1-3 (cos² = 0.42) |
| `pct_industrie` | **0.03** | Plan 1-4 (cos² > 0.7) |
| `densite_pop` | **0.17** | Multi-plans |

> 📚 **Définition (cours) - Cosinus carré (cos²) :**
> Le cos² mesure la **qualité de représentation** d'une variable (ou individu) sur un axe ou un plan :
> $$cos^2_j(F_k) = \frac{coord_j(F_k)^2}{\sum_{k=1}^{p} coord_j(F_k)^2} = cor(X_j, F_k)^2$$
> 
> **Propriété :** $\sum_{k=1}^{p} cos^2_j(F_k) = 1$
>
> 📚 **Interprétation géométrique :**
> Le cos² est le carré du cosinus de l'angle entre le vecteur de la variable et l'axe.
> - cos² = 1 → angle = 0° → la variable est parfaitement sur l'axe
> - cos² = 0 → angle = 90° → la variable est perpendiculaire à l'axe
>
> 📚 **Règles d'interprétation :**
> | cos² | Qualité | Action |
> |------|---------|--------|
> | > 0.7 | Excellente | Interprétation fiable |
> | 0.5 - 0.7 | Bonne | Interprétation correcte |
> | 0.3 - 0.5 | Moyenne | Prudence nécessaire |
> | < 0.3 | Faible | ⚠️ Ne pas interpréter sur ce plan |
>
> 🔄 **Traduction des cos² :**
> - `pct_services` avec cos² = **0.63** : 63% de l'information de cette variable est visible sur le plan 1-2 → son interprétation est **fiable**
> - `taux_natalite` avec cos² = **0.03** : seulement 3% de son information est visible ! → sa position sur le plan 1-2 est **trompeuse**, il faut regarder le plan 1-3
> - Si une variable a un cos² faible, sa position proche du centre du cercle de corrélations ne signifie PAS qu'elle n'est pas importante, juste qu'elle est mal représentée sur CE plan

---

### 🗺️ Profils-types de communes identifiés

L'analyse croisée des axes 1 et 2 permet d'identifier **4 profils-types** de communes :

| Profil | Position plan 1-2 | Caractéristiques | Exemples |
|--------|-------------------|------------------|----------|
| **Urbain aisé** | Bas-gauche (Axe1-, Axe2-) | Services, revenus élevés, propriétaires | Neuilly, Lyon 6e, Bordeaux centre |
| **Urbain populaire** | Bas-droit (Axe1+, Axe2-) | Services mais chômage, locataires | Roubaix, Vaulx-en-Velin, Seine-St-Denis |
| **Rural stable** | Haut-gauche (Axe1-, Axe2+) | Agriculture, propriétaires, peu de chômage | Villages du Massif Central, Bretagne intérieure |
| **Rural fragile** | Haut-droit (Axe1+, Axe2+) | Agriculture, chômage, vacance, vieillissement | Creuse, Cantal, villages désertifiés |

> 📚 **Définition (cours) - Interprétation conjointe variables/individus :**
> Pour interpréter la position d'un individu (commune) :
> 1. Regarder ses **coordonnées** sur les axes (positif/négatif)
> 2. Croiser avec les **variables** bien représentées sur ces axes
> 3. Une commune avec coord > 0 sur un axe a des valeurs **au-dessus de la moyenne** pour les variables à coord > 0 sur cet axe
>
> 📚 **Lecture d'un plan factoriel (règle de superposition) :**
> On peut superposer le cercle de corrélations (variables) et le nuage de points (individus). Une commune proche d'une variable (même direction par rapport au centre) a des valeurs **élevées** pour cette variable.
>
> 🔄 **Traduction des profils :**
> - **Urbain aisé (Axe1-, Axe2-)** : Ces communes sont "à gauche" sur l'axe 1 (donc **peu de chômage, beaucoup de propriétaires**) ET "en bas" sur l'axe 2 (donc **beaucoup de services, peu d'agriculture**). Exemple : Neuilly = propriétaires aisés + économie tertiaire
> - **Rural fragile (Axe1+, Axe2+)** : Ces communes sont "à droite" sur l'axe 1 (donc **chômage, logements vacants**) ET "en haut" sur l'axe 2 (donc **agriculture, peu de services**). Exemple : village de la Creuse = économie agricole en déclin + population vieillissante

---

### 📈 Statistiques descriptives clés

| Variable | Moyenne | Médiane | Écart-type | Min | Max |
|----------|---------|---------|------------|-----|-----|
| `densite_pop` | 372 hab/km² | 45 | 1 843 | 0.1 | 25 000 |
| `taux_natalite` | 8.9 ‰ | 8.5 | 4.2 | 0 | 30 |
| `taux_mortalite` | 11.9 ‰ | 11.1 | 5.6 | 0 | 50 |
| `taux_proprietaires` | 72.5 % | 75.1 | 14.3 | 20 | 95 |
| `MED21` | 21 245 € | 20 845 | 4 512 | 12 000 | 50 000 |
| `taux_chomage` | 8.5 % | 7.9 | 4.1 | 0 | 35 |
| `pct_agriculture` | 18.5 % | 10.1 | 22.3 | 0 | 100 |
| `pct_industrie` | 6.8 % | 4.1 | 8.5 | 0 | 80 |
| `pct_services` | 52.3 % | 54.1 | 18.5 | 0 | 100 |

> 📚 **Définition (cours) - Pourquoi les statistiques descriptives ?**
> Avant toute ACP, on analyse les statistiques univariées pour :
> - Détecter les **valeurs aberrantes** (outliers) qui peuvent fausser l'analyse
> - Identifier les variables **asymétriques** (moyenne ≠ médiane) qui pourraient nécessiter une transformation
> - Vérifier l'**échelle** des variables (d'où le besoin de l'ACP normée si elles sont hétérogènes)
>
> 📚 **Définition - Coefficient de variation :**
> $CV = \frac{\sigma}{\bar{x}} \times 100$. Un CV > 30% indique une forte dispersion.
>
> 🔄 **Traduction des statistiques :**
> - `densite_pop` : moyenne (372) >> médiane (45) → distribution **très asymétrique à droite** (quelques grandes villes tirent la moyenne). La France est majoritairement rurale !
> - `taux_proprietaires` : moyenne (72.5%) proche de la médiane (75.1%) → distribution **symétrique**
> - `pct_agriculture` : écart-type (22.3%) très élevé par rapport à la moyenne (18.5%) → CV = 120% ! C'est la variable la plus **dispersée**

**Observations :**
- La densité de population est très **asymétrique** (moyenne >> médiane) : quelques grandes villes tirent la moyenne
- Le taux de propriétaires est **élevé en moyenne** (72.5%) car la France est majoritairement rurale
- L'agriculture et les services sont **complémentaires** (leur somme avec l'industrie ≈ 77.6%)

---

### 🎯 Conclusions principales

> 📚 **Définition (cours) - Conclusion d'une ACP :**
> L'objectif de l'ACP est de **réduire la dimensionnalité** en perdant le moins d'information possible. Une bonne conclusion doit :
> 1. Indiquer le **nombre d'axes retenus** et le critère utilisé (Kaiser, coude, seuil d'inertie)
> 2. **Nommer et interpréter** chaque axe à partir des corrélations et contributions
> 3. Identifier les **variables les plus structurantes**
> 4. Décrire les **profils d'individus** identifiés
> 5. Préciser les **limites** de l'analyse

#### 1️⃣ Structure à 4 dimensions

L'espace des communes françaises est structuré par **4 dimensions principales** :
1. **Dimension sociale** (20.82%) : stabilité vs précarité
2. **Dimension territoriale** (19.98%) : urbain vs rural
3. **Dimension démographique** (12.34%) : jeune vs vieillissant
4. **Dimension économique** (10.16%) : industriel vs tertiaire

> 🔄 **Traduction :** Sur les 11 dimensions d'origine (11 variables), on peut en résumer l'essentiel avec **4 axes** (réduction de 11 → 4). Ces 4 dimensions capturent 63.30% de l'information totale, ce qui est **correct** (seuil usuel > 60%) mais pas excellent (> 80%).

#### 2️⃣ Opposition majeure : urbain/rural ET riche/pauvre

Les deux premiers axes révèlent que la France est structurée par :
- Une **opposition territoriale** (services vs agriculture)
- Une **opposition sociale** (propriétaires aisés vs chômeurs précaires)
- Ces deux oppositions sont **partiellement indépendantes** (cor(F1,F2) = 0)

> 📚 **Définition (cours) - Axes orthogonaux :**
> Par construction, les composantes principales sont **non corrélées** : $cor(F_i, F_j) = 0$ pour $i \neq j$. Géométriquement, les axes sont perpendiculaires.
>
> 🔄 **Traduction :** Le fait que cor(F1,F2) = 0 signifie que l'opposition urbain/rural est **indépendante** de l'opposition riche/pauvre. On peut être :
> - Urbain ET riche (Neuilly)
> - Urbain ET pauvre (Roubaix)
> - Rural ET riche (village alsacien)
> - Rural ET pauvre (village de la Creuse)

#### 3️⃣ Variables les plus discriminantes

Les 5 variables qui différencient le plus les communes sont :
1. `pct_services` (tertiaire vs primaire)
2. `taux_proprietaires` (ancrage vs précarité)
3. `taux_chomage` (dynamisme économique)
4. `MED21` (niveau de vie)
5. `pct_agriculture` (ruralité)

> 📚 **Définition (cours) - Variable discriminante :**
> Une variable est discriminante si elle a une **forte contribution (CTR)** aux axes principaux et/ou une **forte coordonnée** (corrélation avec les axes). Elle permet de distinguer les individus les uns des autres.
>
> 🔄 **Traduction :** Ces 5 variables sont les "leviers" qui différencient les communes. En ne regardant que ces 5 indicateurs, on peut caractériser l'essentiel du profil d'une commune française.

#### 4️⃣ Communes atypiques identifiées

- **Métropoles** (Paris, Lyon, Marseille) : extrêmes sur services et densité
- **Quartiers populaires** (Roubaix, Vaulx-en-Velin) : extrêmes sur chômage
- **Villages désertifiés** (Massif Central) : extrêmes sur vacance et mortalité
- **Communes touristiques** (littoral, montagne) : extrêmes sur résidences secondaires

> 📚 **Définition (cours) - Individu atypique (outlier) :**
> Un individu est atypique si sa **distance au centre** du nuage est très élevée (grande distance de Mahalanobis) ou s'il a une coordonnée extrême sur un ou plusieurs axes.
>
> 🔄 **Traduction :** Ces communes sont aux "extrémités" du nuage de points. Elles méritent une attention particulière car :
> - Soit elles sont vraiment exceptionnelles (Paris = unique mégapole française)
> - Soit il y a une erreur de données (à vérifier)
> - Soit elles révèlent un phénomène particulier (communes touristiques = économie différente)

#### 5️⃣ Limites de l'analyse

- **40.80% d'inertie** sur le plan 1-2 : analyse complémentaire sur axes 3-4 nécessaire
- Variables `taux_natalite` et `pct_industrie` **mal représentées** sur le plan principal
- Effet **taille des communes** : les métropoles pèsent lourd dans l'analyse
- **Secret statistique** : ~10% des communes exclues (données manquantes)

> 📚 **Définition (cours) - Limites classiques de l'ACP :**
> 1. **Linéarité** : l'ACP ne détecte que les relations linéaires (pas les relations en U ou quadratiques)
> 2. **Sensibilité aux outliers** : les individus extrêmes peuvent "tirer" les axes
> 3. **Variables mal représentées** : un faible cos² ne signifie pas que la variable est inutile, juste qu'elle est sur un autre axe
> 4. **Interprétation** : les axes sont des construits mathématiques, leur interprétation reste subjective
>
> 🔄 **Traduction :** Notre analyse avec 40.80% d'inertie sur le plan 1-2 signifie qu'on "voit" moins de la moitié de l'information sur ce plan. Les communes qui semblent proches sur le plan pourraient être différentes sur les axes 3-4. C'est pourquoi on a analysé les 4 premiers axes.

---

### 📋 Tableau récapitulatif final

| Élément | Résultat |
|---------|----------|
| **Individus analysés** | 31 249 communes |
| **Variables actives** | 11 quantitatives |
| **Axes retenus** | 4 (critère Kaiser) |
| **Inertie expliquée (4 axes)** | 63.30% |
| **Inertie plan 1-2** | 40.80% |
| **Variable la + contributive Axe 1** | `taux_proprietaires` (24.55%) |
| **Variable la + contributive Axe 2** | `pct_services` (17.28%) |
| **Opposition principale Axe 1** | Stable/aisé vs Précaire |
| **Opposition principale Axe 2** | Urbain/tertiaire vs Rural/agricole |
| **Profils identifiés** | 4 (urbain aisé, urbain populaire, rural stable, rural fragile) |

---

### PICCI - Les 5 étapes
| Lettre | Étape | Action |
|--------|-------|--------|
| **P** | Préparation | Charger, nettoyer, centrer-réduire |
| **I** | Inertie | Valeurs propres, scree plot |
| **C** | Cercle | Corrélations variables-axes |
| **C** | Contributions | Qui contribue à quoi ? |
| **I** | Individus | Projection des observations |

### COS² = "Combien On Se fie"
- cos² proche de 1 → **bien représenté** ✅
- cos² proche de 0 → **mal représenté** ⚠️
- **Interprétation** : qualité de la projection sur le plan

### CTR = "Combien Tu Représentes"
- CTR > 100/p → **forte contribution**
- CTR = 100/p → **contribution moyenne**
- CTR < 100/p → **faible contribution**
- **Seuil pour 12 variables** : 100/12 = **8,3%**

### Règle du COUDE
> Le coude = là où la courbe d'inertie **"casse"**

C'est le nombre d'axes à retenir visuellement sur l'éboulis.

### FaCoCo GPS - Les packages
| Mnémo | Package | Rôle |
|-------|---------|------|
| **Fa** | FactoMineR | Moteur ACP |
| **Co** | factoextra | Beaux graphiques |
| **Co** | corrplot | Matrices corrélation |
| **G** | ggplot2 | Graphiques avancés |
| **P** | psych | Stats descriptives |
| **S** | skimr | Résumé données |

### Lecture du cercle
| Configuration | Signification |
|---------------|---------------|
| Variables **longues** | Bien représentées |
| Variables **proches** | Corrélées (+) |
| Variables **opposées** | Corrélées (-) |
| Variables **perpendiculaires** | Non corrélées |

---

## � COURS COMPLET : LA RECETTE DE L'ACP (POUR LA PRÉSENTATION)

### 🎯 Qu'est-ce que l'ACP ?

> **Définition officielle (cours) :**
> L'**Analyse en Composantes Principales (ACP)** est une méthode statistique d'analyse multivariée qui transforme des variables quantitatives **corrélées** en nouvelles variables **non corrélées** appelées **composantes principales**, ordonnées par variance décroissante.

**En langage simple :**
> L'ACP est une méthode qui permet de **résumer** beaucoup de variables en quelques axes synthétiques, en perdant le moins d'information possible.

**Métaphore de la photo :**
> Imaginez un objet 3D (une sculpture). L'ACP cherche les meilleurs **angles de vue** (les axes) pour prendre une photo 2D qui capture le maximum de l'objet. La première photo (axe 1) montre le plus de détails, la deuxième (axe 2) montre des détails différents, etc.

---

### 📊 Les 5 étapes de l'ACP : "PICCI"

| Étape | Mnémonique | Action | Question clé |
|-------|------------|--------|--------------|
| **1** | **P**réparation | Charger, nettoyer, centrer-réduire | "Mes données sont-elles prêtes ?" |
| **2** | **I**nertie | Calculer les valeurs propres | "Combien d'axes garder ?" |
| **3** | **C**ercle | Analyser les corrélations variables-axes | "Que signifient les axes ?" |
| **4** | **C**ontributions | Identifier qui contribue à quoi | "Quelles variables/individus sont importants ?" |
| **5** | **I**ndividus | Projeter et interpréter les observations | "Quels sont les profils ?" |

---

### 📖 ÉTAPE 1 : PRÉPARATION (P)

#### 🔧 Quoi faire ?
1. **Charger les données** : tableau individus × variables
2. **Nettoyer** : supprimer les NA, les outliers aberrants
3. **Sélectionner** : garder uniquement les variables quantitatives
4. **Centrer-réduire** : standardiser les données

#### 📚 Définition : Centrage-Réduction

**Centrer** une variable X :
$$X_{centré} = X - \bar{X}$$

**Réduire** une variable X :
$$X_{réduit} = \frac{X - \bar{X}}{\sigma_X}$$

| Avant | Après |
|-------|-------|
| Moyenne ≠ 0 | Moyenne = 0 |
| Écart-type variable | Écart-type = 1 |
| Unités différentes | Variables comparables |

#### 🔄 Pourquoi centrer-réduire ?

**Exemple concret :**
- Revenu médian : 18 000 € à 50 000 € (variance = millions)
- Taux de chômage : 0% à 30% (variance = centaines)

Sans standardisation, le revenu dominerait l'analyse car ses valeurs sont plus grandes !

**Code R :**
```r
# Chargement et nettoyage
insee <- read.csv("base_cc_comparateur.csv", sep = ";")
df_acp <- na.omit(insee[, variables_quanti])

# L'ACP avec FactoMineR centre-réduit automatiquement
res.acp <- PCA(df_acp, scale.unit = TRUE)  # scale.unit = TRUE = centrer-réduire
```

---

### 📖 ÉTAPE 2 : INERTIE (I) - Valeurs propres

#### 🔧 Quoi faire ?
Calculer les **valeurs propres** (eigenvalues) et décider **combien d'axes garder**.

#### 📚 Définition : Valeur propre (λ)

> La **valeur propre** $\lambda_k$ de l'axe k représente la **variance de la k-ième composante principale**.

**Propriétés :**
- $\lambda_1 \geq \lambda_2 \geq ... \geq \lambda_p \geq 0$ (ordre décroissant)
- $\sum_{k=1}^{p} \lambda_k = p$ (en ACP normée)
- % d'inertie de l'axe k = $\frac{\lambda_k}{p} \times 100$

#### 🎯 Critères de sélection du nombre d'axes

| Critère | Règle | Notre cas (11 variables) |
|---------|-------|--------------------------|
| **Kaiser** | Garder si $\lambda > 1$ | 4 axes (λ₁=2.29, λ₂=2.20, λ₃=1.36, λ₄=1.12) |
| **Coude** | Cassure visuelle dans l'éboulis | Coude après l'axe 2 ou 4 |
| **% cumulé** | Viser 70-80% d'inertie | 63.3% avec 4 axes, 71.9% avec 5 axes |
| **Bâton brisé** | Comparer à l'aléatoire | 2-4 axes selon rigueur |

#### 🔄 Traduction du graphique "Éboulis" (Scree plot)

![Éboulis](images/02_eboulis_valeurs_propres.png)

**Ce que vous voyez :**
- Barres décroissantes = % de variance par axe
- Courbe = % cumulé

**Comment lire :**
1. L'axe 1 capture **20.82%** de l'information totale
2. L'axe 2 en capture **19.98%** de plus
3. Ensemble (plan 1-2) = **40.80%**
4. Les 4 premiers axes = **63.30%**

**🔄 Traduction :**
> "Si je regarde mes 31 249 communes sur le plan 1-2, je vois environ 40% de ce qui les différencie. Les 60% restants sont sur les autres axes (3, 4, ..., 11)."

---

### 📖 ÉTAPE 3 : CERCLE DES CORRÉLATIONS (C)

#### 🔧 Quoi faire ?
Analyser les **corrélations entre variables et axes** pour **nommer les axes**.

#### 📚 Définition : Coordonnée d'une variable sur un axe

La coordonnée de la variable $X_j$ sur l'axe $F_k$ est égale à leur corrélation :
$$coord_j(F_k) = cor(X_j, F_k) = \sqrt{\lambda_k} \times v_{jk}$$

**Interprétation :**
- coord proche de +1 : variable très corrélée positivement à l'axe
- coord proche de -1 : variable très corrélée négativement
- coord proche de 0 : variable non liée à cet axe

#### 🔄 Traduction du graphique "Cercle des corrélations"

![Cercle](images/04_cercle_correlations.png)

**Ce que vous voyez :**
- Un cercle de rayon 1
- Des flèches (vecteurs) partant du centre
- Chaque flèche = une variable

**Règles de lecture :**

| Observation | Signification | Exemple |
|-------------|---------------|---------|
| Flèche **longue** (proche du cercle) | Variable bien représentée | `pct_services` |
| Flèche **courte** | Variable mal représentée sur CE plan | `taux_natalite` |
| 2 flèches **proches** | Variables corrélées positivement | `taux_chomage` et `taux_mortalite` |
| 2 flèches **opposées** (180°) | Variables corrélées négativement | `pct_services` et `pct_agriculture` |
| 2 flèches **perpendiculaires** (90°) | Variables non corrélées | `densite_pop` et `taux_natalite` |

**🔄 Traduction de notre cercle :**

> **Axe 1 (horizontal) = "Stabilité socio-économique"**
> - À droite (+) : chômage, mortalité → communes **fragiles**
> - À gauche (-) : propriétaires, revenus → communes **stables**
>
> **Axe 2 (vertical) = "Typologie territoriale"**
> - En haut (+) : agriculture, logements vacants → communes **rurales**
> - En bas (-) : services, densité → communes **urbaines**

---

### 📖 ÉTAPE 4 : CONTRIBUTIONS (C)

#### 🔧 Quoi faire ?
Identifier quelles variables/individus **fabriquent** les axes.

#### 📚 Définition : Contribution (CTR)

La contribution de la variable j à l'axe k :
$$CTR_j(F_k) = \frac{coord_j(F_k)^2}{\lambda_k} \times 100$$

**Propriétés :**
- Somme des CTR de toutes les variables = 100%
- Seuil théorique = $\frac{100}{p}$ (contribution uniforme)
- Pour p = 11 variables : seuil = **9.1%**

#### 📚 Définition : Cos² (Qualité de représentation)

Le cos² de la variable j sur l'axe k :
$$cos^2_j(F_k) = coord_j(F_k)^2$$

**Interprétation :**
- cos² proche de 1 : variable **parfaitement** représentée sur cet axe
- cos² proche de 0 : variable **invisible** sur cet axe

**Différence CTR vs cos² :**

| Indicateur | Question | Somme = 100% sur... |
|------------|----------|---------------------|
| **CTR** | "Cette variable fabrique-t-elle l'axe ?" | Les variables |
| **cos²** | "Cette variable est-elle visible sur l'axe ?" | Les axes |

#### 🔄 Traduction du graphique "Contributions"

![Contributions](images/07_contrib_dim1.png)

**Ce que vous voyez :**
- Barres horizontales = contribution de chaque variable
- Ligne rouge = seuil de 9.1%

**🔄 Traduction :**
> "`taux_proprietaires` (24.55%) et `taux_chomage` (21.60%) **fabriquent** l'axe 1. À elles deux, elles représentent 46% de l'axe. Ce sont les variables **leaders** de la dimension sociale."

---

### 📖 ÉTAPE 5 : INDIVIDUS (I)

#### 🔧 Quoi faire ?
Projeter les individus (communes) et identifier les **profils-types**.

#### 📚 Définition : Coordonnée d'un individu

La coordonnée de l'individu i sur l'axe k :
$$F_{ik} = \sum_{j=1}^{p} x_{ij}^* \times v_{jk}$$

où $x_{ij}^*$ = valeur centrée-réduite de l'individu i pour la variable j.

#### 🔄 Traduction du graphique "Nuage des individus"

![Individus](images/11_individus_cos2.png)

**Ce que vous voyez :**
- Chaque point = une commune
- Position = coordonnées sur les axes
- Couleur = qualité de représentation (cos²)

**Règle de lecture :**
> Un individu dans la direction d'une variable a des **valeurs élevées** pour cette variable.

**🔄 Traduction des 4 quadrants :**

| Position | Axe 1 | Axe 2 | Profil | Exemple |
|----------|-------|-------|--------|---------|
| Haut-Gauche | Stable (-) | Rural (+) | **Rural stable** | Village breton propriétaire |
| Haut-Droit | Précaire (+) | Rural (+) | **Rural fragile** | Village du Cantal déserté |
| Bas-Gauche | Stable (-) | Urbain (-) | **Urbain aisé** | Neuilly-sur-Seine |
| Bas-Droit | Précaire (+) | Urbain (-) | **Urbain populaire** | Roubaix |

---

### 📊 TRADUCTION COMPLÈTE DES 16 GRAPHIQUES

#### 📷 Image 1 : Matrice de corrélation
**Ce que c'est :** Tableau des corrélations entre toutes les paires de variables.
**Ce que ça montre :** Les liaisons linéaires avant l'ACP.
**Pourquoi c'est utile :** Vérifie qu'il y a des corrélations (sinon ACP inutile).
**Traduction :** "Services et agriculture sont fortement opposés (r = -0.72). Propriétaires et chômage aussi (r = -0.56). L'ACP va pouvoir créer des axes synthétiques."

#### 📷 Image 2 : Éboulis des valeurs propres
**Ce que c'est :** Barres montrant le % de variance par axe.
**Ce que ça montre :** L'importance relative de chaque axe.
**Pourquoi c'est utile :** Décide du nombre d'axes à garder.
**Traduction :** "L'axe 1 (20.8%) et l'axe 2 (20.0%) sont quasi-équivalents. Ensemble ils capturent 40.8%. On garde 4 axes (63.3%)."

#### 📷 Image 3 : Bâton brisé
**Ce que c'est :** Comparaison de nos valeurs propres avec l'aléatoire.
**Ce que ça montre :** Si nos axes sont "meilleurs que le hasard".
**Pourquoi c'est utile :** Validation statistique du nombre d'axes.
**Traduction :** "Nos 4 premiers axes dépassent légèrement le seuil aléatoire. La structure n'est pas ultra-marquée mais significative."

#### 📷 Image 4 : Cercle des corrélations (Dim1-Dim2)
**Ce que c'est :** Variables projetées dans le plan principal.
**Ce que ça montre :** Les relations variables-axes et inter-variables.
**Pourquoi c'est utile :** Nommer et interpréter les axes.
**Traduction :** "L'axe 1 oppose propriétaires (gauche) à chômage (droite) = dimension sociale. L'axe 2 oppose services (bas) à agriculture (haut) = dimension territoriale."

#### 📷 Image 5 : Cercle avec contributions
**Ce que c'est :** Cercle coloré par la contribution au plan.
**Ce que ça montre :** Quelles variables fabriquent les axes.
**Pourquoi c'est utile :** Identifier les variables leaders.
**Traduction :** "Rouge = forte contribution. `pct_services`, `taux_proprietaires`, `taux_chomage` construisent le plan."

#### 📷 Image 6 : Cercle avec cos²
**Ce que c'est :** Cercle coloré par la qualité de représentation.
**Ce que ça montre :** Quelles variables sont bien projetées.
**Pourquoi c'est utile :** Savoir quelles variables interpréter.
**Traduction :** "Bleu = mal représenté. `taux_natalite` et `pct_industrie` ne sont pas interprétables sur ce plan."

#### 📷 Image 7 : Contributions axe 1
**Ce que c'est :** Barres des contributions à l'axe 1.
**Ce que ça montre :** Qui fabrique la dimension 1.
**Pourquoi c'est utile :** Nommer l'axe 1.
**Traduction :** "`taux_proprietaires` (24.6%) et `taux_chomage` (21.6%) dominent. Axe 1 = stabilité socio-économique."

#### 📷 Image 8 : Contributions axe 2
**Ce que c'est :** Barres des contributions à l'axe 2.
**Ce que ça montre :** Qui fabrique la dimension 2.
**Pourquoi c'est utile :** Nommer l'axe 2.
**Traduction :** "`pct_services` (17.3%) et `pct_agriculture` (16.6%) dominent. Axe 2 = typologie territoriale."

#### 📷 Image 9 : Contributions plan 1-2
**Ce que c'est :** Synthèse des contributions aux deux axes.
**Ce que ça montre :** Les variables structurantes globalement.
**Pourquoi c'est utile :** Vue d'ensemble.
**Traduction :** "6 variables font 70% du plan. `natalite` et `industrie` sont négligeables sur ce plan."

#### 📷 Image 10 : Qualité cos² des variables
**Ce que c'est :** Barres de qualité de représentation.
**Ce que ça montre :** Fiabilité de l'interprétation.
**Pourquoi c'est utile :** Éviter les erreurs d'interprétation.
**Traduction :** "4 variables ont cos² > 0.5 (fiables). 2 variables ont cos² < 0.15 (à éviter)."

#### 📷 Image 11 : Nuage des individus
**Ce que c'est :** 31 249 communes projetées.
**Ce que ça montre :** La dispersion des territoires.
**Pourquoi c'est utile :** Identifier groupes et atypiques.
**Traduction :** "Nuage étiré = forte variabilité sociale. Points extrêmes = métropoles et villages déserts."

#### 📷 Image 12 : Individus sélectionnés (cos² > 0.5)
**Ce que c'est :** Communes bien représentées uniquement.
**Ce que ça montre :** Les profils les plus marqués.
**Pourquoi c'est utile :** Focus sur l'interprétable.
**Traduction :** "27% des communes sont 'très lisibles' sur ce plan. Ce sont celles aux profils extrêmes."

#### 📷 Image 13 : Top 30 contributeurs axe 1
**Ce que c'est :** Communes qui tirent l'axe 1.
**Ce que ça montre :** Les individus influents.
**Pourquoi c'est utile :** Comprendre qui oriente l'analyse.
**Traduction :** "Paris, Lyon, Marseille pèsent lourd. Les métropoles orientent l'axe urbain/rural."

#### 📷 Image 14 : Biplot
**Ce que c'est :** Individus + variables superposés.
**Ce que ça montre :** Qui a quoi.
**Pourquoi c'est utile :** Interprétation conjointe.
**Traduction :** "Communes vers `pct_services` = urbaines tertiaires. Communes vers `pct_agriculture` = rurales."

#### 📷 Image 15 : Heatmap corrélations axes
**Ce que c'est :** Tableau coloré des corrélations variable-axe.
**Ce que ça montre :** La signification de chaque axe (1 à 5).
**Pourquoi c'est utile :** Nommer les 4 axes.
**Traduction :** "Axe 1 = social, Axe 2 = territorial, Axe 3 = démographie, Axe 4 = industrie."

#### 📷 Image 16 : Cercle Dim1-Dim3
**Ce que c'est :** Plan alternatif pour les mal représentés.
**Ce que ça montre :** L'information sur l'axe 3.
**Pourquoi c'est utile :** Compléter l'analyse des variables invisibles en 1-2.
**Traduction :** "`taux_natalite` est maintenant visible (cos² = 0.42). L'axe 3 capture la démographie."

---

## 🎓 QUESTIONS DE PRÉSENTATION ET RÉPONSES

### ❓ Questions sur les définitions

**Q1 : Qu'est-ce que l'ACP ?**
> "L'ACP est une méthode qui transforme des variables corrélées en nouvelles variables non corrélées appelées composantes principales, ordonnées par variance décroissante. Elle permet de réduire la dimensionnalité tout en conservant le maximum d'information."

**Q2 : Qu'est-ce qu'une valeur propre ?**
> "La valeur propre λ_k représente la variance de la k-ième composante principale. Elle mesure la quantité d'information capturée par cet axe. En ACP normée, la somme des valeurs propres égale le nombre de variables."

**Q3 : Qu'est-ce que l'inertie ?**
> "L'inertie est la variance totale du nuage de points. C'est la somme de toutes les valeurs propres. L'inertie d'un axe est le pourcentage de cette variance totale qu'il capture."

**Q4 : Quelle est la différence entre CTR et cos² ?**
> "La **contribution (CTR)** mesure combien une variable **fabrique** un axe. Le **cos²** mesure combien une variable est **représentée** par un axe. CTR répond à 'qui construit l'axe ?', cos² répond à 'qui est visible sur l'axe ?'"

**Q5 : Pourquoi centrer-réduire les données ?**
> "Pour mettre toutes les variables sur la même échelle. Sans ça, une variable en euros (milliers) dominerait une variable en % (dizaines). Le centrage-réduction rend les variables comparables."

---

### ❓ Questions sur les critères

**Q6 : Comment choisir le nombre d'axes ?**
> "Trois critères principaux :
> 1. **Kaiser** : garder les axes avec λ > 1
> 2. **Coude** : repérer la cassure dans l'éboulis
> 3. **% cumulé** : viser 70-80% d'inertie
> Dans notre cas, les 3 critères convergent vers 4 axes (63.3%)."

**Q7 : Qu'est-ce que le critère de Kaiser ?**
> "On garde les axes dont la valeur propre est supérieure à 1. Justification : un axe doit capturer au moins autant d'information qu'une variable seule (qui a une variance de 1 après standardisation)."

**Q8 : Qu'est-ce que le critère du bâton brisé ?**
> "On compare nos valeurs propres à celles attendues sous l'hypothèse nulle (pas de structure). Si notre λ dépasse le seuil aléatoire, l'axe est significatif. C'est plus conservateur que Kaiser."

---

### ❓ Questions sur l'interprétation

**Q9 : Comment interpréter le cercle des corrélations ?**
> "Chaque flèche représente une variable. Sa **longueur** indique la qualité de représentation. Sa **direction** indique la corrélation avec les axes. Deux flèches proches = variables corrélées positivement. Opposées = négativement. Perpendiculaires = non corrélées."

**Q10 : Comment nommer un axe ?**
> "On regarde les variables qui y contribuent le plus (CTR élevé) et on cherche le concept commun qui les relie. Par exemple, si 'propriétaires' et 'revenus' sont à gauche, et 'chômage' à droite, l'axe oppose stabilité et précarité."

**Q11 : Que faire si une variable a un cos² faible ?**
> "Ne pas l'interpréter sur ce plan ! Un cos² faible signifie que la variable est mal représentée ICI, pas qu'elle est inutile. Il faut regarder sur quels autres axes elle a un cos² élevé."

**Q12 : Comment interpréter le biplot ?**
> "Sur le biplot, un individu dans la direction d'une variable a des valeurs élevées pour cette variable. Un individu opposé a des valeurs faibles. Un individu perpendiculaire a des valeurs moyennes."

---

### ❓ Questions sur notre analyse

**Q13 : Que signifie l'axe 1 dans notre analyse ?**
> "L'axe 1 (20.8%) est un axe de **stabilité socio-économique**. Il oppose les communes stables (propriétaires, revenus élevés, services) aux communes fragiles (chômage, mortalité, logements vacants)."

**Q14 : Que signifie l'axe 2 ?**
> "L'axe 2 (20.0%) est un axe de **typologie territoriale**. Il oppose les communes urbaines (services, densité) aux communes rurales (agriculture, logements vacants)."

**Q15 : Pourquoi le plan 1-2 n'explique que 40% ?**
> "Parce que nos données ont une structure complexe : les 11 variables ne se résument pas à 2 dimensions. Il faut 4 axes pour capturer 63% de l'information. C'est pourquoi on analyse aussi les axes 3 (démographie) et 4 (industrie)."

**Q16 : Quelles variables sont mal représentées sur le plan 1-2 ?**
> "`taux_natalite` (cos² = 0.03) et `pct_industrie` (cos² = 0.03). Ces variables varient sur les axes 3 et 4 respectivement. Il ne faut pas les interpréter sur le plan 1-2."

**Q17 : Quels sont les 4 profils de communes identifiés ?**
> "1. **Urbain aisé** (bas-gauche) : services, revenus, propriétaires
> 2. **Urbain populaire** (bas-droit) : services mais chômage
> 3. **Rural stable** (haut-gauche) : agriculture, propriétaires
> 4. **Rural fragile** (haut-droit) : agriculture, vacance, vieillissement"

---

### ❓ Questions sur la méthode

**Q18 : Pourquoi l'ACP et pas l'AFC ou l'ACM ?**
> "L'ACP est pour les variables **quantitatives continues** (taux, pourcentages, euros). L'AFC est pour les **tableaux de contingence** (croisement de 2 variables qualitatives). L'ACM est pour les variables **qualitatives** (catégories). Nos données sont quantitatives, donc ACP."

**Q19 : Quelles sont les limites de l'ACP ?**
> "1. **Linéarité** : ne détecte que les relations linéaires
> 2. **Sensibilité aux outliers** : les valeurs extrêmes influencent les axes
> 3. **Interprétation subjective** : nommer les axes est un choix
> 4. **Perte d'info** : on ne garde pas 100% de la variance"

**Q20 : Pourrait-on compléter cette analyse ?**
> "Oui, avec :
> - Une **CAH** (Classification Ascendante Hiérarchique) pour grouper les communes
> - Une variable qualitative **illustrative** (région, département) pour colorer les groupes
> - Une analyse des **axes 3 et 4** pour les variables mal représentées"

---

### ❓ Questions pièges

**Q21 : Si deux variables sont perpendiculaires sur le cercle, sont-elles vraiment non corrélées ?**
> "Attention ! L'angle entre deux variables sur le cercle n'approxime leur corrélation que si elles sont **bien représentées** sur le plan (cos² élevé). Si une variable a un faible cos², la règle ne s'applique pas."

**Q22 : Un individu au centre du nuage est-il "moyen" ?**
> "Pas forcément ! Il peut être au centre pour 2 raisons :
> 1. Il a vraiment des valeurs moyennes sur toutes les variables
> 2. Il est **mal représenté** sur ce plan (cos² faible) et ses caractéristiques sont sur d'autres axes"

**Q23 : Peut-on comparer les CTR de deux axes différents ?**
> "Non directement. Une CTR de 20% sur l'axe 1 (λ=2.29) n'a pas le même impact qu'une CTR de 20% sur l'axe 4 (λ=1.12). L'axe 1 est plus important globalement."

---

## 📋 CHECKLIST AVANT PRÉSENTATION

### ✅ Je maîtrise les définitions
- [ ] ACP = transformation de variables corrélées en composantes non corrélées
- [ ] Valeur propre = variance d'une composante principale
- [ ] Inertie = variance totale
- [ ] CTR = contribution à la construction d'un axe
- [ ] cos² = qualité de représentation sur un axe
- [ ] Centrage = soustraire la moyenne
- [ ] Réduction = diviser par l'écart-type

### ✅ Je sais interpréter les graphiques
- [ ] Éboulis : choisir le nombre d'axes (coude, Kaiser)
- [ ] Cercle : nommer les axes (flèches longues = bien représentées)
- [ ] Contributions : identifier les variables leaders (> 9.1%)
- [ ] Nuage : identifier les profils-types (quadrants)
- [ ] Biplot : lire qui a quoi (direction = valeur élevée)

### ✅ Je connais les critères
- [ ] Kaiser : λ > 1
- [ ] Coude : cassure visuelle
- [ ] % cumulé : viser 70-80%
- [ ] Bâton brisé : comparaison à l'aléatoire
- [ ] Seuil CTR : 100/p = 100/11 = 9.1%
- [ ] Seuil cos² : > 0.5 = bonne représentation

### ✅ Je connais les résultats de mon analyse
- [ ] 31 249 communes, 11 variables
- [ ] 4 axes retenus, 63.3% d'inertie
- [ ] Axe 1 = stabilité socio-économique (20.8%)
- [ ] Axe 2 = typologie territoriale (20.0%)
- [ ] Axe 3 = dynamisme démographique (12.3%)
- [ ] Axe 4 = tissu industriel (10.2%)
- [ ] 4 profils : urbain aisé, urbain populaire, rural stable, rural fragile

### ✅ Je sais répondre aux questions pièges
- [ ] Angle = corrélation seulement si cos² élevé
- [ ] Centre du nuage ≠ forcément "moyen"
- [ ] CTR non comparables entre axes
- [ ] Variables mal représentées → regarder autres axes

---

## 📁 Structure du projet

```
ACPCCM1/
├── README.md                          # Ce fichier
├── base_cc_comparateur.csv            # Données INSEE (8 MB)
├── meta_base_cc_comparateur.csv       # Dictionnaire des variables
├── base_cc_comparateur_csv.zip        # Archive source
├── images/                            # 16 graphiques PNG
│   ├── 01_matrice_correlation.png
│   ├── 02_eboulis_valeurs_propres.png
│   ├── 03_baton_brise.png
│   ├── 04_cercle_correlations.png
│   ├── 05_cercle_contribution.png
│   ├── 06_cercle_cos2.png
│   ├── 07_contrib_dim1.png
│   ├── 08_contrib_dim2.png
│   ├── 09_contrib_plan12.png
│   ├── 10_cos2_variables.png
│   ├── 11_individus_cos2.png
│   ├── 12_individus_selection.png
│   ├── 13_top_contrib_dim1.png
│   ├── 14_biplot.png
│   ├── 15_correlation_axes.png
│   └── 16_cercle_dim1_dim3.png
└── data/
    └── PCA/
        ├── ACP_INSEE_Communes.R       # Script R principal
        └── generate_plots.R           # Génération des graphiques
```

---

## 📚 Références

1. **Cours E. Périnel** - M1 Statistique, 2024-2025
2. **INSEE** - Base du comparateur de territoires
   - https://www.insee.fr/fr/statistiques/2521169
3. **FactoMineR** - Documentation
   - http://factominer.free.fr/
4. **factoextra** - Package R
   - https://rpkgs.datanovia.com/factoextra/

---

## ✍️ Auteur
Cheriet Abdelmalek M1 Statistique - Université de Strasbourg

Date : Janvier 2025
