# ✈️ Système de Gestion d’Aéroport  
### Projet Administration des Bases de Données – Oracle

## 📌 Description
Ce projet consiste en la conception et la mise en œuvre d’un **système de gestion d’aéroport**
permettant de centraliser et automatiser les opérations liées aux **vols, passagers,
réservations, avions et maintenance**.

L’objectif principal est de garantir une **gestion fiable, cohérente et sécurisée des données**
en appliquant des **règles métier strictes directement au niveau de la base de données**
à l’aide de **PL/SQL (triggers, procédures, fonctions)**, avec un backend Flask en support.

---

## 🎯 Objectifs du projet
- Concevoir une **base de données relationnelle robuste** sous Oracle
- Appliquer des **règles de gestion complexes** garantissant l’intégrité des données
- Mettre en place une **gestion des rôles et privilèges utilisateurs**
- Automatiser les processus métier via **triggers et procédures PL/SQL**
- Synchroniser les **états des entités** (avion, vol, réservation, maintenance)
- Fournir une base solide pour une **application backend (Flask)**

---

## 🧩 Fonctionnalités principales

### 👤 Gestion des passagers
- Enregistrement des passagers avec contraintes fortes
- Gestion des passagers mineurs avec obligation de **guardian**
- Vérification de l’unicité du passeport
- Validation des informations de contact

### 🎟️ Gestion des réservations
- Interdiction des réservations doubles pour un même vol
- Vérification de la capacité des vols
- Gestion automatique des états :
  - Pending
  - Confirmed
  - Cancelled
  - Boarded
- Annulation automatique des réservations en cas d’annulation du vol

### 🛫 Gestion des vols
- Création et planification des vols
- Interdiction des vols avec date passée
- Affectation unique d’un avion à un vol (pas de chevauchement temporel)
- Gestion des états :
  - Scheduled
  - In Service
  - Full
  - Cancelled
  - Finished

### ✈️ Gestion des avions
- Suivi de l’état des avions :
  - Ready
  - In Service
  - Maintenance
  - Out of Service
- Interdiction d’affecter un avion en maintenance à un vol
- Synchronisation automatique avec les vols et maintenances

### 🛠️ Gestion de la maintenance
- Planification des opérations de maintenance
- Changement automatique de l’état de l’avion
- Interdiction de vol tant que la maintenance n’est pas terminée
- États :
  - Scheduled
  - In Progress
  - Completed

---

## 📐 Modélisation & Architecture

### Diagramme de classes
Le système repose sur les entités suivantes :
- Passengers
- Flights
- Reservations
- Aircrafts
- Maintenance
- Employees

Les relations entre entités sont définies avec des **clés primaires et étrangères**
et des **cardinalités strictes** garantissant la cohérence des données.

---

## 🔐 Sécurité & gestion des accès
Le projet implémente une **gestion fine des rôles Oracle**, incluant :

- ADMIN_AEROPORT
- AGENT_ENREGISTREMENT
- AGENT_BILLETERIE
- AGENT_CONTROLE
- RESPONSABLE_VOLS
- RESPONSABLE_MAINTENANCE

Chaque rôle dispose de privilèges spécifiques (SELECT, INSERT, UPDATE, DELETE)
selon les tables accessibles.

---

## ⚙️ Règles métier implémentées (exemples)
- Un passager mineur doit obligatoirement avoir un guardian adulte
- Un guardian doit être inscrit sur le même vol que le mineur
- Un avion ne peut pas assurer deux vols simultanément
- Un avion en maintenance ne peut être affecté à aucun vol
- Un vol annulé entraîne automatiquement l’annulation de ses réservations
- Les transitions d’états sont contrôlées et validées par des triggers PL/SQL

---

## 🛠️ Technologies utilisées
- **Base de données** : Oracle SQL
- **Langage procédural** : PL/SQL
- **Backend** : FastApi (Python)
- **Frontend** : 
- **Automatisation** : Triggers, procédures, fonctions, transactions

---

