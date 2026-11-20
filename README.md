
# 🏠 Projet – Base Adresse Nationale (BAN)

![PostgreSQL](https://img.shields.io/badge/PostgreSQL-Database-4169E1?logo=postgresql&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-Environment-2496ED?logo=docker&logoColor=white)
![SQL](https://img.shields.io/badge/SQL-Database%20Design-orange)
![MERISE](https://img.shields.io/badge/M%C3%A9thode-MERISE-green)
![Status](https://img.shields.io/badge/Statut-En%20cours-yellow)

## 📌 Présentation du projet

Ce projet consiste à concevoir et mettre en place une base de données relationnelle à partir des données de la **Base Adresse Nationale (BAN)**.

Réalisé dans le cadre de la formation **Concepteur Développeur d'Applications (CDA)** chez Simplon, il a pour objectif d'exploiter un jeu de données réel et volumineux afin de mettre en pratique les compétences en conception, modélisation et administration de bases de données.

Le projet s'appuie sur la méthode **MERISE** pour concevoir un modèle de données cohérent, normalisé et optimisé, exploitable par une future application.

Le jeu de données utilisé correspond au département du **Nord (59)**.

## 🎯 Objectifs du projet

- Découvrir et analyser un jeu de données réel au format CSV.
- Identifier les entités, associations et dépendances fonctionnelles.
- Concevoir un modèle conceptuel de données (MCD).
- Décliner le modèle logique de données (MLD).
- Construire le modèle physique de données (MPD).
- Normaliser et optimiser la structure relationnelle.
- Mettre en place les contraintes d'intégrité et les index.
- Importer et transformer les données brutes vers un modèle normalisé.
- Développer des requêtes SQL d'analyse.
- Implémenter des procédures stockées et des triggers.
- Documenter et versionner l'ensemble du projet.

## 🗂️ Source des données

Les données proviennent de la **Base Adresse Nationale (BAN)**, référentiel national des adresses en France.

- **Source officielle :** https://adresse.data.gouv.fr/
- **Téléchargement CSV :** https://adresse.data.gouv.fr/data/ban/adresses/latest/csv/
- **Fichier étudié :** `adresses-59.csv`
- **Département :** Nord (59)

Le fichier CSV original est conservé localement et n'est pas versionné dans ce dépôt en raison de son volume.

## 🛠️ Environnement technique

| Technologie | Utilisation |
|---|---|
| PostgreSQL | Système de gestion de base de données relationnelle |
| Docker | Conteneurisation de PostgreSQL |
| Docker Compose | Configuration et orchestration des conteneurs |
| DBeaver | Interface graphique d'administration et d'exécution SQL |
| Visual Studio Code | Édition des scripts SQL et documentation |
| Git | Gestion de versions |
| GitHub | Hébergement et partage du projet |
| MERISE | Méthode de modélisation des données |

## 🏗️ Architecture du projet

L'environnement repose sur PostgreSQL exécuté dans un conteneur Docker.

DBeaver permet de se connecter à la base pour effectuer les opérations d'administration et tester les requêtes SQL.

Visual Studio Code est utilisé pour développer, organiser et versionner les scripts SQL.

```text
CSV BAN (adresses-59.csv)
          |
          v
   Importation brute
          |
          v
     PostgreSQL
       (Docker)
          |
          v
  Transformation SQL
          |
          v
 Base relationnelle
   normalisée
          |
     +----+----+
     |         |
     v         v
 DBeaver    VS Code
     |         |
     +----+----+
          |
          v
        GitHub
```

## 📁 Organisation du dépôt

```text
projet-banque-adresses_TD/
│
├── README.md
├── compose.yml
├── .gitignore
│
├── data/
│   ├── raw/
│   └── processed/
│
├── documentation/
│   ├── presentation_projet.md
│   ├── dictionnaire_donnees.md
│   ├── regles_gestion.md
│   ├── rapport_questionnement.md
│   └── schemas/
│       ├── MCD.png
│       ├── MLD.png
│       └── MPD.png
│
├── sql/
│   ├── 01_creation_tables.sql
│   ├── 02_import_brut.sql
│   ├── 03_migration.sql
│   ├── 04_index.sql
│   ├── 05_requetes_analyse.sql
│   ├── 06_procedures.sql
│   └── 07_triggers.sql
│
├── tests/
│   ├── tests_coherence.sql
│   └── tests_performance.sql
│
└── screenshots/
```

### Description des dossiers

| Dossier | Description |
|---|---|
| `data/` | Données brutes et transformées |
| `documentation/` | Documentation et modélisation MERISE |
| `sql/` | Scripts de création, migration et analyse |
| `tests/` | Tests de cohérence et de performance |
| `screenshots/` | Captures d'écran des réalisations |

## 🗄️ Modélisation MERISE

La conception de la base de données suit les trois niveaux de modélisation de la méthode MERISE.

### MCD – Modèle Conceptuel de Données

Identification des entités, associations, cardinalités et règles de gestion.

### MLD – Modèle Logique de Données

Traduction du modèle conceptuel en relations, avec identification des clés primaires et étrangères.

### MPD – Modèle Physique de Données

Implémentation du modèle dans PostgreSQL avec définition des types, contraintes, index et relations.

Les schémas seront disponibles dans `documentation/schemas/`.

## ⚙️ Installation et démarrage

### Prérequis

- Docker installé et opérationnel.
- Docker Compose.
- DBeaver.
- Visual Studio Code.
- Git.

### 1. Cloner le dépôt

```bash
git clone git@github.com:SIMPLON-DIST-CDA-P9-200473/projet-banque-adresses_TD.git

cd projet-banque-adresses_TD
```

### 2. Configurer l'environnement Docker

Le fichier `compose.yml` définit les services nécessaires au fonctionnement de la base PostgreSQL.

Vérifier la configuration :

```bash
docker compose config
```

### 3. Démarrer les conteneurs

```bash
docker compose up -d
```

Vérifier leur état :

```bash
docker compose ps
```

Consulter les journaux :

```bash
docker compose logs -f
```

### 4. Connexion avec DBeaver

Créer une nouvelle connexion PostgreSQL dans DBeaver avec les paramètres définis dans `compose.yml` :

- **Hôte :** localhost
- **Port :** port PostgreSQL exposé
- **Base de données :** selon la configuration Docker
- **Utilisateur :** selon la configuration Docker
- **Mot de passe :** selon la configuration Docker

### 5. Arrêter les conteneurs

```bash
docker compose down
```

Les données PostgreSQL sont conservées dans le volume Docker configuré, si celui-ci est utilisé.

## 🔎 Analyses SQL prévues

Les requêtes SQL permettront notamment de :

- Lister les adresses d'une commune en les triant par voie.
- Compter le nombre d'adresses par commune.
- Compter le nombre d'adresses par commune et par voie.
- Identifier les communes distinctes.
- Rechercher les voies contenant un mot-clé.
- Identifier les adresses dont le code postal est manquant alors que la commune est renseignée.

## ⚡ Optimisation et qualité des données

Plusieurs mécanismes seront étudiés et mis en œuvre :

- Normalisation jusqu'à la troisième forme normale (3NF), lorsque les dépendances fonctionnelles le permettent.
- Mise en place de clés primaires et étrangères.
- Contraintes d'unicité et d'intégrité.
- Gestion des valeurs manquantes et des doublons.
- Indexation des colonnes fréquemment recherchées.
- Mesure des performances avec `EXPLAIN ANALYZE`.

## 📦 Livrables attendus

1. Modélisation MERISE : MCD, MLD et MPD.
2. Rapport de questionnement et justification des choix de conception.
3. Scripts SQL de création des tables.
4. Script SQL de migration des données brutes vers le modèle normalisé (bonus).
5. Requêtes SQL d'analyse (bonus).

Des procédures stockées, triggers et tests complémentaires viendront enrichir le projet.

## 📊 État d'avancement

Projet en cours de réalisation.

## 👨‍💻 Auteur

Projet individuel réalisé dans le cadre de la formation **Concepteur Développeur d'Applications (CDA)**.

**Organisme de formation :** Simplon

**Dépôt GitHub :** https://github.com/SIMPLON-DIST-CDA-P9-200473/projet-banque-adresses_TD

---

*Projet pédagogique de conception et d'exploitation d'une base de données relationnelle à partir de données ouvertes de la Base Adresse Nationale.*
