# 🎓 Système de Gestion Intégrée (SGI) - Club ITIRC ENSAO

Un système d'information complet développé pour la gestion administrative, financière et logistique du **Club ITIRC (École Nationale des Sciences Appliquées d'Oujda)**. Ce projet a été conçu dans le cadre du module académique de Python/SQL, en alliant modélisation de base de données avancée (MySQL) et développement d'une API backend robuste (FastAPI).

## 🎯 Objectif du Projet
Ce projet vise à numériser et centraliser l'organisation du club à travers son architecture en cellules. Il permet au Pilotage et au Bureau de gérer les membres, de suivre les cotisations mensuelles, et d'organiser efficacement les événements (comme la Journée de Filière) en assignant des tâches spécifiques à chaque cellule (Média, Formation, Rédaction, etc.).

## ✨ Fonctionnalités Principales
* **Gestion des Ressources Humaines :** Suivi des membres (3A, 4A, 5A), de leurs rôles hiérarchiques et de leur affectation aux différentes cellules spécialisées.
* **Suivi de Trésorerie :** Enregistrement des cotisations avec détection automatique des retards de paiement.
* **Gestion Événementielle :** Création d'événements, allocation de budget et assignation de tâches de préparation.
* **Audit et Sécurité (SQL) :** Traçabilité des actions sensibles assurée de manière autonome par le moteur de base de données via des Déclencheurs (`TRIGGERS`).

---

## 🏗️ Architecture du Projet (Domain-Driven Design)

Le projet adopte une architecture professionnelle de type **Domain-Driven Design (DDD)** couplée au **Repository Pattern**. Le code est strictement séparé entre l'infrastructure SQL et la logique métier Python.

### 1. Arborescence des Fichiers

```text
📁 SGI_Club_ITIRC/
│
├── 📁 infrastructure/                <-- PARTIE SQL (Livrable Base de données)
│   └── 📁 mysql_scripts/
│       ├── 📄 01_ddl_schema.sql      (Tables : Membres, Cellules...)
│       ├── 📄 02_views.sql           (Vues : Tableaux de bord)
│       ├── 📄 03_triggers.sql        (Déclencheurs : Audit et Sécurité)
│       └── 📄 04_procedures.sql      (Procédures : Processus automatisés)
│
├── 📁 src/                           <-- PARTIE PYTHON (API FastAPI)
│   ├── 📄 main.py                    (Point d'entrée du serveur)
│   │
│   ├── 📁 core/                      <-- Configurations de base
│   │   ├── 📄 database.py            (Connexion MySQL Singleton)
│   │   └── 📄 config.py              (Chargement des variables d'environnement)
│   │
│   └── 📁 domains/                   <-- LOGIQUE MÉTIER (Isolée par domaine)
│       │
│       ├── 📁 membres/               (Gestion RH et Cellules)
│       │   ├── 📄 router.py          (Endpoints HTTP)
│       │   ├── 📄 schemas.py         (Validation Pydantic)
│       │   ├── 📄 service.py         (Règles métier)
│       │   └── 📄 repository.py      (Exécution requêtes MySQL)
│       │
│       ├── 📁 tresorerie/            (Suivi financier)
│       │   └── ... (router, schemas, service, repository)
│       │
│       └── 📁 evenements/            (Organisation et Tâches)
│           └── ... (router, schemas, service, repository)
│
├── 📄 .env                           (Variables sensibles - DB_PASSWORD, etc.)
└── 📄 requirements.txt               (Dépendances du projet)
